---
title: "WNA3100 Wireless Drivers"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by Strangegibberish on 2013-01-27
First: Total noob here.

I've been trying to install the drivers that i need to get my USB wireless card ( a netgear WNA3100)  working.  So far, no good.

I've been able do install "ndisgtk" - a program for the purpose of interacting with wireless drivers from windows.   I have ( i beleive) downloaded the correct drivers, and installed them with ndisgtk.  Ndisgtk will give me a check mark on the installed drivers, and even register that the hardware in question is present.  ( I have access to a wired Internet connection, but it's not at all feasible for any use - just for the occasional - "carry my tower to the location for a few minutes" sort of thing.)

And yet, it will not work to detect the wireless networks present.  Now, I'm dual  booting, so i know this card works, and yet, I'm completely stumped here..

This  link suggests i go to a "system>admin>hardware manager thing, which does not seem to exist in my linux menus.  (Using 64 bit Quetzal, btw.  And yes, the driver i've got is a 64 bit one.)- [http://community.spiceworks.com/how_to/show/1250-how-to-install-ndisgtk-ndis-wrapper-gui-in-ubuntu-gnu-linux-for-the-few-wireless-devices-without-drivers-built-in](http://community.spiceworks.com/how_to/show/1250-how-to-install-ndisgtk-ndis-wrapper-gui-in-ubuntu-gnu-linux-for-the-few-wireless-devices-without-drivers-built-in)

I assume this article is out of date, since i can't find the approprate menu things. (I read that this option used to exist, somewhere.)



Help!  I would really love to be able to kick Windows to the curb, but if i can't get this card working, I can't do that!

---

### Post by Cheesehead on 2013-01-27
Your hardware has been discussed several times.
For example, [http://ubuntuforums.org/showthread.php?t=1549190](http://ubuntuforums.org/showthread.php?t=1549190) had a successful conclusion. The thread shows how to use ndiswrapper and how to find your windows drivers.

The solution is kernel-specific. Every kernel upgrade (several times each year) may break your wireless again, and require you to reinstall the kernel module again.

Good hardware manufacturers add their modules (drivers) to the Linux kernel to prevent precisely this problem.

---

### Post by squakie on 2013-01-27
So when you say the driver is 64-bit, I assume that you are therefore running 64-bit Ubuntu?

Just a couple of thoughts for you:

[LIST]
[*]ndiswrapper normally requires only the XP .inf and .sys files.  On the rare occasion it has worked with others, but it normally requires XP drivers *only*.
[*]remember the architectures must match: 64-bit driver for 64-bit Ubuntu, 32-bit for 32-bit Ubuntu.  You say the driver is 64-bit - did you install 64-bit Ubuntu?
[/LIST]
Since ndisgtk is a graphical front-end to ndiswrapper, try the following in a terminal window:


sudo ndiswrapper -l (that's a lower case "L" for list)


What does that return?


sudo ndiswrapper -r <device returned on the -l command>


Repeat this until no devices are shown.  Then go back to ndisgtk and try again, and let us know the results.  Also let us know if the architectures match and if you are using the correct XP driver.

Is "Wireless" (not connections, just the group) showing in network manager?  If not, try enabling the wireless there and wait a few seconds for it to come up and then see what it says.

---

### Post by Strangegibberish on 2013-01-30
Cheesehead - If the solution is Kernal Specific, have there been any kernel updates to Ubuntu since '06, when the thread was posted?  I did read through that thread, and found no specific information about my problem with Ndiswrapper.  (Driver installed, but not working.)  In fact, that thread is where I first found the driver I used, and where I got the idea to try ndiswrapper in the first place. 
 
Squakie - Yes, I'm running 64 bit ubuntu, thus using the 64 bit drivers.  I downloaded my driver from a non-offical source, (In a support thread somewhere), so the thought has occured to me that I might have better luck with a freshly downloaded driver on the netgear site. (Thanks for the thought. Frankly, I'm amazed that didn't occur to me in the first place.)
  I'll try that, and if that fails, try the terminal commands you suggest. 
I'm not at home at the moment - so I cannot post results just yet. Will return to do so.

---

