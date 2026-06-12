---
title: "[Gutsy] No DRI, FireGL V5250"
date: 2008-01-23
forum: Multimedia &amp; Video
---

### Post by Crackh34d on 2008-01-23
Hello,

I have a Thinkpad T60p with a FireGL V5250, comparable to a ATI Radeon X1700. I installed Gutsy 32 bit alternate, but X wouldn't start. So i downloaded the fglrx-driver from a repository and put it on my USB-stick. Then I installed the fglrx-driver in recovery mode, and now almost everything works. 

It is just that I need xserver-xgl, which sometimes takes up to 400 mb RAM, and I have no DRI. So I tried installing the newest 8.1 version (Which supports AIGLX) with the help of the wiki. But it failed, when I got to my desktop everything was terribly slow and when I tried to enable desktop effects my screen got all scrambled. 

I also tried Envy, same result. 

The 7.10 live-cd won't even get me to the desktop. 

glxinfo gives me this: 

bart@Ubuntu:~$ glxinfo
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)


But I'm pretty new to Linux, so I would appreciate some help on this :)

Regards,

Bart

---

### Post by Crackh34d on 2008-01-23
Topic kick :)

---

### Post by Crackh34d on 2008-01-25
No-one?

---

### Post by unbuntu on 2008-01-26
I wish I could help.  I have a T60P (FireGL 5250) as well and currently running XGL with the Ubuntu restricted driver.  I've been cautious in upgrading to the newest driver as I heard bad things about this version.  Maybe wait for another 10 years and hopefully they will come up with a driver that sucks less...sigh...

---

