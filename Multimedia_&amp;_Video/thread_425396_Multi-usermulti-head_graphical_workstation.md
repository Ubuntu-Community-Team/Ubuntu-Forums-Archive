---
title: "Multi-user\multi-head graphical workstation"
date: 2007-04-27
forum: Multimedia &amp; Video
---

### Post by atomicfire on 2007-04-27
So i've got MythTV setup and working wonderfully. The trick was to NOT use a ATI video card, I dug out an old Geforce 2 MX440 and used nvtv, and everything worked on the first try.

Now i'm on to bigger goals. Technically this computer has 2 video cards installed, and one of the two cards can do TV out. What I want to do is use the TV out as an independent MythTV session that always only loads MythTV when the computer is powered on. Simple right? I set GDM to autologin the used mythtv, then set that user's autoexecute on login to mythfrontend...I already have that done. Now I want to have the other video card run an independent GDM session so another user can log in at the same time and use the computer.

So this is like a terminal server....except not using seperate client computers. Essentially 2 people would be using the same one computer at the same time. Controls are not a problem because MythTV is controller by a wireless gamepad, and mouse and keyboard can be used for the other login session.

I'm pretty sure it can be done, just how would I accomplish this?

Thanks

---

### Post by cogadh on 2007-04-27
I'm not sure how you would do it, but I would think you could do it by having Mythtv launch in a seperate X session from the desktop login (i.e. Mythtv is on terminal 3 while the desktop login is on terminal 1).

---

