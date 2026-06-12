---
title: "I want to use both wired and wireless ports"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by grahams on 2009-10-09
I need to use my laptop to connect to a development network that is not connected to the internet. While I'm connected there I would like to be able to check emails etc.

How can I configured my 9.04 system to enable the wired Ethernet port to connect to the dev network while the wireless port connects to a corporate WPA wireless network. 

Windows users can easily do this.

---

### Post by Iowan on 2009-10-09
To use more than one interface you will need to configure (more than one) via */etc/network/interfaces*. Part of that configuration will include setting up routing (gateway).

---

### Post by grahams on 2009-10-11
Thanks

The issue I had adding wlan0 in /etc/network/interfaces is that I do not know how to connect to a wireless LAN with an WPA2 passphase. iwconfig does not seem to support WPA2. Networkmanager does this part well, but does not support 2 connections.

I've also tried wicd but it sees no networks. The only tool that seems to fully support the Intel 4965 AG chip in this laptop seems be networkmanager.

---

### Post by Iowan on 2009-10-11
[Here]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") is a help page... but somewhat dated.  [Another]("http://ubuntuforums.org/showthread.php?t=202834") one that reports being tested with Jaunty.

---

### Post by houstonbofh on 2009-10-11
> **grahams said:**
> I need to use my laptop to connect to a development network that is not connected to the internet. While I'm connected there I would like to be able to check emails etc.

How can I configured my 9.04 system to enable the wired Ethernet port to connect to the dev network while the wireless port connects to a corporate WPA wireless network.
If I am reading this right, you want to browse the Internet on wlan, while also connecting to a single network on lan.  This is easy.

1) Right click on your network manager icon, and select 'Edit Connections.'

2) Under 'Wired' click '+ Add'

3) Name it something, uncheck 'connect automatically' select the 'IPV4' tab, and give yourself static IP, but do not fill in the gateway.

By not putting a gateway in, your lan interfaces has no default gateway, so the wlan one can be used.  Otherwise the lan gateway takes precedence.

---

### Post by grahams on 2009-10-11
Many thanks, I will give it a go on Monday

---

### Post by grahams on 2009-10-12
Even when turning off auto connect, assigning a static IP with no gateway I still can not get the wlan0 and eth0 to both be on. 

As soon as I select a wired network, it disconnects from me from the wireless network. Somewhat of a PITA

Thanks in advance for any suggestions.

---

### Post by houstonbofh on 2009-10-12
It does not do this for me.  How is your "static configured?  All options, please...

Like for me,

Connect Automatically is off.
First two tabs (Wired and 802.1x Security) are stock.
IPv4 has been set to manual, IP, subnet, no gateway, no DNS, no search domains, no routes.

Also, both networks are different subnets.

---

### Post by Iowan on 2009-10-12
Have you tried setting up eth0 in */etc/network/interfaces* and letting NM manage the wireless?

---

### Post by grahams on 2009-10-12
I have actually the following

Connect automatically, turned off

manual ip, 192.xxx.xxx.xxx, netmask 255.255.25 Gateway 0.0.0.0
No routes, no dns

As soon as the wired cable is pulled in, the wireless is disconnected and "enable wireless" is greyed out

---

### Post by grahams on 2009-10-12
> **Iowan said:**
> Have you tried setting up eth0 in */etc/network/interfaces* and letting NM manage the wireless?

I tried setting eth0 in /etc/network/interfaces, but NM still blocks me settling the wireless port if the wired port is active and will disconnect me as soon as I plug in the wired cable.

The only way I've got both ports to light up is by removing NM and adding eth0 and wlan0 in /etc/network/interfaces, but then I can not connect to the WPA2 wireless lan.

---

### Post by PrePenguin on 2009-10-12
> **grahams said:**
> I tried setting eth0 in /etc/network/interfaces, but NM still blocks me settling the wireless port if the wired port is active and will disconnect me as soon as I plug in the wired cable.
 
The only way I've got both ports to light up is by removing NM and adding eth0 and wlan0 in /etc/network/interfaces, but then I can not connect to the WPA2 wireless lan.
 
 
Ubuntu has a bug with wpa2 read the sticky at top of this forum section for possible fix.

---

### Post by grahams on 2009-10-13
Boy do I feel dumb. 

I just found a bios setting on my laptop (Compaq 2510p) for "LAN/WLAN Switching" and it was set to enable. After I disabled it I can connect both LAN and WLAN port simultaneously via NM

Thanks for the advice. Sorry for wasting people's time

---

### Post by Iowan on 2009-10-13
Not a waste of time - perhaps you have helped someone else solve a similar problem.

---

