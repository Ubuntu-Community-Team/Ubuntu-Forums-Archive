---
title: "Checking to see what is working and what is not..."
date: 2006-06-09
forum: Multimedia &amp; Video
---

### Post by evil_elman on 2006-06-09
Hello all!

I've just installed Ubuntu 6.06 and everything works fine. Wi-Fi, touchpad, sound, FAT32 drives, dual-boot and so on. I think I've even got the 3D acceleration working thanks to some forgotten FAQ on the Internet.

However, 2D acceleration seems to lacking or something else is wrong (jerky video playback, jerky window movements and a general sluggishness in the UI). Also, video playback results in 100% CPU usage.

I've tried to look around forums, Wiki's and FAQ's but have not found anything that is useful for me... So here I am.. :-)

I would like to know how to check and confirm that the following are ABSOLUTELY working to at least a functional, but maybe not optimal, degree...

* 3D acceleration
* 2D acceleration
* Speedstep (for Pentium M)
* Optimal DMA (HDD's, optical drives) speeds and settings.

Thanks in advance..

/ Tobias

---

### Post by Dr. Nick on 2006-06-09
hmm 3d acceleration requires a good video card, what do you have? nvidia, ati, or other. If you have nvidia then 3d acceleration is pretty easy. just install the nvidia-glx package and the restricted drivers, their are a few nvidia how-tos on here aleady.

---

### Post by evil_elman on 2006-06-09
The laptop:

CPU
# Bus Speed: 533 MHz
# Clock Speed: 1600 MHz (WORKS, apparently with speedstep)
# CPU Brand: Intel
# CPU Model Number: 730

RAM
# RAM Size (installed): 512 MB
# RAM Speed: 333 MHz

System
# Chipset Model: Intel 915PM Express
# PCI Express 16x: Yes

Storage
# Hard Drive Size: 60 GB (Toshiba MK6026GAX)
# Hard Drive Speed: 5400 rpm

Optical Drives
# Drive Type: CDRW + DVD Combo (Reading works fine, writing is unconfirmed)

Video
# Graphics Chipset: ATI Mobility Radeon X600 PCI-E (3D seems to work, 2D seems sluggish)
# Graphics Memory Size: 64 MB, dedicated

Display
# External Display Resolution (maximum): 2048 x 1536 pixels
# Screen Form: 4:3
# Screen Resolution: 1400 x 1050 pixels (Works fine)
# Screen Size: 15.0 "

Devices
# Built In Microphone: Spec says there isn't one but there actually is
# Keyboard: Standard (Works fine)
# Pointing Device: Mouse Touch Pad with 4 way Scroll (Works fine)

Input/Output
# Docking / Port Replicator: Yes (Unconfirmed)
# DVI Out: No
# FireWire IEEE 1394: Yes - 4 Pin (Unconfirmed)
# Infrared: Yes (Unconfirmed)
# Line In / Microphone Socket Yes (Unconfirmed)
# Line In Socket: Yes (Unconfirmed)
# Line Out / Headphone Socket: Yes (Unconfirmed)
# Parallel Port: No
# PS/2 Port: No
# SPDIF In/Out: No
# S-Video In: No
# S-Video Out: Yes (Unconfirmed)
# USB 2.0 Ports: 3 (Working fine)
# VGA Out: Yes (Unconfirmed)

Multimedia
# Sound Card Type: MS-Sound Compatible (Works fine)
# Speaker Setup: 2 Speakers

Communications
# 56k V92 Data/Fax Modem: Yes (Unconfirmed)
# Bluetooth: No
# Ethernet Controller: Gigabit 10/100/1000 Mbps (Unconfirmed)
# Wireless Networking: 802.11b/g (Works fine)

Cards / Expansion
# PCMCIA Slots: 1 x Type II (Unconfirmed)

Card Reader
# Card Reader: 4 in 1, Memory Stick, Memory Stick Pro, Multimedia Card, Secure Digital (Unconfirmed)

---

### Post by Dr. Nick on 2006-06-09
look here for 3d accel on the ati.
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.25.18_drivers_in_Ubuntu_Dapper_Manually)

I have never done it so cant be of much further help. Thats the only one of your initial ?'s that I have any expierence with. Sorry

---

### Post by evil_elman on 2006-06-09
According to the link provided and the two commands run

'fglrxinfo' and 'dmesg | grep fglrx'

both return expected results compaired to the page on the link.

I can't draw a conclusion on whether or not the guy who wrote the FAQ have the same problem or not.

---

### Post by Dr. Nick on 2006-06-09
[quote=evil_elman]According to the link provided and the two commands run

'fglrxinfo' and 'dmesg | grep fglrx'

both return expected results compaired to the page on the link.

I can't draw a conclusion on whether or not the guy who wrote the FAQ have the same problem or not.[/quote]

If the results in the "confirm that it worked section" are the same I would then think you had 3d acceleration. Since I dont have a ati card at the moment I cant test it myself. you may play around with some of the oengl screensavers and see if they play correctly or are jerky

---

### Post by evil_elman on 2006-06-09
I've also managed to find that (at least) my HDA is using DMA. Don't know which DMA mode, though...

3D screensavers (Endgame, GLFlux and Busy Spheres) work fine so I think we can establish that 3D works.

However, 3D isn't the problem... 2D is, however... :-(

---

### Post by Aurelias on 2006-06-09
My setup is very similar to yours and I've been having 2D render problems as well.  is turningMy only guess is that the fglrx driver is using the GPU to render the graphics, but using the CPU to calculate placement, etc.  The one thing I'd recommend is to add
```
Option      "VideoOverlay" "on"
Option      "OpenGLOverlay" "off"
```
to your xorg.conf file inside the "Device" section.  Although it might not help with general 2D rendering, it might make movies play a bit smoother.

For messing with speedstep, I use klaptop (I'm on KDE) and the only way I'm sure that it's working is to judge how often the system fan turns on (no tools report the clock speed correctly; they always say it's at max).  To this end, I only ever use the powersave and performance regulators, since I think the load-based ones (userspace, powersave, and conservative) are being tricked by the 2D rendering problem into always running the CPU at max speed.
----------
System specs (for reference):
Gateway laptop with...
Pentium M CPU, 1.66Mhz
512Mb ram
40Gb SATA hdd
dvd/cd-rw drive
ATI Radeon Mobility X600 graphics card (fglrx drivers)

---

### Post by Dr. Nick on 2006-06-09
not sure what is wrong with the 2d, The little black squares on minimize/maxamize are normal unfortunately. I dont know why video playback would go 100% cpu.

Here is a good link for hard driver performance
[http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html)

its fairly old now but still has some info. You can install the hdparm in synaptic, may have to enable the extra repos.

---

### Post by evil_elman on 2006-06-09
The DMA mode(s) and other HDD settings using HDPARM does not seem to be the issue. I'm not getting any speed increases or other positive (or negative) effects from doing those settings...

However, I've just discovered that some of the 2D 'sluggishness' I'm experiencing is due to a feature. Whenever I drag a window it sticks to other windows (the edges) and also the desktop borders... Is there any way of disabling this 'sticky windows' feature...?

---

