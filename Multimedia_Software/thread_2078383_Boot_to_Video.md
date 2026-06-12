---
title: "Boot to Video?"
date: 2012-10-30
forum: Multimedia Software
---

### Post by albertnet on 2012-10-30
Hi everyone, this time I can't find any hint on how to run a string search about this topic. What I need to achieve is to play into a loop a video as soon as the PC boots up, I think there should be a dedicated distro for this purpose but can't seem to find any. The sole idea is to create a marketing display and that the client/user won't have to tinker with it but to only turn it on. Also, if the client/user would like to play a diferent video, he/she would only need to swap the sd card and turn on the video display. Is it possible?, What distro do you recommend? It's no secret that ubuntu have some issues by playing video, this being not as smooth as it runs on other OS's, so if you know of any distro who can play videos smoothly or if there's any distro created specifically for this use, I'll be glad to hear from it. Thank you all for your support that I've always had and be well.

Ferno Rosas

---

### Post by Destructo47 on 2012-10-30
As far as I know, you can't just "play video" upon boot. That would mean that the BIOS loads a video and, tries to get either the CPU or the GPU to render it frame-by-frame. Is that what you want, or am I mistaken? As far as I know, that would require an obnoxiously large CMOS chip to accommodate the loading and rendering software (not to mention necessary hardware drivers), and still more complex if you want sound to play. Aside from On-screen branding (which is just a small cached image on the BIOS), there really isn't much you can do display-wise at boot.

---

### Post by albertnet on 2012-10-30
Hey Destructo47! Thank you for your answer. Actually no, what I meant was to know if there's a linux distro capable of doing such feat. I mean, I know any linux distro will (after some start up scripts) do it without any issue, but I just wanted to know if any out there knows of such distro designed to this commercial aplication. If not, then which is the best video reproduction distro and at the same time the lightest. 
After that I will had to ask for some help to play at startup such video but from an SD card, and if the customer/user wants to change animations it would only require to swap SD's :)

I hope I explained it well enough. hehe

---

### Post by Destructo47 on 2012-10-31
Thanks for clarifying that. Unfortunately, there are no Linux distributions capable of doing that without making it a hassle. Looking through the descriptions on [_Wikipedia's list of Linux distributions_]("http://en.wikipedia.org/wiki/List_of_Linux_distributions"), I couldn't find one that matches your request. Granted, the list is long, so there's a good possibility I missed a few, even after looking over the list twice. You might want to take a look for yourself, because I don't see one on that list, though the relatively short descriptions might not yield the whole truth. My guess would be to look at distributions that focus on visuals & multimedia, or perhaps ones that focus on business, but again, my tired eyes are not finding any appropriate targets.

---

### Post by cybergalvez on 2012-10-31
you might be insterested in this [http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu02.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu02.htm)

---

### Post by Scott Goodgame on 2012-10-31
If you want to boot into x you could put vlc xxx.avi in your startup apps, just be sure you configure vlc to go fullscreen and loop.
   Scott

---

### Post by albertnet on 2012-11-10
Thank you for your answers but my dear friend Cybergalvez just gave me the perfect answer, thank you! That's precisely what I was looking for, I mean, I was considering an option similar to what Scott Goodgame proposed, but this is the solution to all my needs. Now I can run some searches to see what I can find, now that I know the name of what I'm looking for. The name is a kiosk sistem, so in that order, Does anyone knows of a box with a kiosk system? This is because I was told there was a little box around $100.00 dollars that behaved just the way I needed but I didn't know what to look for.

---

### Post by Merrattic on 2012-11-10
XBMC (the distro) will do this with a bit of scripting.

The old Geexbox (1.2.4) can be setup to do this also

---

