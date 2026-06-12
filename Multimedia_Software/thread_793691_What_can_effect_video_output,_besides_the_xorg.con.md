---
title: "What can effect video output, besides the xorg.conf?"
date: 2008-05-14
forum: Multimedia Software
---

### Post by BetterSense on 2008-05-14
I was having a bit of trouble getting my Sony TV to display as a dual monitor via HDMI. I seemed to have hit on something that worked, and it was working fine. It totally was setup as a separate x-screen, compiz worked, everything. Life was good. FWIW, the TV would display everything like the regular monitor, including the bootup text and Nvidia splash screen. So I saved my xorg.conf to a backup.

Now, it's not working again. It alternates between juddering/tearing/morphing and not displaying anything at all. Furthermore, it shows nothing until after login. This is how it was behaving before, before I 'got it' working. 

I cross checked my xorg.conf with that that I saved when it was working, and it's identical. 

So, what could be causing this, besides things that change the xorg.conf? I don't suppose it's even worth messing with the Nvidia settings manager, since the xorg.conf hasn't changed since it was working. Bad Cable? Bad motherboard? Even bad TV?

---

### Post by hermes0710 on 2008-05-14
I don't know what it might be but for sure i know that nvidia-settings do effect the output. A .nvidia-settings file is both created in /root and /home/yourusername folder. Try reconfigure the second monitor through gksudo nvidia-settings

---

### Post by BetterSense on 2008-05-14
I started my computer up this morning, and it worked. It's leading me to believe the reason it works after being turned off for a few hours is my graphics card has cooled down. It stands to reason. But what should I do?

---

