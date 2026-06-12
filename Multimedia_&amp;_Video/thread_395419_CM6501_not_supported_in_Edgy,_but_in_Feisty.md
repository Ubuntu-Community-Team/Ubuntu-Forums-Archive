---
title: "CM6501 not supported in Edgy, but in Feisty?"
date: 2007-03-28
forum: Multimedia &amp; Video
---

### Post by jamyskis on 2007-03-28
Hi everyone,

I know there's been a few threads already about this sound chipset, but my question is slightly different - since there is no reasonable way of getting this chipset to work under Edgy, and it is apparently supported in the latest versions of ALSA (trying to recompile the latest alsa-source under Edgy produces an error because of a bug in the kernel).

Is anyone using this chipset under Feisty testing and can report success? I'm actually doing this for a friend who I'm trying to convince to switch to Linux and because of this sound problem he's not too convinced atm (loved Beryl though). If it works, I'll switch over to Feisty testing until the final release comes out.

---

### Post by jamyskis on 2007-03-29
Anyone?

---

### Post by jamyskis on 2007-04-07
Never mind - he's given up and gone back to Windows.

---

### Post by wooom on 2007-05-30
Hi

I also have a motherboard with the CM6501 C-media USB audio (ASUS M2N-E SLI). 
It did not work right away.
To make the sound work it is very simple. In System menu > Preferences > Sound,
you change Sound playback and capture from ALSA to USB Audio :p

Also found this page concerning ALSA compatibility with CM6501: [http://www.qbik.ch/usb/devices/showdev.php?id=3925](http://www.qbik.ch/usb/devices/showdev.php?id=3925)
It says you need 1.0.14 version of ALSA to be able to play also 48 kHz sound.
There is also a patch for ALSA 1.0.13 on web.

---

### Post by Fishnuts on 2007-06-09
The USB audio solution works for me somewhat. Most apps can play audio now, but no luck with the microphone input. No Skype or Gizmo for now I guess.

---

### Post by lmandrake on 2007-08-04
I hab no problems playing music with the CM6501 out of the box but I can't get the mic to work :/ Upgraded Alsa to 1.0.14 and the mic is still not working. All the mixers look fine in KMix. I've read that the mic is not functional when the device is set to 7.1 sound. Is there a way to set it to 2.0/2.1 manually? Or does somebody else had any luck?

---

### Post by tatadeluxe on 2007-10-01
I have problems with flash audio.
I was looking for help and i found something different on my system.
On the [snd-usb-audio module web]("http://alsa-project.org/main/index.php/Matrix:Module-usb-audio") page says:
```
chmod a+rw /dev/dsp /dev/mixer /dev/sequencer /dev/midi 
```
But on my system only exists:
> /dev/dsp1 /dev/mixer1 /dev/sequencer1
I had created symbolic links and give permissions:
```
 sudo ln -s /dev/mixer1 /dev/mixer
 sudo ln -s /dev/dsp1 /dev/dsp
 chmod a+rw /dev/dsp /dev/mixer /dev/sequencer
```
But nothing happens with the flash sound and mixer sound
I tried with
```
alsamixer -c1
asoundconf set-default-card c1
```

But the problem continue ...

Someone was lucky? and fix the problem.
My system info:
[http://foros.ubuntu-cl.org/viewtopic.php?p=15353](http://foros.ubuntu-cl.org/viewtopic.php?p=15353)

---

