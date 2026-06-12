---
title: "Odd issues with wireless"
date: 2010-04-06
forum: Networking &amp; Wireless
---

### Post by eldonkr on 2010-04-06
Ever since I've installed 9.10 on this laptop I've had issues with the wireless. At first it wasn't picking up my own router in the house, but I could see all the other wireless signals from the neighbors.

Then a week later I was over at a friends house trying to find a wireless signal to tap into while I was there, and every unsecured signal that I'd been able to get on before wouldn't work. They were still unencrypted, I just couldn't get the laptop to connect to them.

The only time I can get online with this laptop is when I'm hardlined directly into a modem or router, which is kind of counter-intuitive seeing as I've got a completely good wireless adapter that I'd like to use with it.

Any suggestions?

---

### Post by Iowan on 2010-04-06
Wireless problems don't seem rare with Karmic...Post results of **sudo lshw -C network** - that should provide some indication of what the current configuration is - or if Ubuntu doesn't recognize the interface at all.

---

### Post by eldonkr on 2010-04-07
```

eldonkr@ekr-mobile:~$ sudo lshw -C network
[sudo] password for eldonkr: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 42
       serial: 00:00:39:ba:e0:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.102 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:11 memory:ff9ff000-ff9fffff ioport:df40(size=64)
eldonkr@ekr-mobile:~$ 

```

I've come to the conclusion that my internet stick isn't being recognized, and luckily for me, NETGEAR doesn't do support for Linux at all. I'm doing some reading on NDISWRAPPER. Any other support you guys have to offer is a big help, though. Thanks.

---

### Post by eldonkr on 2010-04-07
Ok, this is completely awesome. This post is powered by (for the first time since I installed Karmic) wireless internet!

I guess you could technically flag this thread as 'Solved', but I had another question.

This laptop also has a built in wireless adapter that has never worked. I'm just not sure if that is because it's broken, or if it's not compatible.

How can I tell?

---

### Post by kidxcore on 2010-04-07
what did you do?

---

### Post by eldonkr on 2010-04-07
> **kidxcore said:**
> what did you do?

I located the Windows driver for my internet stick and installed it using Wine. Then I installed ndiswrapper and ndisgtk. To the best of my knowledge I think that they can both be located in the Ubuntu Software Center. If not, just Google them and you'll find what you're looking for. After this, I used ndisgtk on the installed windows driver and the program used it's 'buntu Magic to power my laptop with wireless internet juice.

And apparently I did everything correctly, because when I powered up the laptop just now I was still able to pick up wireless.

Not that it's really important, but, does anyone have any idea how I can tell if the built in wireless adapter on my laptop is incompatible with Karmic, or just broken?

---

