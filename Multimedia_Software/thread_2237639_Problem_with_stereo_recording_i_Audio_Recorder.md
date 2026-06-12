---
title: "Problem with stereo recording i Audio Recorder"
date: 2014-08-03
forum: Multimedia Software
---

### Post by Daniel_Strauss on 2014-08-03
When I try to record a .wav-file i audio-recorder the result always ends up in mono. The format is .WAV (lossless 44khz) and the audio source is Build-in Audio Analog Stereo.
Recording .flac with the same source gives me stereo but as soon as I change to .wav it results in mono.

---

### Post by ajgreeny on 2014-08-03
Same problem here when recording as a .wav.

I had not noticed this before as I always use either flac or mp3 depending on what I want the files for.
I have looked for a config file for the application but can not find anything so far, but surely there must be one somewhere.

---

### Post by osmoma on 2014-08-05
Hello,
You are absolutely right. The channels= attribute should be 2. I will fix this at least for Ubuntu 14.10.
Thanks for reporting this.

Please see:
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/view/head:/src/media-profiles.c)

It is fixed in the source code. Please study revision 354. 
[http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/revision/354](http://bazaar.launchpad.net/~osmoma/audio-recorder/trunk/revision/354)

$ file $HOME/Audio/*.wav
/home/xxx/Audio/2014-08-05-19:41:15.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 16 bit, **stereo** 44100 Hz
...

---

