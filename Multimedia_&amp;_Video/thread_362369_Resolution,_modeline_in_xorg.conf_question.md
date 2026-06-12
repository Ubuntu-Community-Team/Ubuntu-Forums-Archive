---
title: "Resolution, modeline in xorg.conf question"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by MiniMe on 2007-02-15
Hello,

I have a question about setting the modeline in /etc/X11/xorg.conf

I managed to get my 22" LCD widescreen working at 1680x1050 and 1440x900 with my ATI radeon X800 pro by installing the ATI drivers and adding a MODELINE in xorg.conf under ' Section "Monitor" '.

I think the modeline is necessary only when the monitor doesn't send it's specs to the OS?

The modeline I added to get 1680x1050 going was:
ModeLine "1680x1050" 146.25 1680 1784 1960 2240 1050 1053 1059 1089 +hsync -vsync

My question is, what do all those numbers beside the resolution represent?

Is it correct that hsync and vsync are only for CRT monitors? Is it optimal to leave them there for my LCD screen? What are the "+" and "-" in front of hsync and vsync for?

Everything seems to work for me now but I'd like to uncover the mysteries surrounding this.

Thanks in advance!

---

### Post by brodiepearce on 2007-02-17
The other numbers are higher widescreen resolutions, I don't know why they're there, but you can tell just by looking at the numbers (E.g. 1680 .... 1050, 1784 ... 1053 etc.).

---

### Post by JymmyZ on 2007-09-12
I have a Samsung 940B 19" standard LCD (1280x1024, 60Hz) and a Samsung 206BW 20" widescreen (1680x1050, 60/70Hz) connected to an nVidia 7950GT and Gutsy Gibbon Tribe 5 did a great job of setting up most of the dual-screen details but it did not set the modelines for the widescreen correctly (I was stuck at 1400x1050) .  I searched around for a few days and finally found this post which solved my problem.  Thanks.
Now to figure out why I can't get desktop effects working...

---

### Post by dcstar on 2007-09-12
> **MiniMe said:**
> Hello,
.........
My question is, **what do all those numbers beside the resolution represent**?

Is it correct that hsync and vsync are only for CRT monitors? Is it optimal to leave them there for my LCD screen? What are the "+" and "-" in front of hsync and vsync for?

Everything seems to work for me now but I'd like to uncover the mysteries surrounding this.

Thanks in advance!
In a terminal:
```
gtf 1680 1050 60 **-v**
```

---

### Post by mhenry35 on 2007-09-13
What do all those numbers mean?

I found some documentation for the xorg.conf file, here is the link:

[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

I am still not able to get mine working, so it may be a trip back to Windows for me.

---

