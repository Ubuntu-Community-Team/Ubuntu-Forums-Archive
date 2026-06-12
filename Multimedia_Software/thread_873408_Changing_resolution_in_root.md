---
title: "Changing resolution in root?"
date: 2008-07-29
forum: Multimedia Software
---

### Post by karabas1543 on 2008-07-29
Hello everyone,

I just installed ubuntu 8.04, worked out wireless by myself, got to the internet, downloaded the ATI catalyst for my Radeon 9800 Pro, but it made my computer run super slow (i.e. xorg took up 95% of my cpu if i tried to do anything). I understood that this some kind of conflict with the driver and then I discovered that ubuntu has its own ATI drivers (in hardware drivers) menu. So I tried installing those instead.

I'm not really sure if that worked. When I restarted, my monitor gave me an out of range error (i.e. it couldn't display the resolution/refresh rate), but I can still use alt+ctrl+F1. The only way for me to get back into the system is to restore all settings to default in root. But that fails to solve the problem.

Is there any way I can change the screen resolution/refresh rate outside of the gnome desktop? I'm thinking that if I change it to a supported resolution for my monitor, the system should run fine.

Thanks so much for your help!

---

### Post by tuxxy on 2008-07-29
Did you remove the first driver you installed? this may of caused a conflict...

Remove all drivers and re-install it from **system > administration > hardware drivers**

---

### Post by karabas1543 on 2008-07-29
Ok so nothing shows up in Hardware Drivers except for the ATI restricted driver that was available from the beginning. I did have Catalyst installed but when I tried running it said that there was an error and it could not load it. I uninstalled the Catalyst and installed the restricted driver and still have the same problem - my monitor says the display is out of range.

---

### Post by karabas1543 on 2008-07-29
So I solved the problem but now I have a new one.

I edit xorg.conf by adding limits to frequency. The driver is now enabled and performs fine with one strange problem. At 1280x1024, the monitor has a large blank rectangle covering the bottom of the screen. I cannot see the bottom taskbar (though I can use it, which I found out by right-clicking on the place where the trash should be). If I launch an app, its bottom is covered by this empty rectangle.

I have tried various other resolutions, including of the same ratio, but none of them have this problem save 1280x1024. I used this resolution in Windows, so I definitely know the monitor/card can handle it. Any ideas? Should I make a new topic for this problem?

UPDATE: I turned off special effects in background properties and everything works fine. However, enabling them again makes the bottom taskbar disappear, although it is still useable. So weird.

---

