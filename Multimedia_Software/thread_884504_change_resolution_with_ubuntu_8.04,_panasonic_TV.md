---
title: "change resolution with ubuntu 8.04, panasonic TV"
date: 2008-08-09
forum: Multimedia Software
---

### Post by gggerard on 2008-08-09
Hi there,

After discovering that the DVI connection is not hot-plugable, now I've got the panasonic plasma to show ubuntu desktop as a 2nd display.

However, ubuntu autodetect-tool only offers a 1280x720 resolution. This is not the desired resolution, since I am only viewing a half of the desktop.

The native resolution is 1024x768. How can I get that resolution?

This is my xorg.conf.

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection




So, how can I change the resolution? Thxs!

---

### Post by overdrank on 2008-08-09
> **gggerard said:**
> Hi there,

After discovering that the DVI connection is not hot-plugable, now I've got the panasonic plasma to show ubuntu desktop as a 2nd display.

However, ubuntu autodetect-tool only offers a 1280x720 resolution. This is not the desired resolution, since I am only viewing a half of the desktop.

The native resolution is 1024x768. How can I get that resolution?

This is my xorg.conf.

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection




So, how can I change the resolution? Thxs!

Hi and what is the model of the graphics card?
Have you tried the command ```
gksu displayconfig-gtk
```

---

### Post by gggerard on 2008-08-10
Hi there, it is a radeon 9250. From what I have read, the old ATI driver might not be (or is not) compatible with newer ubuntues. So in that situation, the provided free driver is OK. It appears to be correct for me since I have activated the 3D acceleration.

I have tried the command you say (just few minutes ago). The panasonic model does not appears (it is a plasma px80). I have tried some other panasonic models that were similar in the name (p70 could refer to a px70 or pz70?), just some Generic LCD or MONITOR models, or the plugnplay option. In all cases the TEST button gave me an error (saying to check the drivers or something).

The driver of the grafic card was "none". I have tried the ATI, the RADEON and the VESA. None of them worked, even with the second display disabled. An error message ("check drivers and configuration") was given in all cases except in some cases when the second display was disabled, then an awful resolution with a grey background was shown for the main monitor (acer AL732), asking if I wanted to keep that characteristics or not, obviously not)

So the application displayconfig-gtk is still not working for me, although I guess this has to be the substitute of xorg.conf (and it looks pretty great).

Thanks for the idea. Any other suggestion?? I can smell the solution ...

---

### Post by gggerard on 2008-08-11
I have read to add the next sentence in xorg.conf
Option        "NoDDC"             "true"
"... Mobility 7500 uses DDC (Display Data Channel) instead of EDID (Extended Display Identification Data) and DDC is returning only one resolution. "

My ATI 9250 is probably already using EDID, so this option would be unsuccessful for me, wouldn't it?

- Or how could I add the resolution for the second display in xorg.conf??
- Or how could I introduce the panasonic px80 "model" in the displayconfig-gtk application??

---

### Post by gggerard on 2008-08-11
Ouch, I have remembered that indeed, since the pixels are not squared in the px80, the 720p resolution is indeed 1280x720.

If you know spanish, the explanation is in this thread
[forodvd.com]("http://www.forodvd.com/showthread.php?p=380532")

[I][COLOR="DimGray"]"La Panasonic espera una imagen 16:9 por HDMI en 720p, si le pasas una resolucion 1024x768 estás pasandole una imagen 4:3.
Que no te engañe la resolucion que tiene el plasma ya que los pixeles de la pantalla no son cuadrados por eso a pesar de tener esa resolución si que es panorámica."[/COLOR][/I]

So, the problem now is WHY if the resolution is correct, I am only seeing the half of the desktop. I do not understand the problem ... since this is another problem, I will post a new thread. I write the response also here because the "2nd display problem" is indeed solved.

Thanks!

---

