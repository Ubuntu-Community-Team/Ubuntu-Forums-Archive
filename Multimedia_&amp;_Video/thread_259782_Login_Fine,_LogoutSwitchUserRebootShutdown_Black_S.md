---
title: "Login Fine, Logout/SwitchUser/Reboot/Shutdown Black Screen"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by Vert on 2006-09-17
Ok, I have an Nvidia GeForce 5600 Ultra 128Mb.  I installed the drivers using this guide [http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)  Everything is fine until I try to Logout or Switch User or Reboot/Shutdown.  When I do any of these I get a black screen and must turn off my computer manually.  When I go to Reboot or Shutdown it goes to the screen to shutdown Ubuntu like normal, however the screen is messed up so bad that you can't read anything.  The screen is very glitchy, I don't know how else to describe it (and then I must turn off computer manually of course).  I've tried reinstalling the Nvidia drivers, I've tried reinstalling Xorg and resetting it's configuration file to it's default [[http://ubuntuforums.org/showthread.php?t=184965](http://ubuntuforums.org/showthread.php?t=184965)] (with the drivers set to "nv" and "nvidia", neither of which solved the problem or had any effect).  In my BIOS I set my Video Adapter to PCI (as opposed to AGP/Onboard) which solved the problem, but only temporarily apparently.  Now the problem is back and I'm completely out of ideas.  Any help is appreciated and I would like to thank anyone who does help me in advance.  (I've checked various posts about this same topic, but none of them seemed to be of any help)

---

### Post by MikeDK on 2006-09-18
hey i have that same problem on an 5900 ultra 128mb, thou i used the latest Nvidia_Dapper-site cant remember the link but if u have a solution on that, it would be nice to get some help.

Kind Regards MikeDK

found the link [https://help.ubuntu.com/community/Latest_Nvidia_Dapper]("https://help.ubuntu.com/community/Latest_Nvidia_Dapper")

---

### Post by Vert on 2006-09-18
Mike, the answer was in the link :D   Thanks for providing the link (although it accomplished something you didn't think it would).  Mike the answer was in front of us the entire time.  It's at the bottom of the link.  

"13) If you own a Nvidia FX5900 or a 5700 card (but not only) you might be affected by a bug which prevents (or shows buggy graphics when) users from logging out, switching to another user, shutting down or changing to a console (ALT-(F1-6)).

Try this:

sudo nano -w /boot/grub/menu.lst

look for this line:

# defoptions=quiet splash

Remove the word "splash" from it.

Save and exit: press CTRL+X

Then type this in Terminal or Konsole:

sudo update-grub

and restart your computer

After that, you will have no pretty usplash screen to look at anymore but the bug should be gone."
Mike, thank you for posting this link.
Tseliot, thanks for saving my life :P

---

