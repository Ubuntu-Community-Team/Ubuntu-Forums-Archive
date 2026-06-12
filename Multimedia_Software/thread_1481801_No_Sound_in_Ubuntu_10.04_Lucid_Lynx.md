---
title: "No Sound in Ubuntu 10.04 Lucid Lynx"
date: 2010-05-12
forum: Multimedia Software
---

### Post by smythie86 on 2010-05-12
I get no sound for anything, I am running Ubuntu Lucid-amd64. Pulseaudio detects my sound card, and appears to be playing to it when I look at pavucontrol. But I get no sound for anything, not even alerts. I don't eve know how to debug it, because everything I have looked at looks like it should be working. I have checked every mute button I can find, and nothing is muted that I can see. The relevant information for my sound card from lspci -v is:

07:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs Device 100a
	Flags: bus master, medium devsel, latency 32, IRQ 21
	I/O ports at 1000 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

Does anyone have any idea what could be wrong?

Thanks in advance!

---

### Post by lidex on 2010-05-13
Was this an upgrade or clean install? Is this an add-on card? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by smythie86 on 2010-05-13
This was a clean install

```

$ uname -a
Linux home-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

$ ls /proc/asound/card*
/proc/asound/cards

/proc/asound/card0:
ca0106_i2c    ca0106_reg8   id      oss_mixer  pcm1c  pcm2p
ca0106_reg16  ca0106_regs1  iec958  pcm0c      pcm1p  pcm3c
ca0106_reg32  ca0106_regs2  midi0   pcm0p      pcm2c  pcm3p

/proc/asound/card1:
id  oss_mixer  pcm0c


```

---

### Post by lidex on 2010-05-13
I hate that codec :mad:
Try upgrading alsa using the upgrade link in my sig.

---

### Post by jhayner on 2010-05-17
> **lidex said:**
> I hate that codec :mad:
Try upgrading alsa using the upgrade link in my sig.

Just wanted to thank you, I was having the same problem with my sound, found this thread via google and your fix worked great.

---

### Post by starbityop on 2010-05-24
> **lidex said:**
> Was this an upgrade or clean install? Is this an add-on card? Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

I also made a clean istall of Lucid and most of the output is the same but then this:


veronica@veronica-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:244: snd_ctl_pcm_next_device


veronica@veronica-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

veronica@veronica-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

Thanks for yout help :)

---

### Post by lidex on 2010-05-25
> **starbityop said:**
> I also made a clean istall of Lucid and most of the output is the same but then this:


veronica@veronica-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
aplay: device_list:244: snd_ctl_pcm_next_device


veronica@veronica-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

veronica@veronica-laptop:~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

Thanks for yout help :)
Try this. 
Using a Terminal="Applications->Accessories->Terminal"
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Logout/in.

---

