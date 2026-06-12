---
title: "USB Dongle to Monitor Mode"
date: 2006-03-24
forum: Networking &amp; Wireless
---

### Post by Funktown on 2006-03-24
Hello all!

I've wrestled with my D-Link G122 USB Dongle to finally connect, and all is good. I can browse my favorite sites, check my email, talk with friends and whatnot.. but I can't connect it to monitor mode.

I've made sure the connection is up, and **iwconfig wlan0 mode monitor** returns an error saying that "Monitor" is an invalid option. I'm on windows right now, so I can't reproduce the error message exactly.. but it was basically saying that it didnt know of a Monitor mode. 

Has anyone else had this problem? I'm using the windows drivers through ndiswrapper.. maybe I should try switching to native linux drivers (no idea how, though)? Does the Dongle call "Monitor" mode something else?

EDIT: Forgot, I'm using Breezy.. not Dapper.

---

### Post by towsonu2003 on 2006-03-25
it is possible that the driver you are using does not know a monitor mode. some drivers have that problem. not everything works with some drivers... you could check out the driver's maintainer's page (ndiswrapper?), google, file a bug report to ubuntu... someone else here may have better suggestions though.

---

### Post by Funktown on 2006-03-25
I heard that the native linux driver rt2500 works with this. I installed all of it from the repositories and **sudo modprobe rt2500** worked just fine. I don't really think I understand the concept all that well. though.. having little experience in wireless networking and kernel structure/workings. How do I tell my USB Dongle which module/driver to use? I want to scrap ndiswrapper and replace it with rt2500.. but have no idea how.

---

