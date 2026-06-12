---
title: "wlan0 to wlan1 as AP"
date: 2012-04-19
forum: Networking &amp; Wireless
---

### Post by jojojoris on 2012-04-19
Hello,

I am trying to create an educational robot (running ubuntu-server). It has to communicate with a user trough a wifi connections. 

It also has to pass internet trough but with some filtering. (like not allowing facebook while learning)

I got 2 wifi adapters. One for receiving a existing wifi connection and one configured as an AP. 

Receiving internet is not a problem. 

Getting the AP to work is another story.
I tried a lot of tutorials but none of them seem to work. 
almost all of them were about hostapd and dhcp3-server

One of the most prommising tutorials was:
[http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/](http://exain.wordpress.com/2011/03/31/making-a-wifi-hotspot-access-point-using-linux-wifi-lan-cardusb-adapter/)

I was able to detect the AP's ssid but i could not connect to it.

The adapters i use, have a RALINK 5370 Chipset and i use the rt2800usb module.

Hope someone can point me in the right direction.

---

### Post by Tesla01 on 2012-04-19
Hi,
 
I am doing nearly exactly the same at the moment.
Task is creating an Access-Point for smartphones and get the Internet from a public wlan which is so far away that I have to use a yagi-antenna.
 
I have done this with ubuntu 11.10, a Samsung Netbook NC-10 and an ALFA AWUS036NHR USB Adapter with yagi.
 
The AP ist the internal wlan0 of the Netbook (ath5k).
 
I used also the documentation you mentioned.
 
What I discoverd so far is, that hostapd runs good with some cards, with other cards not and with some cards it seem to run but you cannot connect (but the clients sees an AP).
For Example if I try to use the AWUS036NHR as the Accesspoint, nobody can connect to the wlan.
 
I think its more a problem of the driver and not the hardware, so I will try again with ubuntu 12 if the final is out in the next days.

---

