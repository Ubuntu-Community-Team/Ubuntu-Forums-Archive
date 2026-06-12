---
title: "Enable Svideo in Intel915"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by rosy_12 on 2008-01-02
How to enable S-Video in Intel915 board?

---

### Post by chichilalescu on 2008-01-02
you should know a little about xorg.conf

I've recently tried to get this to work, and I can only get a black and white image on the TV screen, because for the moment the i810 driver doesn't know how to handle a PAL TV. I assume it should work fine with NTSC tv sets (that have s-video inputs).

here's another thread on the subject, that you should read:

[http://ubuntuforums.org/showthread.php?t=27261](http://ubuntuforums.org/showthread.php?t=27261)
this is marked SOLVED, but I have no idea why, because I can't see any solution for the black and white output.

good luck

---

### Post by rosy_12 on 2008-01-02
We are using HDTV which supports NTSC & PAL formats.I need to see the output to the TV connecting the SVideo port of the Intel915 board to the TV input.Let me know how to configure to get the Svideo output.Do we need to configure it in xorg file?

---

### Post by chichilalescu on 2008-01-08
As I understand it, you have a TV with an S-video port.

I know that the i810 driver can be used for intel 915 cards, and I assume this is a laptop we are talking about.

to use the TV as a clone, you will need to edit the "Device" section of your xorg.conf, where the driver (and name) of your video card is specified. Add the following two lines:

```

Option        "MonitorLayout"   "TV,LFP"
Option        "Clone"           "True"
Option        "CloneRefresh"    "60"

```

If you want to watch movies on TV, use mplayer with the gl driver output, ("mplayer -vo gl <filetoopen>") otherwise you won't see the film on the TV screen. (this is what works for me).

I hope this works, otherwise you'll have to ask someone else. Good luck.

---

