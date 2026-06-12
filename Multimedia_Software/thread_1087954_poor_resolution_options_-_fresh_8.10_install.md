---
title: "poor resolution options - fresh 8.10 install"
date: 2009-03-05
forum: Multimedia Software
---

### Post by ambidextrousone on 2009-03-05
hey, as usual, you have my promise that i have searched every corner of the internet and have tried numerous solutions and fixes to no avail :(

ive started from scratch, deleted xorg, and im back to square one


Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


im using a nvidia Geforce 7600GS with the reccomended .177 drivers.
the issue we seem to be having is getting a more suitable reolution than 1024x768 - the screen we are running it on a 42" samsung plasma through DVI to HDMI. although it has already correctly detected this monitor in the nvidia x server settings, manually entering a resolution in the advanced settings either results in a very stretched looking appearence, usually combined with something similar to a desktop zoom effect

help :P ty

---

### Post by avrilrox on 2009-03-05
Try this command:

```
xrandr -s 1024x768
```

Change the resolution accordingly to your display.

---

### Post by ekidd91 on 2009-03-05
Extremely sorry for going completely off topic here, but can I just ask where your avatar is from ambidextrousone. Thanks, again sorry.

---

### Post by avrilrox on 2009-03-05
You should have sent him either a visitor message or a private message :p

---

### Post by ekidd91 on 2009-03-05
> **avrilrox said:**
> You should have sent him either a visitor message or a private message :p

yeah that's a good point, sorry!

---

### Post by ajgreeny on 2009-03-05
Try adding the detailed information on the display you have, and the resolutions you want, in the format like my* xorg.conf* shown below.  I had minor, but annoying problems in my test of 8.10, when the resolution was too big and I lost the lower panel.  Copying this info from a previous version of ubuntu, (6.06 I think), put everything right.  I am using an ati 9200SE card which has always been detected properly in the past but 8.10 got it wrong for the first time
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
            HorizSync    30-80
            VertRefresh    50-75
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    SubSection "Display"
        Modes        "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```
I hope this helps; I know it has in a few cases, so you may be another lucky one.

---

### Post by ambidextrousone on 2009-03-05
I tried "xrandr -s 1024x768" just to be reminded that the mode isnt availiable, although it has been very handy for when the screen goes all distorted when i try using a 16:9 resi :)

as for the change to xorg, which ive tried a few times tonight, it was always led to ubuntu going into low graphics mode.. i really am out of ideas

im still wondering if this has anything to do with the hdmi, because this is a problem im trying to sort for a friend, all my other ubuntu installs have been easy sailing in regard to monitor and resolution support.

---

