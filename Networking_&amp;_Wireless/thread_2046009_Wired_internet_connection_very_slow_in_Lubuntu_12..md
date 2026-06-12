---
title: "Wired internet connection very slow in Lubuntu 12.04"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by eldudorinio on 2012-08-22
Hi,

I have recently installed Lubuntu 12.04 (dual boot with Windows XP SP3) on my machine and I've been having some issues with my **wired** internet connection. After running a few internet speed tests it seems that in Lubuntu 12.04 I have very low internet speeds. On the other hand in Windows XP the internet works fine.

I first noticed this issue from the very beggining, when downloading updates and programs from both Update Manager and apt-get in terminal. Then I noticed it at various other software downloads.

Find below some information on my system.

Here are my basic system specifications:
```
Processor:	AMD Athlon(tm) 64 Processor 3500+
Memory:	                3016MB (833MB used)
Operating System:	Ubuntu 12.04.1 LTS
OpenGL Renderer:	GeForce GT 630/PCIe/SSE2
Audio Adapter:	        VIA8237 - VIA 8237
Ethernet controller:	Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet (rev 41)
```

Result from lspci -nn | grep -e 0200 -e 0280:
```
00:0e.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IP1000 Family Gigabit Ethernet [13f0:1023] (rev 41)
```

Result from lsb_release -d:
```
Description:	Ubuntu 12.04.1 LTS
```

Result from ping -c3 8.8.8.8:
```
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=49 time=107 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=49 time=106 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=49 time=107 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 106.659/106.983/107.243/0.449 ms
```

*EDIT:*
_What I have already tried:_

1) I have already tried the proposed solution found [here]("http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html"), with no success.

2) I have also tried disabling IPv6 from the Network Connections settings, by selecting my wired connection ->Edit and under IPv6 Settings selected Method:Ignore. No success either.

*End of EDIT*

Can anyone help?

If any additional information is needed for troubleshooting, please let me know.

Thank you,
Yiannis

---

### Post by chili555 on 2012-08-22
Let's have a look at:```
nm-tool
dmesg | grep ipg
```Thanks.

---

### Post by eldudorinio on 2012-08-22
Hi and thank you for the quick response.

Output from nm-tool:
```
NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            Sundance Technology IPG Triple-Speed Ethernet
  State:             connected
  Default:           yes
  HW Address:        00:50:8D:D7:C0:A3

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.10.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.10.254

    DNS:             192.168.10.254

```

Output from dmesg | grep ipg:
```
[    1.101952] ipg: 0000:00:0e.0: IC PLUS IP1000 1000/100/10 based NIC
```

---

### Post by eldudorinio on 2012-08-22
Please note that I have already tried the proposed solution found [here]("http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html"), with no success.

I have also tried disabling IPv6 from the Network Connections settings, by selecting my wired connection ->Edit and under IPv6 Settings selected Method:Ignore.

Thank you,
Yiannis

---

### Post by chili555 on 2012-08-22
Frankly, I don't yet see anything wrong here. We might suspect DNS nameservers but when you ping by number, it's still slow. You are connected at 100 Mb/s although the card seems capable of gigabit speeds; even so, it ought to be faster than this:> 64 bytes from 8.8.8.8: icmp_req=1 ttl=49 time=107 msLet's dig a bit deeper:```
dmesg | grep -e eth0 -e 00:0e
sudo cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20
```Mrs. Chili has requested lunch in the big city; back later!

---

### Post by eldudorinio on 2012-08-22
Here are the results from the commands.

Output from dmesg | grep -e eth0 -e 00:0e:
```
[    0.109026] pci 0000:00:0e.0: [13f0:1023] type 0 class 0x000200
[    0.109041] pci 0000:00:0e.0: reg 10: [io  0xec00-0xecff]
[    0.109050] pci 0000:00:0e.0: reg 14: [mem 0xdfffe000-0xdfffe0ff]
[    0.109085] pci 0000:00:0e.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    0.109109] pci 0000:00:0e.0: supports D1 D2
[    0.109111] pci 0000:00:0e.0: PME# supported from D1 D2 D3hot D3cold
[    0.109115] pci 0000:00:0e.0: PME# disabled
[    0.191006] pci 0000:00:0e.0: BAR 6: assigned [mem 0xd8000000-0xd800ffff pref]
[    1.101948] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.101952] ipg: 0000:00:0e.0: IC PLUS IP1000 1000/100/10 based NIC
[    1.101958] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: PCI: Disallowing DAC for device
[    1.150856] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Ethernet device registered
[   19.803566] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.797910] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
[   22.797917] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control
[   22.797927] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
[   22.797930] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control
[ 1800.513721] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
[ 1800.513727] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control
[ 1921.478648] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
[ 1921.478654] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control

```

Output from sudo cat /var/log/syslog | grep -e etwork -e eth0 | tail -n20:
```
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info>   address 192.168.10.6
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info>   prefix 24 (255.255.255.0)
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: nm_ip4_route_set_prefix: assertion `prefix > 0' failed
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info>   gateway 192.168.10.254
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info>   nameserver '192.168.10.254'
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info>   domain name 'lan'
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 22 11:35:30 yiannis-desktop NetworkManager[949]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> DNS: starting dnsmasq...
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> Activation (eth0) successful, device activated.
Aug 22 11:35:31 yiannis-desktop NetworkManager[949]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Aug 22 11:35:43 yiannis-desktop ntpd[1939]: Listen normally on 3 eth0 192.168.10.6 UDP 123
Aug 22 12:04:21 yiannis-desktop kernel: [ 1800.513721] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
Aug 22 12:04:21 yiannis-desktop kernel: [ 1800.513727] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control
Aug 22 12:06:22 yiannis-desktop kernel: [ 1921.478648] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: Link speed = 100Mbps
Aug 22 12:06:22 yiannis-desktop kernel: [ 1921.478654] Sundance Technology IPG Triple-Speed Ethernet 0000:00:0e.0: eth0: setting full duplex, TX, RX flow control

```

Thanks and Bon Apetit :)

---

### Post by drashed on 2012-08-22
i usually windows seven but after installling ubuntu i cant my broadband connection 
in win = 7
open network and sharing center> set up a new connection > connect to the internet > broadband ( pppoe ) > provide name and password

---

### Post by chili555 on 2012-08-22
> **drashed said:**
> i usually windows seven but after installling ubuntu i cant my broadband connection 
in win = 7
open network and sharing center> set up a new connection > connect to the internet > broadband ( pppoe ) > provide name and passwordPlease start your own new thread. This thread involves wired ethernet, not broadband.

---

### Post by marinara on 2012-08-22
dsl?

---

### Post by mutap on 2012-08-22
Could it be the driver issue?

Had the same problem with Realtek driver for my card, with one version of the driver network is slow, with other is just fine. And in Windows it worked without problems.

---

### Post by eldudorinio on 2012-08-23
> **marinara said:**
> dsl?

Yes my connection is DSL, but how does that make any difference? The connection is fine under Windows on the same machine.

---

### Post by eldudorinio on 2012-08-23
> **mutap said:**
> Could it be the driver issue?

Had the same problem with Realtek driver for my card, with one version of the driver network is slow, with other is just fine. And in Windows it worked without problems.

It could be a driver issue. How can I check that?

---

### Post by chili555 on 2012-08-23
I suspect it is a driver issue. Your device is pretty rare and, I suspect, the driver not well maintained. All of the information I can find about it on Google is quite old. Here is a snip from *modinfo*:> chili@LAPTOP60:~$ modinfo ipg 
filename:       /lib/modules/3.4.0-030400-generic-pae/kernel/drivers/net/ethernet/icplus/ipg.ko
license:        GPL
description:    IC Plus IP1000 Gigabit Ethernet Adapter Linux Driver
author:         [COLOR="Red"]IC Plus Corp. 2003[/COLOR]
I can't find any driver alternative to install or compile.  

You might try an MTU more approriate to DSL; I use 1492. [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)

I'd probably give this device a nice funeral and welcome a new ethernet card to the party.

"...or elduderino if you're not into the whole brevity thing."

---

### Post by eldudorinio on 2012-08-23
> **chili555 said:**
> You might try an MTU more approriate to DSL; I use 1492. [http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html](http://www.prash-babu.com/2009/06/how-to-change-mtu-in-ubuntu-using-gui.html)


I tried changing the MTU to 1492, 1454, 1452 and 1460. The only one that worked was **1492**, however it wasn't a complete success.

After changing the MTU to 1492 I managed to do a few updates with Update Manager (that I could not do before) and also managed to download TeamViewer (also couldn't do it before). 

The downside was that:
[LIST=1]
[*]I still do not get the download speed the connection can offer
[*]Dropbox application cannot establish secure connection
[*]Could not connect to all websites (including this one). I had to change the MTU to automatic in order to connect to the forum.
[/LIST]

I have found online some other suggestions for changing the MTU. I will give it a try and let you know.

---

### Post by eldudorinio on 2012-08-25
Hi,

I have tried a couple more MTU values with no success.

It seems I will have to settle with this network performance until I manage to get a new network adapter.

Thanks for all the help :)

---

### Post by eldudorinio on 2012-09-10
> **chili555 said:**
> I'd probably give this device a nice funeral and welcome a new ethernet card to the party.

I have just installed a new PCI Gigabit network adapter and everything works great!

Thanks again :)

---

### Post by chili555 on 2012-09-10
Awesome! Glad it's working.

---

