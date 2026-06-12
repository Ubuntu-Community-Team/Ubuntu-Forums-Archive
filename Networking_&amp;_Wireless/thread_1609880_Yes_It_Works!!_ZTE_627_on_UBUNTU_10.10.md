---
title: "Yes It Works!! ZTE 627 on UBUNTU 10.10"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by takenouchi on 2010-10-30
:KS:KS hi mates, I'm new comer here, My name Yusuf Bachtiar from Indonesia, nice to be here :)
2 days ago I download Ubuntu Netbook Remix 10.10,
really beautifull, and so simple, but it can't detect my ZTE 627 GSM modem, so I try to find the solution,
actually its already [SOLVED] in this thread [http://ubuntuforums.org/showthread.php?t=1595964](http://ubuntuforums.org/showthread.php?t=1595964)
maybe its good if I post that solution here, 

what I have done just :
- Right Click on Network Manager, choose Mobile Broadband> Add and you'll find several tabs on it
  1. connetion name : up to you, connect automatically (tick it if you want)
  2. ipv4setting : automatic (PPP)
  3. Mobile Broadband : number : *99#, username, password, apn : depends on your Operator/Provider
  4. PPP setting > configure methode > untick all except PAP

- Open Terminal and type sudo gedit /etc/udev/rules.d/zte_eject.rules
- type the my password
- type this code SYSFS{idVendor}=="19d2", SYSFS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
- reboot my Netbook
- plug in my ZTE 627
- and click the network manager and Connect (or click the connection name as you made on step 1)

.......
I post this using my new Ubuntu Netbook remix 10.10 and ZTE 627
really nice to be a part of Linux Community
have a nice day mates,

(sorry for bad english :razz:)

---

