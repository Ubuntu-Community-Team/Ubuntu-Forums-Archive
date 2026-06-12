---
title: "Error: &quot;Cannot Display This Video Mode&quot;"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by zhinker on 2007-04-21
Just last night I (a brand new Ubuntu 6.10 user) was patting myself on the back on managing to fix the lack of audio on my PC.  I went to bed smiling.  Today I turned on my computer, saw Ubuntu booting normally, then right when the actual Ubuntu desktop started loading, I got a brief glimpse  of my Ubuntu background before the screen went completely blank except for the words "Cannot Display This Video Mode" glaring at me from the center of the screen.  

It looks like I somehow managed to change the settings to become incompatible with my monitor (a Dell E173FP), but I don't know what it was or how I did it.  The only thing I can think of is that I tried to install some 3D desktop program using the more advanced program installer (I forget what it was called, started with an 'S').  Since it didn't seem to work, I decided to uninstall it.  The computer didn't mess up at once of course, but it (if it is the cause) showed it's ugly fangs on reboot.  

But it's not all lost, I can still access the Ubuntu desktop in the safe mode, but of course I can't install or uninstall anything.

Please help!

--a noob in need is a noob indeed

---

### Post by taurus on 2007-04-21
Boot into recovery mode and either post your /etc/X11/xorg.conf here.

```
cat /etc/X11/xorg.conf
```
Or reconfigure your X again.

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by zhinker on 2007-04-21
> **taurus said:**
> Boot into recovery mode and either post your /etc/X11/xorg.conf here.

```
cat /etc/X11/xorg.conf
```
Or reconfigure your X again.

```
cp /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak
dpkg-reconfigure -phigh xserver-xorg
```

Thanks, it worked beautifully, I just had to do another reconfigure after that.

I used
```
sudo dpkg-reconfigure xserver-xorg
```

---

