---
title: "black tv screen on boot"
date: 2010-01-19
forum: Mythbuntu
---

### Post by linuxhippy on 2010-01-19
I'm new to mythbuntu...9.10 booted fine on my monitor, but when I hooked an S video cable into my Radeon card and just booted from my old CRT TV (old 4:3 Apex...it's mono) I got a black screen.  From my keyboard I was able to get into the GRUB screen and do a rescue boot to the login.  In the rescue mode I upgraded my system using my DSL and rebooted.  Same thing-black screen but I could get to a CLI login doing rescue mode boot.  From there I tried startx and got a blue screen...it didn't go back to the CLI.

How do I adjust this for low resolution?

EDIT:

Also, I can do an ssh from another pc on my network and get in that way too.

---

### Post by nickrout on 2010-01-19
What does /var/log/Xorg.0.log tell you?

---

### Post by linuxhippy on 2010-01-19
there's a lot of information in that file.  This stands out:

(II) RADEON(0): Output: VGA-0, Detected Monitor Type: 0
(EE) RADEON(0): Using CRT default
(II) RADEON(0): Total number of valid Screen mode(s) added: 0
(II) RADEON(0): Not using default mode "640x350" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "720x400" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "640x480" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "800x600" (vrefresh out of range)
(II) RADEON(0): Not using default mode "1024x768" (vrefresh out of range)

---

### Post by nickrout on 2010-01-19
I guess that the X server is unable to determine the right parameters for that TV.

You will need to amend your /etc/X11/xorg.conf - google for recipes for your particular model of card and CRT tv. I am not familiar enough with radeon to give you the exact incantation.

---

### Post by linuxhippy on 2010-01-20
aha, I was hoping it was that file and not my old TV!

---

### Post by linuxhippy on 2010-01-20
I made an xorg.conf file with Xorg -configure and moved the file to /etc/X11/xorg.conf...all the modules are commented out.  Are any radeon x300 modules included in mythbuntu?

---

### Post by nickrout on 2010-01-20
> **linuxhippy said:**
> I made an xorg.conf file with Xorg -configure and moved the file to /etc/X11/xorg.conf...all the modules are commented out.  Are any radeon x300 modules included in mythbuntu?

Its not going to self configure on a TV that offers no edid information. I suggested google I think.

---

### Post by linuxhippy on 2010-01-20
> **nickrout said:**
> Its not going to self configure on a TV that offers no edid information. I suggested google I think.

So, I need a new TV to record?  Are you sure about that?  I found this [here]("http://wiki.linuxmce.org/index.php/EDID"):

We decided that to use a consumer TV with a home theater PC (and still have HD video) it would be simpler to use manual output type/resolution configuration for all video output, no matter whether a TV or a PC monitor is used. 

************************************************************

This goes on to talk about manually specifying the A/V in a file (sounds like /etc/X11/xorg.conf

This is not from mythtv but linuxmce which sounds similar in some ways...it controls lights too, though.  Maybe mythtv is different.  I'm new at this and didn't know about EDID till you brought it up.

---

### Post by nickrout on 2010-01-20
Actually you do not need any sort of output device just to record! But obviously you do to watch :)

What you need is the correct xorg.conf to get tvout working on your radeon card. I haven't got a radeon card, so I can't test anything for you.

By googling I found this:

> In the "Device" section:

             Driver  "radeon"
             Option "TVDACLoadDetect" "TRUE"
             Option "TVStandard" "ntsc"
             Option "monitor-S-video" "TV-monitor"

In the "Monitor" Section:

               Option  "PreferredMode"  "800x600"

In the "Screen" section:

              DefaultDepth  24
              SubSection "Display"
                      Depth          24
                      Modes         "800x600"
              EndSubSection



I found this here: [http://www.x.org/wiki/radeonTV](http://www.x.org/wiki/radeonTV)

Quite why you want to use a mono TV is beyond me. Also ATi is generally regarded as a bad choice for mythtv, nvidia work much better.

---

### Post by Caps18 on 2010-01-20
I think you need to tell X (xorg.conf) what screen you are hooking up to it.  It should be 640x480, 60 Hz if it is a 4:3 SDTV.  

You may look into getting a VGA -> TV box.  They are probably really cheap on eBay.  It will allow you to use the same settings on your monitor as your TV.

edit: [http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac](http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac)

---

### Post by linuxhippy on 2010-01-20
Couldn't get the analog TV working with those additions to xorg.conf.  I think the TV I have is cheap and bulky.  Now that I have a pc with a tuner card in it, could I just buy a big widescreen LCD monitor and watch TV if my pc is on?

---

### Post by Caps18 on 2010-01-20
That is what I did, and it has worked out well.

Make sure you get a TV with the right display ports that you need.  If your computer has HDMI or DVI, make sure the new TV has that.  VGA would be the next option.  Just pay attention to the resolution, and know that your xorg.conf file has to be correct, no matter what TV you connect (I use 1920x1080 on every monitor I have).

If you bought a TV tuner card that does HDTV, it would be a good choice anyway.

---

