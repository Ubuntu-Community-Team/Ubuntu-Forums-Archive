---
title: "X Windows doesn't output to DVI on Radeon 9600 (or not an output my TV accepts)"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Contrarian on 2008-07-27
I just installed MythBuntu.  I have a Radeon 9600 and using the open source drivers for it.  It's connected to a pretty generic Dell monitor on the VGA port, and to the back of my HD TV via the DVI output.

During boot up and when I go to tty1-6, the display outputs fine to the TV on the DVI, but it doesn't when I'm in X/Gnome.  

What do I need to put in the xorg.conf in order to get xwin to output through the DVI to the TV?  Pointing me to a good doc on the topic would be appreciated as well.  I've searched around and found voluminous amounts of information, but nothing that's very particularly helpful or poignant.  

Thanks,

---

### Post by jpreston84 on 2008-07-28
I have pretty much the same problem. I had a working install of MythBuntu with a Radeon 7000. I swapped it out with a Radeon 9600 to make use of the DVI output, connecting that via an HDMI adapter to my 42" LCD TV.

Text/console output is fine, but any time X goes to initialize the graphic device, I get a blank screen and nothing more. I've tried open-source, frglx, and EnvyNG for getting the drivers installed, but nothing works.

(Is it just me, or has anyone noticed how many graphic problems there have been since the 8.04 release?)

Is the Radeon 9600 known to be incompatible, or in need of specific drivers?

---

### Post by warp99 on 2008-07-29
You need to use the aticonfig app and have the fglrx drivers installed to set dual head and add the additional options for this particular card in your xorg.conf:

```
sudo aticonfig --initial=dual-head --screen-layout=above
```

If you have this already setup then you can force the card into dual-head mode "on the fly" by using the "Dynamic Display Management Options" with aticonfig:

```
sudo aticonfig --enable-monitor=crt1,crt2
```

I use this all of the time on my Radeon 9600 since the card sometimes does not read the changes I made in the xorg.conf correctly. Once I force the card everything works normally. Type 'sudo aticonfig' by itself for the full list of available options.

---

