---
title: "Failed to load NVIDIA kernel module"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by chylee on 2006-06-17
I can't get into Kde when boot up my computer. What happens is it boot up with the splash screen showing my what is loading. But when it suppose to enter into the kdm it go's back to the splash screen. 

I try running the X server, that don't run. It did tell me that the NVIDIA kernel module failed to load. I did try to run xgl on my system and it did work but not 100%. So I don't use it but it is still there. Everything seems to ok until yesterday.

---

### Post by tseliot on 2006-06-17
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

and set the driver to "nv". If you don't know the answer to the other questions just press ENTER.

then type:
```
sudo /etc/ini.t/gdm restart (or "kdm restart" if you use KDM)
```

---

### Post by chylee on 2006-06-17
Yes that has sorted that. Thanks 

But I was wondering now I am using the "nv" in X server. If I decide to use xgl   would I have to set it up again.

---

