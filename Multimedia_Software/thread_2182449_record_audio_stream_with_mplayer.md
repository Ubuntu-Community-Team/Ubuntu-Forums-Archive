---
title: "record audio stream with mplayer"
date: 2013-10-21
forum: Multimedia Software
---

### Post by bill-lancaster on 2013-10-21
Is it possible to record the output from my sound card using mplayer?

---

### Post by tgalati4 on 2013-10-21
There are several ways to do it.

You could install *streamripper* if the sound source is a streaming file.

You could install *sox* and use *rec* (record) to capture the sound.  It requires several parameters to get exactly what you want.

You could use *audacity* if you need to manually monitor the recording--input levels, EQ, noise, etc.

You can use *mplayer* to rip a WAV file.  See Tip #3:  [https://help.ubuntu.com/community/MPlayerTips](https://help.ubuntu.com/community/MPlayerTips)

You can use *mencoder* to encode a DVD into a digital stream.

---

### Post by bill-lancaster on 2013-10-21
Thanks, I'd like to use mplayer.
Example #3 recommends:-
```
mplayer input.wma -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```
So, I guess input.wma is the source.  How would I replace that to record anything audio from the sound card?

---

### Post by tgalati4 on 2013-10-21
Since all devices are files in linux you can usually just substitute the sound card designation (say /dev/snd/pmcC0D0c) for the input file.  Similarly you can specify an output device instead of a file to get the device to "play" the file.  Experiment and let us know what works.

---

### Post by bill-lancaster on 2013-10-22
Here's an interim report!
```
~$aplay -l
``` produces :-
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

So, running ```
mplayer plughw:0,0 -vc null -vo null -ao pcm:fast:waveheader:file=output.wav

```
or ```
mplayermplayer /dev/snd/pmcC0D0c -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```
or ```
mplayer hw:0.0 -vc null -vo null -ao pcm:fast:waveheader:file=output.wav
```
Produces reports like:-
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing hw:0.0.
File not found: 'hw:0.0'
Failed to open hw:0.0.

I'll continue fiddling for a bit more!

---

### Post by tgalati4 on 2013-10-22
```
ls -la /dev/snd
```

tgalati4@Mint14-Extensa ~ $ ls -la /dev/snd
total 0
drwxr-xr-x   3 root root      220 Sep  9 11:02 .
drwxr-xr-x  16 root root     4320 Oct 22 07:57 ..
drwxr-xr-x   2 root root       60 Sep  9 11:02 by-path
crw-rw---T+  1 root audio 116,  7 Sep  9 11:02 controlC0
crw-rw---T+  1 root audio 116,  6 Sep  9 11:02 hwC0D0
crw-rw---T+  1 root audio 116,  5 Sep  9 11:02 hwC0D1
crw-rw---T+  1 root audio 116,  4 Sep  9 11:02 pcmC0D0c
crw-rw---T+  1 root audio 116,  3 Oct 18 15:17 pcmC0D0p
crw-rw---T+  1 root audio 116,  2 Sep  9 11:02 pcmC0D2c
crw-rw---T+  1 root audio 116,  1 Sep  9 11:02 seq
crw-rw---T+  1 root audio 116, 33 Sep  9 11:02 timer


I'm going to guess that *seq* (sequencer) and timer (master audio clock) are not helpful in this case.  The other devices are either your capture (c) or playback (p) devices.

You also need to add yourself to group* audio*:

tgalati4@Mint14-Extensa ~ $ groups
tgalati4 adm cdrom sudo dip plugdev lpadmin

```
man addgroup
sudo addgroup bill-lancaster audio
groups bill-lancaster
```


Here are some other tips:  [http://superuser.com/questions/597227/linux-arecord-capture-sound-card-output-rather-than-microphone-input](http://superuser.com/questions/597227/linux-arecord-capture-sound-card-output-rather-than-microphone-input)

```
man arecord
arecord -L
```

Use the -D switch to specify the device that was listed above.

---

### Post by bill-lancaster on 2013-10-22
I tried them all! (except the clock & sequence)
```
mplayer //dev/snd/pmcC0D0p -vc null -vo null -ao file=output.wav

``` gives:-
MPlayer svn r34540 (Ubuntu), built with gcc-4.7 (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing //dev/snd/pmcC0D0p.
File not found: '//dev/snd/pmcC0D0p'
Failed to open //dev/snd/pmcC0D0p.

---

### Post by SeijiSensei on 2013-10-22
There should be only one slash before /dev.  I don't know if that will fix the problem, though.

I used [OutRec]("http://sourceforge.net/projects/outrec/files/") for this purpose, but it's no longer maintained.  It worked in 10.04, but it's written in something called "Gambas" and the packaged version has dependency problems.  I suppose I could try compiling from source, but I'd have to install Gambas support first.

---

### Post by tgalati4 on 2013-10-22
Try:

```
arecord -D front -f cd front_speaker_audio_output.wav
```

Control-C to stop.

Then play it back:

```
aplay front_speaker_audio_output.wav
```

There is no pmc device, it is pcm.

This appears to do something, but it is not putting out the wave file:  (so it requires further tweaking)

(You must start playing something first to fill the device file.)

mplayer /dev/snd/pcmC0D0p -vc null -vo null -ao pcm:fast:waveheader:file=output.wav

---

