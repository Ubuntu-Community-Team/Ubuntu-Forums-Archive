---
title: "Aargh, Audacity in Kubuntu Edgy 6.10?"
date: 2006-12-20
forum: Multimedia &amp; Video
---

### Post by kalahari875 on 2006-12-20
Has anyone gotten the Audacity package to run in Kubuntu Edgy? Whenever I run it, I get the following message:

```

There was an issue initializing the audio i/o layer. You will not be able to play or record audio.

Error: Host error.

```

I've RTFM'd as best I can. Per [http://audacityteam.org/wiki/index.php?title=Linux_Issues](http://audacityteam.org/wiki/index.php?title=Linux_Issues), I have disabled the sound system before running Audacity via kcontrol | Sound and Multimedia | Sound System | (Uncheck) Enable the sound system. 

I have also tried issuing artsdsp audacity to start the application, but this results in: Segmentation fault (core dumped)

I have manually killed artsd before running Audacity via killall artsd.

I have edited ~/.audacity and tried specifying the audio devices. Originally there were no devices listed:

```

[AudioIO]
PlaybackDevice=
RecordingDevice=

```

For the PlaybackDevice and RecordingDevice I have tried using /dev/dsp and /dev/dsp1 (both are listed under /dev) :
```

crw-rw---- 1 root audio 14,  3 2006-12-17 19:05 /dev/dsp
crw-rw---- 1 root audio 14, 19 2006-12-17 19:05 /dev/dsp1

```

Additionally, I have confirmed that my user account is in the audio group.

Any ideas? I'd love to get this working. ](*,)

---

### Post by kalahari875 on 2006-12-20
Well, I don't know which of the following two things fixed the problem, but it is now working.
[LIST=1]
[*]I installed libsdl1.2debian-all, replacing libsdl1.2debian-alsa (to fix sound in VMWare Server).
[*]I rebooted after applying a kernel update.
[/LIST]

---

