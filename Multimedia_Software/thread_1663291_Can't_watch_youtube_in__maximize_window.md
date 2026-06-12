---
title: "Can't watch youtube in  maximize window"
date: 2011-01-09
forum: Multimedia Software
---

### Post by sembagdod on 2011-01-09
Whenever i try to maximize the Youtube window to full screen,the sound played well, but the video stuck on the first frame (i can't watch the video), and if i tried to restore it's original size it will work perfectly.  

Am using "Chromium 6.0.472.63 (59945)" On "Ubuntu 10.10" and installed "Adobe Flash Player 10.1.85.3"

I couldn't find any setting can be done on the graphic card.. and in fact I don't know if anything related can be done from there 

Anyone can help on this issue. 

Regards

---

### Post by efflandt on 2011-01-09
That sounds like an old flash version.  Did you use **flashplugin-installer** package in Synaptic or something else?

Have you searched the many other posts about full screen flash to see if or how they resolved it?  Most of us have never had any issues with full screen flash, except maybe dropped frames on older slower computers, or momentary freezes on really old computers or if internet connection is too slow (or choking).  Often systems get choked doing internet file sharing without proper settings.

You have not provided any details about your cpu, RAM, video card/chip, and whether using default or proprietary video drivers (version?).

---

### Post by sembagdod on 2011-01-09
In installed the flash using "Ubuntu Software Center" and when i checked that on Adobe, it was the latest version of it. 

I searched the forums and i didn't find similar issue, so i know am the only one who suffering from it, but i need some help to solve it as am new to linux world. 
MY PC specification are good generally and fast DSL internet, everything else is working fine. 

CPU   : Intel(R) Core(TM)2 Duo CPU E4500@2.20GHz
RAM   : 2G
Audio :Intel N10/ICH 7 Family High Definition Audio Controller
Video : Intel 82945G/GZ Integrated Graphics Controller
network: RTL8111/8168B PCI Express Gigabit Ethernet controller

Please advice me in details with "commands" if you need more info. 

Appreciate your help.

---

### Post by lovinglinux on 2011-01-09
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it from Firefox. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. The extension also applies some teaks to improve performance and solve fullscreen issues.

I know you are using Chrome, but it will also detect the plugin installed by Flash-Aid. However, if you are on 32bit, you will need to disable the plugin bundled with Chrome. To do that, type **about[noparse]:[/noparse]plugins** in the address bar, then click the "Details" option on the upper-right corner, then scroll to the Shockwave Flash section and disable the plugin located at **/opt/google/chrome/libgcflashplayer.so**

---

### Post by sembagdod on 2011-01-11
Well i did install Flash-Aid on Firefox and restart the application. now when i try to maximize the youtube window i got this message

[CENTER][B]"The Adobe Flash plugin has crashed. no report available, reload the page to try again"  
[/B][/CENTER]

also i tried to disable the plugins on chrome, it didn't detect the new one at all. 

now let's focus on Firefox, the installation was so smooth why it didn't work? :(

---

### Post by lovinglinux on 2011-01-11
> **sembagdod said:**
> Well i did install Flash-Aid on Firefox and restart the application. now when i try to maximize the youtube window i got this message

[CENTER][B]"The Adobe Flash plugin has crashed. no report available, reload the page to try again"  
[/B][/CENTER]

also i tried to disable the plugins on chrome, it didn't detect the new one at all. 

now let's focus on Firefox, the installation was so smooth why it didn't work? :(

Go to the extension Help tab, generate a report and post it.

Keep in mind that by default, the extension will install the beta version of Flash from Adobe. However, if you tick the "Expert Mode" you can select other versions, like the Adobe from the repositories. Trying different versions with Flash-Aid is a breeze. Just select the source you want, execute the script and restart Firefox.

---

