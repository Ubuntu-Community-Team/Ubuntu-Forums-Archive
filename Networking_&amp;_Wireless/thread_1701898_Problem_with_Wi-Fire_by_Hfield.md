---
title: "Problem with Wi-Fire by Hfield"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by broadw on 2011-03-07
Hello... I have checked this forum pretty extensively, but could not find any information on Hfield's Wi-Fire range booster antenna for improving reception of wifi.  If this has been answered before, my apologies, and please guide me to the thread.  Also, if this is not the proper forum for this question, please let me know and I'll move it.

I have been using Ubuntu's 10.04 netbook edition very successfully on my Asus 1005HAB.  It is dual booting with Windows XP (which I hardly ever use any more). 

Recently I bought a Wi-Fire wifi antenna to improve my range in certain wifi areas, and it works great on this Asus under Windows, but I can't get it working under Ubuntu.  It plugs into a USB port, and I have tried having it plugged in before turning the netbook on, as well as plugging it in while Ubuntu was up and running.

The problem is that the netbook under Ubuntu tells me that the device is disconnected (or rarely, not available).  When I  click on my wifi icon, it tells me:

(ZyDAS USB2.0 WLAN) disconnected

That is definitely the WiFire showing up... it disappears as soon as I unplug the antenna from its USB port.  When I first plug in the WiFire, there is no response from the netbook indicating something has been plugged into a USB port, however.

I would love to use the WiFire, and it is supposed to be compatible with this version of Ubuntu.  Can anyone offer any advice as to how to get my netbook to utilize it?

Thanks!

Matt

---

### Post by broadw on 2011-03-08
Do I have this posted in the wrong forum?  I thought these Wi-Fires would be used by a fair amount of people, especially after all of the good reviews.  Mine is amazing under Windows... I just can't get it going under Ubuntu.

Has anyone heard of ANYONE using Linux getting one of these Wi-Fires to work with their machine?

---

### Post by broadw on 2011-03-10
Beuller?

---

### Post by buddy0101 on 2011-03-13
Hi, Just bought one myself and it would not work either. I finally got it to work using two out of the box ubuntu software packages. &quot;Wine&quot; and &quot;Windows Wireless Drivers&quot;.  Wine allows you to install and run windows programs in Linux. Use Wine to install the windows drivers for WiFire on your pc (the ones that come on the CD with the Wi-Fire or download it from the Wi-Fire site) /media/cdrom0/Windows/Wi-FireInstaller_Win_2_3.exe  Install Wi-FireInstaller_Win_2_3.exe by placing the file on you destop and type in terminal mode  cd ~/Desktop wine Wi-FireInstaller_Win_2_3.exe  I should mention at this point that even though wine has installed the windows program for the wi-fire, it won't work through ubuntu. I've really only used this program to get the windows driver unpacked from the exe file.  After you install Wi-FireInstaller_Win_2_3.exe use the Wine browse the C:drive utility and look for the file ZD1211BU.INF (all caps) in folder Program Files/hfield technologies inc/wi-fire connection manager/drivers.  Copy ZD1211BU.INF to your desktop.  There are some other files with the same name in the some of the highfield technoligies inc sub folders but they won't work in the &quot;windows wireless drivers&quot; program.  Next install the &quot;windows wireless drivers&quot; program. You'll find the program under your system administration tab. Open the program (it will ask for you password) and select &quot;install new driver&quot;. Select the desktop for the location and install ZD1211BU.INF  If you have the wi-fire plugged in it should install and tell you that the hardware is present. If it tells you that you don't have a valid driver, then you've copied the wrong ZD1211BU.INF file. Remove the driver pick another from the &quot;wine&quot; C drive and try again, it is in there.  Once you have ZD1211BU.INF installed as a valid driver you're wi-fire should be up and running. My is working great.  Hope this helps and works for you. First time I've posted on one of these forms so if you have any questions let me know.

---

