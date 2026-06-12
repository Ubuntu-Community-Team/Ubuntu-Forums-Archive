---
title: "Cannot connect to internet through wireless network"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by CrammitTheFrog on 2010-01-11
I just recently purchased a wireless network and I have dial-up internet.  Since, the router-to-modem connection is for broadband, I was forced to setup a peer-to-peer network with static IPs and one computer act as a gateway.  Also, all computers in my house run windows which connects to the internet fine, but my laptop running Ubuntu 8.04 will not.  After I set my static info in the network config, I can no longer see the wireless network.  If I set the config to be roaming, then the network is available and works properly except accessing the internet since the gateway is not established while in roaming mode.  My guess is what I enter in the SSID field.  I tried the network name, but that did not work.

---

### Post by Iowan on 2010-01-11
Do you have a DHCP server on your network? (You mentioned static addresses, so I suspect not.) Is your configuration via Network Manager or */etc/network/interfaces*? 
I just noticed that this Hardy workstation has "roaming" enabled. I may try disabling it to see if there's any change.

---

### Post by CrammitTheFrog on 2010-01-11
No, I do not have a DHCP server setup, and I'm using Network Manager.

---

### Post by Iowan on 2010-01-11
More questions: 
The laptop connects via wireless?
How does the wireless tie into the modem/router?
Is the router also the wireless access?
Are the Windows machines wired or wireless?

[Here]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") is a help page for wireless troubleshooting - you've probably seen it already...

---

### Post by CrammitTheFrog on 2010-01-12
All computers, windows and my laptop running Ubuntu, are connected via the wireless network.  The wireless network only acts as a network and does not connect to the modem.  The connector from the router to the modem doesn't match because all modern routers are made for a broadband connector.  The modem is connected to one computer, not the laptop, which is the gateway for the network.

The router is the Netgear open-source wireless g router and the modem is an external U.S. Robotics.  I don't know the part numbers off the top of my head and I'm not next to them now.

---

### Post by Iowan on 2010-01-12
OK, I'm starting to absorb what you mentioned in your first post. It does sound like something in the static setup may not be quite right. Except that the Windows boxes are working, it might be that the router needs to have it's gateway address adjusted to point at the modem-machine. I'm still not sure how roaming works - but I presume it's DHCP... and the router wants to use the broadband connection.

---

### Post by CrammitTheFrog on 2010-01-15
Iowan,

Thank you for your help.  You were right that the static IP address were not right.  The info I entered into the Network Manager was not getting implemented like it should.  I had to manually enter the addresses to get it to work.

The problem may be that there is no option for no password.  The Network Manager may just make the password blank, but still implements the incryption setting.  I do not know for sure, but this is my hypothesis.  I will have to take a look in see.  I have not set a password for my wireless network yet, because I have been having trouble doing so.  It's probably something to do with the unique network setting that is currently being used.

Here is the link that helped me fix this problem, [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539).

I have one question though, I could not find the terminal command for setting the DNS addresses.  If you know it, will you post it here so that I can have it in the future?

---

