---
title: "Can't download Nvidia-Settings,"
date: 2006-02-02
forum: Multimedia &amp; Video
---

### Post by POLO on 2006-02-02
I tried to install my nvidia drivers, so I did like the sticky ubove said, but it states nvidia-settings is not availible.

I tried to do the setup using:
[http://help.ubuntu.com/starterguide/C/ch04.html](http://help.ubuntu.com/starterguide/C/ch04.html)
but my Synaptic doesn't list (show) the nvidia-settings, but it does show nividia-glx

I have a BFG 6800 ultra oc, if that helps anyone.

I tried to do some reaserch on this, though I am very new to Linux.
Saw this thread and thought I might try this:
[http://www.ubuntuforums.org/showthread.php?t=122428](http://www.ubuntuforums.org/showthread.php?t=122428)

Or if any one knows an easy fix to this it would be greatly appreciated.  I am stuck on 1024x768 and it sucks.

---

### Post by MartinG on 2006-02-02
Have you enabled the extra repositories? And then updated?

In many ways the easiest way to do all this is with Automatix:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

---

### Post by POLO on 2006-02-02
[QUOTE=MartinG]Have you enabled the extra repositories? And then updated?

In many ways the easiest way to do all this is with Automatix:
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)[/QUOTE]

No I have not enabled the extra repositories, aka don't know how.
If you could please point or tell me how to do that it would be greatly appreciated.

Sorry, but I can't use Automatix.  I am using an amd64 processor.
Thanks though!

---

### Post by MartinG on 2006-02-02
[QUOTE=POLO]No I have not enabled the extra repositories, aka don't know how.
If you could please point or tell me how to do that it would be greatly appreciated.

Sorry, but I can't use Automatix.  I am using an amd64 processor.
Thanks though![/QUOTE]The guide you quoted ([http://help.ubuntu.com/starterguide/C/ch04.html](http://help.ubuntu.com/starterguide/C/ch04.html)) includes instructions to enable the extra repositories using synaptic (section 4.1.1), so do you mean you haven't followed them, or did you think I meant still further ones?  If you have followed them you should have all you need.

It may be (I use a 32-bit processor) that nvidia-settings is not available for AMD64, or maybe once you've enabled the repositories and updated that you will find it.  However, you don't *need* it for the drivers to work, so it's quite safe to install nividia-glx and run the configuration process in the first two lines of section 3 of the guide page.Then restart Gnome and it should be OK.

I do have nvidia-settings installed, but I never use it!

---

### Post by POLO on 2006-02-02
Thanks for pointing that out!  I will try that as soon as i get home.

When I loaded ubuntu, it asked me for the screen resolution and I put in mine (1680x1050) but when I went to settings it only allowed me to go to 1024x768.

Is this because I don't have nvidia-settings? or something else?

I thought that since i don't have the nvidia-settings it is why I can't increase my resolution.  This is the main goal of this topic:  Increase my screen resolution so that i can explore the rest of ubuntu comfortably!

---

### Post by MartinG on 2006-02-02
[QUOTE=POLO]Thanks for pointing that out!  I will try that as soon as i get home.

When I loaded ubuntu, it asked me for the screen resolution and I put in mine (1680x1050) but when I went to settings it only allowed me to go to 1024x768.

Is this because I don't have nvidia-settings? or something else?

I thought that since i don't have the nvidia-settings it is why I can't increase my resolution.  This is the main goal of this topic:  Increase my screen resolution so that i can explore the rest of ubuntu comfortably![/QUOTE]It's because you don't have the nvidia driver, rather than the nvidia-settings package.  If you inspect your /etc/X11/xorg.conf, I think you'll find at present that in the section "Device" the driver is given as nv; this is an open-source driver, without the capabilities of the non-free driver.  After installation this should have nvidia instead.

One thing you *might* have to do after installation is run "sudo dpkg-reconfigure xserver-xorg".  Only do this if you still haven't got the resolution you want available through the normal controls.

---

### Post by POLO on 2006-02-02
Opening the repositories worked and now I have the nvidia-settings THANK YOU SIR!, but my screen resolution didn't give me the option to increase.

Under "Device" the driver is given as nvidia now, but still not able to increase screen resolution.

I went into "sudo dpkg-reconfigure xserver-xorg" and selected the correct screen resolution... didn't work

I looked at my /etc/X11/xorg.conf file and it states in the "Displays" Modes: "1680x1050" for all, but still can't change it in Screen Resolution... now i am really lost.

---

### Post by MartinG on 2006-02-03
[QUOTE=POLO]Opening the repositories worked and now I have the nvidia-settings THANK YOU SIR!, but my screen resolution didn't give me the option to increase.

Under "Device" the driver is given as nvidia now, but still not able to increase screen resolution.

I went into "sudo dpkg-reconfigure xserver-xorg" and selected the correct screen resolution... didn't work

I looked at my /etc/X11/xorg.conf file and it states in the "Displays" Modes: "1680x1050" for all, but still can't change it in Screen Resolution... now i am really lost.[/QUOTE]Ouch, I'm afraid I'm getting lost now as well :(

All I can suggest is that you go for the latest drivers direct from nvidia.  See this HOWTO from tseliot:
[http://www.ubuntuforums.org/showthread.php?t=75074](http://www.ubuntuforums.org/showthread.php?t=75074)
What you have done so far is Method 1; try Method 2.

Two extra thoughts:
1. It should be possible to move between the screen resolutions listed in your xorg.conf by using the keyboard: Ctrl+Alt+"+or-" (that third key is the + or - key on you numeric keypad, not the ones next to the Backspace key).  Try it and see.
2. Could you post your xorg.conf file here so I can see if I can spot anything.

---

### Post by POLO on 2006-02-03
Ok, I finally was able to get the resolution by just reinstalling,

When it came to possible screen resolutions, I ONLY selected my lcd's native resolution, and unselected the default possibilities! It works now!

Hopefully I can get myself to install the offical drivers once I learn a bit more,

Thanks for all your help!

---

