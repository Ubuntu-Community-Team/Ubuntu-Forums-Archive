---
title: "holding on to connectivity why do i lose it?"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Neill_R on 2010-08-10
this is a mobile broadband issue (ubuntu 10.04 with Option ICON 225 usb dongle connecting to Orange UK network) 

while NM tell me I am connected the computer loose connectivity to the internet. 

however if this recursive script is running i do not 

#!/bin/bash
echo ""
echo ""
echo "ping dns 2 times once per half minute"
ping -c 2 -i 20 193.xx.xx.100
echo " ============================================================ "
/home/xxxxx/Desktop/pingdns.sh

CAN ANYONE  give an explanation please?

also I see from nm 0.8.0.998 that my primary dns is my own IP address given out by Orange 
secondary is their dns server 193.xx.xx.100  why is this and is it correct ? I do not wish to run a dns server at all.

cheers

---

