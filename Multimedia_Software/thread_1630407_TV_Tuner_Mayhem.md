---
title: "TV Tuner Mayhem"
date: 2010-11-25
forum: Multimedia Software
---

### Post by Nortesidin on 2010-11-25
mayhem because, this is getting caaaarazy!
Installed ubuntu 9.10 32 bit (iheard 64bit was a problem child)
And got my tv tuner card in, and my graphics card in.
GFX card - geforce 4 mx420
TV  card - phillips saa7130 series

Card is in, I downloaded "tv time" and turned it on and tried to configure it, but it acts like there is no signal.. How can i fix this?
 Is there another program that is easy to setup that can record? i record some things off of my xbox 360 and need to start again =)

---

### Post by Nortesidin on 2010-11-25
happy thanksgiving!

ps
any ideas anyone?

---

### Post by xc3RnbFO8P on 2010-11-25
In Terminal show the output of:
> lspci -vnn
and 
> dmesg

---

### Post by Nortesidin on 2010-11-25
00:07.0 Multimedia controller [0480]: Philips Semiconductors SAA7130 Video Broadcast Decoder [1131:7130] (rev 01)
	Subsystem: Philips Semiconductors Device [1131:0000]
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at cfffbc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134
and
"[ 3774.349624] VFS: busy inodes on changed media or resized disk sr0" about a zillion times

---

### Post by xc3RnbFO8P on 2010-11-25
Try:
> sudo gedit /etc/modprobe.d/modprobe.conf
and add this line:
> options saa7134 card=10 tuner=2
restart the computer
do dmesg, copy/paste here
or try Tvtime again.

---

