---
title: "Error: couldn't find RGB GLX visual!"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by AntiKris on 2006-06-11
Alright, guys.  I've got my FGLXR working, but no 3d.   I keep getting the above message when I enter fglrxinfo:  "Error: couldn't find RGB GLX visual!"  I've got the feeling that I'm close... real close.  

Not sure if it matters, but I'm running AMD64, with an ati x800.  Cheers.

---

### Post by campnic on 2006-06-11
comment out the line:
#       Load  "extmod"
in /etc/X11/xorg.conf

It worked for me, it hopefully will work for you.

---

### Post by AntiKris on 2006-06-11
Thanks, but that didn't work for me.  I've got the feeling that I'm actually missing something, but I'm not sure what.

---

### Post by Patsoe on 2006-06-11
I got it working only when I added the line "fglrx" (and don't mistype it like you did in the opening post :)) to /etc/modules. I don't understand why it helps for me. but it does... the only thing that's different I think, is that this gets the kernel module loaded at an earlier stage. *edit: oh, and this trick requires a reboot, too*

---

### Post by campnic on 2006-06-11
[QUOTE=AntiKris]Thanks, but that didn't work for me.  I've got the feeling that I'm actually missing something, but I'm not sure what.[/QUOTE]


Alright, how did you install?  I'd recommend doing it from the repos, because thats how i did it.  When I installed using the howto thats commonly followed, I got the same error you did.  Also, I got that when my driver was set to "vesa" in /etc/X11/xorg.conf.  Did you run aticonfig --initial when you instaled the driver?  Sorry, these are all in the instructions so give me more background on what you did.

---

