---
title: "Please help - X completely died."
date: 2007-07-31
forum: Multimedia &amp; Video
---

### Post by NobleSavage on 2007-07-31
I just installed Feisty.  Everything was fine.  I tried the "restricted drives" and then enabled the desktop effects.  After a reboot it worked fine.  Upon the next reboot I could only get the smallest resolution.  I figured something was wrong with the proprietary nvida driver so I clicked to uninstall the restricted driver.   Then upon reboot the login screen looks normal, but when I log in I get a blank screen.   

I can only log in by switching to an xterm session at login. I can edit the /etc/xorg.conf file that way, but I can't paste the entire contents here for inspection -- I have to switch to a different computer to use the web. 

My video card is a GeForce FX 5200.   Any help is GREATLY appreciated.

---

### Post by kyphi on 2007-08-01
I would try to reload that driver.  I assume that it was the nvidia-glx driver.

After you have done that, try

```
# nvidia-glx-config enable
```

Try that first and good luck.

---

