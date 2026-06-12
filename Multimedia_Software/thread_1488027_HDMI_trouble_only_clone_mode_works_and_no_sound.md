---
title: "HDMI trouble: only clone mode works and no sound"
date: 2010-05-19
forum: Multimedia Software
---

### Post by Destr0 on 2010-05-19
Updated Kubuntu 9.10 > Kubuntu 10.04.

I have no HDMI sound and only clone mode HDMI video.

Computer is connected to LCD monitor with VGA and TV with HDMI. 
Both are using onboard hardware.

HDMI audio and video were both working fine with 9.10.

```
uname -a
Linux HTPC 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux
```

Computer is Shuttle DVO SG33G5M Deluxe.
```

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 IDE interface: JMicron Technology Corp. JMB368 IDE controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:09.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
03:09.1 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)
03:09.2 Multimedia controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)
03:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

There is also DVB-T card in computer. 
I Haven't tried yet if it plays nice with 10.04 or not.

**Video**
Clone sortof works but not any other mode. 
If I try to change mode to something else GUI reboots(or something) and after that TV HDMI setting is back to clone mode.  
```

From xorg.log
Warning	The directory "/usr/share/fonts/X11/cyrillic" does not exist.
Warning	Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
Warning	Falling back to old probe method for vesa
Warning Falling back to old probe method for fbdev	
Probed	RandR disabled
```

**Audio:**
Shortly after 10.04 update there was annoying pop-up:

"Removed Sound Devices
Do you want KDE to permanently forget about these devices?
This is the list of devices KDE thinks can be removed:..."
Accidentally I clicked yes...

There used to be HDMI output HW:0,3.
```
aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: Intel [HDA Intel], laite 0: ALC888 Analog [ALC888 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: Intel [HDA Intel], laite 1: ALC888 Digital [ALC888 Digital]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
```
```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on May 15 2010 for kernel 2.6.32-22-generic (SMP).
```

HDMI audio probably starts working when HDMI works right...?

---

### Post by lidex on 2010-05-20
How did you get that alsa version? Did you manually upgrade or install alsa-backports? I'm curious as a lot of users seem to have alsa problems after a recent update and I'm trying to figure out the culprit. For you, try re-installing: ```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
Reboot.

Now, output from:
```
aplay -l
```

---

### Post by Destr0 on 2010-05-20
After 10.04 update I have tried uninstalling and installing alsa several times with KPackageKit and apg-get.

Last time I used apt-get.

I Haven't tried backports.

I ran alsa apg-get reinstall once more exactly as typed.

Didn't have gstreamer installed, but HDMI output is still no-show.
```
aplay -l
**** Luettelo PLAYBACK laitteista ****
kortti 0: Intel [HDA Intel], laite 0: ALC888 Analog [ALC888 Analog]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
kortti 0: Intel [HDA Intel], laite 1: ALC888 Digital [ALC888 Digital]
  Alalaitteet: 1/1
  Alalaite #0: subdevice #0
```

(BTW analog sound works, but no HDMI sound.)

---

### Post by Destr0 on 2010-05-24
Syslog
```

kdm[934] X server for display :0 terminated unexpectedly

```

lspci -v
```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3106
        Flags: bus master, fast devsel, latency 0, IRQ 27
        Memory at fde80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ff00 [size=8]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:02.1 Display controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
        Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3106
        Flags: bus master, fast devsel, latency 0
        Memory at fdf00000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: <access denied>

```

---

### Post by Destr0 on 2010-06-04
Haven't found solution for my HTPC output problem!
Windows seems to be only really working OS nowdays...

HDMI audio

I tried to rename phonondevicesrc.
System created new one.
Still no hdmi output...?

Could it be that linux thinks that the HDMI connection is DVI as both (computer and tv) connectors can be used as DVI too?
CABLE IS HDMI.

HDMI video 

This is kinda weird. 

GUI crashes allways if desktop is stretched to left or right,
but not allways if desktop is stretched up or down.

Clone mode changes resolution of both devices to the same (if change at all). *buntu seems to love 1680x1050 resolution.

Every reboot system is back to clone mode and both LCD display and TV resolutions are back to 1680x1050. No exeptions.

---

### Post by Destr0 on 2010-06-16
Help! Anyone?!

---

