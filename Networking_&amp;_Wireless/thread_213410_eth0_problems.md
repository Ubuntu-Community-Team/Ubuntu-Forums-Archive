---
title: "eth0 problems"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by leto82 on 2006-07-11
hi, i have an ethernet card realtek 8139.
When i activate it doesn't retrieve the DHCP ip from the DHCP server.
I tried to configure dhclient unsuccesfully.

thanks

---

### Post by Paerez on 2006-07-11
can you run the following code from a terminal and paste the output (everything on the terminal please)?
```
# sudo ifconfig eth0 down
# sudo ifconfig eth0 up
# sudo ifconfig eth0
# sudo dhclient eth0
```

---

### Post by simonfishley on 2006-07-12
Hi there!

I am experiencing the same problem as the original poster but as he did not post a preply I thought I might respond with my output and see if anyone can shed some light on the matter.

#ifconfig eth0 down
#ifconfig eth0 up
SIOCSIFFLAGS: Device or resource busy
#ifconfig eth0
eth0   Link encap: Ethernet HWaddr 00:11:95:65:f3:fc
       inet addre:192.168.200.190 Bcast:192.168.200.255 Mask: 255.255.255.0
       BROADCAT MULTICAST  MTU:1500 Metric:1
       RX - all 0 (this is me saving typing..)
       TX - all 0
       collisions:0
       RX Bytes - all 0
       Base address:0x400
#dhclient eth0
Internet Systems Consortium DHCP Client V3.0.3
Copyright blah blah

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on Device LPF/eth0/00/00:11:95:65:f3:fc
Sending on   LPF/eth0/00/00:11:95:65:f3:fc
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
#

This is a fresh install of 6.06 server - I have tried 4 different LAN cards - 3Com, Dlink, Realtek, Intel as well as tried different PCI slots to rule out hardware troubles.  The LAN cable in question works perfectly on my 6.06 laptop install assigning me an IP immediately. Autoconfig during setup tells me my DHCP server is slow or not responding.
This machine is supposed to be a squid proxy so i will need to add a second  eth card at some point but right now I just want to get it onto my network!

Any help will be greatly appreciated.

Thanks
Simon

---

### Post by MrHorus on 2006-07-12
> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down

As it states, the network is down.

If the interface is up then this is likely to be some sort of hardware or cabling problem, perhaps a lose wire or some other sort of fault.

---

### Post by simonfishley on 2006-07-12
Hi MrHorus

I just changed the flylead to be certain but as I said another dapper machine works perfectly on the same link...

Thanks anyway!
Si

---

### Post by jimp180 on 2006-07-12
What do you have in your /etc/network/interfaces 

This is not a fix but since you have several cards why not throw another 1 in there and set up eth1 and see if you can connect with it, then maybe you can work out the differences to find out whats going on with eth0.

---

### Post by Paerez on 2006-07-12
> If you're frustrated by the fact that you can't seem to get your network card to work in Linux, because it's failing with the error: SIOCSIFFLAGS: Device or resource busy, I may have a fix for you. Simply changing the Plug&Play OS setting inside of your BIOS to no. I was receiving the above error on an SiS900 network card built into the motherboard until I turned off the Plug&Play OS setting and then everything worked perfectly.

As taken from:
[http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=562&mode=thread&order=0&thold=0](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=562&mode=thread&order=0&thold=0)

hope that does it!

---

### Post by mips on 2006-07-12
Do a search here for '8139' as there are known issues with that chipset.

---

