---
title: "Mythbuntu Hangs when I activate my wireless connection"
date: 2008-01-16
forum: Mythbuntu
---

### Post by fredBuntu on 2008-01-16
Setup:

wireless pci card usr 5416

[http://www.usr.com/support/product-template.asp?prod=5416](http://www.usr.com/support/product-template.asp?prod=5416)

Mythbuntu, latest release from site: [http://www.mythbuntu.org/](http://www.mythbuntu.org/)

Wireless network - dhcp - using wpa-psk encryption

First installation, newbie with mythbuntu.

=====================================================

Hi everybody, and thank you for your time reading this,

I have this problem, when I try to activate the wireless connection,

Going in: system network

 the system freeze completely.

Upon restart, it hangs on : "starting NFS common utilities"

I have read this: 

[http://ubuntuforums.org/showthread.php?t=624433](http://ubuntuforums.org/showthread.php?t=624433)

And this

[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

And all sorts of other information in this forum or on the web, but I am still stuck.

I have edited my interfaces conf and did not manage any results.

If I erase the entries in interfaces completely, the system restarts normally.

Whenever I make an attempt to activate the connection, the system freezes again.

When I go in the settings panel for my network connection in the gui, it 'sees' my ssid with no problems, it will juste not connect to it.

Any clue ?

---

### Post by fredBuntu on 2008-01-21
Anybody else experiencing these hangs when connecting to wireless ?

---

### Post by fredBuntu on 2008-01-22
FOUND IT !

Well, simply the drivers for the pci wireless card did not support wpa, doh!

Now I updated the drivers by using the ones provided for windows and uploaded them via linuxant.

[http://www.linuxant.com/driverloader/](http://www.linuxant.com/driverloader/)

Problem, in order to do this you need a license key from linuxant, I have at the moment a trial key for 30 days.

Are there any other solutions to this ??

---

### Post by browndog289 on 2008-01-22
I had a similar problem with my system - it would freeze after around 10 - 36 hours. I eventually identified the problem as my Netgear WG311v3 Wireless card. The card worked fine with ndiswrapper and WPA and I could browse the web, update the system etc but every so often it would lose association with my router and nothing but a reboot would fix it - if I didn't reboot then after 10 - 36 hours the system would freeze.

I have removed it and ordered a wireless bridge instead which ubuntu will just see as a wired network - this may be an option for you too.

Best of luck,

browndog

---

### Post by fredBuntu on 2008-01-24
Hi, thanks, my system is stable now, and the wireless works fine with the linuxant solution.

I am just wondering if I could achieve that without using the linuxant driverloader, because when the trial period is over, you have to buy a permanent license.

---

