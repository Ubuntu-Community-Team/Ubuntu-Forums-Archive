---
title: "Open VPN"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by davisty on 2010-02-10
Im a total newbie to Ubuntu so PLEASE have patience. I had one two many viruses on Windows, so Im here at Ubuntu.

1. I have installed OpenVPN. I need to connect to an AS/400 after hours.
2. I have downloaded the unbuntu version.
3. I have extracted using the package manager.

Question: How do I actually run the program? There are no icons or anything generated ...

I know how to configue VPN, not asking that. Just how to run the program.

ANY Help is most appreciated

---

### Post by bogdan.veringioiu on 2010-02-11
Hi.
It is quite simple to connect via networkmanager (assuming that you already installed the package network-manager-openvpn):
-click on network manager icon, and you will have a section "vpn connections". From there, you have "configure vpn".
-select openvpn as vpn type, and go on, try to fill the settings.
Bogdan

---

### Post by davisty on 2010-02-11
I dont have that. The network manager doesnt list it. The package only contains openvpn-as

I downloaded it from [http://openvpn.net](http://openvpn.net)

Im using version Ubuntu 9 amd/x86 32 bit

---

### Post by bogdan.veringioiu on 2010-02-11
Hi.
Try to install it:
open a terminal and type:
> sudo apt-get install network-manager-openvpn

Then, try to add the vpn connection in network manager (it might need a reboot after installing the packages, in order to see the vpn connection type).
Bogdan

---

### Post by davisty on 2010-02-11
Thank You for your reply, it installed the network version.

But, it's not accepting the apply button it's grayed out.

I am using the password method with no certificates. Using that method the accept button isnt working.

ANY help is MOST appreciated.

Thank You for all your help

Ty Davis
Mobile, AL USA

---

### Post by bogdan.veringioiu on 2010-02-11
Personally I use the connection with certificates, and it works with no problem. I did not try password only.
However, for connecting with openvpn, you are only provided with username and password? No certificate, no config file (.ovpn)?
Bogdan

---

### Post by davisty on 2010-04-21
> **bogdan.veringioiu said:**
> Personally I use the connection with certificates, and it works with no problem. I did not try password only.
However, for connecting with openvpn, you are only provided with username and password? No certificate, no config file (.ovpn)?
Bogdan


Is there another ubuntu vpn client that I can use to connect to a windows vpn server. Ive never been able to get openvpn to work

---

### Post by mosquetero on 2010-04-21
When you were using Windows, did you know how to use OpenVPN? Which one of the machines is the server and which one is the client?

To execute OpenVPN in Ubuntu you must go to /etc/OpenVPN and there execute the command $openvpn followed by the config file, which is the same you had in Windows (Supposing that you know how OpenVPN works)

---

### Post by davisty on 2010-04-21
> **mosquetero said:**
> When you were using Windows, did you know how to use OpenVPN? Which one of the machines is the server and which one is the client?

To execute OpenVPN in Ubuntu you must go to /etc/OpenVPN and there execute the command $openvpn followed by the config file, which is the same you had in Windows (Supposing that you know how OpenVPN works)

Im new to Ubuntu and Linnux. I found the pptp(I think that's what it is) vpn and installed it and used it. Works like a champ. Started up first time.

Thank you for your gracious reply, I can tell you what, the Ubuntu community is Johnny on the spot for helping out newbies like me. Ubuntu is HANDS DOWN better than windows

---

