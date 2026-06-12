---
title: "Problems enabling 3D Graphics with NVidia Card..."
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by sojakfa on 2006-07-24
Ok, first up: I'm *very* new to linux, so please assume I don't know anything!

My machine has been sporting a Geforce FX 5600 for a while now and I downloaded linux this evening. I installed the drivers for it and then typed in 

```
sudo nvidia-glx-config enable
```

just like the drivers told me to. This is what I see:

```
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section from nv to nvidia.
```

So I type in that long string of code and this is what I get:

```
71d57e300cff49e57ecb74ff9b9036c1  /etc/X11/xorg.conf
```

So then I type in glxinfo | grep rendering to see if my 3d acceleration is on and get this:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
```

I'm not sure what to do from here. Like I said, I'm a linux noob and I followed all the instructions, not sure where it went wrong :(

---

### Post by X_X_X on 2006-07-24
Had the same problem,

I manualy edited the .conf file and changed the Driver from nv to nvidia. Drivers worked fine

However the system hangs whenever i try to reboot or shutdown. When the gui is exited and before i see the sutdown screen with all the services shutting down. I changed nvidia back to nv and all is fine again.

Can someone solve this???????????????

---

### Post by tseliot on 2006-07-24
Read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

---

### Post by sojakfa on 2006-07-24
You, sir, are awesome. It did the trick perfectly!

Now just to hammer out my other problems!

---

### Post by X_X_X on 2006-07-30
> **tseliot said:**
> Read my guide:
[http://www.ubuntuforums.org/showthread.php?t=139264](http://www.ubuntuforums.org/showthread.php?t=139264)

Ok problem solved with the system hand when i reboot or shoutdown

I solved by editing my grub menu and defaulting grub to vga=791 which puts me 1024*768 from the start and i have no hangs anymore and the slash is still on.

Here is what it looks like

title		Ubuntu, kernel 2.6.15-26-686
root		(hd0,0)
kernel		/vmlinuz-2.6.15-26-686 root=/dev/sda3 **vga=791** ro quiet splash
initrd		/initrd.img-2.6.15-26-686
savedefault
boot

Thanks for the guide teseloit include this in it as well for people that wanna have a pretty boot up screen.

---

### Post by tseliot on 2006-07-30
> **X_X_X said:**
> Thanks for the guide teseloit include this in it as well for people that wanna have a pretty boot up screen.
Unfortunately that doesn't work for everyone.

---

### Post by X_X_X on 2006-08-02
Cool

---

