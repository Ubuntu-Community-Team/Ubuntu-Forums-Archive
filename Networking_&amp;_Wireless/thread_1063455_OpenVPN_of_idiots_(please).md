---
title: "OpenVPN of idiots (please)"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by MannyL on 2009-02-07
In [http://ubuntuforums.org/showthread.php?t=1063395](http://ubuntuforums.org/showthread.php?t=1063395) It was suggested that a Vpn Server will allow me to accomplish what I want to do and OpenVPN was suggested. I tried searching this forum and could not find a guide that I was able to understand. Could someone please tell me (in small words) how to setup OpenVPN so I can use my laptop to access my local network remotely.

I'm using 192.168.3.X as my ip structure

---

### Post by NoobBiscUiT on 2009-02-07
I think we're going to need some more information from you, and the network you would like to set up in order to help you out.

---

### Post by MannyL on 2009-02-07
> **NoobBiscUiT said:**
> I think we're going to need some more information from you, and the network you would like to set up in order to help you out.

Ok I;m not sure what info you will need but this is everything I know

<cable modem>---->Linksys Voip Router (192.168.3.1)

From that router is an 8 port 10/100/1000 switch with the following attached

Linksys Wireless Router   - 192.168.3.2
2003 Server               - 192.168.3.3
Xubuntu system as storage - 192.168.3.4

XP Pro desktop 1           - 192.168.3.100
XP Pro desktop 2           - 192.168.3.101

XP Pro laptop              - 192.168.3.200 (when wireless)
                             192.168.3.103 (when wired) 
Vista Laptop               - 192.168.3.201 (When wireless)
                             192.168.3.104 (when wired)

The rest of the addresses are dynamicly assigned to guests at the house connecting over wifi, an xbox and WII

My primary goals are

1) Being able to retrieve files off the xubuntu, 2003 Server and XP Pro Desktop 1 from outside my lan (such as at Panera bread) using my vista laptop

2) Being able to use VNC to view/control any of the systems remotely to assist my parents when they have problems.

---

### Post by MannyL on 2009-02-12
bump

---

### Post by Iowan on 2009-02-13
[Here]("https://help.ubuntu.com/community/SSH_VPN") is a VPN help page - but it's based on OpenSSH instead of OpenVPN.

---

### Post by MannyL on 2009-02-16
Thank you for that page but I can't quite grasp it because my systems (except for one) are Windows ones so thye don't hjave the tun

---

### Post by dmizer on 2009-02-16
It's long, but thorough: [http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

---

### Post by MannyL on 2009-02-16
Thank you that is a huge help, Now I need to get OpenVPN properly configured.

---

### Post by uzi09 on 2009-03-19
[http://www.youtube.com/watch?v=BfZV4MnGfkk](http://www.youtube.com/watch?v=BfZV4MnGfkk)

---

