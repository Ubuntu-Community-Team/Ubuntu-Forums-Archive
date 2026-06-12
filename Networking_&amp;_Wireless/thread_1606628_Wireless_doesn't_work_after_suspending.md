---
title: "Wireless doesn't work after suspending"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by theorigamist on 2010-10-26
I was not a fan of the Unity interface, so I installed the full desktop edition of Ubuntu 10.10 on my Asus Eee PC 1000.  I don't usually turn my netbook off.  Instead, I just suspend it.  But after waking back up, the wireless internet does not reconnect.  I need to restart the computer to get wireless back.  (A hardware issue with my router won't let me use the wired connection anyway, so I haven't tested if this problem affects the wired connection.)

Any ideas?  The 'net on a netbook is kind of a deal breaker.  If I can't get this working, I'm probably going back to UNR 10.04.

Thanks in advance.

---

### Post by grahammechanical on 2010-10-26
Is there a keyboard key that you can press to switch off the wireless card? If so, try switching off wireless by the keyboard before suspending. 

Regards

---

### Post by TBABill on 2010-10-26
How long are you waiting for reconnect? In 10.04 mine reconnects pretty quickly after standby, but in 10.10 it took at least 20-30 seconds before it would even start to try connecting again. I don't know why and have since reverted back to 10.04 for that one and several other reasons. If you have waited minutes after standby then it is definitely something else. 

Do you have a hotkey to enable and disable wireless? Is it possible the soft switch is disabled at standby and needs to be re-enabled after?

---

### Post by theorigamist on 2010-10-26
Thanks!  There is a key to toggle the wireless card on and off (for any other Eee PC 1000 users, Fn+F2), and after toggling I was able to connect to the internet.  But it took over 1 minute.  This seems pretty silly.  That's not enough on its own for me to go back to 10.04, I suppose.  

TBABill, what were the other reasons that you went back to 10.04?  I'm debating it, and I'm sort of hoping that I'll find some workarounds for things like this to save myself the hassle.

---

### Post by TBABill on 2010-10-27
The wireless connection delay thing was just a nuisance, but I had wireless issues I could not resolve on one machine. Plus it was more sluggish in overall performance than 10.04, even with proprietary drivers installed. It just didn't quite snap as much, but others have had better speed with 10.10 so it is an inconsistency as far as I can tell. And other than a few minor changes there was little difference for me. I just didn't gain enough to want to stay with 10.10 when 10.04 is solid on any of my machines. 
 
One thing I did take from 10.10 was the new font. I use it in my browser and throughout the distro. I'm not sure how long I'll keep it like that but I like it for now. 10.10 was fine for the most part, but it just had some quirks I want to wait to get worked out before worrying about it, or I will wait for 11.04 has been out a month or so to try it. I don't like to do immediate release installs because they seem to be pass or fail on hardware and the first major update seems to care for a lot of those.

---

### Post by not_a_phd on 2010-10-29
Toggling fn+f2 worked for me as well (eee901 + ubuntu10.10 + manufacturer drivers). Is there a way to have this happen 
automatically when the system goes into suspend?

---

### Post by rg4w on 2010-11-01
> **not_a_phd said:**
> Toggling fn+f2 worked for me as well (eee901 + ubuntu10.10 + manufacturer drivers). Is there a way to have this happen 
automatically when the system goes into suspend?
This thread did it for me:
[http://ubuntuforums.org/showthread.php?t=1169016](http://ubuntuforums.org/showthread.php?t=1169016)

---

