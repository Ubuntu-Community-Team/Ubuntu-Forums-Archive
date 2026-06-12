---
title: "Networking in a hotel - DHCP cannot grab IP. Win XP works fine"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by 1script on 2009-02-26
I have been having this problem every time (well, three so far) I check into a hotel that provides Internet, free or paid, with my dual boot XP Home/Ubuntu 8.10 Acer Aspire One laptop. Since I haven't mastered its WiFi yet, I'm limited to wired connectivity only on Linux, so everything below is about its eth0. 

So, basically, title sums it all up: Ubuntu cannot get its IP address (and other info) assigned by a hotel's DHCP server. Everything works fine at home (also DHCP, simplest out-of-a-box setup). Everything works fine in Win XP at the hotel (including Wireless, how embarrassing :oops: ) 

What on Earth can be causing any difference in the dhcp client operation / dhcp server response and what's so special about hotels? I have been watching the dhcp process in the messages and it looks fine to me (except it fails to produce results). Broadcasts on  port 67, waits for response, does not get one and times out.
I cannot watch the process play out in Windows but, apparently, it succeeds and DOES get the response since everything works.

Can it be that Ubuntu's *"Internet Systems Consortium DHCP Client V3.1.1"* behaves differently from Windows' DHCP client and leaves a trace of some kind that hotel's DHCP server does not like for some sick reason?

What troubleshooting steps would the community suggest to get this over with?

P.S. I have not had a chance to try this relatively new laptop in a different environment so hotels are the only sample of a LAN outside my home that I have.

---

### Post by 1script on 2009-02-26
Just to add: looked in the config files I know of that may have something to do with DHCP:

/etc/network/interfaces - file empty
/etc/dhcp3/dhclient.conf - requesting all usual stuff, not requiring any. Increased timeout to 120 sec - did not change anything. Still cannot get an IP.

Any ideas anyone?

---

### Post by kevdog on 2009-02-27
Try configuring from command line if you haven't done it!

---

### Post by YWELLC on 2009-02-27
You say there is nothing in /etc/network/interfaces?

Open up the file in an editor:

```
sudo gedit /etc/network/interfaces
```

And add the following lines to set eth0 to auto and dhcp:

```
auto eth0
iface eth0 inet dhcp
```

Then restart networking with:

```
sudo /etc/init.d/networking restart
```

and try to connect...

---

### Post by superprash2003 on 2009-02-27
post output of **ifconfig** and **iwconfig** from the terminal .. is your wifi set to roaming mode?

---

### Post by 1script on 2009-02-27
Sorry guys, unintentionally gave a wrong info: 
/etc/network/interfaces was not an empty file it had 
```
auto lo
iface lo inet loopback
```

in it which I changed to 
```
auto eth0
iface eth0 inet dhcp
```

Unfortunately, made no difference. Here is the output of those two other commands as requested:

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1e:68:de:94:38  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:218103795 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:219 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)


```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.


```

and here is what I get on *sudo /etc/init.d/networking restart*
```
 * Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:68:de:94:38
Sending on   LPF/eth0/00:1e:68:de:94:38
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

Hope it helps to pinpoint the issue.
Thanks

---

### Post by YWELLC on 2009-02-27
Perhaps there is a problem with your ethernet card and dhcp under Ubuntu? Do you know what card it is? You can find out with this:

```
lspci | grep Ethernet
```

You can also view the startup logs for this device and look for errors with:

```
dmesg | grep -i eth0
```

On your home network do you use this Ethernet card with Ubuntu and dhcp?  

Here is a long shot you can try from the command line:

```
sudo ip addr flush dev eth0
sudo ifdown eth0
sudo ifup eth0
sudo /sbin/dhclient eth0
```

---

### Post by 1script on 2009-02-28
Thanks for your input!
Still no go. Output of the commands you posted is below. And yes, both Ubuntu and Win XP home on this Acer One laptop work fine at home on the LAN with DHCP. It's only outside the home that I have a problem with getting dhcp-ed IP address from routers. Win XP works fine (using it now to post)

So here goes:
*lspci | grep Ethernet*
```
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev ff)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

*dmesg | grep -i eth0*
```
[    4.841685] eth0: RTL8169 at 0xf8852000, 00:1e:68:de:94:38, XID 24a00000 IRQ 219
[   70.372102] r8169: eth0: link up
[  214.808038] eth0: no IPv6 routers present
[  485.000124] NETDEV WATCHDOG: eth0 (r8169): transmit timed out
[  485.816151] r8169: eth0: link up

```

Here is what I get on *sudo ifdown eth0*

```
sudo ifdown eth0
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 4366
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:68:de:94:38
Sending on   LPF/eth0/00:1e:68:de:94:38
Sending on   Socket/fallback


```
and here is *sudo ifup eth0*
```
sudo ifup eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:1e:68:de:94:38
Sending on   LPF/eth0/00:1e:68:de:94:38
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


```

*sudo /sbin/dhclient eth0* does pretty much the same as *sudo ifup eth0* i.e. stalls at trying to get the IP through *DHCPDISCOVEER on eth0 ...*

Still looking for ideas.

Thanks!

---

### Post by anjames on 2010-11-09
This issue remains in Lucid. I have the following wifi card:

0c:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

Using the same machine, I can connect to wifi at my university using WPA, and I can connect to wifi at the Hyatt in Chicago where the 52nd APS-DPP conference is, but when I try to connect to the free wifi at Hotel 71 where I am staying I get the same error as above about no DHCP responses, even though I can connect to the access point. Using an ipod touch I can connect to the same access point, browse while sitting in the same chair, and both my laptop and ipod report strong signal.

The network-manager finds the access point on my laptop, and can even connect to it, but the DHCP negotiation fails for some reason.

I'll report back later from wireshark what is going on between my ipod and the router which is different than my laptop and the router... and maybe we'll work toward sorting this out?

---

