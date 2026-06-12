---
title: "how to connect a usb modem through the terminal"
date: 2012-08-17
forum: Networking &amp; Wireless
---

### Post by ernes on 2012-08-17
Hello experts. I'v spent the past 2 days and 1½ hour from the third day trying to figure out how to configure my USB modem to start surfing on the net. And now i give up. Obviously i dont know what i'm doing so i need some help. I'm gettin an error when trying to connect with wvdial. Here is the error from the terminal: ```
--> Initializing modem. 
--> Sending: AT + CGDCONT=1, "IP", "bredband.tre.se" 
AT + CGDCONT=1, "IP", "bredband.tre.se" 
OK 
--> Modem initialized. 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: AT + CGDCONT=1, "IP", "bredband.tre.se" 
AT + CGDCONT=1, "IP", "bredband.tre.se" 
OK 
--> Modem initialized. 
--> Sending: ATDT*99# 
--> Waiting for carrier. ATDT*99# ~[7f]}#@!}!}!} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&URy,kT~ 
CONNECT 
--> Carrier detected.  Waiting for prompt. 
~[7f]}#@!}!}"} }9}#}%B#}%}(}"}'}"}"}&} } } } }%}&URy,'9~ 
--> PPP negotiation detected. 
--> Starting pppd at Fri Aug 17 19:20:17 2012 
--> Pid of pppd: 10401 
--> Using interface ppp0 
--> pppd: &#65533;&#65533;B  
--> pppd: &#65533;&#65533;B  
--> pppd: &#65533;&#65533;B  
--> pppd: &#65533;&#65533;B 
--> pppd: &#65533;&#65533;B  
--> pppd: &#65533;&#65533;B  
--> pppd: &#65533;&#65533;B  
--> Disconnecting at Fri Aug 17 19:20:18 2012 
--> The PPP daemon has died: A modem hung up the phone (exit code = 16) --> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 40 seconds
```And my wvdial.conf looks like this: ```
[Dialer Defaults]  
Init1 = AT + CGDCONT=1, "IP", "bredband.tre.se" 
Modem Type = USB Modem 
Phone = *99# 
ISDN = 0 
Username = * 
Password = * 
Modem = /dev/ttyACM0 
Baud = 460800 
Pin = 7702
```This is the lsusb output: 
```
Bus 001 Device 007: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard 
Bus 001 Device 004: ID 0bdb:1902 Ericsson Business Mobile Networks BV F3507g v2 Mobile Broadband Module 
``` I've changed the wvdial.config several times with no success and if i change Init1 to: 
```
Init1 = ATZ  
Init2 = AT + CGDCONT=1, "IP", "bredband.tre.se"
``` 
i get an error saying ATZ Error Bad init string.  Here's the modem i'm using [http://www.google.se/imgres?imgurl=http://www.4gltesolution.com/description_image/e372-j4.jpg&imgrefurl=http://www.4gltesolution.com/blog/portable-huawei-e372-usb-stick-helps-quicken-the-network/&usg=__x0jp65Do5fIo7xczffNSWDIJjLk=&h=400&w=400&sz=24&hl=sv&start=12&zoom=1&tbnid=c5Jw3o_vx4NKIM:&tbnh=124&tbnw=124&ei=3bIwUOIm8I3iBNb5gaAP&itbs=1](http://www.google.se/imgres?imgurl=http://www.4gltesolution.com/description_image/e372-j4.jpg&imgrefurl=http://www.4gltesolution.com/blog/portable-huawei-e372-usb-stick-helps-quicken-the-network/&usg=__x0jp65Do5fIo7xczffNSWDIJjLk=&h=400&w=400&sz=24&hl=sv&start=12&zoom=1&tbnid=c5Jw3o_vx4NKIM:&tbnh=124&tbnw=124&ei=3bIwUOIm8I3iBNb5gaAP&itbs=1) I really need some help here.  Thanks in advance.

---

### Post by dandnsmith on 2012-08-18
Can you give us some more info about your setup.
It looks to me as if you're attempting to use a serial-line dialup tool with a usb modem - but what sort of modem, and is there really a serial line connection, or is this a broadband linkup you're attempting? Is it to connect over a mobile-phone link?

---

### Post by ernes on 2012-08-18
@dandsmith i'm using a Huawei E372 USB Modem Dongle, it's a mobile broadband modem. It has a sim-card in it and it requires a pin number of 4 digits to be able to connect. I tested it on Ubuntu 12.0.4 and it works fine but i'm having a really hard time trying to set it up on Backtrack 5 R3. Any help would be much appreciated.

---

### Post by dandnsmith on 2012-08-19
I don't know anything about Backtrack.
I tried to follow the link in your edited posting - but it isn't a proper link, and goes nowhere.
Good luck in your hunt.

---

### Post by ernes on 2012-08-19
Hi, you're right, the link was broken. It seem that the post was removed. See my edit, i added a picture of the USB dongle i'm using. Do i need to provide more information? Is my question not clear enough? Thanks.

---

### Post by dandnsmith on 2012-08-20
I'm clear about what you're attempting, and the details of the device.

Unfortunately, you're outside my comfort zone and experience - I was attracted by the combination of terms 'terminal' and modem' in the post title, and wondered what exactly the situation was.

I suspect that there may be some country-oriented experience needed, given the ISP name - is there a forum closer to home for you to consult?

The whole technique of addressing the modem, and setting up the link using old-fashioned AT codes gets into an area where I could once have said what to do, but my experience is no longer relevant.

Sorry

I just found [this thread](http://ubuntuforums.org/showthread.php?t=1613373) which mentions the PIN. It could be that you'll find some bits of use, even tho' it's a different modem.

---

### Post by ernes on 2012-08-20
Ok, thanks anyway for the attention. I'll keep looking for an answer. Have a nice one.

---

