---
title: "nvidia - This driver is activated but not currently in use (compiz fails)"
date: 2011-08-25
forum: Multimedia Software
---

### Post by Laen on 2011-08-25
I have a geforce 8400GS and nvidia-current installed.

However, the Additional Drivers app advises that "No proprietary drivers are in use on this system" and that the driver is activated but not in use.

I know other people have complained about this problem, but for me this is breaking 3D content and I can't get compiz to work either.

When I try to start compiz manually (compiz --replace), I get this error:
```
compiz (code) - Fatal: Couldn't open display
```

My Xorg has nvidia as device driver.

I'm using the NVIDIA X Server settings program to setup my two monitors, so I know that this is what is in use.

In addition to the compiz problem (which I can get over), sometimes I can see the desktop background through the active window. It's hard to explain so I'll take a screenshot when it happens again.

Things I've tried:

1. Installing nvidia's latest drivers - The installer was extremely picky, constantly complaining about other modules and drivers. After I finally managed to remove everything it didn't like and install it, X wouldn't load.

2. Reinstall nvidia-current - tried multiple times with no change.

3. Link /usr/lib/xorg/modules/extensions/libglx.so to /usr/lib/nvidia-current/xorg/libglx.so.270.41.06 - didn't make a difference.

Any suggestions would be very welcome.

Thanks!

---

### Post by realzippy on 2011-08-25
You should have a look at your Xorg.0.log....

---

### Post by Laen on 2011-08-25
Unfortunately there's no errors there.

I think to enable compiz you have to find "Desktop effects" in System -> Preferences, but there's no such thing there.
It's also missing from the Appearance applet.

---

### Post by realzippy on 2011-08-25
Do you use xinerama?

---

### Post by Laen on 2011-08-25
Did use it before, but disabled it to see if it does anything.
I think it did make a difference because I can now see the 3D screensavers (GLCells, GLMatrix, etc) which would only show a blank screen before!

I'm using TwinView.

Link to the generated xorg.conf:
[http://pastebin.com/N4DXNzuB](http://pastebin.com/N4DXNzuB)


Thanks for trying to help!

---

### Post by realzippy on 2011-08-25
maybe you should test adding a virtual resolution...

---

### Post by realzippy on 2011-08-25
Also your xorg.conf seems to be a little messed up due to formerly using
xinerama.Afaik you do not need 2 device or screen sections for twinview,only 2 monitor sections.Would run nvidia-xconfig to create vanilla...

---

### Post by Laen on 2011-08-25
> **realzippy said:**
> Also your xorg.conf seems to be a little messed up due to formerly using
xinerama.Afaik you do not need 2 device or screen sections for twinview,only 2 monitor sections.Would run nvidia-xconfig to create vanilla...

You're right about it being messed up. The nvidia app was merging changes to the xorg.conf by default instead of wiping it.

Cleaned it up and figured out my problem with compiz.

It couldn't start because the $DISPLAY var was not set since I was trying to run it from terminal...
Why it didn't start with Gnome I'm not sure.

That said, using xinerama was throwing me off and causing problems with the opengl screensavers.

It ended up not having anything to do with the nvidia driver not being in use message.
That seems like a bug which doesn't affect me at this point.

Thanks for your input, realzippy!
I'm pretty sure the cleaner xorg.conf and compiz will prevent that other annoying problem I was having with the background bleeding through the active window.

---

