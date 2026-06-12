---
title: "Ubuntu and Sharp AQUOS HDTV (1366 x 768 resolution)"
date: 2006-08-12
forum: Multimedia &amp; Video
---

### Post by Dralt on 2006-08-12
I would like to connect my Ubuntu laptop to my HDTV...the native resolution of the TV is quite unusual: 1366 x 768

What do I need to do to make that work?

---

### Post by tseliot on 2006-08-12
How will you connect it to your PC? Through a VGA port?

For the resolution you can try this guide:
[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)


OR this one (read where it says "Getting the Right Mode for an LCD monitor"):
[https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration](https://wiki.caosity.org/tiki-index.php?page=X%20Server%20Configuration)

---

### Post by Dralt on 2006-08-12
I could do VGA or DVI...the card is an ATI x1400...I'll check your guides...

---

### Post by Dralt on 2006-08-12
Also, the problem is that I do not know which vertical frequency is supported at the native resolution of 1366x768...the Sharp specifications don't say...

The exact model is LC-37D5U...

I was told the EDID structure built into the firmware reports 1280x1024 at 60Hz as the maximum resolution.

---

### Post by tseliot on 2006-08-12
> **Dralt said:**
> Also, the problem is that I do not know which vertical frequency is supported at the native resolution of 1366x768...the Sharp specifications don't say...

The exact model is LC-37D5U...

I was told the EDID structure built into the firmware reports 1280x1024 at 60Hz as the maximum resolution.

If it's LCD the refresh rate is 60hz

you can set the resolution by following those guides.

And BTW you can also disable EDID

---

### Post by Xvani on 2007-03-30
So every time I want to connect my HDTV or switch monitors (which is EVERY DAY, since I have different monitors at home, on my laptop, and at work) I have to manually config the xorg.conf file?

that SUCKS


Or is there another solution?

---

### Post by PRGUY85 on 2008-01-07
I am trying to do the same thing and I have been able to have the correct resolutions working.  The problem is the HDMI connection with Ubuntu sets itself on Stretch mode and I am not able to remove it, so I cannot see the entire screen....Is there any way to turn off these auto-stretch mode or make the Ubuntu output signal work in some way that doesn't tell the TV to just stay on Stretch mode because it is a digital signal through HDMI?

---

