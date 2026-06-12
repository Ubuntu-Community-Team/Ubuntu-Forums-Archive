---
title: "ATI - 3D Rendering Issue"
date: 2008-09-15
forum: Multimedia Software
---

### Post by sbhargav21 on 2008-09-15
I have a ATI Radeon X1300 Pro Video card & the 3D Rendering is not getting enabled. Following are the things I tried to enable it.
- Method 2 from [http://wiki.cchtml.com/index.php/Ubu...allation_Guide](http://wiki.cchtml.com/index.php/Ubu...allation_Guide)
- Mirror mode tweak entioned in Post#5 of [http://ubuntuforums.org/showthread.p...deo+overlay+TV](http://ubuntuforums.org/showthread.p...deo+overlay+TV)
- Envy [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)
- Post# 120 in [http://ubuntuforums.org/showpost.php...&postcount=120](http://ubuntuforums.org/showpost.php...&postcount=120)
- Method 1 & 2 in [http://www.mythtv.org/wiki/index.php...rietary_Driver](http://www.mythtv.org/wiki/index.php...rietary_Driver)
- None of the above methods have worked so far, the only thing that gets loaded is the MESA ones!

Should I reinstall mythbuntu or how else can I fix this?

---

### Post by sdowney717 on 2008-09-23
For Hardy, this card does not work properly with ubuntu and fglrx.

I have 2 machines with this card and never could get any 3d.
And 1 machine is always white screened

If I put in a 9600, these machines will configure.
SO, the software is poorly written.

---

### Post by sdowney717 on 2008-09-23
for example simply following those envy commands and then trying to run text mode yields errors right from the website this is shown here, look at the end.

friarron2@friarron-desktop:~$ sudo apt-get remove envy
[sudo] password for friarron2: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package envy is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
friarron2@friarron-desktop:~$ sudo apt-get remove envyng
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
friarron2@friarron-desktop:~$ sudo rm -R /usr/share/envy
friarron2@friarron-desktop:~$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
envyng-gtk is already the newest version.
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
friarron2@friarron-desktop:~$ sudo apt-get install envyng-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
envyng-core is already the newest version.
envyng-core set to manually installed.
The following packages were automatically installed and are no longer required:
  libwxgtk2.6-0 libwxbase2.6-0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
friarron2@friarron-desktop:~$ sudo envyng -t
/usr/bin/envyng: line 6: cd: /usr/share/envy: No such file or directory
python: can't open file 'interface.py': [Errno 2] No such file or directory
friarron2@friarron-desktop:~$

---

### Post by sdowney717 on 2008-09-23
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

for example, follow this for hardy, both methods, neither one will work.
I tried the ubuntu way and I did the download from ATI build pckg way and still I only have mesa.

---

### Post by markbuntu on 2008-09-23
That how to is wrong, I never got anything to work following that. Try this one, Method 2, it always worked for me:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

---

### Post by sdowney717 on 2008-09-25
I have discovered something that might be the cause of this white screen!
ECD modules are reporting bad info on these cards. Follow these threads to blacklist these modules and rmmod and see if this works. 
I will try once again and report back.


[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=671181&highlight=blacklist+i82875p_edac](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=671181&highlight=blacklist+i82875p_edac)

[http://openwetware.org/wiki/Computing/Linux/Ubuntu](http://openwetware.org/wiki/Computing/Linux/Ubuntu)
----------------------------------------
> From: [email]sdowney717@msn.com[/email]
> To: [email]sdowney717@msn.com[/email]
> Subject: agp blacklist module
> Date: Wed, 24 Sep 2008 23:57:05 -0400
> 
> 
> [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=877421](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=877421)
> [https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684)
> 
> [http://www.linuxmint.com/forum/viewtopic.php?t=6317](http://www.linuxmint.com/forum/viewtopic.php?t=6317)


well unfortunately NOW I HAVE A BLACK SCREEN.
so, I will be stuck with the radeon driver and no 3d on a perfectly good card.

---

### Post by markbuntu on 2008-09-25
You should file a bug report with ati so they know about the problem and can fix it.

---

### Post by DrMega on 2008-09-25
> **markbuntu said:**
> You should file a bug report with ati so they know about the problem and can fix it.

+1 to that.

ATI claim that they monitor various forums for feedback about their stuff, but they can't possibly read everything on every forum. If they don't know about a bug, they won't fix it.

---

### Post by sdowney717 on 2008-09-26
I solved this using the free driver, no fglrx!

follow this link

[http://ubuntuforums.org/showthread.php?p=5861462#post5861462](http://ubuntuforums.org/showthread.php?p=5861462#post5861462)

[http://ubuntuforums.org/showthread.php?p=5861435#post5861435](http://ubuntuforums.org/showthread.php?p=5861435#post5861435)

I have an AGP x1300 PRO 256mb

and it is running compiz on IBEX 

If you upgrade to ibex, you will have the right wersion of xserver 1.5, xorg 7.4 and mesa 7.2 to run direct rendering and compiz without using the fglrx crap driver,

---

