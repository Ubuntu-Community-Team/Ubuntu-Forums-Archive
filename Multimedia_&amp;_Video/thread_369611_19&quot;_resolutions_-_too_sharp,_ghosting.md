---
title: "19&quot; resolutions - too sharp, ghosting"
date: 2007-02-24
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2007-02-24
Just got a new 19" flatscreen the other day. Booted up with my old xorg.conf, set up for a 17" CRT at 1024x768. Everything was pleasantly blurred, soft if you will, but I wanted to take advantage of the bigger screen space, so upped the res to 1280x1024. Now everything is just too sharp. Images on webpages come across all pixlelised and there's slight ghosting around everything. It's really not easy on the eyes.
Is this just the way things are with a bigger resolution or is there some way to get the best of both worlds - a nice sized resolution without the harsh, pixely display (and ghosts/shadows)?

---

### Post by taurus on 2007-02-24
Maybe you need to include the right horizontal and vertical refreshing rates for your new monitor in /etc/X11/xorg.conf.

---

### Post by pickarooney on 2007-02-24
It could be that. I ran xorg-xserver-configure (or whatever it's called), but it only gave me a very vague range of values 
```

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

```
Would I gain by specifying an actual value for the VerRefresh rate?

---

### Post by taurus on 2007-02-24
You need to look at your monitor to see what those values are.  Then, edit /etc/X11/xorg.conf and replace those old values with the values that your monitor supports/uses.

```
gksudo gedit /etc/X11/xorg.conf
```

See if that helps.

---

### Post by pickarooney on 2007-02-24
The monitor itself has nothign pertinent marked on it. These are its [stats](http://www.lcd-compare.com/moniteur-GENMJ9BNK-GENERIQUE-MJ9BNK.htm).
When I bring up the OSD it says **1280x1024, H 80.0KHZ  V 75.1HZ**
Should I just put those in as my Horiz and VertRefresh rates?

---

### Post by taurus on 2007-02-24
I believe those are the max values.  The monitor doesn't even come with a booklet or a manual?

---

### Post by pickarooney on 2007-02-24
Afraid not. It did originally, but when I opened the packaging the monitor was damaged, so I sent it back for a replacement. That replacement came back without the paperwork.

---

### Post by taurus on 2007-02-24
Can you look it up from the manufacture's website for that info?  I think this is the right place but it's in French, I assume.

[http://www.acheter-moins-cher.com/asp/produit100_rwt_p_168516.htm](http://www.acheter-moins-cher.com/asp/produit100_rwt_p_168516.htm)

---

### Post by pickarooney on 2007-02-24
Tha manufacturer is actually Nitstek, but I can't even get their website to load - just a blank white screen. I tried using the OSD-indicated values but it made no difference.

---

### Post by hikaricore on 2007-02-24
Hmm usually the ranges are marked on the back of the monitor on a little sticker.  >.<

---

### Post by pickarooney on 2007-02-25
All I've got is **Input 50/60 Hz, 1.44 max**

---

### Post by pickarooney on 2007-02-27
I've tried with a whole set of different H and V synch values but it's still the same. 
Is there any point reinstalling graphics drivers for this or is there any other way to soften the image a little?

---

