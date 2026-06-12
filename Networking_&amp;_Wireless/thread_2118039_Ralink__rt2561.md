---
title: "Ralink  rt2561"
date: 2013-02-20
forum: Networking &amp; Wireless
---

### Post by PantherStu on 2013-02-20
Hi everyone, I am trying to get my built in wireless adapter to work under Ubuntu.
My wireless adapter is an [Asus PCI- G31]("http://www.asus.com.au/Networks/Wireless_Adapters/PCIG31/").
I am relatively inexperienced with Ubuntu, but I'm not afraid to get into terminal etc if need be.

So here is what I have fund so far, any help from here would be greatly appreciated.  

so when I ran ```

lspci -v | grep -iA 10 'network'

```
I got 
```

02:06.0 Network controller: Ralink corp. RT2561/RT61 802.11g PCI
	Subsystem: ASUSTeK Computer Inc. Device 837e
	Flags: slow devsel, IRQ 21
	Memory at fbe00000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	Kernel modules: rt61pci

02:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
	Subsystem: MEDIATEK Corp. Device 170b
	Flags: medium devsel, IRQ 22
	I/O ports at c800 [size=256]

```

When I run
```
ifconfig
```
I get
```
stu@Stu-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 20:cf:30:e1:3d:0b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2085 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:220482 (220.4 KB)  TX bytes:220482 (220.4 KB)

wlan1     Link encap:Ethernet  HWaddr 00:60:64:2e:a3:d6  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::260:64ff:fe2e:a3d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:261645 errors:0 dropped:0 overruns:0 frame:0
          TX packets:165533 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:360780758 (360.7 MB)  TX bytes:18451999 (18.4 MB)

```
You can see there wlan1 is in use but thats by
```

lsusb
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

```

Only way I can get online at the moment.

So any help would be appreciated. or if you need more info please let me know.

Thanks Stu

---

### Post by chili555 on 2013-02-20
Your internal device has a driver:> Network controller: Ralink corp. RT2561/RT61 802.11g PCI
	Subsystem: ASUSTeK Computer Inc. Device 837e
	Flags: slow devsel, IRQ 21
	Memory at fbe00000 (32-bit, non-prefetchable) [size=32K]
	Capabilities: <access denied>
	[COLOR="Red"]Kernel modules: rt61pci[/COLOR]
Please unplug the USB device, reboot so we have a clean slate and run and post:```
iwconfig
dmesg | grep -e rt6 -e wlan
```Thanks.

---

### Post by PantherStu on 2013-02-20
So here is the outcome of these, straight after a restart with no usb dongle in
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ dmesg | grep -e rt6 -e wlan
$ 

```

---

### Post by chili555 on 2013-02-20
Let's force it a bit:```
sudo modprobe rt61pci
dmesg | grep -e rt6 -e wlan
```Thanks.

---

### Post by PantherStu on 2013-02-20
Ok so,

```

$ sudo modprobe rt61pci
[sudo] password for stu: 
$ dmesg | grep -e rt6 -e wlan
$ 

```

---

### Post by chili555 on 2013-02-21
Please reboot without the USB inserted and run:```
dmesg > panther.txt
```Find the text file panther.txt in your user directory and paste it here and give us the link in your reply. You have a weird case there, Stu!

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by PantherStu on 2013-02-22
Ok so all done and pasted to

[http://paste.ubuntu.com/1704704/](http://paste.ubuntu.com/1704704/)

hope it helps.  its 2427 lines long, and all along the lines of
```

[   26.162009] cmipci: invalid PCM pointer: 0xffff

```

Thanks for looking.
Stu

---

### Post by chili555 on 2013-02-22
> cmipci: invalid PCM pointer: 0xffffWhen I google this, it seems to be a bug that was fixed in 2010. Are you running an older Ubuntu version?```
lsb_release -d
```Second, please see attached.

---

### Post by PantherStu on 2013-02-22
Firstly.

```

$ lsb_release -d
Description:	Ubuntu 12.10

```
second not sure on the pastebin, but i repasted (I wonder if thats a word)
[http://paste.ubuntu.com/5556167/](http://paste.ubuntu.com/5556167/)

---

### Post by chili555 on 2013-02-22
The paste went through and, as you noted, it is 2400+ lines of the same thing you quoted above. This is a sound card issue according to Google and the module in question is:```
$ modinfo snd-cmipci
filename:       /lib/modules/3.5.0-24-generic/kernel/sound/pci/snd-[COLOR="Red"]cmipci[/COLOR].ko
license:        GPL
description:    C-Media CMI8x38 PCI
author:         Takashi Iwai <tiwai@suse.de>
srcversion:     6D907DCD701F45E632A4877
alias:          pci:v000010B9d00000111sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000112sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000111sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000101sv*sd*bc*sc*i*
alias:          pci:v000013F6d00000100sv*sd*bc*sc*i*
depends:        snd-pcm,snd,snd-opl3-lib,snd-mpu401-uart,gameport
intree:         Y
vermagic:       3.5.0-24-generic SMP mod_unload modversions 
parm:           index:Index value for C-Media PCI soundcard. (array of int)
parm:           id:ID string for C-Media PCI soundcard. (array of charp)
parm:           enable:Enable C-Media PCI soundcard. (array of bool)
parm:           mpu_port:MPU-401 port. (array of long)
parm:           fm_port:FM port. (array of long)
parm:           soft_ac3:Software-conversion of raw SPDIF packets (model 033 only). (array of bool)
parm:           joystick_port:Joystick port address. (array of int)
```I don't know whether your sound system struggling to get going correctly is inhibiting your other PCI devices, such as wireless, but I strongly suspect it is. 

This may or may not be useful: [http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/Procfile.txt)> 
59	The card-specific files are found in /proc/asound/card* directories.
60	Some drivers (e.g. [COLOR="Red"]cmipci[/COLOR]) have their own proc entries for the
61	register dump, etc (e.g. /proc/asound/card*/[COLOR="Red"]cmipci[/COLOR] shows the register
62	dump).  These files would be really helpful for debugging.
63	
64	When PCM devices are available on this card, you can see directories
65	like pcm0p or pcm1c.  They hold the PCM information for each PCM
66	stream.  The number after 'pcm' is the PCM device number from 0, and
67	the last 'p' or 'c' means playback or capture direction.  The files in
68	this subtree is described later.I suggest you go over to Multimedia and start a thread and reference error messages in dmesg and try to get sound working before we proceed. [http://ubuntuforums.org/forumdisplay.php?f=334](http://ubuntuforums.org/forumdisplay.php?f=334)

I am inexperienced in such matters. My sound cards just work.

If you have a stand-alone (not integrated into the motherboard) sound card, you might temporarily remove it and see what dmesg says after you reboot and, most importantly, whether the wireless works.

---

### Post by PantherStu on 2013-02-22
Hmmm, strange sound card is working perfectly, lol.

I will try and unplug and see if that makes a difference to the wireless, I will let you know, in the mean time, thanks for all your help.

---

### Post by PantherStu on 2013-02-24
Ok so update on this, the sound card, (Which was working perfectly) was the cause of this problem, I have since removed the card (and installed a new one) and my wireless is working perfectly. So obviously something with the old card, was interfering with the the wireless card.

Moral of the story, what you think is the problem is not always the problem.
Thanks for all your help, I will now mark this as solved.

---

### Post by chili555 on 2013-02-24
Glad it's working!

---

