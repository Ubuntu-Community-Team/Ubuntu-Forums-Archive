---
title: "VNC crashes when cutting and pasting?"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by tegwilym on 2010-04-08
I've had this problem for a while and wondering if anyone has an idea what is going on.  
I'm running 9.10 on a computer at home, and when I VNC into it from my Mac at work.  
When I do a right-click copy or ctrl-c, the vnc will crash and won't connect again.  I can reach the computer with SSH and reboot, but it's kind of annoying when it does this.  Has anyone seen this before and is there a fix?

Tom

---

### Post by tegwilym on 2010-04-08
> **tegwilym said:**
> I've had this problem for a while and wondering if anyone has an idea what is going on.  
I'm running 9.10 on a computer at home, and when I VNC into it from my Mac at work.  
When I do a right-click copy or ctrl-c, the vnc will crash and won't connect again.  I can reach the computer with SSH and reboot, but it's kind of annoying when it does this.  Has anyone seen this before and is there a fix?

Tom

Ooops...make that Ctrl-V not C.  you know what I mean!

---

### Post by cscat on 2010-04-15
It's so weird! I have the same problem... please can someone help?

---

### Post by tegwilym on 2010-04-16
> **cscat said:**
> It's so weird! I have the same problem... please can someone help?

Oh good!  It wasn't just me.  It's not the end of the world, but when I have to remotely reboot my machine so I can do a 'cut-and-paste' it gets kind of annoying.
When I reboot, it seems to work again, but eventually drops the VNC again.

Still better than Windows though!
:P

Tom

---

### Post by cscat on 2010-04-16
I found This is a bug for RealVNC. Now I am using UltraVNC, a bit slower but no problem.

---

### Post by snapper711 on 2010-04-19
This happens to me with UltraVNC... The VNC server seems to crash on the Ubuntu machine so I restart it with the "vncserver" command through a command shell... That way I can restart more elegantly... 

Anyone know why this is happening?

---

### Post by tegwilym on 2010-04-19
I did try to restart from ssh using vncserver, but that didn't seem to work either.  Maybe I need to try the same thing with UltraVNC?  Worth a try I guess.  
I just have to ssh to the machine and reboot, then I can cut and paste again, until it locks up....

Tom

---

### Post by muzzamo on 2012-07-22
Over 2 years later, on ubuntu 12.04, this is still occuring :-(

Anyone have any suggestions?

---

### Post by muzzamo on 2012-07-28
For anyone reading this, I discovered the problem was limited for me to using realVNC on windows. As a workaround, using ultraVNC for windows instead stops the problem from happening.

---

### Post by wildmanne39 on 2012-07-28
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

