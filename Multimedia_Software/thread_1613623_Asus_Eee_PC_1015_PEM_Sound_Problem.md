---
title: "Asus Eee PC 1015 PEM Sound Problem"
date: 2010-11-04
forum: Multimedia Software
---

### Post by sinanaykut on 2010-11-04
Hello, i ve bought a netbook (Asus Eee PC 1015 PEM) and installed Ubuntu 10.10 Netbook Edition near to Windows 7 Starter.

After the latest update and effords on installing BURG, to be honest i don't know the real reason, my speakers doesn't send voice anymore. Unlike Ubuntu, on Windows my speakers still working.




```
sinan@sinan-1015PEM:~$ aplay -l
**** PLAYBACK Donan&#305;m Ayg&#305;tlar&#305;n&#305;n Listesi ****
kart 0: Intel [HDA Intel], ayg&#305;t 0: ALC259 Analog [ALC259 Analog]
  Altayg&#305;tlar: 1/1
  Altayg&#305;t #0: subdevice #0


00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: ASUSTeK Computer Inc. Device 841c
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
```

---

### Post by khamami on 2010-11-30
just install alsamixer GUI. you can use synaptic to find it. then unmute your speaker

---

### Post by pete_ter on 2011-01-18
I lost sound as well when I installed 10.10 netbook edition on the same machine.  I installed the alsamixer gui, but the speakers were not muted. Did you find a fix for this?

---

### Post by fryx01 on 2011-01-23
i'm also suffering the same problem. not only on my ubuntu, but my unr, linux mint, jolicloud, everything. i tried all the method but fail to solve the problem.

the sound from internal speaker is not coming out but when i plugged in my headphone, the sound is there

there are alse several mystery about this problem that i dont understand:-

1. the sound is not working in ubuntu, but runs perfectly fine on my windows 7 home premium (im dual-booting, using wubi)

2. the sound is not working if i install ubuntu (wubi, different partition) but runs perfectly fine when inserting live cd/usb

3. the sound is coming out, but i can see the volume wave going up and down (i'm not sure what to call them), as if the sound is coming out, but its not.its like its stuck at something


i am a complete newbie, so be gentle :P

---

### Post by Nikolayoso on 2011-01-27
All you have to do, probably, is to hard reset your system. Just press the power button until it shuts down and then power it back on! 
That should do the trick!

---

### Post by lidex on 2011-01-27
Try this using a Terminal="Applications->Accessories->Terminal"
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by stad on 2011-02-25
I have this machine and had this problem once when I first installed Jolicloud. A hard reset fixed it. Please let us know if that worked.

---

### Post by sinanaykut on 2011-02-25
> **stad said:**
> I have this machine and had this problem once when I first installed Jolicloud. A hard reset fixed it. Please let us know if that worked.

Yes, I ve also found that a hard reset solves everything. Maybe this issue is realated with Windows 7, they may have lock the device for a reason.

---

### Post by MiOiM on 2011-03-04
Hi all!

I am having the same sound issue with my dual boot Asus eee pc 1015PED (windows 7) and Ubuntu 10.10 (USB HD). I've also tried Pinguy OS with the same results.

When I installed it, the sounds worked fine. Even updating/rebooting. But after using windows 7, I get no sounds in Ubuntu. I haven't tried the hard reset suggested by stad, but if it works, it makes sense that windows is locking the device as sinanaykut pointed out.

Any idea how to deal with this?

---

### Post by lidex on 2011-03-04
> **MiOiM said:**
> Hi all!

I am having the same sound issue with my dual boot Asus eee pc 1015PED (windows 7) and Ubuntu 10.10 (USB HD). I've also tried Pinguy OS with the same results.

When I installed it, the sounds worked fine. Even updating/rebooting. But after using windows 7, I get no sounds in Ubuntu. I haven't tried the hard reset suggested by stad, but if it works, it makes sense that windows is locking the device as sinanaykut pointed out.

Any idea how to deal with this?
You should file a bug report. 
Try running this command in a terminal for 10.04 or later:
```
ubuntu-bug audio
```
Reference the Ubuntu-Bug Audio link in my sig.

---

### Post by MiOiM on 2011-03-04
Done. Thanks for the hint.

---

### Post by Afief.h on 2011-05-17
I wonder, did you ever solve the problem?

I have the same laptop, and for me too the sound only plays through the headphones and not through the speakers.

Thanks in advance

---

