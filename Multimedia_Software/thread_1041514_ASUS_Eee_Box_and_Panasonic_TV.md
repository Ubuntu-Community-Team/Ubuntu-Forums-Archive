---
title: "ASUS Eee Box and Panasonic TV"
date: 2009-01-16
forum: Multimedia Software
---

### Post by ErBah on 2009-01-16
I'm running out of patience with this little ASUS Eee Box I've just picked up. I was having some issues with WiFi and the on-board sound that I've fixed, but now I'm having a really hard time getting the on-board video to work with my Panasonic 42" TV (PH-42PX75U). It works fine with a regular LCD monitor without tweaking, but when I hook it up to the TV (which is widescreen) the display becomes corrupted. The right half of the desktop is on the left half of the TV, and two thirds of the left half of the desktop is on the right half, with a nice big bar of static down the center. I've tried all kinds of tweaks and such in various forums, mostly concerning xorg.conf, and so far, my best result has been when the display set itself to 800x600, centered on the TV. However, I should say that the only way to got that to happen was when my conf file had a parsing error on it somewhere. I've been unable to duplicate the 800x600 since, and it seems the conf file has be unparsable but still have a certain line in it. Aside from X, the other ttys are corrupt as well, in a different way, but still unreadable for the most part, though I don't care about that since I've just been sshing into the machine thus far.

Please let me know what information I need to provide. I can acquire anything that I can get at through SSH, since the GUI is fairly unbearable.

Thanks in advance,
e

PS: I should probably mention that the BIOS, POST messages, and Ubuntu loading screen are all fine. It's only when the login window shows up that the screen becomes corrupt.

---

### Post by ErBah on 2009-01-16
Changing the driver to "vesa" in the xorg.conf allowed me to run Ubuntu at 800x600 without problems, however, I'm still unable to set the resolution any higher, regardless of what I set in the conf.

---

### Post by Jose Catre-Vandis on 2009-01-16
What options do you have to output the video to the TV:
1. VGA
2. DVI
3. DVI-> HDMI
4. HDMI
5. Composite
6. SVideo

Are you trying to view LCD monitor at the same time?

Worth a shot to download a copy of GeexBox, burn it to CD or do a USB install, and boot it up. Do you get the same problems then? Similarly with a live cd of Ubuntu. Does the screen work OK with another PC?

What type of TV? Plasma/LCD/CRT? I have a big old Panasonic CRT 36" that won't run past 1024 x 768 so you need to make sure you are not pushing too high a resolution out to the TV

Would be useful to see your /etc/X11/xorg.conf contents and are you running any proprietory drivers?

So many variables but check it's not the hardware first before we move onto settings. The post and bios screen will generally be OK, its when you get to X that the fun starts :)

---

### Post by ErBah on 2009-01-16
I think you may be confusing the Eee Box with the Eee PC. The Box is just an ultra small desktop. It has no screen. The only video output available is DVI. I'm 100% certain it's not the hardware, since I was previously running on a Samsung 24" flatscreen monitor at a resolution higher than 1024.

Also, I just found out that the VESA drivers work, but only up to 800x600. I'm thinking it has something to do with the Intel drivers. The onboard video card is an Intel 945GME. I'm also thinking it may have something to do with the Panasonic, so I was hoping for some advice about maybe getting the Intel drivers to be more cooperative, or some insight into how Ubuntu interacts with the EDID stuff coming from the TV.

---

### Post by Jose Catre-Vandis on 2009-01-17
No, not confused, I know the difference between an EEE Box and an EEE PC just do not know what hardware options you have :)

Just running through my usual trouble shooting options and asking for **more information** so that we can pinpoint the problem. If you are on Ibex I beleive you have the latest driver. I still think it is hardware related and communication between PC and TV, on the TV side as it appears you can run successfully on a 24" monitor. Any settings on the TV that can be tweaked?

---

