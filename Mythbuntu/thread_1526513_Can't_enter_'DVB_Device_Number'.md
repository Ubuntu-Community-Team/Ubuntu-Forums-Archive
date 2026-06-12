---
title: "Can't enter 'DVB Device Number'"
date: 2010-07-08
forum: Mythbuntu
---

### Post by Sharft 6 on 2010-07-08
[color="red"]_**Very easy new solution I use**_
1. create the conf file '/etc/modprobe.d/saa7164.conf'
2. type the following inside that file:
   options saa7164 card=4
3. reboot

_here's the list of card options_
card=0 -> Unknown
card=1 -> Generic Rev2
card=2 -> Generic Rev3
card=3 -> Hauppauge WinTV-HVR2250
card=4 -> Hauppauge WinTV-HVR2200
card=5 -> Hauppauge WinTV-HVR2200
card=6 -> Hauppauge WinTV-HVR2200
card=7 -> Hauppauge WinTV-HVR2250
card=8 -> Hauppauge WinTV-HVR2250
[/color]

[COLOR="green"]Complicated Solution (if you have an HVR-2200/2250 _**and**_ you have already been through [this]("http://www.mythtvtalk.com/forum/hardware/10906-you-waiting-hvr-2200-2250-linux-driver.html#post51419") guide):
- download [this]("http://steventoth.net/linux/hvr22xx/firmwares/4038864/") magical firmware and copy it to your /lib/firmware directory. Once you've done that, a cold boot might help.

_how to quickly get it working again after a kernel update_
cd saa7164-stable/
sudo make distclean
sudo make menuconfig *#(Push 'y' on '[*]Enable drivers not supported by the kernel')*
sudo make CONFIG_DVB_FIREDTV:=n
sudo make install
sudo shutdown -r 0
[/COLOR]

So my HVR-2200 arrived today. But when I go into 'mythTV Backend Setup -> capture cards -> Add capture card -> type: DVB DTV capture card' I can't enter a device number into the 'DVB Device Number' field :(

computer:
AMD 3200+ 2Ghz
2GB DDR
NVIDIA 6600 GT
Hauppauge WinTV HVR-2200
Mythbuntu 10.04 64bit

what i've tried:
- [this]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200#Making_it_Work")
- Changing firedtv from &#8220;=m&#8221; to &#8220;=n&#8221; in &#8220;v4l/.config&#8221;
- [this]("http://ubuntuforums.org/showpost.php?p=7429539&postcount=2")
- Installing 119 mythbuntu updates.
- [this]("http://ubuntuforums.org/showpost.php?p=7749033&postcount=")
- [this]("http://ubuntuforums.org/showthread.php?p=9562581#post9562581")

---

### Post by Archmage on 2010-07-08
I think it is possible that your card hasn't been reconice and the driver loaded, therefore it wont allow you to enter any number there. (AFAIK this should be enter automatical).

---

### Post by Saubazi on 2010-07-08
From a quick look on google I found some posts from 2009 about the HVR-2200 and linux. It seems there is an experimental driver or so - meanwhile it could be of course in the kernel. This you can clarify with terminal by getting ls -la /dev/dvb/ (if it is the only adapter you've got it should list there as adapter0 - if not tough luck).

Anyway should it not be in the latest kernel you can still get it running - 
for example with this wiki:
[http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200](http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-2200)

---

### Post by Sharft 6 on 2010-07-09
```

-mythbuntu:~$ ls -la /dev/dvb/
ls: cannot access /dev/dvb/: No such file or directory

```

I chose to buy this card for 4 reasons. 
1. There is a way to get it working in linux that apparently works for absolutely everyone.
2. There are lots of places that sell this card.
3. it has DVB-T.
4. It's internal.

(New HTPC builder here)

What I've tried:
[this]("http://www.mythtvtalk.com/forum/hardware/10906-you-waiting-hvr-2200-2250-linux-driver.html#post51419")

---

### Post by andree_b on 2010-07-09
/dev/dvb not existing can have two reasons:
1) no driver loaded successfully
Check output of dmesg or lspci

2) UDEV setup problem - in this case you probably have
/dev/dvb0.frontend0 and similar instead.

---

### Post by Sharft 6 on 2010-07-09
```

-mythbuntu:~$ dmesg | grep 7164
[   27.293410] saa7164 driver loaded
[   27.305886] saa7164 0000:03:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   27.306053] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[   27.306059] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[   27.306065] saa7164 0000:03:00.0: setting latency timer to 64
[   27.501491] saa7164_downloadfirmware() no first image
[   27.501542] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   27.501547] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   27.817496] saa7164_downloadfirmware() Upload failed. (file not found?)

```

the firmware is in my firmware directory
```

-mythbuntu:~$ ls /lib/firmware/dvb*
**/lib/firmware/dvb-fe-tda10048-1.0.fw**    /lib/firmware/dvb-usb-dib0700-1.20.fw
/lib/firmware/dvb-fe-xc5000-1.6.114.fw

-mythbuntu:~$ ls /lib/firmware/*7164*
**/lib/firmware/v4l-saa7164-1.0.2.fw  /lib/firmware/v4l-saa7164-1.0.3.fw**

```

```

-mythbuntu:~$ lspci | grep 7164
03:00.0 Multimedia controller: Philips Semiconductors Device 7164 (rev 81)

```

```

-mythbuntu:~$ ls /dev/dv*
ls: cannot access /dev/dv*: No such file or directory

```

---

### Post by nickrout on 2010-07-09
the answer is there - you have no firmware!

---

### Post by Sharft 6 on 2010-07-09
> **nickrout said:**
> the answer is there - you have no firmware!

yes i do. I've downloaded, extracted and copied the firmware 4 times

I copied 'v4l-saa7164-1.0.3.fw' to 'v4l-saa7164-1.0.3**-3**.fw'
now I get this:
```

-mythbuntu:~$ dmesg | grep 7164
[   17.909494] saa7164 driver loaded
[   18.111964] saa7164 0000:03:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   18.112132] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[   18.112138] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[   18.112144] saa7164 0000:03:00.0: setting latency timer to 64
[   18.320079] saa7164_downloadfirmware() no first image
[   18.320128] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[   18.320133] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[   19.114812] saa7164_downloadfirmware() firmware read 3978608 bytes.

```

still can't add it to mythtv setup :-(

---

### Post by nickrout on 2010-07-10
well you didn't when you first posted!


what does ```
find /dev|grep dvb
``` show?

Also in mythtv-setup in the place where you enter the dvb device number I think it should be pre-populated with what is detected. Try using the left and right arrow buttons.

---

### Post by Sharft 6 on 2010-07-10
Yea sorry bout that. I tend to first post a draft then edit bits n pieces onto it.

'find /dev|grep dvb' doesn't find anything.

Yea every time I try to add the card, I push the arrow keys and zero key while the device number field is selected. But nothing ever happens.

---

### Post by nickrout on 2010-07-10
The lack of dvb nodes in /dev means that the drivers are not working properly, they should create something like the output in mine, eg

> nick@media:~$ find /dev|grep dvb
/dev/dvb
/dev/dvb/adapter1
/dev/dvb/adapter1/frontend0
/dev/dvb/adapter1/net0
/dev/dvb/adapter1/dvr0
/dev/dvb/adapter1/demux0
/dev/dvb/adapter0
/dev/dvb/adapter0/frontend0
/dev/dvb/adapter0/net0
/dev/dvb/adapter0/dvr0
/dev/dvb/adapter0/demux0
/dev/.udev/db/dvb:dvb0.dvr0
/dev/.udev/db/dvb:dvb0.demux0
/dev/.udev/db/dvb:dvb0.frontend0
/dev/.udev/db/dvb:dvb0.net0
/dev/.udev/db/dvb:dvb1.frontend0
/dev/.udev/db/dvb:dvb1.net0
/dev/.udev/db/dvb:dvb1.dvr0
/dev/.udev/db/dvb:dvb1.demux0


I have two cards so two adaptors. Can you see anything else in dmesg?

Try removing the driver then loading it with debug enabled:

```
modprobe -r saa7164
modprobe saa7164 debug=1
```

---

### Post by Sharft 6 on 2010-07-10
I bolded what I think are points of interest.
```

**[  278.961794] saa7164 0000:03:00.0: PCI INT A disabled**
[  312.428482] saa7164 driver loaded
[  312.428632] saa7164 0000:03:00.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[  312.429011] CORE saa7164[0]: subsystem: 0070:8940, board: Hauppauge WinTV-HVR2200 [card=9,autodetected]
[  312.429021] saa7164[0]/0: found at 0000:03:00.0, rev: 129, irq: 16, latency: 0, mmio: 0xfd400000
[  312.429032] saa7164 0000:03:00.0: setting latency timer to 64
**[  312.429057] saa7164[0]: Device running firmware version 0.0.0.0 (0x0)**
**[  312.620031] saa7164_downloadfirmware() no first image**
**[  312.620044] saa7164[0]: Device running firmware version 0.0.0.0 (0x0)**
[  312.620051] saa7164_downloadfirmware() Waiting for firmware upload (v4l-saa7164-1.0.3-3.fw)
[  312.620059] saa7164 0000:03:00.0: firmware: requesting v4l-saa7164-1.0.3-3.fw
[  312.643925] saa7164_downloadfirmware() firmware read 3978608 bytes.
[B][  312.643930] xc5000: firmware incorrect size
[  312.643939] Failed to boot firmware, no features registered[/B]

```

I tried moving 'dvb-fe-xc5000-1.6.114.fw' out of my firmware directory and into my home directory but still get the same messages.

---

### Post by nickrout on 2010-07-10
Try the firmware from here:

[http://steventoth.net/linux/hvr22xx/firmwares/4038864/](http://steventoth.net/linux/hvr22xx/firmwares/4038864/)

Also you need to make sure you cold boot or the new firmware won't be loaded. IE don't reboot, shut down, leave it off while you make coffee, then boot again.

---

### Post by Sharft 6 on 2010-07-10
OMFG it works!!!!! YAY!!!!!!!!!

Maybe there is a difference between 1.0.3 and 1.0.3-3 and the 1.0.2-3 one haha. Now i guess the question is - Why the pants don't any of the guides tell me to download the 1.0.3-3/1.0.2-3 firmware? Frankly I couldn't care less cause it works now WOHOO!

Thanks everyone for your time, i really really appreciate it.

---

### Post by nickrout on 2010-07-10
As a point of interest i found the answer by googling v4l-saa7164-1.0.3-3.fw and found this page that dealt with it in an answer to the comments. 

[http://www.kernellabs.com/blog/?p=721](http://www.kernellabs.com/blog/?p=721)

---

