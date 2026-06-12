---
title: "Jaunty Problem recognizing net adapter"
date: 2010-01-05
forum: Networking &amp; Wireless
---

### Post by Timbot2000 on 2010-01-05
Hello All,

I have 2 computers, old ones, that I have been repurposing for my kids using Xubuntu 9.04 (9.10 was unstable on one). 

Long story short, last night I managed to get the older, weaker box on the net and running simply by plugging in the Belkin N-wireless adapter, discovering the Network Manager icon (this really should also be accessible from the system pull-down menu), left clicking to see all the local networks, selecting mine, and inputting the security key, and rebooting. Voila!)
However, on the newer, more powerful box, the network Manager gives me nothing but "Wired connection" at every boot (there is no such connection), I created a wireless connection under the settings (accessed through create VPN settings), but the Manager sees no wireless networks. Reboot solves nothing Network Manager is not seeing anything, I suspect that the card although powered by the USB, is not being seen by the system. 

ANy help appreciated.
Note Bene: Script newbie, not strong on terminal commands, ergo, please be methodical, sequential, and specific on any commands or scripts.

---

### Post by Timbot2000 on 2010-01-05
Addendum: Performed clean install. No change. unlike other box, Belkin adapter does not flash rhythmically, but is a solid blue light (powered)

---

### Post by changingstate on 2010-01-05
Any chance you could get the output from lsusb, please?

---

### Post by Timbot2000 on 2010-01-05
Perhaps, but keep in mind I am a newbie, just how would I do that please?

---

### Post by Timbot2000 on 2010-01-05
In addition, I tried upgrading to 9.10, whereupon there was instantaneous recognition of the adapter, as well as detection of neighboring networks, but as the system, as before started freezing up, I had to downgrade to 9.04. I currently have it on a wired connection (since the system wants one so badly), and am installing the upgrades for 9.04. Lets see.

---

### Post by teward on 2010-01-05
you have Jaunty.  yay!  open a terminal window and then type the command lspci and post the output.

---

### Post by Timbot2000 on 2010-01-06
Progress Report

Box 1, Upgraded to Karmic

Box 2 Downgraded to Jaunty (even fully updated Karmic unstable)

Moved USB adapter 1 (Belkin F5D8053 V4) from Box 1 where it formerly worked to Box 2
Worked perfectly, detecting home network and signign on easily)

USB Adapter 2 (Belkin F5D8053 V3) moved to Box 1 (Karmic) where adapter is detected, wireless enabled, but home network not recognized. Home network can be manually programmed in, and connection established, but with no send/receive (i.e. not a real connection)
lsci does not return the belkin device as identified (queries go no farther with the v4 card it was detected as a belkin device driver rt2800usb) 
Seed to get right driver to see device. 
Any help would be helpful

---

### Post by Timbot2000 on 2010-01-07
OK, guys here's where I'm at. 


Belkin F5D8053 V3001 sr2870 chipset (when plugged in computer recognizes that it has a wireless card, detects every faint network in the vicinity except my powerful network. Cannot really connect to the network even if forcibly programmed) my last option is to assume that like 4001 there is a driver conflict in Karmic, so I need to alternately blacklist and unblacklist drivers until something works. 
Could somebody please instruct me briefly how to (un)blacklist drivers?
Also, which command will help me check the driver currently operating on the device?

Thank you in advance

---

### Post by Timbot2000 on 2010-01-10
Solved

---

