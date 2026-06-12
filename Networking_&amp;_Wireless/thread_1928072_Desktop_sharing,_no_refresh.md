---
title: "Desktop sharing, no refresh"
date: 2012-02-19
forum: Networking &amp; Wireless
---

### Post by ormeskirk on 2012-02-19
I recently upgraded from Ubuntu 10.04 through three releases to get to Ubuntu 11.10.  When I did, my SSH would not longer connect using Putty (it says connection refused by server).  Also, when I tried to connect to the Ubuntu box using VNC viewer on a Windows 7 machine via my LAN, it would connect but the screen would never refresh.  

If I used Pocket Cloud on my iPad I could see it doing everything on the actual screen the box is connected to, but nothing updated on the iPad.

So I decided to do a fresh install. . . it was due anyway. . . everything else works, but I have the same problems with SSH and Desktop Sharing.  

Any ideas?

---

### Post by ormeskirk on 2012-02-20
I got the SSH to work, I was putting in the wrong port.  No VNC viewer I use will refresh when connected.  It is always what is initially up on the screen.  If I am watching the screen the ubuntu box is connected to the changes are happening as I click or type, but it does not refresh in the viewer?!?!?

---

### Post by ormeskirk on 2012-02-20
Figured it out by reading the reviews of "vino" in the Ubuntu Software Center.  I guess vino does not play well with unity.  So I have switched to x11vnc & all is well.

---

### Post by krunge on 2012-03-02
> **ormeskirk said:**
> Figured it out by reading the reviews of "vino" in the Ubuntu Software Center.  I guess vino does not play well with unity.  So I have switched to x11vnc & all is well.
Glad you have x11vnc working. For reference, in some cases one gets no updates in x11vnc as well because the Xorg video driver has a bug with respect to the X DAMAGE extension. In cases like these (not yours) one needs to add the "-noxdamage" option to the x11vnc cmdline.

---

