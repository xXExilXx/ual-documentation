# UnityAudioLink System Documentation

## Main AudioLink Class

### Public Variables

- `audioSource`
  - The audio source to extract data from. Set this to the `AudioSource` component responsible for playing the music or sound in the scene.
  ```cpp
  // Example usage
  AudioLink audioLink = GetComponent<AudioLink>();
  audioLink.audioSource = myAudioSource;
  ```

- `subBassSmoothing`
  - Smoothing factor for sub-bass frequencies. Determines how quickly the amplitude values for sub-bass frequencies are smoothed over time. Higher values result in slower changes, providing a more stable output.
  ```cpp
  // Example usage
  audioLink.subBassSmoothing = 5.0f;
  ```

- `bassSmoothing`
  - Smoothing factor for bass frequencies.
  ```cpp
  // Example usage
  audioLink.bassSmoothing = 5.0f;
  ```

- `middleSmoothing`
  - Smoothing factor for middle frequencies.
  ```cpp
  // Example usage
  audioLink.middleSmoothing = 5.0f;
  ```

- `highSmoothing`
  - Smoothing factor for high frequencies.
  ```cpp
  // Example usage
  audioLink.highSmoothing = 5.0f;
  ```

- `fullRangeSmoothing`
  - Smoothing factor for the full frequency range.
  ```cpp
  // Example usage
  audioLink.fullRangeSmoothing = 5.0f;
  ```

### Public Methods

- `ReturnFreqency(targetFrequency)`
  - Returns the amplitude of the specified frequency range.
  ```cpp
  // Example usage
  float subBassAmplitude = audioLink.ReturnFreqency(AudioLink.FreqencyRange.SubBass);
  ```

- `ReturnFreqencySmoothed(targetFrequency)`
  - Returns the smoothed amplitude of the specified frequency range.
  ```cpp
  // Example usage
  float subBassAmplitudeSmoothed = audioLink.ReturnFreqencySmoothed(AudioLink.FreqencyRange.SubBass);
  ```

- `ReturnFrequencyBoolSmoothed(targetFrequency, sensivity, isClamped, threshold)`
  - Returns true if the amplitude of the selected frequency range is over the specified threshold.
  ```cpp
  // Example usage
  bool isSubBassLoud = audioLink.ReturnFrequencyBoolSmoothed(AudioLink.FreqencyRange.SubBass, 1.5f, true, 0.8f);
  ```

- `ReturnFrequencyBool(targetFrequency, sensivity, isClamped, threshold)`
  - Same as `ReturnFrequencyBoolSmoothed`, but unsmoothed.
  ```cpp
  // Example usage
  bool isSubBassLoud = audioLink.ReturnFrequencyBool(AudioLink.FreqencyRange.SubBass, 1.5f, true, 0.8f);
  ```

- `ReturnRawData()`
  - Returns an array containing raw audio data.
  ```cpp
  // Example usage
  float[] rawData = audioLink.ReturnRawData();
  ```

## BeatDetector Class

### Public Variables

- `audioLink`
  - The AudioLink component to which the BeatDetector is linked. Make sure to set this field in the Unity Editor to connect the BeatDetector with the AudioLink component.
  ```cpp
  // Example usage
  BeatDetector beatDetector = GetComponent<BeatDetector>();
  beatDetector.audioLink = myAudioLink;
  ```

### Methods

- `Beat()`
  - Returns a boolean value indicating whether a beat is currently detected. This method can be used in other scripts to synchronize game events with the music beat.
  ```cpp
  // Example usage
  if (BeatDetector.Beat())
  {
      // Perform actions on beat
  }
  ```

---

&copy; 2024 UnityAudioLink Documentation