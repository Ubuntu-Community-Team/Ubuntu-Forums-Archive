---
title: "Common Video Solution not working"
date: 2006-05-25
forum: Multimedia &amp; Video
---

### Post by freddy_ramone on 2006-05-25
First, I will get this out of the way, I am a total Linux/Ubuntu noob.

I know nothing about Linux or Ubuntu other than I want nothing to do with DOS/Windows (Even though I know more than enough to suffice in that world) anymore.

Well, after installing Ubuntu (Which took about 2.75 hours to do), I got the standard error message about how Xserver is not properly configured.

So, after that, I began to take a log of what I did and what response I got, and hopefully, you can help me, as I tried to get the best details I could get.

FROM MY LOG:

> sudo nano /etc/X11/xorg.conf

Changed device from "trident" to "vesa"
Changed driver from "trident" to "vesa"

Then I tried:

sudo dpkg-reconfigure xserver-xorg

Selected "kernel framebuffer"
Selected "16-bit" color depth

Got error message:

"xserver-xorg postinst warning: overwriting possibly customize configuration file; backup in /etc/X11/xorg.conf .200605251335"

Retried "sudo dpkg-reconfigure xserver-xorg"

Gave monitor name "NEC MultiSync XE15"
Turned off 1024x768 and 640x480 (I want to use 800x600)

Ran "sudo nano /etc/X11/xorg.conf" and saw "sudo dpkg-reconfigure -phigh xserver-xorg"

Tried "sudo dpkg-reconfigure -phigh xserver-xorg" got "xserver-xorg postinst warning" again.

***Turned off PC. Rebooted***

Recieved error message:

"X Window System Version 6.8.2 (Ubuntu 6.8.2-77) 20051010174523 [email]root@vernadsky.buil[/email]dd)
Release Date: 9 February 2005
X Protocol Version 11, Revision 0, Release 6.8.2
Build Operating System: Linux 2.6.10 i686 [ELF]
Current Operating System: Linux noodle2 2.6.12-9-386 #1 Mon Oct 10
13:14:56 BST 2005 i586
Build Date: 10 October 2005
       Before reporting problems, check http:/wiki.X.org 
       to make sure that you have the latest version.
Module Loader Present
OS Kernel: Linux Version 2.6.12-9-386 (buildd@rothera)(gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6 ubuntu 8)) #1 Mon Oct 10 13:14:36 BST 2005
Markers: (--), Probed (**) from config file, (==) default setting

Retried "sudo dpkg-reconfigure xserver-xorg"

Changed "trident" driver to "vesa"
Renamed "Trident 4400" (I believe) to "Trident Vesa"

Gave 1024KB System Memory to video card

Autorenamed monitor "Generic Monitor"

Kept 1024x768, 800x600, 640x480 resolutions

Used simple monitor setup (15-inch)

Kept "24-Bit" Color Depth

Recieved error message: "xserver-xorg postinst warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf .200605251418


At that point, I gave up.

I have an AMD K6 @ 240MHz
96 MB RAM
15GB IBM DeskStar HardDisk
24x CD-ROM
Trident 4400 (I believe) Video Card
Voodoo Graphics Accelerator
Most recent Ubuntu release
NEC MultiSync XE15 Monitor

I know some of this information may be a bit extraneous, but I figured that the more info I give, the more likely I can get help.

So can anyone help me, or is this a lost cause?

---

### Post by freddy_ramone on 2006-05-25
Okay, I got it fixed with the help of my Linux using pal.

Now, my problem is resolution...

It's stuck at 640x480, and I know for a fact that my monitor and video card can handle 800x600 @ 16bit Color, so I don't see why ubuntu keeps loading in 640x480.

Any advice?

---

