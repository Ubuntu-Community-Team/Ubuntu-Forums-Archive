---
title: "nVidia card not working properly"
date: 2007-07-05
forum: Multimedia &amp; Video
---

### Post by saggio on 2007-07-05
I installed Ubuntu a little while ago, and was using my ATi card - but after being unable to get fglrx working at all, I downgraded to an old spare nVidia card I had lying around. It's an 5900XT, and I can't get it to work!

I've followed about three different howtos to get the stupid thing to work, but other than make X unable to boot a couple of times (currently have it working), I've done nothing. When I boot into GNOME and attempt to enable the restricted module stuff I get this error message:

E: /var/cache/apt/archives/nvidia-glx_1%3a1.0.9631+2.6.20.5-16.29_i386.deb: subprocess pre-installation script returned error exit status 2

I don't know what to do! I was told that nVidia is alot easier to deal with than ATi as far as drivers go, but I'm running into the same stupid sort of problems that I had with my ATi card. 

Please help!

---

### Post by Trueno22 on 2007-07-05
Open terminal type:

sudo dpkg-reconfigure xserver.xorg

When you get to the video section choose to run the nv driver and finish the install. Reboot then try to install the nvidia drivers.

---

### Post by saggio on 2007-07-05
Alright, it says xserver.xorg is not installed. But that doesn't make sense, because I'm using X right now...!

What should I do?

---

### Post by NeoLithium on 2007-07-05
```

sudo dpkg-reconfigure xserver-xorg
```
not .xorg :)

---

