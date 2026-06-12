---
title: "Can't connect to wireless network, passwordbox will display over and over again."
date: 2012-08-10
forum: Networking &amp; Wireless
---

### Post by Egonosaur on 2012-08-10
Hello everyone! :)

A couple of days ago I bought a new Netgear N600 WNDA3100v2, which I tried to install according to the little guide @ [COLOR=Blue][http://ubuntuforums.org/showthread.php?t=1964173](http://ubuntuforums.org/showthread.php?t=1964173)[/COLOR].

However I've not managed to connect to the wireless network since the passwordbox will show up over and over again, prompting me to write the correct password or passphrase for the network.

I really need my wireless adapter to work since I don't have any possibilities to drag any ethernet cables to my computer.

I have recently converted to linuxeism so I'm quite new.
I'm using Ubuntu 12.04 LTS, WPA2-PSK encryption on the network,

and when I use lsusb 

i get:  Bus 001 Device 002: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323].

I really appreciate all help I can get, and big thanks in advance!

//Egonosaur

---

### Post by MichaelMale on 2012-08-10
Hi,

Out of curiosity, is your ISP BT? Are you able to connect to other networks?

If it is BT, check this thread. The fixes haven't worked very well for me, but I hope they do for you:

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

---

### Post by Egonosaur on 2012-08-10
> **MichaelMale said:**
> Hi,

Out of curiosity, is your ISP BT? Are you able to connect to other networks?

If it is BT, check this thread. The fixes haven't worked very well for me, but I hope they do for you:

[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473)

Hi there!
Nope, my ISP is not British Telecom, and I have connectivity from the router to Internet, I tried to connect to my other wireless router yesterday, and both of them are using wireless passwords, 
and the computer does the same thing with the passwordboxes. (Tries to connect and pops up a new passwordbox again)

Thanks for your interest :)

---

### Post by Egonosaur on 2012-08-11
bump

---

### Post by Egonosaur on 2012-08-19
any ideas?

---

### Post by Egonosaur on 2012-09-06
no ideas?

---

### Post by steeldriver on 2012-09-06
if you search the forum for your device's pci id '0846:9011' it looks like others have had to use ndiswrapper to make this device work

you will need to get the correct windows driver (either 32 bit or 64 bit depending which you're running)

I've never needed to use ndiswrapper so I'll leave the detailed steps for someone else

hope this helps

---

