---
title: "External monitor native resolution out of range in 10.4"
date: 2010-06-21
forum: Multimedia Software
---

### Post by elijah-man on 2010-06-21
So I am running 10.4 on an HP dv7t with a nVidia card.  Previously running 9.10 and everything was working well until my HDD died and I had to get a new one.  I did a clean install of 10.4 and I can't get my display settings to work right.  Under system>preferences>monitors the 17" laptop screen is set to the native 1600x900, but when I set the external 26' monitor to its native 1920x1200, the monitor only displays "out of range".  It works just fine at 1440x900 or even a bizarre 1280x1024, but everything looks like crap at those non-native resolutions.  I'm a photographer and need my external monitor to work at native resolution.  I'm thinking I might need to manually set the virtual resolution but I'm not sure how.  Does 10.4 even use an xorg.conf?  Is there an xrandr command line I can use?  Ideas?  Feel free to give me command line input and I will post output.  Any help would be much appreciated.
Thanks, Eli

---

### Post by AgentLinux on 2010-06-21
I can only help with my own recent experiences, being an ATI user.

To get my two monitors to work as expected with the preferred screen resolutions with my basic Ubuntu 10.04 install, I believe had to install or rather activate the "hardware drivers" offered via:

System --> Administration --> hardware drivers = activate

On my desktop machine, these are ATI drivers for my ATI Radeon 5850 card, or rather the Radeon series.

So with this installed, I could open the ATI Catalyst control panel, and then set it up with the following mode:

Single display desktop (multi desktop)

Only this way could I get full resolution on my primary 24" screen, together with my 17" secondary screen.

This is not a 100% acceptable solution in my case, as I cannot drag a folder between the screens, but the mouse cursor does ofc move across over between the screens.

Perhaps dual screen users with the same screen resolution have an easier time? There is an option on my setup to use some other mode, which creates one big desktop over both screens, but iirc, I could not get full resolution on my main screen this way.

Maybe things will improve later on, if I install some newer ATI drivers.

---

### Post by elijah-man on 2010-06-21
I'm trying to avoid the proprietory "Nvidia" driver since last time I tried it, it messed everything up.  I think Nouveau is the default driver for 10.4 with an nvidia card (or is it still the NV driver?).  Any other thoughts?

---

### Post by BobLand on 2010-06-21
It sounds like a driver to me.  Go to the Hardware Drivers in the menu system.  I can't remember which one but you'll see it.  Select it and it will tell you that your NVIDIA driver is an old one.  Select the "recommended" one and it will install it for you. 

If, in the end, that doesn't work for you, go back to that place and uninstall it.  It is very simple.  However, it does take a few minutes so don't get impatient if it seems like it's not doing anything or it is stuck.

The new driver will allow you to set the resolution to whatever the monitor will allow, provided you have adequate memory on the card.

Hope this helps...
bobland

---

### Post by elijah-man on 2010-06-21
Bobland, thanks for the reply, but I think you missed the point.  I dislike the binary blob that Nvidia tries to shove down our throats.  I think the proprietary driver is a piece of crap, which is why I don't mess around with it.  I have tried it in the past and it does not work for me.  Just to see, I went ahead and activated the Nvidia driver to see if something has changed... nope.  I'm now back on the Nouveau driver and everything seems good except for the virtual resolution.  I could not give a crap about 3D acceleration, but I must have a seamless 2-screen desktop to stay productive in my work.  My computer is pretty new and my video card has 1GB of ram, so it's definitely not a hardware deficiency.  Like I said earlier, Nouveau was working just fine with my 9.4 installation on this same machine.

Does anyone have some xrandr commands or a better Nouveau driver I should try?  

Thanks, Eli

---

