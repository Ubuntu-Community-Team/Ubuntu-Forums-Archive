---
title: "/etc/network/interfaces and WEP"
date: 2005-03-09
forum: Networking &amp; Wireless
---

### Post by otterit on 2005-03-09
I'm having a tough time connecting to my wireless router (NETGEAR MR814v2).  The router is setup as:

* Channel - 7
* Shared Key
* 64 Bit (##########)
 
On Ubuntu, i have my /etc/network/interfaces setup as:

iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid homelan
wirless_key ####-####-## [4]
wireless_channel 7


Can someone tell me where I am making a mistake in my /interfaces?  

Thank you!

---

### Post by KenLin on 2005-03-09
[QUOTE=otterit]I'm having a tough time connecting to my wireless router (NETGEAR MR814v2).  The router is setup as:

* Channel - 7
* Shared Key
* 64 Bit (##########)
 
On Ubuntu, i have my /etc/network/interfaces setup as:

iface wlan0 inet dhcp
name Wireless LAN card
wireless_essid homelan
wirless_key ####-####-## [4]
wireless_channel 7


Can someone tell me where I am making a mistake in my /interfaces?  

Thank you![/QUOTE]
 My key doesn't have any dashes in it. try that?

---

### Post by otterit on 2005-03-10
[QUOTE=KenLin]My key doesn't have any dashes in it. try that?[/QUOTE]

Here's what I tried.... I think I am getting closer.

iface wlan0 inet static
name Wireless LAN card
wireless_essid "lanconnect"
wireless_key restricted [4] 1a2b3c7c8c90
wirless_channel 7
wireless_mode managed
address 192.168.0.18
netmask 255.255.255.0
broadcast 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1 

Any suggestions??!!

---

### Post by Swab on 2005-03-11
Does it work if you disable WEP on the router and in the interfaces?  If so then maybe you could try changing the WEP key on the router to open system and then setting:
wireless_key open 1a2b3c7c8c90

---

### Post by otterit on 2005-03-12
[QUOTE=Swab]Does it work if you disable WEP on the router and in the interfaces?  If so then maybe you could try changing the WEP key on the router to open system and then setting:
wireless_key open 1a2b3c7c8c90[/QUOTE]

Hmm...That might be a good idea.

My new problem is that I have a 'blinking link' light on the WUSB device.  I haven't found a way to make the light stop blinking.

The wlanctl-ng stuff doesn't work.  :-(

I am about to give up completely and load Win98 on this machine.

---

### Post by ichoudhury on 2005-03-13
What is your output for

ifconfig

and 

iwconfig 

??

---

