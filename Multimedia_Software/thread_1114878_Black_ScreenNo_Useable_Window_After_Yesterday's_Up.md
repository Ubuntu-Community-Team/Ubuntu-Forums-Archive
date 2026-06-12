---
title: "Black Screen/No Useable Window After Yesterday's Update"
date: 2009-04-03
forum: Multimedia Software
---

### Post by Anlace on 2009-04-03
Greetings,

I updated yesterday and with this morning's reboot I can't view the Kubuntu 8.1 desktop using the Nvidia driver.  All I have is a black screen and no clue what happened.

I edited xorg.conf to boot up using the vesa driver (which gives me very low res), reinstalled Nvidia 180 driver using jockey, rebooted to a black screen.

I noticed when the update happened yesterday that it was for xorg.intel.[something I don't remember].  Why would xorg need to update intel video drivers on a Nvidia PC?  Even the motherboard is Nvidia 780i chipset.  Could this be the issue?  Why does xorg install intel drivers by default?

My xorg.conf is the same config that I have been using successfully for more than a year through multiple updates and kernel updates with no problem.

Any help is appreciated.

---

### Post by Tobi-fp on 2009-04-03
if i were you i would try to completely remove any of your nvidia and intel drivers (i believe the drivers have been corrupted by the intel ones), afterwards just install the nvidia ones..

---

### Post by Anlace on 2009-04-03
Thanks, I'll give that a try.

It's just way too early in the morning for troubleshooting :-P  My brain doesn't even fire up for another couple of hours and lots more coffee.

---

### Post by Anlace on 2009-04-03
Nope that didn't do it.  I got a screen with scrambled colors and my keyboard locked up briefly.  That was the only change after reinstalling the Nvidia drivers and everything that was associated, i.e. kernel source, modules, etc.

---

### Post by Anlace on 2009-04-03
Ok, here is how I "fixed" the problem.

Upon rebooting the system went into it's regular fsck routine and after that rebooted into my much welcome desktop.  HURRAY!

Then as I was typing my reply to this thread, the power went out.  When power came back on rebooting resulted in a black screen again.

I used my GParted Live boot CD to run a check on /root and /home and sure enough when I rebooted there was my desktop as it should be.

So now I have a question and will open a new thread if there is no reply here.

Is there a log file that I can view so I can see exactly what was repaired with fsck?  I am concerned about bad sectors on the HD or corrupted files and would like to see exactly what happened to cause/repair this issue.

Thanks again for the reply.

---

