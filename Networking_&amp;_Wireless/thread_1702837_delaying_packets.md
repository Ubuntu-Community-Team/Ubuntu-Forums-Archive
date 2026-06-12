---
title: "delaying packets"
date: 2011-03-08
forum: Networking &amp; Wireless
---

### Post by sudarshan.bit on 2011-03-08
hi, can any1 let me know how to delay packets before forwarding them on a link. Is there any tool to do so?? thanks in advance

---

### Post by outlaw45k on 2011-07-06
/bump
i want to know this

---

### Post by Dangertux on 2011-07-06
Yes it is possible. Through the use of various traffic shaping and packet metering processes 

Breaking down the process fully would be very detailed so the key points to start researching would be. 

Traffic shaping
QoS
Packet metering


Keep in mind these techniques all involve limiting bandwidth to an interface OR prioritizing traffic based on type (protocol,port, source,destination,etc). If done improperly they can make your network really wonky. 

For a very simplified program in ubuntu check out wondershaper.

---

