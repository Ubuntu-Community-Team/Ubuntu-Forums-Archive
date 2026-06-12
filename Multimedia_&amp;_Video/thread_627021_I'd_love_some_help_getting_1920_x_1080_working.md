---
title: "I'd love some help getting 1920 x 1080 working"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by tobycatlin on 2007-11-29
Hi

I am sorry to post another 'I can't get my tele working' post. I have been reading through posts for the last couple of days and i have got myself pretty confused. I have tried lots of things suggested by lots of people. i have changed my xorg.conf to no avail

Heres my setup:
Core 2 duo
nvidia grforce 7600 GT graphics card
sony bravia 40" 1080p tele
Ubuntu gutsy

Now i have got the video card drivers working ok. compiz works and all seems well since i put this card in. I can run nvidia-settings but can only choose resolutions up to 1024x768. It recognises that it has a sony tv plugged in and i set the res to auto. I also looking in the screen and displays menu and chose a default panel at 1920 x 1080 and logged in and out. now i get a differnet range of resolutions but still no 1920x1080
here some of my xorg.conf:
<code>
Section "Device"
        Identifier      "nVidia Corporation G70 [GeForce 7600 GT]"
        Boardname       "nv"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Vendorname      "Generic LCD Display"
        Modelname       "LCD Panel 1024x768"
        Horizsync       31.5-48.0
        Vertrefresh     56.0 - 65.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G70 [GeForce 7600 GT]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1024    768
                Modes           "1024x768@60"   "800x600@60"    "800x600@56"    "640x480@60"
        EndSubSection
EndSection
</code>

I tried to add 1920x1080@60 to the list on 'default screen' and when i rebooted it said it was running in low graphics mode.

Any help would so much apprecated, thanks

toby

---

### Post by rboutros78 on 2007-12-12
I've actually gotten 1080p working two times now, once with Ubuntu Feisty and once with Gutsy. I'm trying for a third time now for Kubuntu Gutsy. I'll post my xorg.conf once I figure it out again. I don't know why I just don't save this file somewhere offline whenever I go to install a fresh new version. It always takes me forever to actually get it to work :confused:

---

### Post by nutz on 2007-12-17
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1920x1080"
	Horizsync	31.5-67.0
	Vertrefresh	56.0 - 65.0
	Modeline "1920x1080_60.00"  172.80  1920 2040 2248 2576  1080 1081 1084 1118  -HSync +Vsync
EndSection
```

Works with my 1920x1080 TV flawlessly.

---

