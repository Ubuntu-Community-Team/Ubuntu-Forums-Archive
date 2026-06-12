---
title: "Drivers etc to connect from laptop to tv via HDMI"
date: 2013-11-10
forum: Multimedia Software
---

### Post by kfehr911 on 2013-11-10
Well I just converted my laptop to Xubuntu.  I very pleased.  My laptop has a hdmi out port and I tried to connect to to my HDTV.  No signal.  Can someone point me in the right direction so use the HDMI port.  Thanks

---

### Post by sanderj on 2013-11-10
No drivers needed.

On Ubuntu (I don't know about Xubuntu) you can start "gnome-control-center", then choose Displays, then select your HDTV (or HDMI)

---

### Post by kfehr911 on 2013-11-10
That is not an option. It hasn't even recognized that there is an HDMI port. Hence why I thought I was missing a driver.

---

### Post by SeijiSensei on 2013-11-10
Make sure you have connected the TV to the computer before booting.  It may ignore the port because it doesn't see a display connected there.  In principle it should be "plug-and-play" but that may not always be the case.  

Also if you have a proprietary graphics adapter from NVIDIA or ATI, make sure that it is the adapter being used.  This is especially complicated on "hybrid" machines with both an NVIDIA or ATI adapter and an Intel one.  On one HP laptop I own, I had to disable the Intel chip in the BIOS to make sure the operating system relied on the ATI adapter.

Please post the results of the command "lspci | grep VGA" in [noparse]```

```[/noparse] tags.

---

### Post by kfehr911 on 2013-11-11
It does recognize the TV when attached via HDMI but then the display crashes. Even if I return it to previous setting. I tried to rest the display through terminal but was unable. 

Maybe I'm using the wrong commands. 
Because it is a rescent install I reinstalled and tried again with the same results. 

As an after thought I realized that it may be the TV. It is Play Station 3d tv. 

Obviously I want to use the HDMI connection. I'm willing to try it on a different television 
But I'm not interested in installing xubuntu again. 

Could someone list the entire code necessary to reset the display to default or send me to a link that does. What tired didn't work.

---

### Post by SeijiSensei on 2013-11-11
Often the TV will not support the same resolutions as the laptop uses.  The machine I'm using to write this has a 1366x768 native display, but that isn't a resolution that my Sony Bravia supports.  I can display at 1280x720 on the TV since that is a standard "HD" resolution.  Take a look at the TV's manual and see what resolutions it supports.  Try to find one that works on both displays.

---

### Post by Yellow Pasque on 2013-11-11
You still haven't told us what laptop you have, and what GPU it contains:
```
lspci | grep VGA
```

---

