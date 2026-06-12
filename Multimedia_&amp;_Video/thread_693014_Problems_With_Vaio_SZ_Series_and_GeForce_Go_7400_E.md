---
title: "Problems With Vaio SZ Series and GeForce Go 7400 External Monitor"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by JCoster on 2008-02-10
Hi there.

I'm running Gutsy 7.10 on a Sony Vaio VGN-SZ4XWN laptop.  

I've only recently started using Linux full-time but I'm starting to really reap the benefits.

Almost everything on the laptop is working yet I have a couple of kinks which I still need kinkered out; primarily the display modes.

I'm really struggling to get the VGA-output working for use with an external monitor.

The native resolution of the 13.3" laptop panel is 1280x800 (nVidia Geforce Go 7400) and it's configured via the 'Screen and Graphics Preferences' as an LCD Panel 1280x800 widescreen generic monitor using the nv driver.

I would like to be able to easily configure the monitor output to work at any resolution required either as a clone of the default monitor or as an extended desktop- either will do.

But I'm having trouble getting an output to it.

At the moment I'm trying to get it working on a Sony Bravia KDL-26S3000 LCD TV with a native resolution of 1366x768.  

I'm assuming that to configure it, it should be as easy as clicking on 'Screen 2' in the preferences and setting up the display as an (in this case the nearest res. to the the native is 1360x768) and setting it as a 'Secondary Screen,' clicking on 'OK' and then logging out and in again to restart xServer.

However, when I do this I get forced into 'Safe-Graphics mode' which resets the video driver to a VESA-compliant one, which - in all honesty - I don't really know what it is...  

If I try setting a secondary output with the VESA driver then pretty much the same thing happens.

Other options I've set have really screwed up the screen and given me lined and coloured displays repeating the same image 4 times and I've had to reset the xorg.conf file with 'sudo dpkg-reconfigure -phigh xserver-xorg'.

Any advice will be greatly appreciated I desperately need this resolved by the end of the week.

After doing a bit of Googling I've realised that since the Vaio SZ-series has two graphics cards (one nVidia and the other an Intel I believe) it could be a problem with this?  For those unfamiliar with this series laptop there is a 'speed' and 'stamina' mode which basically switched between the two graphics cards to enhance power performance. I never use stamina mode and so the nvidia card is the one I'm interested in.

The output of my lspci is as follows:
-----------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
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
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
-----------------------------------------------

If you need any more information please just ask...

It also may be worth noting that the 'NVIDIA accelerated graphics driver (latest cards)' under the 'Restricted Drivers' is active, and when I try to decrease the brightness using the hot keys it crashes the whole display and I have to restart the laptop by holding down the power button.

Thanks.

---

### Post by JCoster on 2008-02-11
I have spent this morning trying to fix this still..

Using 'nvidia-settings' I have discovered that I can get one display to work at once.

However, if I try to configure the two displays simultaneously I get an 'Unable To Set MetaMode' error.

Just thought I'd add that..

---

