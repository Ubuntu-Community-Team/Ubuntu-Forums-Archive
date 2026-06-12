---
title: "Logitech Quickcam Chat, Skype, video requirements"
date: 2008-03-04
forum: Multimedia &amp; Video
---

### Post by arch0njw on 2008-03-04
Are there video card or xorg.conf requirements to get a webcam to work with camorama, skype, or ekiga?

My cam is a "Logitech Quickcam Chat" (ID 046d:092e Logitech, Inc.).

I have a laptop with these specs that just doesn't seem to want to play nice with the cam:
-- hp pavilion ze5500 | Kubuntu 7.10 32-bit
-- Intel 2.66 Ghz | 1Gb RAM | ATI RS200/RS200M IGP 340M

The issues in order are:
* camorama:  just hangs at start.  I see the controls, but nothing is clickable and the capture box is frozen
* skype: testing the video hangs skype; no video available during chat
* ekiga:  testing the video hangs; have not yet tested a call

I had a Logitech Communicate STX and it mostly worked -- it would crash after about 20 minutes of use with skype, and would not work with camorama or ekiga.  The integrated mic seemed to cause problems if I used it, so I exchanged it for the "Quickcam Chat" which does not have an integrated mic.

I took the Quickcam and hooked it up to the following system and it worked:
-- Asus P5W-DH, Intel E6750, Corsair Ballistix 2x1GB 1066, Seasonic M12 500w
-- EVGA 7900 GS KO, Samsung 204B
-- Creative Audigy (yes, just the basic)
-- Kubuntu 7.04 64-bit | Windows XP 32-bit

On system 1 I have had a lot of issues with the graphics card because it is (1) an ATI, and (2) it is really old.  I have managed to get the "ati" driver working, but am now wondering if there are special settings in the xorg.conf that need to be made to support a webcam and any rendering it needs to do.

Help on this would be enormously appreciated.  Please let me know if there is any other information that would help.

---

### Post by itix on 2008-03-04
I have no idea waht it might depend on. I have Ubuntu 7.10 with an unsupported logitech quickcam for notebooks that works with no probs at all in skype, and yet yours is supported and does NOT work. This is odd.

---

### Post by arch0njw on 2008-03-04
> **itix said:**
> I have no idea waht it might depend on. I have Ubuntu 7.10 with an unsupported logitech quickcam for notebooks that works with no probs at all in skype, and yet yours is supported and does NOT work. This is odd.

Do you have an ATI graphics card?  If so, can you post the "Device" section of your xorg.conf?

I might be on the wrong path, but I am highly suspicious of the graphics card.

---

### Post by itix on 2008-03-04
```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
```

Intel for what I can tell, and believe me, it sucks big time. It has this strange dual buffer system with a blue underlayer and it's so ridiculously worthless that if I start any video bound application, the entire GUI becomes useless. I can't do anything without closing down the video.

---

### Post by arch0njw on 2008-03-04
itix - thanks.  That looks about like my xorg.conf for my "ati" settings.  I found something elsewhere that I'm going to try later when I have time.

"After putting options (such as "VideoOverlay" "on" and "TexturedVideo" "on") to xorg.conf (see [http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400](http://www.thinkwiki.org/wiki/ATI_Mobility_Radeon_X1400)), I was able to enjoy video call with my family."  -- I'll follow up on this thread if that works or leads me to something that does work.

---

### Post by AegisTalons on 2008-03-04
You may want to try loading a module named V4L2 (video fore linux 2).

in your xorg.conf:

```

Section "Module"
    Load           "v4l2"
EndSection
```

see if that helps, obvious have v4l2 installed. for more info just google v4l2 on how to install, really need to start homework.

---

