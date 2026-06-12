---
title: "How can i get my ADSL working?"
date: 2005-12-20
forum: Networking &amp; Wireless
---

### Post by Dark Damo on 2005-12-20
Hey all i plan on switching back to Ubuntu 5.10, But i dont know how to get my ADSL to work on it :confused: 

I have a 4 port router and a Siemens SpeedStream ADSL modem. I am currently using Ethernet. What can i do?

I am Australian and my ISP is Telstra Bigpond

---

### Post by LoclynGrey on 2005-12-20
when you plug it in, turn on your unbuntu system what happens next?

---

### Post by Dark Damo on 2005-12-20
Uh i dont have it installed ATM but i did before and could never get it to work lol. I'm expecting a ATI Radeon 9800 pro in a few days so i will install when i have that plugged in :) But can you offer any help or clues on anything?

---

### Post by LoclynGrey on 2005-12-20
> Siemens SpeedStream ADSL modem
Is that a USB modem? 

and is it connected to your router or your PC?

---

### Post by Dark Damo on 2005-12-20
Its a USB/Ethernet modem I use Ethernet and its plugged directly into my router which has my computer and my sisters plugged in aswell.

---

### Post by tuxy on 2005-12-20
Good day mate,

How do you want to configure the NIC's ? DHCP or Static ? For small home networks static IP's will be easier. Since Ubuntu is Debian based it assigns the router/modem by default as 192.168.1.1 . To configure the network cards you have to look for /etc/network/interfaces. Edit the 'interfaces' file in /etc/network/interfaces through a text editor. 

In the 'interfaces' file you can add the following lines if you want to go static addressing way, you can change the IP's if you want to:

[B]auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0
gateway 192.168.1.1[/B]

If you want to go DHCP:

**iface eth0 inet dhcp**


How many network cards you have? It's better that you connect the modem/router through ethernet cable instead of USB. Linux picks up straight away if you go ethernet option.

You have do all these as root. Once you have done configuring the NIC's restart the network by:
**/etc/init.d/./networking restart**

---

### Post by mips on 2005-12-20
[http://ubuntuforums.org/showthread.php?t=95273](http://ubuntuforums.org/showthread.php?t=95273)

---

