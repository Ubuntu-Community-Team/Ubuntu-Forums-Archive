---
title: "Skype doesn't work with Pulseaudio"
date: 2008-12-30
forum: Multimedia Software
---

### Post by El Potro on 2008-12-30
Hello!

I've been using Gutsy Gibbon for over a year, with some problems here and there, but everything was "fine".

Now here in 8.10, I guess you have to be very *intrepid* in order to get all the things working alright...

First: the network, (I don't know how I actually did it, but I solved it out, even though every time I boot, I have to wait like 30 seconds and can't get rid of the annoying network tray notification because if I do, it won't work)

Second: the display resolution, (that was really hard, but I found a guide that may be useful for all those who still can't change the resolution of the screen (it's in spanish). [http://vidaextrema.wordpress.com/files/2008/11/cambiar-la-resolucion-de-pantalla-en-ubuntu-810-v-20.pdf](http://vidaextrema.wordpress.com/files/2008/11/cambiar-la-resolucion-de-pantalla-en-ubuntu-810-v-20.pdf)

And now, third: Skype and pulseaudio :-)

I've followed the instructions of hyperair, and read all this thread and others, but I think this one is the more useful [http://ubuntuforums.org/showthread.php?t=686911&page=2](http://ubuntuforums.org/showthread.php?t=686911&page=2), although I couldn't get any good results.

I attached a copy of my default.pa file, and the ~/.asoundrc it's exactly like this:

```
pcm.skypeout
{
	type plug
	slave.pcm "dmix"
}
ctl.skypeout
{
	type hw
	card 0
}
pcm.skypein
{
	type plug
	slave.pcm "dsnoop"
}
ctl.skypein
{
	type hw
	card 0
}
```


I did everything he says it has to be done, but I get this executing pulseaudio:

```
$ W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: alsa-util.c: Device dmix doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL dmix
W: alsa-util.c: Device dsnoop doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL dsnoop
W: module-alsa-source.c: Got POLLERR from ALSA

```


and if I replace ```
load-module module-alsa-source device=dsnoop
``` with ```
load-module module-alsa-source source_name=input
```

what I get is this

```
$ W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: alsa-util.c: Device dmix doesn't support 44100 Hz, changed to 48000 Hz.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL dmix

```

Either way, sound doesn't work nor in totem, nor in skype.

I would REALLY appreciate if someone could give some directions here, since I make a intensive use of Skype and this is a real pain in the *** for me.

Thank you very much,

Mauricio

---

### Post by El Potro on 2008-12-30
Anyone? Pleaasee!

---

