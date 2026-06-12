---
title: "Accessing webcam audio device while using it by another application"
date: 2015-02-17
forum: Multimedia Software
---

### Post by kami2 on 2015-02-17
Hi there! 

My USB webcam audio interface is visible and perfectly usable as hw:1,0. 

The problem is that I have two applications accessing the webcam simultaneously: openCV (python) and pyAudio. When openCV captures the frames and I start an audio recording via pyAudio, frame grapping crashes, while pyaudio does its job without disturbance. Is there an easy way to somehow channel the audio to a virtual device or something and access it there without bothering the cam in its normal operation? 

If there is no easy solution to this, a fix of the following would at least help a little: 
When I initiate a pyAudio recording, the webcam has to start first, which takes appr. 1s. Stopping the recording also shuts down the cam again which takes another second. This wouldn't be necessary if I could access the audio device while the webcam simply runs. Is there a way to do so? 

Thanks in advance! 
    Kami

---

