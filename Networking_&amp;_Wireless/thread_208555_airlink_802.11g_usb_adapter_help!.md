---
title: "airlink 802.11g usb adapter help!"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by holden94122 on 2006-07-03
I just bought the airlink 802.11g usb adapter for my older laptop running ubuntu. After digging for a little bit, I still can't seem to get it to work. 

When I check to see if the computer recognizes the adapter, this is the output I got.

fermat@c-67-161-36-229:~$ lsusb
Bus 001 Device 002: ID 0ace:1215 ZyDAS
Bus 001 Device 003: ID 413c:3200 Dell Computer Corp.
Bus 001 Device 001: ID 0000:0000

So it seems like it's being picked up. When I did a iwconfig this is the output.

root@c-67-161-36-229:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

no wlan0 seems to present when I ran iwconfig wlan0:

root@c-67-161-36-229:~# iwconfig wlan0
wlan0     No such device

When I go look at my network connections, I dont see a wireless connection, only the ethernet connection and the dial up. 

Then I went to System>>Administration>>Windows Wireless Drivers, it says the zd1211u driver is installed, but hardware present. 

So I really don't know where to go from there. If anyone can offer some help, it'd be great. Thanks a lot in advance.

---

