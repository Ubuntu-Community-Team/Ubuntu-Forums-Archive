---
title: "No sound in Hardy Heron"
date: 2008-05-20
forum: Multimedia Software
---

### Post by chunlong on 2008-05-20
Actually, this is kinda 2 problems.

I have one machine where I had sound working after installing hardy heron. It was working fine until I was told I had to reboot, afterwhich I had no sound. The volume control stays on mute, double clicking on it gives me:
No volume control GStreamer plugins and/or devices found.

aplay -l
says no soundcards found


lspci -v lists:
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
	Subsystem: IBM Unknown device 02d9
	Flags: bus master, medium devsel, latency 0, IRQ 3
	I/O ports at 3000 [size=256]
	I/O ports at 3400 [size=64]
	Memory at d03c0800 (32-bit, non-prefetchable) [size=512]
	Memory at d03c0400 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>


Just before I had to reboot, I was playing around with virtual box and had to install virtualbox-ose-modules
I also happened to have installed devede as well, though I don't think any of these had anything to do with it?
I dunno

The other problem is, on another computer, I didn't have sound at all after I installed hardy. my card was an old yamaha one, and I tried the instructions on this:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
but still didn't work (lspci -v returned nothing). Anyone have any tips or leads?

Thanks in advance

---

### Post by Yellow Pasque on 2008-05-20
For the old yamaha card, I would try OSS4 if it matches one of the model numbers below, but if lspci is not seeing it, it could be bad hardware or an IRQ issues. Try another PCI slot and make sure you seat it firmly.
```

oss_ymf7xx	pci1073,10	Yamaha DS-XG YMF744 
oss_ymf7xx	pci1073,12	Yamaha DS-XG YMF754
oss_ymf7xx	pci1073,4	Yamaha DS-XG YMF724
oss_ymf7xx	pci1073,5	Yamaha DS-XG YMF734
oss_ymf7xx	pci1073,a	Yamaha DS-XG YMF740
oss_ymf7xx	pci1073,c	Yamaha DS-XG YMF740C
oss_ymf7xx	pci1073,d	Yamaha DS-XG YMF724F
```
[http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2)

---

### Post by chunlong on 2008-05-21
Thanks genghis, I'll take a look into that, I dunno why i didn't think in the lines that it was a hardware issue. haha

---

