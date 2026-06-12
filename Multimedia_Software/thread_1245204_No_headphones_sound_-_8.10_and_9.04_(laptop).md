---
title: "No headphones sound - 8.10 and 9.04 (laptop)"
date: 2009-08-20
forum: Multimedia Software
---

### Post by alex.mobigo on 2009-08-20
Hi all,
I have been trying to use my headphones since ubuntu 8.10 without success and i have not found any similar solution to this issue. Upgraded to 9.04, same issue, so it seems not related to specific version.
Everything works fine on my laptop but the headphones output sound.
The closest i could get is that the issue is related to auto-mute, since the speakers works, and when i plug in the headphones, i can hear the sound on the headphones for ** 1/10 second**s and then it gets muted. i can notice it  while plugging in and out the headphones.

Can someone help? Please, specific answer (ubuntu 9.04).

Here is the information needed:

**Hardware**: NoteBook STI IS1253 (dual-boot), ubuntu 9.04, gnome 2.26.1
**Detected devices**: HDA Intel (Alsa mixer), Conexant CX 20549 (Venice) (OSS mixer)
> 
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
I am able to record sound from Ext. Microphone, playback to speakers.
Yeah, the device works on windows.

Thanks in advance for any help.

---

### Post by Vesperatus on 2009-08-20
Open a console and do :

alsamixer

Ususally, you should see a bunch of vertical lines. Does the Master line or Headphone line have a number, a "MM" or some value ? 

Try using the arrows to make sure the line is completly filled and if you see some lines with MM, navigate to them and press "M" on you keyboard. That should mute/unmute the lines.

Btw, to quit alsamixer, press ESC twice.

---

### Post by alex.mobigo on 2009-08-21
thanks Vesperatus,

The only thing that was disabled (MM) was the IEC958 and IEC958 D (PCM), i enabled it, but i was not able to change values.
Master and PCM are at 90%.

Would be nice to understand who drives the headphones. I have compared it to my PC that is working fine (Sis SI7012 - Realtek) and i could change its value (it was also 00 and the headphones didnt get muted).

Anything else i should do?

---

### Post by Vesperatus on 2009-08-21
If someone familiar with pulse can jump in, he could explain you how to check everything in pulse. I have it uninstalled on my side and cant really help with it. 

On my laptop, the headphones didnt work correctly because of the alsa version. I had to recompile it. 

You can follow the instructions there :

[http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html](http://webupd8.blogspot.com/2009/08/how-to-upgrade-to-alsa-1020-on-ubuntu.html)

---

### Post by alex.mobigo on 2009-08-21
thanks Vesperatus,

Nice recipe. 
It is my laptop for production, did not want to take that radical compilation, anyway, i took the risk. **Compiled and upgraded to ALSA 1.0.20.** Dont know what will happen when i upgrade to a new kernel.

Still no headphones sound.

In gnome settings i had to change to ALSA instead of autodetect to have it working again.

Any linux expert out there to give us a hand?

Any help would be appreciated .

cheers

---

### Post by Vesperatus on 2009-08-21
If you change kernel, you will have to compile again.

However, you can go in each of the directories and do : make uninstall

I'm out of ideas :(

---

### Post by alex.mobigo on 2009-08-27
just in case someone could give some directions

---

