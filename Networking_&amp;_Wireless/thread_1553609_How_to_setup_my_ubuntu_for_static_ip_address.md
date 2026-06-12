---
title: "How to setup my ubuntu for static ip address"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by polardude1983 on 2010-08-15
Ok so I am trying to access my ubuntu 10.4 pc from my iphone. I have mocha vnc lite installed on my iphone and I got this in my startup applications

x11vnc -forever -usepw -httpdir /usr/share/vnc-java/ -httpport 5800

It only got connected like once, but haven't been able to connect to my pc again. I'm guessing because i need to have a static ip address, My computer is just connected via ethernet to the modem.

This is in my /etc/network/interfaces file

```

auto lo
iface lo inet loopback

```

```


christoph@christoph-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:92:be:fd:0c  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:92ff:febe:fd0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2188115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3879625 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1294666451 (1.2 GB)  TX bytes:759529032 (759.5 MB)
          Interrupt:30 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1829008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1829008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:319524073 (319.5 MB)  TX bytes:319524073 (319.5 MB)

```

---

### Post by Iowan on 2010-08-15
A few options:
You can configure the DHCP server (router?) to configure a "static lease" - essentially a static address.

Network Manager will let you manually configure an address - just be sure the address is in the same subnet, but outside the DHCP server address range.

You can configure a manual address in */etc/network/interfaces*. As Network Manager evolves, it gets more aggressive and *can* conflict with */etc/network/interfaces*. There are ways to fix it, though...

---

### Post by mhgsys on 2010-08-15
The "gui" way.

Click System > Preferences > Network Connections


Go to Wired/Wireless etc "auto eth0 / auto wlan0" click edit > IPv4 Settings > method > manual: and fill in a ip adres
f.e 192.168.1.10 > netmask=255.255.255.0
Gateway -your gateway- / routeradress
f.e; 192.168.1.1

Dns servers will be found in the router settings.
use a , to divide the primary and secondary dns

---

### Post by polardude1983 on 2010-08-16
> **mhgsys said:**
> The "gui" way.

Click System > Preferences > Network Connections


Go to Wired/Wireless etc "auto eth0 / auto wlan0" click edit > IPv4 Settings > method > manual: and fill in a ip adres
f.e 192.168.1.10 > netmask=255.255.255.0
Gateway -your gateway- / routeradress
f.e; 192.168.1.1

Dns servers will be found in the router settings.
use a , to divide the primary and secondary dns

I did this but now i can't connect to the net. what else do i need to do?

---

### Post by polardude1983 on 2010-08-16
I just want my internet back now

---

### Post by polardude1983 on 2010-08-16
> **Iowan said:**
> A few options:
You can configure the DHCP server (router?) to configure a "static lease" - essentially a static address.

Network Manager will let you manually configure an address - just be sure the address is in the same subnet, but outside the DHCP server address range.

You can configure a manual address in */etc/network/interfaces*. As Network Manager evolves, it gets more aggressive and *can* conflict with */etc/network/interfaces*. There are ways to fix it, though...

Yeah that went over my head :P

---

### Post by polardude1983 on 2010-08-16
My computer has been without internet for 2 hours. i can't take it!

---

### Post by polardude1983 on 2010-08-16
I've got like 20 tabs open on trying to configure a static ip and doing what each one says change this or change that and this and that. and still no internet.

And when i switch back to DHCP i dont get internet again. why? argghg

---

### Post by dineshs on 2010-08-16
While configuring NM You should [COLOR="RoyalBlue"]hit enter[/COLOR] after giving IP mask and gateway.Then give DNS and apply.

---

### Post by polardude1983 on 2010-08-16
I entered random numbers in the ip address. like oh 192.168.1.197 saved it restarted my pc and no internet

---

### Post by mhgsys on 2010-08-16
> **polardude1983 said:**
> My computer has been without internet for 2 hours. i can't take it!

Well; You could always set it back to auto again..

I guess you overlooked the fact your suppose to enter the dns servers manually.

You can find your correct dns settings in your router.
logging on to your router, 

f.e my router = 192.168.1.1.. and my dns settings are located under WAN ETHoA 2, in my advanced settings under system statistics.
But this will variate, depending on what router you have.

---

### Post by polardude1983 on 2010-08-16
DNS it says 0.0.0.0 for all 4

---

### Post by polardude1983 on 2010-08-16
i set it back to auto but no internet. :(

---

### Post by polardude1983 on 2010-08-16
OK got it back guess. i will never be able to get my iphone connected to ubuntu. cause i tried what every blog said and it messed up my pc :(

---

### Post by mhgsys on 2010-08-16
> **polardude1983 said:**
> DNS it says 0.0.0.0 for all 4

?
4?
I was talking primary and secondary dns.
 
Anyway; When setting back to auto in the ipv4-settings tab > method > automatic (DHCP) leave the dns field empty if you want it to be auto.

---

