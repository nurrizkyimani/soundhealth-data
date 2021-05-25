# Extracting Spectrograms from Audio with Python
### _Sound spectrograms that are generated using a short-time Fourier transform and can be used in machine learning algorithms for sound classification._


Libraries used: 

- Librosa
- iPython
- Numpy
- Matplotlib


## Loading Audio Files

Audio files can be loaded and read using the librosa.load() function

```sh
librosa.load()
```
The function returns two things, which is the array of amplitudes and the sampling rates.

To play the audio files you can use the iPython.Audio() function to display the audio widget
```sh
ipd.Audio()
```
## Extracting Audio with Short-Time Fourier Transform

The audio that have been loaded previously was in the time domain. To better comprehend the audio signal, it is best to extract them into the time-frequency domain. The Short-Time Fourier Transform (STFT) represents the signal in the time-frequency domain by computing discrete Fourier transform over short overlapping windows.

```sh
librosa.stft(y, n_fft=2048, hop_length=None)
```
Parameters :
```sh
y : np.ndarray [shape=(n,)], real-valued
```
input signal
```sh
n_fft: int > 0 [scalar]
```
The default value, n_fft=2048 samples, corresponds to a physical duration of 93 milliseconds at a sample rate of 22050 Hz, i.e. the default sample rate in librosa. 
```sh
hop_length: int > 0 [scalar]
```
number of audio samples between adjacent STFT columns.

## Calculating Complex Number to Spectrogram

To calculate the spectrogram, we need to convert the complex number returned by the stft function to the squared magnitude of the absolute numbers of the result which will return the number of bins and number of frames in float that can be plotted to the spectrogram.


## Visualizing the Spectrogram

To visualize the spectrogram, we can use the librosa.display.specshow() function to visualize any type of spectrogram-like signal. The function expects the data in a matrix form to display, the sample rate, the hop length, the x axis and y axis.

```sh
librosa.display.specshow(data, sr=22050, hop_length=512, x_axis=None, y_axis=None)
```
