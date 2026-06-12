---
title: "Disable Graphics Card"
date: 2013-05-08
forum: Multimedia Software
---

### Post by darkeale on 2013-05-08
Hi,

I have a Fujitsu Siemens laptop with an ATI Xpress 200m graphics card.  The card kept crashing in Windows, and so I disabled it in Vista's Device Manager, and no it works fine (albeit with reduced resolution, but that's ok).  But with it disabled, I have no idea what the computer is using for the graphics.  But I would like to try the same thing in Ubuntu, because sometimes when I boot up ubuntu freezes with a blank screen before reaching the login, and I wonder if it might be because of the graphics card crashing as it does in Windows.  So how would I do the Ubuntu equivilent of Vista's disabling the graphics card in device manager?

Thanks

---

### Post by Yellow Pasque on 2013-05-08
I'm guessing that means you're using the generic VESA driver on Windows. You can do the same thing on Ubuntu by creating an /etc/X11/xorg.conf file:
```
Section "Device"
        Identifier      "Configured Video Device"
	Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Note that Unity probably won't run well with the VESA driver, since your CPU will now be used to do all the graphics acceleration. You might want to check out alternate desktop environments (xfce) that don't require acceleration.

---

### Post by darkeale on 2013-05-09
I got it to work by blacklisting the radeon module.  Would Lubuntu be a good choice?  Does it require acceleration?  Also in my bios there is an option for VGA Memory UMA Frame Buffer.  Default is 128MB.  If I set it to 256MB (the only other option) will that help things?

Thanks

---

