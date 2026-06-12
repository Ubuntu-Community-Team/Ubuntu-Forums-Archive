---
title: "IPv6 won't work with AVR Raven"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by dirtyheizer on 2010-12-08
Hey,

like another user ([http://ubuntuforums.org/showthread.php?t=1622119&highlight=6lowpan](http://ubuntuforums.org/showthread.php?t=1622119&highlight=6lowpan)) i got a similar prob with my hw/sw.

I tried that Tutorial([http://www.sics.se/~adam/contiki/docs-uipv6/a01107.html]("http://www.sics.se/%7Eadam/contiki/docs-uipv6/a01107.html")),
install of forwarding was done fine; radvd started without any messages...

Hw Config:

2 AVR Raven with LCD
1 AVR RZUSBStick 
--> each with 6LoPWAN-firmware form Contiki 2.5
1 PC with RZusbstick and eth0 Gbit interface

Sw Config:

Ubuntu 32bit @virtualbox with guest install
-> i installed radvd for routing 

*no DHCPv6 routing is running*
*no IPv6 routing is there* (the tut says its not required)
*we got an proxy server here*
*and i work in an domain with an Windows Server*

see my config here in that screeny: [http://www6.pic-upload.de/08.12.10/n7rti6d9b7sw.jpg](http://www6.pic-upload.de/08.12.10/n7rti6d9b7sw.jpg)

I am not able to ping my Raven and not able to ping the RZUSBStick from the Raven's side..

Anyone has a hint for me?

Kind regards,

dirtyheizer

edit: thanks 4 support! solution was to restart the process of radvd, thats all, now its workin' ^^

---

