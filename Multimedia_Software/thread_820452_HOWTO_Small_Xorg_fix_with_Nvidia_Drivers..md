---
title: "HOWTO: Small Xorg fix with Nvidia Drivers."
date: 2008-06-06
forum: Multimedia Software
---

### Post by skymera on 2008-06-06
Hi,

It may not apply to all of you but when i use the Nvidia driver Xorg seems to use a lot of CPU, when watching videos etc. Also it uses a higher amount of RAM.

I found a fix by pure chance (Well, it worked for me.)

```
 gksudo gedit /etc/X11/xorg.conf 
```

Under the secton "Device" where all your graphics info is, add this:

```
 Option "UseEvents" "on" 
```

That's it! It worked for me, might not for you. Just something i thought was useful

[ Source ](http://www.redhatmagazine.com/2007/11/20/tips-and-tricks-why-does-xorgs-cpu-usage-shoot-up-when-using-nvidias-driver/ )

---

### Post by kpkeerthi on 2008-06-06
Thanks for the tip.

---

