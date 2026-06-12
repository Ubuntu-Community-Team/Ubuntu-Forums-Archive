---
title: "Display problem on Acer Aspire 5000"
date: 2009-04-15
forum: Multimedia Software
---

### Post by braindrive on 2009-04-15
Hello, 

I am using Acer Aspire 5000. I think people have already reported problems with this particular VGA compatible controller:

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

The display of my screen flickers which means refresh rate problem, possibly. The current installation is 9.04, Jaunty Jackalope. The 8.10 release also had the same problem.

The thing I don't understand is it worked great in 8.04, Hardy, same laptop, but different versions of xorg-servers?

Following are the cases I tried:

8.04 (fully updated)  Works great
8.10 (Fresh install, updated) Does not work
Upgrading 8.04 to 8.10  Does not work
Upgrading 8.10 to 9.04  Does not work

I am attaching the 9.04 xorg.conf, named as xorg.conf.9.04.txt. This is same as 8.10 version.

I am also attaching 8.04 xorg.conf, named as xorg.conf.8.04.txt which worked great.

I tried to do some modifications to the original 9.04 xorg.conf. So attaching the modified one too, which is currently being used, so the name is "xorg.conf.current.txt"

Also attached is the screenshot of the flickering desktop screen.

Also attached is the log file /var/log/Xorg.0.log, named as Xorg.0.log.zip, which is not a zip file but a simple txt file.

Thanks in advance for the inputs
-bd

---

### Post by braindrive on 2009-04-15
Anyone has a similar problem with 8.10 on any machines using the same VGA controller?

---

### Post by dssdevl on 2009-04-30
I am having a similar problem on my Acer Aspire 3004Wlci.
Your screenshot looks fine, but I was gonna start a new thread before I saw yours and realized when I was gonna post a screenshot that the people here who looked at was not gonna see what I saw cause their computers are working correctly.
Here is a screenshot of my desktop.
I had the same problem with 8.10 and that's why I reverted to 8.04 where I didn't have the problem.
It's a little blurry but you can see the blue artifacts surronding my desktop picture.
I have tried changing the xorg.conf file to sis driver and even copied the xorg.conf file from 8.04 with no joy.

---

### Post by dssdevl on 2009-04-30
I seem to have fixed this problem. After some more digging I found this post:
[http://ubuntuforums.org/showthread.php?t=961964](http://ubuntuforums.org/showthread.php?t=961964)

In it they detail that "sisfb" is not loading as it should and to add it to /etc/modules to force it to load.

Hope it helps you too.

---

### Post by ScottSawyer on 2009-09-10
I know this is an old post, but I had a similar issue.  The fix works "sometimes", after reboot, it may still look bad.  but next reboot, might work.  

Same Aspire 5000 [SIS] 661/741...

When I am in Display Preferences, it shows Monitor: unknown, even when the graphics look right.  

Annoying, but usable.

I'd like to use some of the Compiz candy,

---

