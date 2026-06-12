---
title: "Saturated/blotchy picture quality on my mythbuntu 14.04 box"
date: 2014-11-01
forum: Mythbuntu
---

### Post by ubn2usr on 2014-11-01
I use my myth setup to mainly watch bluRay Movies that I've ripped at home. Since recently moving house I've had to combine backend and frontend due to lack of space in the house. Now the  frontend picture is crisp and clear but then goes blochy like a small jpeg blown up to much then this repeats. This happens in both tv, recordings and video playback. As I'm stuck with the backend/frontend box is there a way to clear the picture up? The hardware isn't cutting edge, cpu E8400 @3.00ghz, Geforce gtx560 ti with hdmi out, 8 TB of sata drives. I'm going to upgrade the motherboard to a  asus z97a board and Intel Core i3-4330. Then use the onboard graphics on the cpu instead of a legacy card sometime in the near future but would like to find an answer to this problem and prevent it happening in furture builds

---

### Post by khPWXxF on 2014-11-01
First questions anyone will ask:
Anything in the frontend log?
Which drivers are you using?  14.04 uses nouveau by default and if you switch to nvidia it chooses (or chose for me) 311 nvidia which with my 8300 graphics were unstable.
Are you using vdpau?
Phil

---

### Post by ubn2usr on 2014-11-01
Hi Phil,
Thanks for the reply Phil. I'm using Nvidia drivers, version below plus some extra info. I just enabled vdpau so I will see how that works through the day. 
Is their a setting that you'd recommend, OpenGL or vdpau high Quality, Normal, Slim or vaapi?
Nvidia driver version 331.38
```

server ver number 11.0server vender version 1.15.1
nv-CONTROL Version 1.29
```

xorg.conf.06052014
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Extensions"
	Option	"Composite"	"Disable"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"DPI"	"100x100"
	Option	"NoLogo"	"1"
EndSection
```

---

### Post by khPWXxF on 2014-11-02
Anything in /var/log/mythtv/mythfrontend.log at the time ?
Do you have an  /etc/X11/xorg.conf?   There's a process somewhere which renames it xorg.conf.mmddyyyy (I see yours did on 5th June!).  I've not found out what process does it but if you copy your xorg back there and make it immutable then you'll frustrate it.
Use the vdpau - start with slim.
Phil

---

