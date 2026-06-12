---
title: "Jumbled-up frontend"
date: 2009-03-27
forum: Mythbuntu
---

### Post by J0ris on 2009-03-27
Hi,

I have just done a fresh 8.10 install with mythtv on top. I used the Mythbuntu control center to set everything up and got as far as configuring the backend (with a working GUI). When starting up the frontend, however, I just get a jumbled up mess of a screen. I suppose there is some config setting within the myth frontend setup screen but, as I can't get to it, how do I get out of this mess? Also, the backend config user interface which is simular in appearance to the frontend, works perfectly fine, i.e. not jumbled up. 
I did have mythtv working before on this hardware setup with one difference, you guessed it, the screen. The current one has a higher resolution (24") and a different aspect ratio (16:10).

Thanks for any help,
Joris

---

### Post by itlarson on 2009-03-27
What is the resolution?  Is it a HDTV or a computer monitor?

---

### Post by J0ris on 2009-03-28
It's a computer monitor running at 1920x1080. Apart from that, about the same setup you've got (mb and cpu).

---

### Post by itlarson on 2009-03-28
Warning: I'm no hacker, but this is what I would try.  Boot from a live CD, or to the console, rename /etc/X11/xorg.conf, then reboot.  When X starts and doesn't find xorg.conf, it will probably be able to figure out something that will work, 800x600 if nothing else.  Then you should be able to start nvidia-settings, and fool with settings.  If xorg fiddling is required you need someone more experienced than me.

---

