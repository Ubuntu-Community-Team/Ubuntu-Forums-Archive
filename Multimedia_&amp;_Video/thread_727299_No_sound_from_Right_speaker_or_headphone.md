---
title: "No sound from Right speaker or headphone"
date: 2008-03-17
forum: Multimedia &amp; Video
---

### Post by rexless on 2008-03-17
Greetings.
Here's a weird one.  As of some point last night or this morning, my right speaker AND/OR right headphone no longer makes any noise.

Seriously... I try playing music files or anything that I've done 1000 times before and the left side sounds normal... the right side is silent. My notebook is a Dell Inspiron 9400 and this affects the on-board speakers when the headphones are unplugged, AND the headphones when they're plugged in.

When I reboot into XP, the system works fine... so it's an OS/Driver issue NOT a hardware issue.

Anyone seen this?

---

### Post by jeffus_il on 2008-03-17
Have you checked the volume in the mixer, the channels can be controlled separately, Is one of the volumes down?

---

### Post by rexless on 2008-03-17
currently the pan volumes are linked, but I did try unlinking them and moving the sliders up/down separately... that didn't help unfortunately.

---

### Post by rexless on 2008-03-17
Someone mentioned that alsa drivers can do this... does that make sense?

---

### Post by jeffus_il on 2008-03-19
What sound "card" do you have? ```
lspci
```

---

### Post by yang83 on 2008-03-23
i have the same issue.. i'm running on my dell laptop e1505 
output from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)



sound only comes out from one speaker or headphone..

---

### Post by _aXXe_ on 2008-04-01
> **rexless said:**
> Someone mentioned that alsa drivers can do this... does that make sense?

Try this site for alsa help.

[http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html](http://www.antonywilliams.com/2007/10/bash-script-to-automate-compiling-alsa.html)

---

### Post by rexless on 2008-04-21
Due to a need to get work done, I gave up and started using XP for awhile.  I went back to Ubuntu a few times to grab stuff or do the odd task and one day I noticed the problem went away.  I don't recall if it was in line with any updates or such.

---

### Post by Mozork on 2008-06-09
I just had the same problem.
The solution was, that I had to switch the device in volume control (File -> Change device) and switch from alsa mixer to the OSS mixer, where the volume of my left speaker was 0% whilst the volume of left one was 100%, and put them both to 100% again.

---

### Post by myromance123 on 2008-06-16
My problem is that ONLY my right speaker works. Im using ubuntu hardy heron,here is the sound test i performed,

 List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I believe the "subdevices: 0/1" should be 1/1, and I havent found anyone with the same problem as me. So if some kind ubuntu user who knows how to deal with this could kindly lead me it would mean a lot. (I cant post threads, dunno why, and so i resort to messages through similar threads)

  Also tested hardware, no prob there. Updates are to the latest and I have only been using ubuntu for 3 days now.

---

### Post by helliewm on 2008-07-07
Bump I have the same problem. Sound coming from one speaker. Tried various fixes to no avail. Sound from one speaker suddenly gone. This has happened before I fiddled with ALSA and it returned but no joy this time. Its not a hardware problem.

---

