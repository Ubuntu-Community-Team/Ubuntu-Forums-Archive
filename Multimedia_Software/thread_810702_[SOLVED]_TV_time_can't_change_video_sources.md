---
title: "[SOLVED] TV time can't change video sources"
date: 2008-05-28
forum: Multimedia Software
---

### Post by theophiles on 2008-05-28
I can't get tv time to change video sources from "default" whatever that is. I assume it is not detecting my tuner card, but don't know what to do. I had it working before, but had to do a fresh install of 8.04 for other reasons. Please help!!!

I'm not sure if this will help, but the output of "lspci" is

```
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1)
04:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
```

---

### Post by theophiles on 2008-05-28
bump

---

### Post by theophiles on 2008-05-29
bump

---

### Post by wolfen69 on 2008-05-29
what's the make and model of your card?

---

### Post by theophiles on 2008-05-29
It is a Sabrent M501-1202 

Previously, I just plugged it in and the video composite part worked with TVTime. I never got the cable part to work, but that was okay. 

While I was trying to get the cable part to work (before giving up and just being happy with video composite), I posted a lot here:
[http://ubuntuforums.org/showthread.php?p=4150067](http://ubuntuforums.org/showthread.php?p=4150067)

Actually, Puppy, you posted a recommendation there. 

I never marked it solved because we never got the cable part working. Now I would be very happy to just have what I had before and will consider this solved when TV-Time recognizes that I have a card at all.

---

### Post by theophiles on 2008-05-30
Problem solved well enough for me using information from here: [http://ubuntuforums.org/showthread.php?t=279438](http://ubuntuforums.org/showthread.php?t=279438)

Since I use my old threads for future reference when I do a new install and because it might be useful to others here is what I did:
```
sudo rmmod saa7134
sudo modprobe saa7134 card=42
```

---

### Post by theophiles on 2008-05-30
For some reason I keep having to do this every time I restart.

---

