---
title: "Howto: Ubuntu 11.04 + Cisco VPN / vpnc"
date: 2011-05-05
forum: Networking &amp; Wireless
---

### Post by nesquik on 2011-05-05
I only have Internet access through a Cisco VPN and had a lot of trouble setting up **Ubuntu 11.04**. Here's what I figured out:

- Before installing Ubuntu, disconnect your LAN cable or the installer will crash at the "Where are you?" screen.

- When done installing, download the following files using a computer with Internet access:

[http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb](http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb)

[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.8.4-1_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.8.4-1_i386.deb)

[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.8.4-1_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.8.4-1_i386.deb)

- Transfer them to your Ubuntu machine (USB flash drive etc.) and install them.

- Restart. Set up your VPN connection. I HAD to check "Available to all users" or it would give me some "VPN secrets" error message. Restart again. Connect your cable, connect to VPN.

- Internet access!


**Update: Ubuntu 11.10**

Files needed:
[http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb](http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb)
[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.9.0-2_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.9.0-2_i386.deb) (new version)
[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.9.0-2_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.9.0-2_i386.deb) (new version)

I had to plug my LAN cable in and out to enable the "Install" button in Ubuntu Software Center.

---

### Post by felixq78 on 2011-06-29
> **nesquik said:**
> I only have Internet access through a Cisco VPN and had a lot of trouble setting up Ubuntu 11.04. Here's what I figured out:

- Before installing Ubuntu, disconnect your LAN cable or the installer will crash at the "Where are you?" screen.

- When done installing, download the following files using a computer with Internet access:

[http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb](http://ftp.debian.org/debian/pool/main/v/vpnc/vpnc_0.5.3r449-2.1_i386.deb)

[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.8.4-1_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc_0.8.4-1_i386.deb)

[http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.8.4-1_i386.deb](http://ftp.debian.org/debian/pool/main/n/network-manager-vpnc/network-manager-vpnc-gnome_0.8.4-1_i386.deb)

- Transfer them to your Ubuntu machine (USB flash drive etc.) and install them.

- Restart. Set up your VPN connection. I HAD to check "Available to all users" or it would give me some "VPN secrets" error message. Restart again. Connect your cable, connect to VPN.

- Internet access!

Is one of the files a duplicate of an update ?

---

### Post by nesquik on 2011-07-01
These are 3 different files, you need all 3.

---

### Post by threepwood960 on 2011-07-06
I use vpn cisco from long time ago and I lost it with Ubuntu 11.04. I have followed your intructions but it doesn't work for me. Any help?

---

### Post by nesquik on 2011-07-06
Please post an error message or so.

---

### Post by qbnronin on 2011-09-11
I can't access external pages, after successful VPNC connection. Yes, I can access all internal pages in my company even our database servers. I followed instructions which actually allowed me to connect to my cisco VPN - THANK YOU for that! However, once connected I can't access any external pages, I get the following error:

[COLOR="Green"]"Google Chrome's connection attempt to [www.google.com](www.google.com) was rejected. The website may be down, or your network may not be properly configured."[/COLOR]

* The connection manager fails to connect if I set the passwords to "Always Ask" (It never asks it just fails to connect)
* The "Last Used" status does not get updated from "Never", even though I successfully connect.
* Is this some kind of proxy setup issue on the browser?
* I don't see any type of hybrid authentication option.
* I was able to successfully connect through Fedora; however, the network manager looks slightly different. Can this also be an issue with this specific version of the network manager?

---

### Post by nesquik on 2011-09-11
I'm using the default settings with both passwords saved. Maybe try this.
Make sure you have "Available to all users" checked.
After editing your settings always run "sudo restart network-manager".
Don't know about hybrid auth.

What's the output of "ping google.com"?

---

### Post by dziegiel on 2011-09-20
I have problem with Cisco VPN too:
> 
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> Starting VPN service 'vpnc'...
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN service 'vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 2601
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN service 'vpnc' appeared; activating connections
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN plugin state changed: 1
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN plugin state changed: 3
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN connection 'Agora' (Connect) reply received.
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <warn> VPN plugin failed: 1
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN plugin state changed: 6
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> VPN plugin state change reason: 0
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <warn> error disconnecting VPN: Could not process the request because no VPN connection was active.
Sep 20 22:46:30 Ubuntu-T60 NetworkManager[2531]: <info> Policy set 'Auto dom_166' (wlan0) as default for IPv4 routing and DNS.
Sep 20 22:46:35 Ubuntu-T60 NetworkManager[2531]: <info> VPN service 'vpnc' disappeared


---

### Post by kyleouellette on 2011-10-24
Hello,

I have to use Cisco VPN for work so instead of installing any GUI for it, I use vpnc
**$ sudo apt-get install vpnc**
then connect using vpnc
**$ sudo vpnc**
and disconnect
**$ sudo vpnc-disconnect**

Hope that helps!

---

### Post by threepwood960 on 2011-10-31
Sorry for the delay. I have connected by kvnc without problems (well, it shows multiple messages: disconnect - connect - dissconnect... though it connect rightly.

But I would like to connect with vpnc (from network-manage). What should I send if you can help me?

---

