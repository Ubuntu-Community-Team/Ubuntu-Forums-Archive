---
title: "Newbie needs help"
date: 2011-12-12
forum: Networking &amp; Wireless
---

### Post by indianaburn on 2011-12-12
As the title says....i am a complete newbie to Ubuntu....and I like the look and feel of it so far.  HOWEVER....i did a complete wipe of my hard drive, and did a clean install of the newest version of Ubuntu.  I have a Toshiba Satellite L675D-S7015. Problem is...I cant get my wireless to connect. It shows my home network, I enter in the key, and it goes to connect, and then just bounces back asking for authentication password again.  I know the key is correct...so what am I doing wrong?  Any help would be great.  I have the dvd back up of the Toshiba drivers and applications, but not my WIN7 dvds, so I am not sure how to get these drivers installed or what not.  Like I said NEWBIE

---

### Post by RealityMaster on 2011-12-12
Are you sure you used the right security type?  

eg WPA2 vs WEP...

---

### Post by indianaburn on 2011-12-12
Thats the thing...it doesnt have the EXACT same type of security type as my router.  the router.  the router security type is WPA-TKIP.  its the new comcast arris cable/phone/net router.  so I dont know what to put in th config type when logging in

---

### Post by Bucky Ball on 2011-12-12
Can you change the security type on the router to match one of the options on your machine? If not you could try the two WPA options and see if one works. Might just be the same with diff name.

---

### Post by RealityMaster on 2011-12-12
If your router supports it switch to WPA2 AES PSK (PreSharedKey), should fix it...


[http://ubuntuforums.org/showthread.php?t=1311866](http://ubuntuforums.org/showthread.php?t=1311866)

---

### Post by indianaburn on 2011-12-12
it does allow me to change it. but when I change it to WPA2 AES PSK, my desktop at home wont connect to the net. says network found but wont connect.  its an older machine running XP.  So I am stuck at what to do.  My desktop works now, and my laptop did with Win7 on it before I wiped the drive.  I am just lost.

---

### Post by RealityMaster on 2011-12-12
Remove the network on your desktop and re-add it then both machines will work.  :)

---

### Post by RealityMaster on 2011-12-13
I should clarify, remove and re-setup the wireless on the XP machine, then both should work.

---

### Post by indianaburn on 2011-12-13
i figured that that was what you meant.  LOL  I am going to install a 54 bit version on my laptop since tha is what I have, and then try that see if it works then before changing things.  Because when I changed it to WPA2 AES PSK Ubuntu connected to the Ubuntu Google homepage, but wouldnt go anywhere else.  so I am not sure whats going on.

---

### Post by Bucky Ball on 2011-12-13
That sounds like you may need to provide the DNS server IPs, although I thought that would be taken care of by ISP as you are getting IP from DHCP, if that makes sense. Did you have to provide DNS servers in any other setup, on a Windows machine, perhaps?

---

### Post by indianaburn on 2011-12-13
No I didnt.  I just gave the encrypt key and it logged right in with no problems.

---

