---
title: "At wit's end w/ Ubuntu sound card(s) issue!"
date: 2008-11-28
forum: Multimedia Software
---

### Post by reznorio on 2008-11-28
Hi,

After about 14 hours over 3 days I've almost given up on this issue and I kindly ask for assistance.

I can't get sound to work in Ubuntu. I've tried 3 sound cards (SL Xtreme Audio PCIe, SB Audigy 2 PCI and Realtek onboard AC97. All exhibit the same issues. I can see them no problem in lspci but alsa -l or ls /proc/sound or any other soundcard detection command reveal absolutely nothing. 

I followed the 'comprehensive sound card guide' (blew everything away and started from scratch), I've installed oss, alsa, etc... even tried the nvidia (nforce K8N) drivers from their taiwan site. I can't modprobe any drivers because it doesn't even see anything. Right now I have the Audigy2 in.

One thing that drove me batty is after one reboot, I actually heard the ubuntu drums! I thought 'FINALLY' and installed amarok and went about my business. I rebooted and GONE. Hasn't been back. I wish I outputted lsmod to see what was loaded but it was too late.

<lspci -v output>
01:08.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
	Subsystem: Creative Labs Device 1003
	Flags: bus master, medium devsel, latency 0, IRQ 5
	I/O ports at df00 [size=64]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1

01:08.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04) (prog-if 10)
	Subsystem: Creative Labs Device 0010
	Flags: bus master, medium devsel, latency 64, IRQ 19
	Memory at fdeff000 (32-bit, non-prefetchable) [size=2K]
	Memory at fdef8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: ohci1394

desktop:/home/me# ls -al /proc/sound
ls: cannot access /proc/sound: No such file or directory

#alsamixer: function snd_ctl_open failed for default: No such device

# aplay -l
aplay: device_list:215: no soundcards found...

I need help!
Thanks in advance,
ReZ

---

### Post by EasyRiderOnTheStorm on 2008-11-28
Strange. The Audigy is supposed to work perfectly with Alsa. Are you sure there are absolutely no messages from "snd_SOMETHING" or "alsa" in the output of dmesg ?

---

### Post by markbuntu on 2008-11-28
The Creative audigy cards will not make any analog (speaker/headphone) sound if the analog/digital box in the soundmixer is checked.

---

### Post by reznorio on 2008-11-29
Hi,
I can't access the mixer because it doesn't recognize my card. 

alsamixer: function snd_ctl_open failed for default: No such device

Nor can I d/c on the volume icon. I get no gstreamer plugins or devices found error.

Before I wasn't getting anything on dmesg | grep snd or alsa.

I grabbed the source for 2.6.27-7-generic ( I was at -9 and reverted back thinking it was a kernel change). I recompiled all the modules and copied them over to the generic lib directory, hoping fresh native drivers would help. I now get this:

 dmesg | grep snd
[   17.255163] snd_ac97_codec: no symbol version for struct_module
[   17.276624] snd_intel8x0: no symbol version for struct_module
[   18.298437] snd_util_mem: no symbol version for struct_module
[   18.299098] snd_ac97_codec: no symbol version for struct_module
[   18.327253] snd_util_mem: no symbol version for struct_module
[   18.327844] snd_ac97_codec: no symbol version for struct_module
[   18.341416] snd_emu10k1: no symbol version for struct_module

ARGH!


2.6.27-7-generic x86_64 GNU/Linux

AMD64 3200+
2gig ram
MSI K8N Nforce

---

### Post by EasyRiderOnTheStorm on 2008-11-29
> [ 17.255163] snd_ac97_codec: no symbol version for struct_module
[ 17.276624] snd_intel8x0: no symbol version for struct_module
[ 18.298437] snd_util_mem: no symbol version for struct_module
[ 18.299098] snd_ac97_codec: no symbol version for struct_module
[ 18.327253] snd_util_mem: no symbol version for struct_module
[ 18.327844] snd_ac97_codec: no symbol version for struct_module
[ 18.341416] snd_emu10k1: no symbol version for struct_module

I see. I don't think these relate to the cause of whatever prevents you from having sound, they seem more like a comilation issue that you caused recompiling stuff - and I can't much help you with that, sorry... 

It does seem though that the cause of the messages might me the same as [[here]("http://archives.free.net.ph/message/20050622.040755.14ae322e.en.html")]. Good luck, and if you can get rid of those errors perhaps trying to insert the listed modules manually could tell you/us what's really wrong with them.

---

