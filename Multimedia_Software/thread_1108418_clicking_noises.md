---
title: "clicking noises"
date: 2009-03-27
forum: Multimedia Software
---

### Post by colsandurz on 2009-03-27
Hello,

I have this bizarre problem with audio.  Basically, whenever I am supposed to hear something, I can only hear this clicking noise, kinda like my speakers are popping.  I know that the speakers and the board are good because I dual boot with (shudder) windows and everything works fine there.  I've followed part of this guide (it's the stickied one)

Comprehensive Sound Problem Solutions Guide v0.5e
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Here are the results from aplay -l and lspci -v (I took all the irrelavent stuff of the lspci)
```
aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at ea200000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

Also, I tried 
```
sudo modprobe snd-hda-intel
```
with no results...

If anyone has any advice, I'd appreciate it.

---

### Post by colsandurz on 2009-03-28
does anyone have any ideas....

---

### Post by colsandurz on 2009-04-03
anyone... anything??

---

### Post by colsandurz on 2009-04-05
Update:

It will work when I specify to use OSS.  So my ALSA is messed up somehow.  However, I reinstalled ALSA and nothing changed.  Does anyone have any ideas??

---

### Post by sailthesea on 2009-04-05
If you are using Itrepid 32bit you could try this in terminal Its a bit smash and grab but it seems to work on the whole


 sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list

 wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 sudo apt-get remove gnash gnash-common libflashsupport mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install alsa-oss faac faad flashplugin-nonfree gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll libavcodec-unstripped-51 libmp3lame0 non-free-codecs sun-java6-fonts sun-java6-jre sun-java6-plugin unrar

 Installs Media Support;)

---

### Post by colsandurz on 2009-04-06
That didn't do it.  I still have the problem.  Thanks for the effort though.

---

### Post by sailthesea on 2009-04-06
Well I had something like this before and ended up reinstalling It was a pain But if you've backed up it won't be a problem 
 Hope  it doesn't come to that!!

---

### Post by colsandurz on 2009-04-16
Can anyone else try to help me?

I'm really not sure how to approach this and I really don't want to reinstall.

---

### Post by colsandurz on 2009-04-27
update2:

pulseaudio also does not work.  It makes the same noise.  I have reinstalled ALSA but not both ALSA and Pulse Audio... maybe that will do something.

edit: that did not work

---

### Post by wimpelmeesje on 2009-04-30
I'm having almost the same problem on 9.04. I do hear the sound but it's accompanied by irritating clicks also on alsa and pulseaudio. No solution found yet.

---

### Post by colsandurz on 2009-05-17
fixed it!  
thanks to this thread

[http://ubuntuforums.org/showthread.php?t=1153133](http://ubuntuforums.org/showthread.php?t=1153133)

---

