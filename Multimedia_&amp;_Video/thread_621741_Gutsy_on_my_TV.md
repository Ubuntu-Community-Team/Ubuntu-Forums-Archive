---
title: "Gutsy on my TV?"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by dseybert on 2007-11-24
Hi all. This might be a stupid question , but I've done some Google searches and haven't found much to answer it, so here goes... I have a Sony Vaio (VGN-A150) running Gutsy. I don't have a real "TV out" port, just an S-vid and the VGA outs. I want to connect to my TV to use it as a monitor. I have a VGA to Composite (RGB) connector, but due to refresh rates I believe, I get a scrambled signal. I believe I need a driver to adjust refresh rates for the television, but have not been able to find anything. Can someone help me out, or at least tell me it can't be done? I don't have any programming experience, so wrting a driver myself is pretty much out of the question I imagine.

---

### Post by steefjeqv on 2007-11-24
Hi,

It can be done using modelines.
You need to edit your xorg.conf and add a "modeline".

The exact modeline to use depends on the following :

- Type of graphics card : Ati, Nvidia.....
- Driver used for this card : closed source, open source
- Type of TV : CRT, LCD, .....
- Connection types available on your TV : Scart, component, ....

I'm using a VGA to Scart (RGB) cable connected to a Sony FQ70 CRT television.

Greetings,
Steven

---

### Post by dseybert on 2007-11-24
- Type of graphics card : ATI
- Driver used for this card : open source, I think... It was included in Gutsy (ati - ATI Mach8, Mach32, Mach64...)
- Type of TV : Panasonic CRT
- Connection types available on your TV : scart (RGB)

How do I edit the "modeline" and what should it look like?

---

### Post by steefjeqv on 2007-11-24
Hi,

* Ati is the easiest type to set this config up.
One thing is required though : you need a low dot clock rate. Most of the ATI cards can do this, but not all of them.

* The driver should be good."ati" or "radeon" should be mentioned in your xorg.conf.

* It should work with your Panasonic CRT and RGB scart. Most importantly, you need a specific cable which is very difficult to find (buy). I had to solder it myself. Where did you find yours ? 

This setup is great for using your computer as a multimedia center, but if you need it for other use too it may be better to get your s-video out working.
This is mainly a single head setup. Once you've modded the driver, your computer screen has no image - only your TV will have image.

Greetings,
Steven

---

### Post by mt330404 on 2008-06-23
how do you do a "modeline"? I am not that good with scripts so if you reply, pleeeease pretend like you're talking to a 10 year old.. thanks :)

---

### Post by steefjeqv on 2008-06-24
Hi,

I've attached an example of an xorg.conf file.
Notice the section "Monitor", were you'll find the modeline.
The modeline in use is the "1024x576". This modeline is specifically intended for use with my Sony FQ70 PAL TV set (widescreen).

There are lots of modelines around on the internet (google).
[http://en.wikipedia.org/wiki/XFree86_Modeline]("http://en.wikipedia.org/wiki/XFree86_Modeline")
[http://www.mythtv.org/wiki/index.php/Modeline_Database]("http://www.mythtv.org/wiki/index.php/Modeline_Database")

To use a modeline, you'll first have to find out the native resolution of your screen (1024x768, 800x600,....), and than apply it by editing the above mentioned file by using your terminal :

sudo gedit /etc/X11/xorg.conf

Backup your original xorg.conf before you apply the modeline (in case things go wrong).

Greetings,
Steven

---

