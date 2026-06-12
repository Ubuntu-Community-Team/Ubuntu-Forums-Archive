---
title: "No graphics even in 'Safe Mode' from Edgy install CD"
date: 2006-10-31
forum: Multimedia &amp; Video
---

### Post by Roobert on 2006-10-31
I have an ATI X300 video driver. My xserver has been broken for a few days now, and changing my 'Device' in /etc/X11/xorg.conf to 'vesa', 'vga', 'radeon', 'ati', and 'radeon' has had absolutely no effect. I was going to try a fresh install of Edgy, but my graphics remain broken, even in the Install cd, when I boot in 'Safe Graphics' mode. Any ideas on where to go from here?

---

### Post by drobvice on 2006-11-01
Are you using the alternate install cd?  I have a 9800 pro and had to install with this, boot to safe mode and edit xorg.conf to "vesa".  I booted to gnome and installed fglrx and got acceleration working (well I figured out there were more steps to follow a few days later and then it was truly working).  I could not use the regular install cd for edgy.  Your card may have a different requirement than mine.  Hope I'm not telling you something you don't know. :)

---

### Post by Krakatos on 2006-11-01
> **drobvice said:**
> Are you using the alternate install cd?  I have a 9800 pro and had to install with this, boot to safe mode and edit xorg.conf to "vesa".  I booted to gnome and installed fglrx and got acceleration working (well I figured out there were more steps to follow a few days later and then it was truly working).  I could not use the regular install cd for edgy.  Hope I'm not telling you something you don't know. :)

SAme ati 9800 pro, exactly same things I had to do -> alternate -> reconfigure- >vesa

Bah... at least I'm not alone

---

### Post by pony-tail on 2006-11-02
On my A64 machine I have a Radeon X850XT-pe I have to install fglrx just to get xwindows.
I installed from the 64bit alernate CD
then rebooted - It came to a locked up X-session 
Then ctrl+alt+F1 to get a console
Then sudo nano -w /etc/apt/sources.list , then unhashed the universe & multiverse repositaries & ctrl+o to save & ctrl+x to exit.
Then sudo aptitude install xorg-driver-fglrx (it should pull the restricted modules in if they are not installed already )
Then sudo dpkg-reconfigure xserver-xorg   & when it comes to the driver part put the fglrx drivers in .
then reboot -n
This will get xwindows up but most likely not 3D.
once you have x up you can follow one of the how to guides and install the fglrx drivers fully 
This is a bit quick and dirty but has worked for me from breezy to edgy on this machine - just to get it up and running .
This only works on the alternative install !
edit:- this card will not work with "vesa" or "vga" drivers (it is PCI-e)

---

