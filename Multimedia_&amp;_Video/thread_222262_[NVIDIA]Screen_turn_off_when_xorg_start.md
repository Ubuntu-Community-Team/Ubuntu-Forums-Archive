---
title: "[NVIDIA]Screen turn off when xorg start"
date: 2006-07-24
forum: Multimedia &amp; Video
---

### Post by chantecode on 2006-07-24
Hi,

Under Ubuntu Dapper, I usually start my xorg server with the "nv" driver for my nvidia graphic card.
Because I need the 3D acceleration, I have to install the official nvidia driver.
That's what I did:

apt-get install linux-restricted-modules-`uname -r` nvidia-kernel-common nvidia-glx

I changed my xorg.conf to set "nvidia" driver instead of "nv".
When I start my xorg server with gdm, my screen turn off and i have to reboot thanks to my keyboard.

I firstly thought the problem came from my resolution , so I changed my settings with a depth in 16 and a resolution in "800*600".
But it was not the solution.:-| 

Here is a pastebin of my xorg logs:
[http://pastebin.ca/98944](http://pastebin.ca/98944)
An a pastebin of my xorg.conf
[http://pastebin.ca/98970](http://pastebin.ca/98970)

My graphical card:
GeForce4 Ti 4200 AGP 8x

And all my packages are up to date.

Thanks....;)

---

### Post by bryonhowley on 2006-07-25
I would double check your Horizsync and VertRefresh setting against your monitor specs.
The Horizsync does not look correct but with out the make and model of the monitor it is hard to tell.
#
HorizSync       31-33 /not much range for Hsyc
VertRefresh     50-80
If theese are incorrect your monitor will be out of sync witch sounds like your problem. If you can reboot from keyboard it is not a hard-lock most likely just out of sync. Can you ctrl-alt-F1 or ctrl-alt-backspace and get any responce, does it drop you to the console?

---

### Post by Manthis on 2006-07-25
Does the screen turns off or does it only turns black?
If it's only black try to type CTRL+ALT+BACKSPACE and see what happens...

---

### Post by tseliot on 2006-07-25
Make sure you know the refresh rate supported by your monitor and then try point 5 of the problems section of this guide:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)

---

### Post by chantecode on 2006-07-25
I get my HorizSync from the hwinfo command.
I changed it to the horizSync I'm using with nv driver ( 28.0 - 51.0)
And I already tested with a smaller verticalSync.

My screen is 14 inch (tiny).

I can hear gdm starting with its little music. I can kill it (ctrl + alt + backspace), I can switch to a console (ctrl + alt + F1) and I can write sudo reboot and it works. But all of these operations can only be made with my turned off screen. When I say turning off, I want to say that my monitor acts as if my computer was halted and the monitor receives no signal (my led is not green but orange). And the screen is black.
Even if I restart my monitor, it doesn't change anything.

I just tried the fourth point in [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#PROBLEMS_SECTION)
including the Option "Accel" "Off".
And it doesn't change anything.

I tried with and without framebuffer too....

That's strange. These last years, under Debian and xwindow-server, i was able to use the official drivers from nvidia by installing them directly from the binaries on their website. And it worked perfectly....

---

### Post by tseliot on 2006-07-25
You should ask here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by chantecode on 2006-07-25
Ok, I will do it.
Thank you all ;)

---

