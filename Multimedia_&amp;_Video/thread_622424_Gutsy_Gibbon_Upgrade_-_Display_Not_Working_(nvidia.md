---
title: "Gutsy Gibbon Upgrade - Display Not Working (nvidia, benq)"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by bodhi.peace on 2007-11-24
I'm new and usually figure things out on my own, but this one has me stumped. I need to get into Ubuntu if for no other reason than to backup the MySQL database on the website I'm working on.

I have a BenQ FP767 LCD with 1280x1024 native resolution and an Nvidia 6600GT w/ 128 mb.

I didn't expect anything to go wrong from Feisty to Gutsy. After the upgrade, the screen was set on 320x240 or 640x480 zoomed in on the upper 1/8 of the actual desktop, so I couldn't access the window to change the display resolution. I ran

```
sudo dpkg-reconfigure xserver-xorg
```

and restarted. Everything appears to go fine until it's just about to put up the init menu, then it flashes to the console and goes black again then it goes to "Ubuntu is running in low graphics mode."

From there if I push continue, same thing happens (black->console->black->console).

If I configure the drivers for both, same story. But if I use the VESA driver, then I see a woven black/white pattern with the confirm dialog partially showing in the upper left corner. However attempting to start with this configuration yields the same black flashes.

Again I ran

```
sudo dpkg-reconfigure xserver-xorg
```

and everything was correct.

Before I had been using the NVIDIA proprietary driver and had started out using Feisty with a CRT, then I had dual monitor with the CRT and LCD, and finally I was just using the LCD before I upgraded. I wonder if this information might help.

Thank you.

---

### Post by bodhi.peace on 2007-11-26
If I can't figure that out, how can I save the mySQL database?

---

