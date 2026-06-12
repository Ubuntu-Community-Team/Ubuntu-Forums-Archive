---
title: "Problem! Please help! Black Stripes, gnome hangs!"
date: 2009-11-26
forum: Multimedia Software
---

### Post by da_minci on 2009-11-26
Helo guys in Ubuntuworld!
I switched from Windows one year ago. Been running Ubuntu and is very satisfied! I had to do a reinstall in Mars, because of some Hard Drive problem, but fixed the problem by making a really small boot partition.
The other day, I shut down the system as usual (I had not installed any new applications). I start the computer the next day, log in.. The screen is filled with black stripes, and gnome hang after 3 secs. I've been running the ati (Radeon X1400) downloaded from the ATI site. It have been working wonderfully. I've been able to have all sorts of 3D enabled, no problem what so ever! Maybe on a couple of games I've had to turn off the desktop effects, or less it will blur (is that the term?). 

However I am able to get into command line, I removed the ati driver, still nothing happened same problem. I've tried reconfig the xorg in all different ways. 
I have also tried:   sudo apt-get remove --purge xorg-driver-fglrx
but no packages installed. I think I have restarted the system 100 times, sometime the login screen looks fine, sometimes not. But gnome crashes after a while. I reinstall the system, the new version Ubuntu 9.10, and problem remain!! I then installed the Ubuntu 8.10. Problem still remain. 

If I login hit, CTRL+ALT+F2, I get in command line, if I then wait a bit, log back and go back to X window it runs fine for a couple of minutes before it hangs. Although the stripes are still there. BUT yesterday, I did this. I got back in X mode, turned of the visual effects and the stripes were gone. Ubuntu run fine for 45 minutes, I did an update of old drivers restarted and we where back to black stripes and henging again! :(:(

Any tips?! Could it be the video card that has retired?

But understand. I have been running visual effects without a problem for half year, I suddently one day turn on the computer and nothing works! How is that even possible? The computer diagnosis in startup returns no Video error what so ever.

Greetings from Norway!

---

### Post by ilil on 2009-11-26
Maybe you change your video card for a while? If the problem is gone you'll know it is the reason

---

### Post by da_minci on 2009-11-26
> **ilil said:**
> Maybe you change your video card for a while? If the problem is gone you'll know it is the reason

You know any the command to check wich video driver is being used, and how to just set a standard VGA driver? The problem also occure when I'm in safe mode

---

### Post by ilil on 2009-11-26
See /etc/X11/xorg.conf for current video driver

---

### Post by da_minci on 2009-11-27
> **ilil said:**
> See /etc/X11/xorg.conf for current video driver

Hi man! I checked the conf. There where just the standard xorg-conf. But however I reinstalled the driver from the ati. And the stripes disapeared. But gnome still hang after 3 seconds. If I log in hit CTRL ALT F2 gnome runs fine as long as I dont start any applications. But however, something interesting has occured!
Afer gnome crash, I have checked the syslog, and each time the last sentence written into the log is:

kernel ----- som number fglrx its not nessesary to adjust system aperture on this ASIC

next line: reboot

Anyone know what this means. There are no desktop effects enabled. I have just reinstalled the system. Ubuntu 8.1.

---

### Post by ilil on 2009-11-27
fglrx is the proprietary driver for ATI video card. So ...

---

### Post by efflandt on 2009-11-27
Are you still using proprietary drivers, since "kernel ----- som number fglrx its not nessesary to adjust system aperture on this ASIC" seems to indicate you are doing something you do not need to do?

Did you try the default drivers in 9.10?  They may work fine unless you are using excessive resolution/color depth with not enough video RAM.  I did not do anything special for the ATI Radeon AGP card (256 MB video RAM) on my main desktop.

Although, I had to install **xorg-driver-fglrx** package (using Synaptic) on older PC for Radeon card with only 32 MB video RAM.

---

### Post by da_minci on 2009-11-27
> **efflandt said:**
> Are you still using proprietary drivers, since "kernel ----- som number fglrx its not nessesary to adjust system aperture on this ASIC" seems to indicate you are doing something you do not need to do?

Did you try the default drivers in 9.10?  They may work fine unless you are using excessive resolution/color depth with not enough video RAM.  I did not do anything special for the ATI Radeon AGP card (256 MB video RAM) on my main desktop.

Although, I had to install **xorg-driver-fglrx** package (using Synaptic) on older PC for Radeon card with only 32 MB video RAM.

I did try the default driver. Because when I installed the system nothing works. There are black stripes and gnome hang after couple of seconds. Then I installed the ati driver, the graphics are okey, but gnome still hangs. The wierd thing, the ubuntu has been working fine with this driver for 6 months, I turn on the computer one day, and nothing works. The first time I installed ubuntu on my computer there were no problem what so ever with the drivers, I could use both default and ati without any problem. Now I install the system there are huge graphic problems. And gnome hangs. I dont see how this can "happen by itself".

---

