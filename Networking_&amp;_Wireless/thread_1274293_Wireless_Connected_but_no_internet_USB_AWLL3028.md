---
title: "Wireless Connected but no internet USB AWLL3028"
date: 2009-09-24
forum: Networking &amp; Wireless
---

### Post by point.vicente on 2009-09-24
Any problem solvers out there?  I installed ubuntu 9.04 on my dell 4700 with a airlink101 usb wireless device and ubuntu actually recognized it.  On verbose bootup it warns about the "experimental" drivers for it but when I first booted it seemed like all was well when it prompted me for the WEP key.  I searched, found it and enteredi it in the dialog and Ubuntu says its signal is 50% but it shows being connected! Great! I thought until I tried opening firefox to [www.google.com](www.google.com) or anything else.  No connection to the internet.  I get the IP address the name servers in the config file and everything but no internet.  Out of the box I thought i was good to go but I was wrong.   If the device lights up and ubuntu tells me i'm connected to my DSL then why no internet?  Any help would be appreciated.

---

### Post by superprash2003 on 2009-09-24
post output of the following from the terminal
1)iwconfig
2)ifconfig
3)ping google.com
4)ping 208.67.222.222

---

### Post by chris1950 on 2009-09-24
> **point.vicente said:**
> Any problem solvers out there?  I installed ubuntu 9.04 on my dell 4700 with a airlink101 usb wireless device and ubuntu actually recognized it.  On verbose bootup it warns about the "experimental" drivers for it but when I first booted it seemed like all was well when it prompted me for the WEP key.  I searched, found it and enteredi it in the dialog and Ubuntu says its signal is 50% but it shows being connected! Great! I thought until I tried opening firefox to [www.google.com]("http://www.google.com") or anything else.  No connection to the internet.  I get the IP address the name servers in the config file and everything but no internet.  Out of the box I thought i was good to go but I was wrong.   If the device lights up and ubuntu tells me i'm connected to my DSL then why no internet?  Any help would be appreciated.

I had to do this to get mine to work -
                                 


                                           [LEFT][IMG]http://kubuntuforums.net/forums/Themes/classic/images/post/lamp.gif[/IMG]                              [/LEFT]
                               [LEFT][COLOR=#000080]_[**How             to make a ADSL connection work with Wicd**]("http://kubuntuforums.net/forums/index.php?topic=3104329.msg183734#msg183734")_[/COLOR]« **on:** June 04, 2009, 08:50:33 pm »[/LEFT]
                          First of all, run into the Konsole:

*user@ubuntu:~$ sudo pppoeconf*

Follow the instructions in the application, then choose do not connect on startup and not connect now.
After that run to become connected:

*user@ubuntu:~$ pon dsl-provider*

Remove any of that applications:

*user@ubuntu:~$ sudo apt-get remove network-manager-kde  network-manager-gnome  network-manager plasma-widget-network-manager*

Run KPackageKit or Adept Manager, edit Software Sources. On Kubuntu Software choose the best server to download from. On Updates tab, check Important Security Updates and Recommended Updates. Hit Close.

If your connection becomes down after the remove of this packages, kill the process "pppd". Hit Ctrl+Esc keys. In the window write "pppd" and hit the Kill Process button. On Konsole:

*user@ubuntu:~$ sudo pon dsl-provider*
*user@ubuntu:~$ plog* **<<<< Take note of the DNS adresses, you will need it.**

Install the Wicd application:

*user@ubuntu:~$ sudo apt-get update && sudo apt-get install wicd*

Restart the computer.

Click the left button of the mouse on the icon of Wicd in the system tray. Click on Disconnect button. Expand the Wired Network connection and choose Scripts. Enter your password. (this connects you to the internet)

In the Pre-connection Script type *'pon dsl-provider'*
In the Disconnection Script type *'poff dsl-provider'*

In Advanced Configurations check "Use static DNS", typed the DNS addresses 1 & 2 (you can have it in the file /etc/resolv.conf if you forget to take note after the "plog" command).
 Hope this helps:)

OOPs sorry thought had trouble getting through the ADSL router

---

### Post by point.vicente on 2009-09-24
I got back on this afternoon after work and low and behold the internet started working.......for a little while.  What does this mean? I'm not sure but atleast its not DNS or other settings or drivers.  The verbose at bootup is consistent with the forum results which are very poor for this device. I keep reading 1 user after another who has intermittent internet. Not sure what to do next other that just uninstall ubuntu until I get my next PC.

---

### Post by point.vicente on 2009-10-07
I'm happy to report that I removed the cabinet with all the books blocking the space between the DSL router and the wireless USB airlink.  It seems to be working as good as the DSL service (which is not that great).  I also had no success resizing the ubuntu's partition to utilize the free space in the hard drive.  Instead I deleted the partition and re-installed ubuntu and its working like a champ.  Oh one more thing this time when i installed, ubuntu installer put grub on the 1st hard drive when ubuntu resides on the 2nd hard drive.  How do I fully remove and reinstall grub without ubuntu? Any help would be appreciated.

---

