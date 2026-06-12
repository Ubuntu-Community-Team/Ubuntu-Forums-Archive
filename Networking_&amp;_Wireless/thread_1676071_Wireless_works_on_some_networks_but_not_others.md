---
title: "Wireless works on some networks but not others"
date: 2011-01-26
forum: Networking &amp; Wireless
---

### Post by lextori on 2011-01-26
Okay,

I have a system 76 panp7, which uses rtl819xSE for it's driver. I also have a Toshiba laptop that uses the same driver, I'm getting the same symptoms from them. The panp7 is using x64, while the toshiba is on 32 bit.


On my home network, at the local coffee shop, and pretty much everyone I know's home wi-fi everything works wonderfully. 

On the university network, I get a useful connection about 1/3 of the time. The wireless disconnects randomly, and once disconnected will not re-associate to any network without a restart.

I've tried turning wi-fi off and back on again to re-establish connection. Reboots will get me another chance at connecting to the uni-network, or let me connect elsewhere without a  problem. 

I strongly suspect that it's the school's fault, since it only happens on their network. but IT won't fix it unless I can prove that it's on their end(and I'll likely need to fight uphill for that).

What logs would be useful in troubleshooting this issue?

---

### Post by Crafty Kisses on 2011-01-26
Can I see some of the results of the following commands?
```
ifconfig
iwconfig
lspci
lsusb
```

---

### Post by gordintoronto on 2011-01-26
What's the SSID of the school network?

---

### Post by lextori on 2011-01-27
the SSID is BLUEZONE

The output of those commands on my Panp7 on my home network are attached.

Are the same things on the toshiba needed, and is the output of these commands location sensitive?

---

### Post by gordintoronto on 2011-01-27
From what I have seen, Ubuntu doesn't like SSIDs with upper case letters. Or maybe it's Network Manager, you might try wicd.

---

### Post by lextori on 2011-01-27
Thanks! gordintoronto, that seems to have solved the issue. Do you know if there is an existing bug for this issue?

---

### Post by gordintoronto on 2011-01-29
I made two suggestions, which one worked?

I have not checked whether there is a bug report on this.

---

### Post by lextori on 2011-02-01
Well damn. 

I thought that installing switching to use wicd had solved the issue, but it appears to be continuing. I'm also now having trouble using this computer on my home network.

What was your second suggestion gordintoronto. I thought you were suggesting using wicd instead of network manager.

---

### Post by gordintoronto on 2011-02-02
My main suggestion was to change the SSID of the router to lower case. I'm sure your school will be pleased to do this for you. [smile]

---

