---
title: "Wireless Connection Problems"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by JFlou on 2009-08-04
Hey I'm slightly new to Ubuntu and I have run into a problem connecting to my wireless network in my home. The encryption is WPA so it requires a password to connect. Ubuntu detects my wireless network, but when I try to connect, it says I need to input the password. When I do this, it seems like it attempts to connect, but about 1 minute later, It opens the same window asking me for my password, but it has a long string of dots in place of my original password, I remove the dots and see a string of letters and numbers that looks like hexadecimal. I then try to connect with the current password, but a minute later, the same window appears. I've tried browsing the forums to figure out what's up, but I can't seem to find anything that fixes my problem. I've also tried connecting to unencrypted wireless networks and it works just fine. PLEASE HELP!!!

---

### Post by realzippy on 2009-08-04
What is your password? ;-)
ASCII or HEX?
Quite shure its ASCII,when you are asked for your pwd,
scroll up or down and select  "ASCII passphrase" instead of HEX..

---

### Post by JFlou on 2009-08-04
Well, it doesn't exactly allow me to scroll through, it just shows me this.

---

### Post by ajgreeny on 2009-08-04
There is no mention of the wireless adapter you are using, which could be the problem.  As an example, an older laptop in this household has a Netgear WG511 v2 pcmcia card and that will only connect using WEP with ndiswrapper with the WinXP .inf driver.  Trying to use WPA just gets me the same problem as you are seeing.

Just to see if the problem is the same as mine change the encryption to WEP and try again to connect.  If that works you will at least be one step further forward, and may just have to accept WEP for the time being, and hope that WPA can be enabled in a future ubuntu version.

---

### Post by JFlou on 2009-08-04
Well my msi laptop is brand new, but i'll try it.

---

### Post by JFlou on 2009-08-04
Okay, for some reason it won't let me connect using WEP, it's back to square one again. also, I can't seem to get ndiswrapper working either, it tells me that there are no windows drivers, but obviously there are if I'm able to access the internet from Vista, right?

---

### Post by realzippy on 2009-08-04
Which driver do you try to use?
Why ndiswrapper?
Which wifi device?
The vista .inf file not has to be the one which works with ndiswrapper..

---

### Post by JFlou on 2009-08-04
Well for some reason it can't read the partition that all of the Vista OS stuff is on, so I can't access it.

---

### Post by realzippy on 2009-08-04
No need to mount vista..
Which card,driver are you attempting to use?

---

### Post by JFlou on 2009-08-18
Well the wireless card I'm using is a RaLink, but for some reason I can't find the exact specs on the card. I'm trying to use the drivers that are included with it, but for some reason the driver is a .sys file and the wrapper only reads .inf files. I have no idea how ndiswrapper works or if it will even solve my problem since the problem isn't with finding networks with my wireless card, but that I simply can't connect to password protected networks.

---

