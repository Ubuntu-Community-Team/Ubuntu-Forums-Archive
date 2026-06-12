---
title: "usb adsl modem connection problem"
date: 2011-01-13
forum: Networking &amp; Wireless
---

### Post by upsla on 2011-01-13
Hi everybody
I am a newbie to Linux and i have Maverick Meerkat 10.10 installed on computer as second OS. My problem is with modem. I use Beetel 100 CX Usb Adsl modem supplied by Airtel,
I have no problem in using under Windows. But under ubuntu i am not good in getting it to work.However i did not give up, so searched the forum and managed to get modem detected and the light is on. "lsusb" command lists the modem.
So somebody from this forum please provide detailed steps to overcome my problem.:confused:


[ATTACH]180908[/ATTACH]

---

### Post by upsla on 2011-01-17
Hi everybody
I am a newbie to Linux and i have Maverick Meerkat 10.10 installed on computer as second OS. My problem is with modem. I use Beetel 100 CX Usb Adsl modem supplied by Airtel,
I have no problem in using under Windows. But under ubuntu i am not good in getting it to work.However i did not give up, so searched the forum and managed to get modem detected and the light is on. "lsusb" command lists the modem.
So somebody from this forum please provide detailed steps to overcome my problem.:confused:

---

### Post by dineshs on 2011-01-17
Maybe you have seen this
[https://help.ubuntu.com/community/UsbAdslModem](https://help.ubuntu.com/community/UsbAdslModem)

---

### Post by upsla on 2011-01-18
hi i am posting my screen grab of lsusb  here

---

### Post by dineshs on 2011-01-18
Do you use a PPPoE dialler in windows.What does ```
ipconfig /all
``` say in windows when connected?pl post results

---

### Post by dineshs on 2011-01-19
Please post what you get for ```
ifconfig -a
```and```
sudo dhclient nas0
```

---

### Post by upsla on 2011-01-24
> Do you use a PPPoE dialler in windows.What does  	Code:
 	ipconfig /all 

Hi sorry for not responding to your question. 
But is it safe to post the ipconfig results forum.

---

### Post by starscalling on 2011-01-28
> **upsla said:**
> Hi sorry for not responding to your question. 
But is it safe to post the ipconfig results forum.

Hello,


if it shows a 192.168 type address, then your mostly fine, you may wish to change the third octet to obscure it, but your behind nat and that's not your external (public ip) so it should be 'ok'

if it shows an external IP address then your not ok to push that out unless your ip address changes often.

the second command the gentleman asked for gives:


$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 4229
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/eth0/mac.address
Sending on   LPF/eth0/mac.address
Sending on   Socket/fallback
DHCPREQUEST of 192.168.5.37 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.5.37 from 192.168.5.1
bound to 192.168.5.37 -- renewal in 33264 seconds.


same rule would apply - i've manipulated the .5 section to obscure mine, but would not have really worried about posting that, i did remove my mac.address

---

