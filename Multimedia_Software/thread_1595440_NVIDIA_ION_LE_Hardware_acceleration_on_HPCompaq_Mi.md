---
title: "NVIDIA ION LE Hardware acceleration on HP/Compaq Mini 311?"
date: 2010-10-13
forum: Multimedia Software
---

### Post by Redinox on 2010-10-13
Hi all,

Yesterday I figured my netbook was better off with the all new (and hopefully improved) Ubuntu 10.10 Netbook remix instead of the preinstalled WinXP SP3. 

Installation was actually a breeze and almost everything works just fine out of the box. Almost....

The HP/Compaq mini 311 has the NVIDIA Ion LE GPU and should be able to play h264/MPEG-4-AVC without a hitch. In fact, it worked perfectly well under WinXP. Well, under Ubuntu it doesn't (tested with same files as under XP), so I pretty sure there is something wrong with my configuration/drivers. 

It looks like MPlayer and VLC (the players I tested) both only use the CPU and do not benefit from the ION LE hardware accelaration. (low bandwith files play just fine, high bandwith result in 100% cpu use and choppy playback)

What did I do:
Installed ubuntu-restricted-extras
Deinstalled nouveau drivers
Installed NVIDIA Linux drivers

What am I missing? Do I need to install additional drivers/software? I read something about VDPAU, but I couldn't quite understand.

---

### Post by Redinox on 2010-10-13
Well, looks like I was right about the missing VDPAU item.

```
$sudo apt-get install vlc vdpau-va-driver
```
(thanks to a different post on this forum)

---

