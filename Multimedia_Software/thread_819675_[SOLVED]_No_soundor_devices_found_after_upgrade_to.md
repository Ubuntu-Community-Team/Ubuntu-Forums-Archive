---
title: "[SOLVED] No sound/or devices found after upgrade today using custom server Kernel 2.6"
date: 2008-06-05
forum: Multimedia Software
---

### Post by heatpumpcontrol on 2008-06-05
I just performed the current updates and now my sound stopped working.
No volume control GStreamer plugins and/or devices found.

I had updated to server Kernel 2.6.24 due to 4gig ram upgrade about a week ago and the sound worked just fine. I believe the original Kernel I installed was 2.6.24.17-Server and now I'm using 2.6.24.18-Server.

I've read that I may have to 'modprobe the modules' but I don't know what that means let alone how to do it.

Here's my lspci o/p

> 00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82P965/G965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HB (ICH8) 4 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon X1650 Pro (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Radeon X1650 Pro (Secondary) (rev 9e)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


My sound card shows up but I guess just like I had to update my video drivers after the Kernel upgrade I now have to do the same for the sound.

What I've tried so far...
1- ```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

2- > sudo apt-get install linux-sound-base alsa-base alsa-utils

3- ```
sudo apt-get install gdm ubuntu-desktop
```
because they were uninstalled in step 1....

4- ```
$ aplay -l
aplay: device_list:205: no soundcards found...
```

5- I also went into synaptics and reinstalled all sound and gstreamer related apps.

[IMG]http://ubuntuforums.org/picture.php?albumid=211&pictureid=737[/IMG]

Please help... I don't have the knowledge to continue here....
Miguel

---

### Post by heatpumpcontrol on 2008-06-05
Solved it by:

```
sudo apt-get install linux-image-2.6.24-19-server
```

Sound is working well again.

Thanks......
to me :mad:

---

### Post by josh_o on 2009-03-26
I also have no sound after today's 2.6.24-24.51 update.
I am using Ubuntu Studio (Hardy).

I don't really want to downgrade my kernel as Miguel did above (right?), and I have even less knowledge than him.

Any info on what files contents/logs I need to post here (and where they are located / how to generate them) would be greatly appreciated.

josh

---

### Post by josh_o on 2009-03-26
btw.. when I boot 2.6.24-23 I have sound again.

---

