---
title: "Help With SSH"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by CaptnEvilStomper on 2009-02-07
Ok, here's my problem. I have a PC running Ubuntu Intrepid 64-bit and a Mac running OS X Leopard. I can connect to the PC from the Mac via SSH, and vice-versa, and everything works fine except I can't run any GUI applications - I get the error message "cannot start display" or something similar. How can I fix this?

Also, if I connect to my PC from my Mac, then open VLC and tell it to play a set of MP3 files, they start playing on the PC. Can I connect to the PC and
run VLC but have the files play on my Mac? Any help with either of these issues would be appreciated.

---

### Post by graysky on 2009-02-07
You can run GUI apps from the shell.  You can use VNC to control your X session (i.e. when you are physically logged into Gnome).  Alternatively, you can use [vnc4server](http://knoppmyth.net/phpBB2/viewtopic.php?t=19428) to setup a virtual desktop(s) that will run in parallel with your physical logins which you can access remotely.

---

