---
title: "ATI Driver Huge Problems"
date: 2010-07-14
forum: Multimedia Software
---

### Post by WesleyNeary on 2010-07-14
Hi

New to Ubuntu and using lucid.

Have scanned all the guides to try and work out how to install native ATi drivers for the following video card:
ATi Mobility Radeon 9600 m10

Have downloaded and used the following files

ATi-driver-installer-10-3-x86.x86_64.run

worked through and created a lucid package,  ran the package which errors half way through installation.

Is this the right driver download for this card, if so any ideas as to solutions, if not can someone please help and tell me where I can find the native driver download for my card thanks.

---

### Post by sanderd17 on 2010-07-14
Is your installation not working out of the box?

Normally all needed drivers are in the linux kernel, some drivers can be installed via the repo's (you'll get a notification if there are drivers you might need) and if drivers arent there, it's a pain to get it working, certainly sindce your quite new here (it's still a pain for me)

---

### Post by WesleyNeary on 2010-07-14
> **sanderd17 said:**
> Is your installation not working out of the box?

Normally all needed drivers are in the linux kernel, some drivers can be installed via the repo's (you'll get a notification if there are drivers you might need) and if drivers arent there, it's a pain to get it working, certainly sindce your quite new here (it's still a pain for me)

Does work out of the box...........Sort of,  screen res is really low and cant use visual effects etc, also vhen using virtual box wont allow me to change virtual machine screen sizes, heard a native driver would solve these problems,  so hope there is a soloution other than this am loving linux so far and really dont want to have to go back to windoze.

please help

---

### Post by cozmicharlie on 2010-07-14
> **WesleyNeary said:**
> Hi

New to Ubuntu and using lucid.

Have scanned all the guides to try and work out how to install native ATi drivers for the following video card:
ATi Mobility Radeon 9600 m10

Have downloaded and used the following files

ATi-driver-installer-10-3-x86.x86_64.run

worked through and created a lucid package,  ran the package which errors half way through installation.

Is this the right driver download for this card, if so any ideas as to solutions, if not can someone please help and tell me where I can find the native driver download for my card thanks.

Is a driver listed in System>administration>Hardware drivers?  If so have you tried to activate it?  Sorry about this if it seems obvious, but you do claim to be new to Ubuntu.  

Did you try this 
[http://ubuntuforums.org/showthread.php?t=1322095](http://ubuntuforums.org/showthread.php?t=1322095)

Looks like there was a bug report in 2009.  I did not read through all the posts to see if it is still a problem.  
 [http://lists.freedesktop.org/archives/xorg-driver-ati/2009-January/007806.html](http://lists.freedesktop.org/archives/xorg-driver-ati/2009-January/007806.html)

You can find your xorg.config at /etx/X11.  Open it as root in gedit and cut and paste the changes.  Make sure and backup your old xorg.config file so you can revert back to it if this does not work.

---

### Post by Yellow Pasque on 2010-07-14
Your card is not supported by proprietary ATI drivers anymore (you would need to use Hardy and install Catalyst 9-3 to use the proprietary drivers). See this to fix your current install: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

---

