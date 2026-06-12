---
title: "built in sound card. NO SOUND!!!!!"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by jake16424 on 2007-11-03
ok, this is the second time i've tried ubuntu.

now im running 7.10

and i like it ALOT.

but there is no sound. yes i've installed the driver packages, and even in windows, i had to use a control panel to reconfigure my sound output BECAUSE my green sound port doesn't work, never has, so i've had to rerout my sound through the aux ports, IE: pink, black.

so anyone know how i can do this with ubuntu?

---

### Post by patis on 2007-11-03
It's hard to help you with such few details you provide. Anyway, I posted -->[here]("http://ubuntuforums.org/showthread.php?t=601433")<-- how I solved my sound problems in Gutsy using a terminal window. You can give it a try to see what happens.

---

### Post by jake16424 on 2007-11-03
> **patis said:**
> It's hard to help you with such few details you provide. Anyway, I posted -->[here]("http://ubuntuforums.org/showthread.php?t=601433")<-- how I solved my sound problems in Gutsy using a terminal window. You can give it a try to see what happens.

realtek alc850 sound chip.

what other details may give advice?

---

### Post by mali2297 on 2007-11-05
> **jake16424 said:**
> realtek alc850 sound chip.

what other details may give advice?

Post the output of these commands:
```

uname -a
aplay -l
lspci -v | grep -A 5 [Aa]udio

```

---

### Post by jake16424 on 2007-11-05
> **mali2297 said:**
> Post the output of these commands:
```

uname -a
aplay -l
lspci -v | grep -A 5 [Aa]udio

```

is as follows.

Linux jake-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1




jake@jake-desktop:~$ lspci -v | grep -A 5 [Aa]udio
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: EPoX Computer Co., Ltd. Unknown device 100b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at ac00 [size=256]
        I/O ports at b000 [size=128]
        Memory at db001000 (32-bit, non-prefetchable) [size=4K]
jake@jake-desktop:~$ 





sorry about the long reply, was at school the whole day. =-\
  Subdevice #0: subdevice #0

---

### Post by dr-nix on 2007-11-06
I have the same Motherboard. I hope this gets solved. I don't want to use nvidias old oss driver. I want to use alsa. Hmm this is so annoying.

I get sound out of my analog output but i don't use that, i use my digital output that's connected to my external amplifier.

I tried updating to the latest alsa driver (1.0.15) but that did nothing. The amplifier isn't even getting a signal from the computer. Why can't they get this damn card to work.

---

### Post by mali2297 on 2007-11-06
> **jake16424 said:**
> is as follows.

Linux jake-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1




jake@jake-desktop:~$ lspci -v | grep -A 5 [Aa]udio
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
        Subsystem: EPoX Computer Co., Ltd. Unknown device 100b
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        I/O ports at ac00 [size=256]
        I/O ports at b000 [size=128]
        Memory at db001000 (32-bit, non-prefetchable) [size=4K]
jake@jake-desktop:~$ 





sorry about the long reply, was at school the whole day. =-\
  Subdevice #0: subdevice #0

This person showed the same output:
[http://ubuntuforums.org/showthread.php?t=502236](http://ubuntuforums.org/showthread.php?t=502236)

The problem was eventually solved. See if the same solution might work for you.

---

### Post by jake16424 on 2007-11-06
thanx dude, nice digging, i'll give it a shot later toinght, =-D

---

