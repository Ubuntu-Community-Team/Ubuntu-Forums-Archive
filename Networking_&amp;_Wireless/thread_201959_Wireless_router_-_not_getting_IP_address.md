---
title: "Wireless router - not getting IP address"
date: 2006-06-22
forum: Networking &amp; Wireless
---

### Post by adagio on 2006-06-22
Dell C600 laptop, Dapper, Belkin wireless router + ADSL modem.

```
eth0      Link encap:Ethernet  HWaddr 00:01:03:86:7B:A1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:19426 (18.9 KiB)
          Interrupt:11 Base address:0x6c00
```

"No DHCPOFFERS received" error from '$ dhclient3 eth0'.

Am paying for an ADSL line so could do to get this up and running as soon as possible.

Thx in advance,


GSO
[http://www.gsowww.uklinux.net/pub](http://www.gsowww.uklinux.net/pub)

---

### Post by malacandra on 2006-06-22
Start with the obvious...

Have you soft reset the router and rebooted the computer?

Then, how are you trying to get an IP address? using "dhclient" in a shell, using NetworkManager? GNOME's Network applet?

---

### Post by adagio on 2006-06-22
Thanks for taking the time to reply, the solution was in the DSL HOWTO[1], namely:
```
3.2.6. Modem/Router Configuration

....

If you need to access the router directly, you will need to know the manufacturer's
default setting for its IP address. See the owner's manual, or ask your provider.
You will then have to set your NIC's interface to the same network as the router.
For instance, if the router has an IP of 10.0.0.1, set your interface's address to
10.0.0.2 (typically eth0), and netmask to 255.0.0.0.

 # ifconfig eth0 10.0.0.2 up netmask 255.0.0.0
 # route add -net 10.0.0.0
 $ ping 10.0.0.1

If everything is in working order, the router should respond to pings. 
```
The bug was caused by my laptop not having an IP on the same network.

That though is using a cable to the router, wireless to do next.


[1] [http://www.tldp.org/HOWTO/DSL-HOWTO/index.html](http://www.tldp.org/HOWTO/DSL-HOWTO/index.html)

---

### Post by adagio on 2006-06-22
Wireless works fine also via the System / Admin. / Networking menu.

The problem was I think that I needed to be able to configure the router and modem via a web page served by the router box itself and whilst connected for security reasons to the laptop by an ethernet cable.

To do that the laptop ethernet port had to be configured with an IP 'on the same network' as the router box (i.e. 192.168.2.x).

---

### Post by adagio on 2006-06-24
Last problem of getting (WEP) encryption to work was fixed after reading this thread:

[http://www.ubuntuforums.org/showthread.php?t=199163](http://www.ubuntuforums.org/showthread.php?t=199163)

---

