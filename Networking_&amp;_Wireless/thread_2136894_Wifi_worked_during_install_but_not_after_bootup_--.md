---
title: "Wifi worked during install but not after bootup -- panel disappears"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by TroySmith80 on 2013-04-18
Kind of a weird problem. I have an old (~2002) Dell laptop that i  thought i'd try Lubuntu on. First i tried Lubuntu 12.10 but that didn't  work because the computer doesn't support PAE. So i googled and found  that i need to use 12.04. So i install the older version and during the  install process the computer was able to "see" the wifi networks in my  area and connect to mine.

After installation was complete i fired  up chromium and got no connection. When the computer boots, i get a  notification that wireless networks are available and that i should use  the network menu to connect to one. So i stumbled around (complete linux  newbie) looking for network  controls. I found the "Network Connections" dialog, but it wasn't  showing any networks. The device  manager type app shows the wifi adapter and all appears ok there as far  as i can tell. I managed to add the "Manage Networks" applet to the  panel, but whenever i click on the little icon for the wifi network, the  entire taskbar panel disappears! To get it back i have to go to the  terminal and type "lxpanel --profile Lubuntu".

What's going on?  Why can the computer tell there are networks out there, but I can't find a way to connect to them? And why does the panel disappear when i click on  the network icon?

Thanks in advance!

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by TroySmith80 on 2013-04-19
3  [URL="http://smg.photobucket.com/user/Trizzle/media/IMG_0409_zps2407dd7e.jpg.html"][IMG]http://img.photobucket.com/albums/v61/Trizzle/IMG_0409_zps2407dd7e.jpg:original[/IMG]
[/URL]
[[IMG]http://img.photobucket.com/albums/v61/Trizzle/IMG_0408_zpscbdfa6f5.jpg:original[/IMG]]("http://smg.photobucket.com/user/Trizzle/media/IMG_0408_zpscbdfa6f5.jpg.html")
1 [[IMG]http://img.photobucket.com/albums/v61/Trizzle/IMG_0407_zpse63ee04b.jpg:original[/IMG]]("http://smg.photobucket.com/user/Trizzle/media/IMG_0407_zpse63ee04b.jpg.html")

---

### Post by TroySmith80 on 2013-04-19
You should be able to click those images (even if it appears broken) and see the results of those commands. 

The computer is a Dell Inspiron 8600. It has a centrino processor at 1400Mhz and 1gb RAM. 

If i go into the system profiler (the thing i referred to before as the device manager type app) under PCI devices i find: 
Network Controller Intel Pro/Wireless LAN 2100 3B Mini PCI adapter (rev 04)    
Kernel Module ipw2100

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by TroySmith80 on 2013-04-22
Ok, thank you for the response. Looks like it's going to be problematic.

---

