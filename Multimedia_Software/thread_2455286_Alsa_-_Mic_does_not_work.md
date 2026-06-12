---
title: "Alsa - Mic does not work"
date: 2020-12-16
forum: Multimedia Software
---

### Post by mileva1010 on 2020-12-16
I'm starting to use ALSA and first I need to test my mic and  speakers. To test speakers I do speaker-test and I can hear the white noise coming  from my left and right speaker, and I obtain the following output:

 ```

speaker-test -c 2

speaker-test 1.1.3

Playback device is default
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 1048576
Period size range from 32 to 349526
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
 0 - Front Left
 1 - Front Right



``` To test mic, I record .wav file using:

```
 arecord -f S16_LE -d 10 -r 44100 -c 2  --device="hw:0,0" test-mic.wav

```
 However, when I play this file I don't hear anything. The file is not empty, and I can play it with aplay, but no sound.
 The output from alsamixer is shown on the two attached pics. 

I need to capture the sound from the internal mic. I don't know what I should change in order to be able to capture the sound from mic and ALSA properly. Thanks for your help.

---

