---
title: "ssh to execute X program remotely (different then most)"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by buminatrain on 2008-12-10
Ok, I've been searching on this but I'm having some difficulties (maybe I'm wording my searches wrong, or maybe the solution doesnt exist in the form im looking for(-: ).

First let me explain the situation,  I have a home studio powered by an amply equipped desktop running ubuntustudio 8.04, i have a slightly older laptop running standard ubuntu 8.10 which i plan on using to control the desktop.
 
  What i would like to do is use ssh to connect to my desktop from my laptop, and then i would like to call for my desktop to run an X program and have it run and display on desktop and mirror a display onto my laptop, so that basically im using the laptop as a remote control (it doesnt even need to display on the desktop so long as it is using the hardware of the desktop)  This is important so that it will allow me to use jack to route audio inputs and outputs hardwired to the desktop, start stop recordings, change mixer values, etc, etc remotely if im not in the control room.  I can accomplish this using VNC but i feel like i should be able to do it in a much cleaner way using ssh.

if anyone has any ideas it will be much appreciated!

---

### Post by rbrcurtis on 2008-12-10
I just tested, and ssh tunneling to open up an app graphically in shh works fine for this, at least with banshee.  It won't display on the local machine but audio outputs fine.

I personally use cygwin on my windows machine in order to do the ssh tunneling.  here's some instructions if you need help with that.
[http://pages.cs.wisc.edu/~dipiazza/cygwinformentor.html](http://pages.cs.wisc.edu/~dipiazza/cygwinformentor.html)

---

### Post by buminatrain on 2008-12-10
> **rbrcurtis said:**
> I just tested, and ssh tunneling to open up an app graphically in shh works fine for this, at least with banshee.  It won't display on the local machine but audio outputs fine.

I personally use cygwin on my windows machine in order to do the ssh tunneling.  here's some instructions if you need help with that.
[http://pages.cs.wisc.edu/~dipiazza/cygwinformentor.html](http://pages.cs.wisc.edu/~dipiazza/cygwinformentor.html)nn

ok, neither one of my machines is windows based and when i do ssh with X11 (quite successfully) i see the hardware of my laptop listed in my audio connections prefs, activating anything that makes sound produces no sound on either computer. thanks anyways though.

---

### Post by Dr Small on 2008-12-10
Why not just run:
```
ssh -X user@desktop
```

And then run your X program through the SSH session?

---

### Post by buminatrain on 2008-12-10
ok after resituating my desktop a few days ago my external sound card has apparently developed some issues, so it seems possible the sound would route out through the desktops hardware, sorry i didnt realize there was an issue on that box.  but does anyone know if it would be possible to display the x program on both machines?

---

