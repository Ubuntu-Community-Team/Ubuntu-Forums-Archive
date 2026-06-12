---
title: "Bluetooth Internet sharing"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by nedim on 2009-04-22
Hello! 

I've been searching the net for an answer to this problem and so far I've had little luck, so I decided to start a thread on ubuntuforums, knowing there will be someone here that can help me.

I would like to configure a computer with Ubuntu or Ubuntu server 8.10 (maybe 9.04 in a few days) to enable Internet connection sharing for bluetooth devices (mainly mobile phones, perhaps laptops). 

I have Ubuntu 8.10 installed, the hardware works fine, the bluetooth adapter is correctly recognized and working, the server is connected to the Internet. I can pair a SE K800i and exchange files between the two. 

The desired scenario is the following: The server is running, there are people nearby with their mobile phones, they access the Internet over bluetooth through the server. 

There is a number of web pages with bluetooth howtos ([here]("http://triptico.com/docs/bluetooth.html"), [here]("http://bluez.sourceforge.net/contrib/HOWTO-PAN"), [here]("http://www.howtoforge.com/bluetooth_pand_debian_etch")), but these seem outdated. Most of them require editing the /etc/bluetooth/hcid.conf or similar configuration files that do not exist in Ubuntu 8.10. How can this be done in Intrepid?

The configuration details are as follows:
- the server is connected to the Internet through the wireless wlan0 interface, and is a dhcp client;
- the server has a bluetooth pan0 interface where multiple users should be able to connect;
- the server should share the Internet connection with all the users;
- the server already knows the bluetooth addresses of the users that are going to connect.

Looking forward to answers and more questions. Perhaps we can write a HOWTO if we solve this problem, since a lot of users are complaining on other forums.

---

### Post by nedim on 2009-04-23
No clues?

---

