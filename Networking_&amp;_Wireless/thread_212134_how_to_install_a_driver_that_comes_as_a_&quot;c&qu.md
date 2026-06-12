---
title: "how to install a driver that comes as a &quot;c&quot; file?"
date: 2006-07-09
forum: Networking &amp; Wireless
---

### Post by anil_robo on 2006-07-09
The only problem that's keeping me from running a web server on a pentium 166MHz oldie machine is that I can't install the driver for ethernet card (DLINK DFE TX 530+ REV F).

The manufacturer gives the driver as a .c file on its site, but there are no instructions. How do I install the driver that comes as a c file?

---

### Post by mpvano on 2006-07-09
Why would a web server need a "driver". Furthermore, why would you want to use any server other than the industry standard apache server, which is installable with a few clicks from the Ubuntu repository and comes with free security updates!

 I can tell you from years of running it on 166 and 200mhz internet servers that apache works great on Pentium IIs like yours.

If your really serious about making a web server, however, consider doing a stripped down "server" install of ubuntu with no GUI. You'll need to learn a few things about the unix shell and linux administration from the command line, but the server should run much better than it will with gnome running....

Mario

---

### Post by anil_robo on 2006-07-10
I'm sorry, I'm on sedatives for common cold, and didn't provide enough details in the first post.

I meant I need to install the driver for ETHERNET card that comes as a c file.

I did try a stripped down version of Ubuntu, but it sucks! First, the pretty huge 1GB hard drive :) proved too small for Ubuntu standard install The installation failed midway due to "no disk space left". So I Removed it, installed Puppy Linux, ran fine - but still no ethernet driver!

Installed Damn Small Linux - ran fine - but no ethernet driver there either!

Given these, I was forced to run apache with windoze98, but I don't want to use windoze. I want to use Linux.


I'll try to install ubuntu server on it when I fly back to Houston (I'm in India now) and let's see if it works well. However, Im afraid the driver problem will remain. I'd really appreciate if someone could tell me how to install a driver that comes as a c file.

Thanks

Anil

---

### Post by mpvano on 2006-07-10
Huh? I haven't tried it yet with Dapper, but the "server" option install for breezy was less than 350mb of disk space.

I Just checked, and It still shows up in the alternate ways to use the CD menus on the "alternate" installation CD ROM for Dapper (NOT the live CD).

Hit the F1 key for help finding that option. Note that this is NOT the enterprise server version available separately from Ubuntu. that version is a lot larger and requires much fancier hardware to shine....

 I have 3 machines running right now using the "breezy" version of this server install

I know the situation's probably different where you live, but 200gb IDE drives here cost about $60.00! Most 1Gb ide drives are old enough that they fail within a few weeks of installing them in servers (Been there, done that!). Furthermore, they're typically 10-20 times slower than newer drives.

I do a lot of work reclaiming older machines for non-profits, etc. here. I'd suggest you should find a slightly more modern drive (4-6Gb) or so, just to take advantage of the higher speed and improved IDE interface. Ask around. People take them out when they upgrade to bigger drives and then give them away for free!

I don't think you're going to find any SAFE enough version of Apache to install in a machine smaller than that. Even the DamnSmall Linux version is out-of-date enough to be broken into remotely by stack crashing it. Any older release is probably way too dangerous to use for a web server.

Anyway, back to your ethernet problem....

Drivers in .c form from vendors like that are usually not a good choice. Are you sure that the card isn't supported by a standard driver shipped with the system? Can you find out what ethernet chip it uses? Earlier versions used the 8139 and there are at least two flavors of drivers that should work with that.

Before trying a source build, I'd try 

sudo modprobe -a 8139cp

and if that gives an error I'd try:

sudo modprobe -a 8139too

If those fail, then try a "sudo  lspci -v" and post the results here. That will show what chip is involved. I'm guessing that if your card doesn't show up in the install, it may not be working at all.

If the card shows up, add that driver name to /etc/modules to have it automatically loaded at each startup.

If the card doesn't show up at ALL in the lspci list, then you have bigger problems. Many old Pentium I and II machines (which is what I presume you are talking about) have obsolete pci bus designs and don't work with newer cards at all! Many cards now require pci 2.2 and some even require 3.3 Volt power, which is rarely present in machines that old.

I suspect that if the card does NOT show up in lspci, you'll need to get another card or another machine....

If none of those approaches work, but the card shows up in lspci, then I'd start thinking about building a driver.

To build drivers, you need to first install the packages named
 
build-essential gcc3.4 and kernel-headers-2.4.27-2
(the suffix must exactly match the kernel version you are using)

You'll then need to follow the directions in the downloaded package exactly. If they have no instructions SPECIFICALLY for Ubuntu, You can try any they give for "Debian" distributions. Most vendors who just give you a source file are basically leaving you on your own to figure out how to install it, and it's anyone's guess what they had in mind. That hasn't worked for years.

Note also that depending on how clever the authors of the source code package have been, you may have to build the module and reinstall it again everytime there's a kernel update.


I strongly suggest avoiding the source install route if at all possible. I'd be amazed if there's isn't a standard driver that works....

hope this helps, if not someone else may have some ideas

good luck...

Mario

---

### Post by tturrisi on 2006-07-10
If you jsut want a straight simple lightweight install that runs apache, php, mysql, etc, then why bother with ANY distribution other than Debian itself?  Download an iso from here & do a net install.  Your net card is supported with it.  I've done countless net installs using that same card, one server I have at home is running woody & another sarge.  You can even use a woody iso & do a dist-upgrade prior to downloading any updates.

[woody]("http://people.debian.org/~dwhedon/boot-floppies/")
[sarge]("http://www.debian.org/CD/netinst/")
[etch]("http://www.debian.org/devel/debian-installer/")

---

### Post by mpvano on 2006-07-10
There's a lot of hardware that Debian refuses to directly support for "purity" reasons. The Ubuntu server install is basically Debian without scruples.....

(Otherwise I agree with you)

Mario

---

### Post by anil_robo on 2006-07-11
> **mpvano said:**
> I know the situation's probably different where you live, but 200gb IDE drives here cost about $60.00! Most 1Gb ide drives are old enough that they fail within a few weeks of installing them in servers (Been there, done that!). Furthermore, they're typically 10-20 times slower than newer drives.
 
Well, the machine is in Houston (Texas), and I do have a new 160GB Western Digital HD with me. However, I just want to make it a point that such ancient machines can host websites without much upgradation. I have spent about $40 on that machine for the ethernet card and USB 2.0 card.
 
> Drivers in .c form from vendors like that are usually not a good choice. Are you sure that the card isn't supported by a standard driver shipped with the system? Can you find out what ethernet chip it uses? Earlier versions used the 8139 and there are at least two flavors of drivers that should work with that.
 
I installed Ubuntu+Gnome on that machine, and it could not fire up the Desktop after 2 hours of continuous HD activity. However, I did not try the server install for the fear of uncomfortable command line. Looks like now is the time to kick some keys! :) I'll install Ubuntu server on that machine as soon as I get back to Houston - in about two weeks.
 
Thanks Mario!

---

### Post by tturrisi on 2006-07-11
I'd install straight Debian net install (base system), apache, php, mysql, fluxbox, nedit & emelfm.  That's all the gui you'll neeed.

---

