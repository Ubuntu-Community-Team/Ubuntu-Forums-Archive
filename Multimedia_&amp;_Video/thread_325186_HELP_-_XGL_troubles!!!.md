---
title: "HELP - XGL troubles!!!"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by ghstzr0 on 2006-12-25
HELP HELP HELP!!!

For some reason I just cannot get XGL to work on my system.  I have had it working many times in the past on this same computer!

I have FGLRX installed and working fine! (fglrxinfo reports so...)

I have followed many instructions - 'sudo apt-get install xserver-xgl' and then edit '/etc/gdm/gdm.conf-custom' and add the Xgl servon on the bottom...

Here is my /etc/gdm/gdm.con-custom:
```

[servers]
0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true

```

when I boot up and login in, XGL is nowhere to be found... fglrx is fully loaded and glxinfo reports direct rendering: yes...

WHY WONT XGL START???

HELP HELP HEPL !!!
](*,) ](*,) ](*,) ](*,)

---

