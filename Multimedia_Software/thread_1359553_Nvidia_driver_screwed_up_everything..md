---
title: "Nvidia driver screwed up everything."
date: 2009-12-19
forum: Multimedia Software
---

### Post by tominated on 2009-12-19
Hi guys,

I FINALLY got my mythbuntu box set up last night (asrock ion 330 barebones), and this morning I activated the nvidia drivers that it recommended. That's where it went downhill. I can no longer do anything because of massive graphical artifacts, freezing, etc. How can I disable it, and is there a guide on installing the newest driver nvidia is offering for linux (i think it is 190 something)?

Thanks in advance!

---

### Post by RedSingularity on 2009-12-19
Before you go any further lets get you some working graphics.  Can you get into a command line?

---

### Post by tominated on 2009-12-19
well, graphics worked fine using the open source driver, but i just installed the 190.53 driver manually, which helped (it actually ran), but i still got some artifacting and it just randomly went back to the login screen after a few minutes. I logged in, and the menu thing didn't open. i could right click the desktop and open things, but they had no window controls. i'm doing an update now, which might help, but we'll see, i guess

---

### Post by tominated on 2009-12-20
OK, i have tried multiple things and as soon as any nvidia software is introduced, the whole thing goes down the sh*tter. I am doing a memtest now, and if that doesn't work i will lower the amount of ram dedicated to gfx

---

### Post by tominated on 2009-12-20
Memtest showed no errors. Changing video memory does nothing, and I am on my 50 bazillionth install. Currently using a very minimal version of ubuntu described here: [http://xbmc.org/wiki/?title=XBMCbuntu#Method_1a:_add_NVIDIA_repository](http://xbmc.org/wiki/?title=XBMCbuntu#Method_1a:_add_NVIDIA_repository). As soon as anything graphical appears, artefacts appear and it crashes. Something to do with nvidia just doesn't agree with my system. Might try get a replacement box.

---

### Post by RedSingularity on 2009-12-20
Post the output of 

cat /etc/X11/xorg.conf

While the problem persists.

---

