---
title: "ATI RV530 Pro/20&quot; Widescreen LCD Issue"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by wh1terabb1t on 2007-10-18
Hello,

I just installed 7.10 and have run into an issue with my graphics card (ATI RV530 which I think is the X1650GT?) and monitor (Dell 20" wide screen).  After the restart following the installation of the restricted ATI drivers, x would not start.  I booted into the recovery mode to have a look at /etc/X11/xorg.conf, which had a resolution above my monitor's max (1680x1050).  I removed the resolution and rebooted normally.  After doing so, X started but some part of Gnome failed, and when I went back into restricted drivers it claimed the ATI driver had not been installed.  Could someone please point me in the correct direction to resolve the problem?  Thanks in advance for your time.

-Andrew

---

### Post by wh1terabb1t on 2007-10-18
After much adieu I managed to get the ATI drivers installed and change my resolution to 1680x1050.  Now I can not seem to get visualizations to function.  At first I did not have composite enabled in xorg.conf but after adding it I receive "desktop effects could not be enabled".  Any suggestions?

---

### Post by wh1terabb1t on 2007-10-18
I think I have worked out all the issues, so I will make some suggestions to people in my boat:

ATI Radeon X1600:

Driver Install Guide: [http://ubuntuforums.org/showthread.php?t=575843](http://ubuntuforums.org/showthread.php?t=575843)
Suggestions: When building, Ubuntu/gusty did not work for me, so I built it as Ubuntu/feisty with out any issue.

Desktop Effects: [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)
Suggestions: I found the startup script unnecessary, it seems to start automatically (at least in my case)

---

