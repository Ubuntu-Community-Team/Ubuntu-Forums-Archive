---
title: "How to re-install AIGLX in Koala?"
date: 2009-11-25
forum: Multimedia Software
---

### Post by PlatosGimp on 2009-11-25
I am running a Dell Inspiron 9100 with Mobility Radeon 9600 and just installed a fresh Ubuntu 9.10. All went well and I as getting around 10,000 fames in 5 seconds with glxgears so I thought I could improve things with fglrx but that was a disaster. After removing it and reinstalling the open-source drivers with

sudo apt-get install xserver-xorg-video-all xserver-xorg-video-ati

and then

sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri

I now only get around 1000 frames in 5 seconds

So I ran compiz -check and get this

Checking for Xgl: not present. 


So I guess aiglx is not loading or something? Are there any suggestions as to how to get back at least the 3d performance I got on the clean install?

Or, do the latest ATI drivers work this card and Koala?

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]

Contents of xorg.conf

Section "Screen"
	Identifier	"Configured Screen Device"
	Device		"Radeon 9600"
	SubSection "Display"
		Virtual	3280 1200
	EndSubSection
EndSection

Section "Device"
        Identifier      "Radeon 9600"
        Driver          "ati"
        Option          "XAANoOffscreenPixmaps"
EndSection


Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection

---

### Post by apheren on 2010-01-29
I didn't install mesa, just remove the xorg drivers and everything runs pretty smooth. You just need a good xorg.conf I guess. And my graphic card is much older than yours, its 9000.

here
Option "XAANoOffscreenPixmaps", I guess you need to set "true"

---

### Post by Yellow Pasque on 2010-01-29
The OP probably had to reinstall xserver-xorg-core to get the open-source version of libglx.so back. fglrx/Catalyst installs a proprietary version of this file and leaves it there.

---

