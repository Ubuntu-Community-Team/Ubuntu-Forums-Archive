---
title: "VNC &quot;no password configured for vnc auth&quot;"
date: 2008-03-25
forum: Mythbuntu
---

### Post by SteveOSupremo on 2008-03-25
Ok I've gone through the steps to enable VNC on my Mythbuntu box and I'm having problems getting RealVNC on my XP machine to recognize the password for the Myth box. 

I get the "no password configured for vnc auth"  any ideas?

SteveO

---

### Post by scottro on 2008-03-25
I know with Ultra VNC you have to uncheck something having to do with MS challenge response. 
You definitely configured the password on your Linux machine?  

Oh---you might have to do something like, if the LInux box has an IP of 10.10.10.2 something like this on the Windows box
10.010.10.2:1

(That :1 is the display.  On Unix and Unix like systems, you usually have to put the display number.  (At other times, I have gotten away with just using the port number, 5900, 5901 or whatever it might be, e.g., 10.10.10.2:5900)

---

### Post by SteveOSupremo on 2008-03-25
thanks Scottro

I tried that I haven't found anything about the MS challenge response

SteveO

---

### Post by scottro on 2008-03-25
That might just be for UltraVNC, so probably not worth looking into.  
The other thing, the :1 and :5900 (or whatever port it listens on) didn't work either? 

NOTE--the rest of this is the proverbial stab in the dark, just guessing.....

Of course, it is saying it's a bad password, and I don't remember off the top of my head, if that's what happens with a Windows machine going to a Unix-like system one or if the window just says failed login.  

Perhaps you could try to reset the pasword on the Linux box.  With tightVNC you do that by removing the .vnc/password (or some similar name) file, but I don't know about RealVNC.  Sorry I can't be more help.  
Darn, I was sure I'd nailed it with the :1 thing though.  (When you started VNCserver, did it say starting on display 1?  Maybe it's on a different number?  That's just another stab in the dark though.)

---

### Post by jbman on 2008-03-25
have you changed your xorg.conf at all i found a change to that causes these problems as well

---

### Post by nasha on 2008-03-25
Try TightVNC, ive had no problems with it, and havent needed to change anything to get it to work. Quick, easy and simple :)

---

### Post by pavel989 on 2008-06-16
TY!!!!, scottro

---

### Post by scottro on 2008-06-16
You're quite welcome.  But which of my various guesses turned out to be helpful?   :)

---

### Post by pavel989 on 2008-06-19
> **scottro said:**
> I know with Ultra VNC you have to uncheck something having to do with MS challenge response. 
You definitely configured the password on your Linux machine?  

Oh---you might have to do something like, if the LInux box has an IP of 10.10.10.2 something like this on the Windows box
10.010.10.2:1

(That :1 is the display.  On Unix and Unix like systems, you usually have to put the display number.  (At other times, I have gotten away with just using the port number, 5900, 5901 or whatever it might be, e.g., 10.10.10.2:5900)

---that

---

