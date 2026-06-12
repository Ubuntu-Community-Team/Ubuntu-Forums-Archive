---
title: "Low Resolution 11.10"
date: 2012-02-09
forum: Multimedia Software
---

### Post by neandero on 2012-02-09
HI, I installed Ubuntu switching from windows xp. the resolution I had was 1280x1024 but now i'm stuck with only 1024x768. I did cvt, I did xrandr, I did all of that but every time I reboot I'm back to 1024x768 with error:
Could not apply the stored configuration for monitors.
I always have to go into .config and delete monitors.xml.

may someone please guide me how to get a better resolution.. 
thank you all,

---

### Post by neandero on 2012-02-09
oh yes, I solved it by following a post by "kevdog" at: [http://ubuntuforums.org/showthread.php?t=1907702](http://ubuntuforums.org/showthread.php?t=1907702)

well, here is what I did:

at terminal type: sudo nautilus

go to /etc/X11

create new empty document and named it: xorg.conf

the above link by "kevdog" include a file named "xorg.conf.txt" you can find it at the very bottom of his post.

I copied the complete content of the file into my new created file the "xorg.conf.

I rebooted and then went into system display.. I got the display I wanted.

thanks kevdog, thanks everyone.

good luck,

---

