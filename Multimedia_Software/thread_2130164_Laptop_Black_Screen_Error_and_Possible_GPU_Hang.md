---
title: "Laptop Black Screen Error and Possible GPU Hang"
date: 2013-03-28
forum: Multimedia Software
---

### Post by TheElfinGuy on 2013-03-28
SOLUTION:

Black Screen Error: use this command in terminal: > sudo gedit /etc/rc,local
 and force your desired brightness level with this line of text:
> 
echo DESIREDVAL > /sys/class/backlight/acpi_video0/brightness

Example of an edited rc.local:

> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 10 > /sys/class/backlight/acpi_video0/brightness
exit 0

GPU Hang:
My graphics driver was not installed, so I went and tried to install it. I couldn't so I updated to Raring Ringtail (13.04)



ORIGINAL PROBLEM:

As the title says, I'm getting a black screen and a possible GPU hang. The black screen occurs when I boot my laptop and once it completely boots (gets to the login screen) the screen says something like "PM Device: Failed to start error." and then the screen goes black. I know the computer is still on because I hear the amazing Ubuntu drum sound. This also happened when I installed Ubuntu using a live DVD. I heard the drum sound then, too. I was able to partially fix the problem by using an external moniter. After installing, I went to settings and turned on my laptop display. Everything seemed fine. But.. everytime I restart my computer I have to plug in the external screen and turn on the laptop display again. Obviously, this shouldn't happen. I also keep getting spammed with an intel-gpu.py error or something from apport. Could this have something to do with it?

I've tried looking up solutions but I haven't found any that work. Here are my specs:

Ubuntu 12.10 64-Bit
Acer Aspire V3 731-4473 (Full specs here: [http://us.acer.com/ac/en/US/content/model/NX.M31AA.005](http://us.acer.com/ac/en/US/content/model/NX.M31AA.005))
I believe I installed this using the Boot Repair remix of Ubuntu, if you need to know that. Also, I had to erase Windows 8 completely.. because of the bane of my existance: UEFI. I used Legacy Boot to install and use Ubuntu.

If you need more information, please ask. Any and all help or suggestions are welcome. Thanks in advance.

---

### Post by kc1di on 2013-03-28
Hello TheElfinGuy,

I think you may need to put nomodeset in your kernel line [here's page]("http://askubuntu.com/questions/38780/how-to-set-nomodeset-for-installation") that explains it. and [this page]("http://askubuntu.com/questions/207175/what-does-nomodeset-do") explains what it does.

---

### Post by TheElfinGuy on 2013-03-28
Hmm.. I'll try that if my current fix doesn't hold out. I installed laptop-mode-tools, configured it, and edited /etc/rc.local to force max brightness. Seems to work for now. How can I fix my GPU hangs? System Settings says Unknown for Graphics..ere

EDIT: Right after replying I got another GPU hang error and an apport error. Here are some screenshots showing more details:

[http://i50.tinypic.com/2me5ll2.png](http://i50.tinypic.com/2me5ll2.png)
[http://i45.tinypic.com/fokb5v.png](http://i45.tinypic.com/fokb5v.png)
[http://i50.tinypic.com/x0wb5y.png](http://i50.tinypic.com/x0wb5y.png)

---

