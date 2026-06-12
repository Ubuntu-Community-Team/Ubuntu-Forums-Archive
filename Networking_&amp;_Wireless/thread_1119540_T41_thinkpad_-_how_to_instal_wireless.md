---
title: "T41 thinkpad - how to instal wireless ?"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by krasnapolski on 2009-04-08
Hi,

I'm pretty new to Linux so please bear with me. I've gotten most of the stuff to work, but Wlan is nogo. I can't seem to get it to work.

Here's info

```
  *-network               
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:11:25:2e:da:8b
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.20-k3-NAPI duplex=full firmware=N/A ip=192.168.0.5 latency=64 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:d9:20:a2:c7:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```


So how do i take it from here ?

---

### Post by krasnapolski on 2009-04-09
Update:

I took this machine to another location, booted up - voilá wlan works. I have no clue how it didn't even recognize the card in device manager before and now all the sudden everything is hunky dory.

Not to flame here but i am quite perplexed that something like this happened. I'm used to sacrificing chickens for my windows desktop.

---

### Post by JackDeth on 2009-06-28
I have been trying for weeks to get Ubuntu to recognize the wireless in this T41 I just acquired.

I am stumped.

What version of the kernel are you using? What version of Ubuntu? What specific wireless tools do you have running?

Any help you could provide would be appreciated.

---

