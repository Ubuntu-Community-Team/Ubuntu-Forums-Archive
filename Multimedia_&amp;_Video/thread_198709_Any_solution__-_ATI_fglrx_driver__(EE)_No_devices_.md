---
title: "Any solution ? - ATI fglrx driver : (EE) No devices detected"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by franck.galbrun on 2006-06-17
I want to get 3d accel on a laptop with ATI Radeon 9200. lspci says: 
> 0000:01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility 9200 IGP

With the "ati" driver set in xorg.conf, everything works fine, but I don't have 3d accel of course.

I installed the lattest (8.25.18-2.6.15.11-2) xorg-driver-fglrx driver from the ubuntu repositories (I know there's an issue with it, but I would get it solved latter on) and changed xorg.conf:
> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Mobility 9200 (RV250 IGP)"
	Driver		"fglrx"
	BusID		"PCI:1:5:0"
EndSection

But X does not start:
> 
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1                           
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:54:44
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-268237
(EE) No devices detected.


I tried to comment BusID, reinstalled the fglrx driver from console having X not running and xorg device set to "vesa" (then changed xorg.conf of course). It did not help.

I would greatly appreciate any help!

Note: replacing "fglrx" by "ati" in the xorg.conf file does make X work normally (without 3d though).
Note 2: 6 Months ago, I had the same probem on the same laptop running Breezy. I could not solve it and had to use the orginal "ati" driver.

---

### Post by Galban on 2006-06-17
I'm not a expert but I think that you should edit your busID to "PCI:1:0:0" in your xorg.conf at your graphic card section. Thats probably why it's not detected. But even if you make it to be succesfully detected,  dont be surprised to still dont have 3D acceleration [-X  , because I guess you are gonna be victim of the "libGL.1.2.so" problem found in the Ati's fglrx drivers (8.25.18 ) on Ubuntu repositories or even those found at Ati's web site. Let's start trying to get detected your card with fglrx drivers.

```
sudo gedit /etc/X11/xorg.conf
```

add this (in red) to your graphic card section:

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9200 SE (RV280)"
Driver "fglrx"
BusID "[COLOR="Red"]PCI:1:0:0[/COLOR]"
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
Option "UseInternalAGPGART" "no"
EndSection

Save, then reboot.

---

### Post by franck.galbrun on 2006-06-20
Thanks for your reply. I did try this, but it did not help. I also tried to install the (8.24) driver directly with the ATI installer as explained in [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) (method 2), and still got the "No devices detected" X error.

I tried to use the ChipID option of the xorg.conf file, setting it to the ID of my chipset. Nothing. Setting it to the ID of another Radeon 9200 chip, it just froze the computer so that I had to desconnect and reconnect the battery to get it boot again (so now I wouldn't try again with another ID!).

So I am just wondering: does anybody got an ATI Radeon Mobility 9200 IGP to work (or event only be detected) by the fglrx driver ? It is on the compatibility list indeed.

---

