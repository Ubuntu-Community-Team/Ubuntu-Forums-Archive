---
title: "Ubuntu 8.04: Atheros 8121 network driver not working"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by Jimrj on 2009-12-05
I have been computer literate since 1972, but unix and linux have passed me by. Ergo, I am a newbie.  My son (deceased) loaded Ubuntu for me, so now I must learn.  The ASUS motherboard P5KPL-CM has an on-board network driver, Atheros 8121.  It works fine on Windows XP, but will not raise the local network when using Ubuntu.  Can someone help?

---

### Post by headvampyre@hotmail.co.uk on 2009-12-05
what type of network are u usin ? wireless or cabled

---

### Post by Jimrj on 2009-12-05
> **headvampyre@hotmail.co.uk said:**
> what type of network are u usin ? wireless or cabled
I'm using a wired network.

---

### Post by northd_tech on 2009-12-06
Hi Jim (and sorry to hear about your son).

Edit:  Whoops- I just read the atheros part- I've only worked on their AR8132? wired interface under ubuntu- nevermind- I had the wrong model number in mind.

Here is a thread about the Atheros wireless cards though:

[http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros+network](http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros+network)

---

### Post by Jimrj on 2009-12-06
> **northd_tech said:**
> Hi Jim (and sorry to hear about your son).

Edit:  Whoops- I just read the atheros part- I've only worked on their AR8132? wired interface under ubuntu- nevermind- I had the wrong model number in mind.

Here is a thread about the Atheros wireless cards though:

[http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros+network](http://ubuntuforums.org/showthread.php?t=1309072&highlight=atheros+network)
Thanks for the reply and the effort, but I didn't find anything on that forum about my problem.  

Regards,
Jim

---

### Post by northd_tech on 2009-12-06
Hey again Jim- it looks like we're neighbors (sort of)- I'm 1 state south of you, and my family has been skiing and fishing in Ketchum, ID since the 1970's.  I really like that West Yellowstone/Montana border area too (I've got a friend up in Bozeman, and I lived in Logan, UT for a bit, so we had to buy our beer and lottery tickets in Franklin, ID on Sundays ;) ).  I worked with a kid from McCall who was a hell of a nice guy too (which is true of most Idaho natives that I've met).

I think you'll have more luck if you search for "AR8121" and Atheros.  I was hoping to find a .deb (Debian) install package for your ubuntu, but I didn't find it yet.

There is a source "tarball" here:

[http://dreamlinuxforums.org/index.php?action=printpage;topic=4339.0](http://dreamlinuxforums.org/index.php?action=printpage;topic=4339.0)

and here:

[http://jan.ucc.nau.edu/~wal2/debian.html]("http://jan.ucc.nau.edu/%7Ewal2/debian.html")

Here is some more Atheros AR8121 ethernet info (but it's for Fedora Linux, not ubuntu linux):

[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-ethernet-card-driver-atheros-ar8121-on-fc9-665507/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-install-ethernet-card-driver-atheros-ar8121-on-fc9-665507/)

Grab those "tarball" files and read through them.  Look for an "INSTALL" or "README" file inside the top directory of those archives.

If you can't figure out how to compile those, someone here should be able to talk you through it.  You might also need to install a bunch of headers and source files in order to compile it.

You might be able to go into System>Administration>Update Manager and enter your password and the network card may be working under a newer kernel (if you are able to get a wireless network connection, that is).

If you can't get a network connection, you might have better luck just downloading a "Live CD" or "Live DVD" and running a 9.10 upgrade (but it could wipe out some data if you do a fresh install, so backup your data and important files first).  There should be some kind of CD recording software installed on ubuntu if you need it- look under your menus at the left upper screen.

As far as the Linux software that is installed, that is usually free/open source, and it's not a bad idea to update it every so often anyway (it is usually more reliable and more compatible in the "stable" but newer versions).  I'd advise you to stay away from "beta" versions though.

The Synaptic Package Manager under System>Administration is where you can install various software packages from (or those "*.deb" files are really easy to install with a right-click, too).

Good luck, and be sure to look for the Beginner Forum here:

[http://ubuntuforums.org/forumdisplay.php?f=73](http://ubuntuforums.org/forumdisplay.php?f=73)

Edit:  Take a look at these threads too:

[http://ubuntuforums.org/showthread.php?t=719863](http://ubuntuforums.org/showthread.php?t=719863)

[http://www.linuxforums.org/forum/ubuntu-help/138496-wireless-not-working-ubuntu-8-10-a.html](http://www.linuxforums.org/forum/ubuntu-help/138496-wireless-not-working-ubuntu-8-10-a.html)

---

