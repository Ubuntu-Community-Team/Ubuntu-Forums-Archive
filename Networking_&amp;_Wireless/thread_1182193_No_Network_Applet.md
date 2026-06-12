---
title: "No Network Applet?"
date: 2009-06-08
forum: Networking &amp; Wireless
---

### Post by ZootHornRollo on 2009-06-08
Hi,

I have installed ubuntutudio 9.04 but am having issues with my wireless.

There is no Network Applet in the top right of the screen (or any other part).  I tried add/remove software and selected it but it won't let me load it as i have no internet connection.

In system/admin/network i tried to configure the connection but there is no option for WPA only WEP.  I also seem to remember the last time i had to configure the card through system/admin/network i ended up selecting 'enable roaming' to get it to work, but that isn't there.  This card works out of the box in a straight Ubuntu 9.04 install and has done since 8.04.

I tried lspci and the card is detected.

tried ```
sudo iwlist scan
```

and my network and my neighbours all show up.

any ideas how i can get connected?

---

### Post by ZootHornRollo on 2009-06-09
anyone?

---

### Post by ZootHornRollo on 2009-06-09
ok...

thus far i have moved my router close enough to the computer so i can get a wired connection.  I can get a wired connection operational and have managed to get everything updated.

I installed network manager via add/remove.  I was not able to get any connection what-so-ever either wireless or otherwise.  I tried numerous settings but no success - even the roaming one.  When left clicking on network applet instead of showing wired networks and wireless networks it states unber both that they are not managed.

i have uninstalled network manager and restarted.  On booting up and logging in it connects to the wired connection without issue.

a working wired connection is better than nothing but is quite inconvenient in terms of the positioning of the router but it is none-the-less something to get me going for now.

In system/admin/network if i enter the SSID of my wireless router it shows up in the drop down with a bar next to it showing the signal strength but as i am using WPA-PSK and not WEP i cannot enter the key to connect.

any help on getting the wireless working would be appreiciated.

---

