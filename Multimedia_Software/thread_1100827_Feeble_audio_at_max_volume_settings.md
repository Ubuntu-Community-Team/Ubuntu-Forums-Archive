---
title: "Feeble audio at max volume settings"
date: 2009-03-19
forum: Multimedia Software
---

### Post by vivithpp on 2009-03-19
Is there any way to reinstall all the audio drivers completely on Hardy 8.04?
I installed some package (i guess its Mplayer from medibuntu) and now my audio is very feeble at loudest volume settings.
I got rid of unwanted applications and reinstalled ALSA and libaudio. But no help.
My laptop is a Dell Vostro 1700.
If I dig in further:
admin@SHYAMALAPRASANNA:~$ cat /proc/asound/oss/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.16 emulation code)
Kernel: Linux SHYAMALAPRASANNA 2.6.24-23-generic #1 SMP Mon Jan 26 01:04:16 UTC 2009 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xfebfc000 irq 21

Audio devices:
0: STAC92xx Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: SigmaTel STAC9205
admin@SHYAMALAPRASANNA:~$ 

It is detecting the hardware correctly, but am I missing something here?

Cheers,
Vivith

---

### Post by antipuls3 on 2009-03-21
I also have fairly quiet sound at the highest volume... is there any way to boost hardware sound volume?:)

---

### Post by inobe on 2009-03-21
what setting do you get when double clicking volume control ?

you should find PCM, you may need to raise some of these sliders...

i had to do the same

---

### Post by antipuls3 on 2009-03-21
I found that my front was only at about 5/6ths the way up, so I turned that up.. but it's still pretty quiet..

---

### Post by inobe on 2009-03-21
there are a few bars responsible.

if you check in preferences you may notice PCM, check off pcm and raise that slider.

---

### Post by antipuls3 on 2009-03-23
> **inobe said:**
> there are a few bars responsible.

if you check in preferences you may notice PCM, check off pcm and raise that slider.

Check off pcm? The slider's all the way up. How do I check it off?

---

### Post by vivithpp on 2009-04-07
Thanks all, I set the PCM slidebar to max. This has improved the audio quality, but still not the loudest (to wake up my neighbours ;)

I guess the generic ALSA does its work. But when it comes to utilising the hardware fully, these generic drivers don't achieve much.
If I play songs in Windows (I've got s*** vista running on the other side, eating up zillions of GBs) the volume is good and loud. 
At the same settings, the Linux plays it very low.
Now I'm using my iPod earphones always with linux.
Is there anyway to improve this? 
Perhaps there could be many other soundcards waiting to pair up with the best audio drivers in Linux.

---

