---
title: "eth0 will not come online when connected to Cisco 1G GLC-T with Ubuntu only"
date: 2012-05-23
forum: Networking &amp; Wireless
---

### Post by sf_basilix on 2012-05-23
I am running 64 bit Ubuntu 12.04 on a Dell E6520. I have been able to get networking to work on every switch so far, except when I plug into a Cisco Nexus 5548 that has a 1G, GLC-T; it will not light up. (I've tried a regular ethernet and cross-over ethernet) The strange thing is that I've tried this on two other identical laptops (same E6520 model) running Windows 7 and it lights up fine.

I have tried ifup eth0, which does not work. I've tried assigning IP addresses manually to eth0 and forcing it up, and it will not come online. The following is the output from a show interface ethernet on the 5548 when I had my laptop plugged in:


```
# show interface ethernet 1/7
Ethernet1/7 is down (Link not connected)
  Hardware: 1000/10000 Ethernet, address: 547f.ee94.497c (bia 547f.ee94.492e)
  Internet Address is 50.50.50.1/24
  MTU 1500 bytes, BW 1000000 Kbit, DLY 10 usec
  reliability 255/255, txload 1/255, rxload 1/255
  Encapsulation ARPA
  full-duplex, 1000 Mb/s, media type is 10G
  Beacon is turned off
  Input flow-control is off, output flow-control is off
  Rate mode is dedicated
  Switchport monitor is off 
  EtherType is 0x8100 
  Last link flapped never
  Last clearing of "show interface" counters 00:58:34
  30 seconds input rate 0 bits/sec, 0 packets/sec
  30 seconds output rate 0 bits/sec, 0 packets/sec
  Load-Interval #2: 5 minute (300 seconds)
    input rate 0 bps, 0 pps; output rate 0 bps, 0 pps
  RX
    0 unicast packets  0 multicast packets  0 broadcast packets
    0 input packets  0 bytes
    0 jumbo packets  0 storm suppression bytes
    0 runts  0 giants  0 CRC  0 no buffer
    0 input error  0 short frame  0 overrun   0 underrun  0 ignored
    0 watchdog  0 bad etype drop  0 bad proto drop  0 if down drop
    0 input with dribble  0 input discard
    0 Rx pause
  TX
    0 unicast packets  0 multicast packets  0 broadcast packets
    0 output packets  0 bytes
    0 jumbo packets
    0 output errors  0 collision  0 deferred  0 late collision
    0 lost carrier  0 no carrier  0 babble 0 output discard
    0 Tx pause
  0 interface resets


interface Ethernet1/7
  no switchport
  speed 1000
  duplex full
  ip address 50.50.50.1/24

```


I'm thinking that because this is working on the same laptop with windows 7, it has to be an ubuntu setting. Is there anything I could do to force this adapter to come online? There is no DHCP server on this new network yet, so I would have to manually configure the IP.

Any thoughts?

Thanks in advance!

---

### Post by sf_basilix on 2012-05-23
So a bit more info regarding this situation. I'm thinking this is a 12.04 bug. I had pulled out my other Dell E6510 laptop running 10.04 (64 bit) and the link light came up right away. I'm beginning to think this is a 12.04 issue, but why would this only be affected with a GLC-T and not any other adapter?

---

