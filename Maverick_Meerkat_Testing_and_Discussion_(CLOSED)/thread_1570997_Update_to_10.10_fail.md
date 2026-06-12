---
title: "Update to 10.10 fail"
date: 2010-09-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by thedrunkfish on 2010-09-09
Basically after updating my ubuntu to the beta 10.10 version it fails to start the x server for some reason on boot up and just ends up with a command line login screen.

Im a absolute n00b at linux command line stuff so dont really know where to begin.

Is there a way to revert back to my old stable version?
If not will i have to download the iso from windows, burn it and fix my install somehow?

Any help would be greatly appreciated.

Jon.

---

### Post by DandyDon on 2010-09-09
At the Grub boot screen, try running Recovery mode. If that fails, try to boot previous versions that are listed until you find one that works. 

Not to scold you, but I never mess with beta versions, beta versions are released to the users to help with debugging. If you can't write code-like me-ignore beta releases.

Good luck.

---

### Post by lisati on 2010-09-09
Moved to "Maverick Meerkat Testing and Discussion"

10.10 is still in a pre-release state. As such, there might be one or two wrinkles to iron out. Good luck.

---

### Post by ranch hand on 2010-09-09
The suggestion to boot to recovery is a good one.

I would do that and when you get to the recovery menu choose the "dpkg fix broken packages" option.  There may be some things that did not upgrade right and this should fix them and then update/upgrade your system to current.

When it is finished it will ask you to hit enter.  This will take you back to the menu.

Choose "return to normal boot" (first option).  This is another text login.  Log in.  When you get another prompt type;
startx

This should get you to the desktop if everything has not gone south on you.

There is no way to go back unless you are installed on 2 partitions / (root) and /home.  If you are then you could reinstall 10.04 and format / but not /home and probably not loose any data (back up is a GOOD idea anyway).

If you do get to the desktop and then shut down and have trouble booting again booting through recovery  and using startx will get you in.

Hopefully you got some kind of warning that this OS is not intended for production use.  There is another solid month before this is released.

READ the stickies on this forum, at least the first post of each, carefully.  There is important information there, in every one of them, that you NEED to know.

Welcome, by the way to the mad house.  This is where all the FUN is.

Our motto is bring on the breakage.

---

### Post by jerrylamos on 2010-09-09
> **thedrunkfish said:**
> Basically after updating my ubuntu to the beta 10.10 version it fails to start the x server for some reason on boot up and just ends up with a command line login screen.
Jon.

That happens on my pc's with integrated intel video graphics.  You can tell what graphics chip you have by entering this at the command line:
lspci | grep VGA
The vertical bar is the thing above the \ key on my keyboard.

If it says intel, then when you boot to the first grub screen add this to the end of the linux line:
i915.modeset=1
Ctrl-x to boot.
That works on my pc's so I make the change permanent:
sudo gedit /etc/default/grub
enter password
replace splash with i915.modeset=1
save & quit
sudo update-grub
wait for that to finish & reboot

If i915.modeset=1 doesn't work, try 
i915.modeset=0
Ctrl-x to boot.
If that doesn't work either, then on the command line enter:
sudo nano /etc/X11/xorg.conf
enter your password
Section "Device"
Identifier "Configured Video Device"
Driver "Vesa"
End Section
Ctrl-o
Ctrl-x
sudo reboot
For many intel video graphics Maverick Beta is supposed to default to the "Vesa" driver but there's a bug (maybe many) in that code.

Let us know what your video graphics is.

Jerry

---

### Post by KPDXHAM on 2010-09-09
> **DandyDon said:**
> At the Grub boot screen, try running Recovery mode. If that fails, try to boot previous versions that are listed until you find one that works. 

Not to scold you, but I never mess with beta versions, beta versions are released to the users to help with debugging. If you can't write code-like me-ignore beta releases.

Good luck.

[-X

Same here...... Let others try & test for now unless you don't mind being frustrated and upset when something goes wrong and you may loose important files UNLESS you back them up all the time .....just in case...  ](*,)

---

### Post by Noz3001 on 2010-09-09
Being noob at command line is not a good thing with beta. Make sure you don't have any proprietary drivers running, fglrx caused problems with me after an update to 10.10

---

### Post by jerrylamos on 2010-09-10
> **Noz3001 said:**
> Being noob at command line is not a good thing with beta. Make sure you don't have any proprietary drivers running, fglrx caused problems with me after an update to 10.10
Hey,

That's how I've learned a lot about practical linux from a user's standpoint.  I started out with Dapper Drake Beta installed on a test system of course then have been fumbling along ever since with pre-Alpha's, Alpha's, Beta's, suggested fixes, you name it.  

Lots of fun, can be frustrating!, and helps point out bugs and evaluate fixes for Ubuntu.

Have at it!  I usually have several partitions going with stable to unstable to very unstable versions of Ubuntu to run.

Ranch hand has lots of good ideas see his various postings.

Jerry

---

