---
title: "Wireless wont connect[please help]"
date: 2011-07-13
forum: Networking &amp; Wireless
---

### Post by Moralityboy on 2011-07-13
please help someone please help, i just downloaded ubuntu 11.04 and installed it and everything off of a cd
and now i cant connect to internet wirelessly! my wifi button on my laptop is orange and i press it and it doesnt go blue like it normally did when i had windows vista. 

i just updated my wireless driver off of ubuntu and restarted and nothing happened! its still not connecting me
to the internet, i only have access through the ethernet im using....please help somebody! i cant go ethernet, this is only temporary and i really want ubuntu, i really need it, but its not letting me go wireless. somebody please help me... 
my wireless driver is this:Broadcom  Corporation BCM4311 802.11b/g WLAN (rev 02)

---

### Post by bkratz on 2011-07-14
Read this thread and pay particular attention to the section about b43-fwcutter without a wired connection, since you do not have a wired connection available.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)


This is the section involved

[COLOR="Red"]Installing b43fwcutter with out the internet connection [/COLOR]

---

### Post by grahammechanical on 2011-07-14
Hi and welcome to the forums. This is what I wonder about:

> restarted and nothing happened!

Ubuntu will not automatically connect you to a wireless network (router) until you select that network and set up the connection. Then you have to mark the connection in Network Manager to connect automatically. Otherwise nothing will happen when you load Ubuntu.

Click on the Network Manager icon on the top panel. Is there a tick mark against Enable Networking and Enable Wireless? If not click on those lines. This is like using an on/off switch.

I guess that you are also using Windows. If so then do not switch off wireless before shutting down Windows. You need the wireless adapter switched on before you run Ubuntu otherwise it will not detect a wireless adapter in the laptop.

Regards.

---

