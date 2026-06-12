---
title: "RTL8139D in Karmic 9.10"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by m3rc on 2010-02-14
I love Ubuntu but so far a lot of the network devices I've tried have been nothing but problems. I'm adding a second NIC to my Karmic 9.10 desktop. It's been 2 weeks and I've tried 2 other cards already with no luck. 

It's especially frustrating because I thought I did my homework on this one and read that it's plug and play on 9.10 here: [https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek](https://wiki.ubuntu.com/HardwareSupportComponentsWiredNetworkCardsRealtek). 

This is the link to where I bought it: [http://www.geeks.com/details.asp?invtid=CX-8139DII&cpc=SCH](http://www.geeks.com/details.asp?invtid=CX-8139DII&cpc=SCH)

```

$lspci
01:06.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)

``````

$uname -r
2.6.31-19-generic-pae

``````

$cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.6
          network 192.168.1.0
          netmask 255.255.255.0
          broadcast 192.168.1.255
          gateway 192.168.1.1

auto eth1
iface eth1 inet dhcp

```I looked around the forums and tried a few things like modprobe 8139too. The card still is not working. Was that the right thing to do with this particular card? 

Thanks in advance for any suggestions!

---

### Post by cariboo on 2010-02-14
What's the output of:

```
lshw -C network
```

---

### Post by m3rc on 2010-02-14
```

$lshw -C network
*-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
       vendor: Hangzhou Silan Microelectronics Co., Ltd.
       physical id: 6
       bus info: pci@0000:01:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=20 maxlatency=40 mingnt=20
       resources: memory:fd7ff000-fd7ff0ff ioport:bc00(size=256) memory:fde00000-fde1ffff(prefetchable)

```

---

### Post by m3rc on 2010-02-15
bump

---

### Post by m3rc on 2010-02-16
I read [here]("http://vishalmanohar.wordpress.com/2007/07/07/configuring-hangzhou-silan-on-ubuntu-linux/") and a few other places that the card I have is a "fake" Realtek card. That seems very ironic to me but I'll roll with it if it'll help me fix this thing. Apparently I need the Silan driver (sc92031), not the Realtek driver.

I did
```

$modprobe sc92031
$sudo /etc/init.d/networking restart

```

I have Wireshark running on my laptop listening to the traffic from eth1 on this box. There were no packets captured after I ran the commands above. 

I'll try ndiswrapper and post how that one worked. In the meantime, I'd really appreciate any suggestions, even if they're completely wrong, off-base, whatever; I'm seriously willing to try anything at this point. It's been over 2 weeks and a very frustrating experience getting this card working.

---

### Post by chili555 on 2010-02-16
It will help us to see the PCI ID for the device. Please post:```
lspci -nn
```After you modprobed sc92031, did ifconfig show a new interface had been created?

Has Network Manager been removed? It does not work and play well with a populated */etc/network/interfaces*.

---

### Post by m3rc on 2010-02-16
Thanks Chili555. 

> 
After you modprobed sc92031, did ifconfig show a new interface had been created?


Yes it did. It did that before, though. My problem is not getting Ubuntu to recognize the interface but to actually send packets over it. I'm still not picking up any on Wireshark.

```

$lspci -nn
01:05.0 Ethernet controller [0200]: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor [1904:8139] (rev 01)

$ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:11:1b:65:e1  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:11ff:fe1b:65e1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:74166 errors:0 dropped:0 overruns:0 frame:0
          TX packets:51771 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:81995061 (81.9 MB)  TX bytes:7477527 (7.4 MB)
          Interrupt:27 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:e0:a0:00:c6:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:fd7ff000-fd7ff0ff 

eth1:avahi Link encap:Ethernet  HWaddr 00:e0:a0:00:c6:06  
          inet addr:169.254.6.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:fd7ff000-fd7ff0ff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:483 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:46056 (46.0 KB)  TX bytes:46056 (46.0 KB)

```

I'm using wicd instead of Network Manager, but it kept asking for my password on startup so I thought that it might be configured wrong; I killed it and have just been using the terminal "dhclient" command to get my internet connected. 

I tried ndiswrapper with no success but I may have had the wrong driver. RTL8139D is not listed in the [ndiswrapper drivers list]("http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:WORKS&from=Intellinet+521710") so I got it off [Realtek's website]("http://www.realtek.com.tw/DOWNLOADS/"). It seems like this is a common card so has anyone had success using ndiswrapper and if so what drivers did you use?

In the meantime, I'll test a few other drivers with ndiswrapper.

---

### Post by chili555 on 2010-02-17
> I may have had the wrong driverThe module sc92031 *thinks* it's the right driver:> $ modinfo sc92031 | grep 8139
alias:          pci:v0000[COLOR="Blue"]1904[/COLOR]d0000[COLOR="Blue"]8139[/COLOR]sv*sd*bc*sc*i*
> ethernet adaptor [[COLOR="Blue"]1904:8139[/COLOR]] (rev 01)
Whether the driver is *effective* in operating the device is another question. Does dmesg or /var/log messages have anything interesting to say after dhclient runs and, I assume, times out?

---

### Post by m3rc on 2010-02-17
Thanks again chili555. That modinfo command is really handy and I've been looking for something like that to help clarify things. I rmmodded ndiswrapper, modprobed sc92031 again, then ran dhclient on eth1, which timed out.

(Disclaimer: only the relevant stuff has been included from the following commands)

```

$dmesg
[36247.036205] eth1: link down
[36247.036723] ADDRCONF(NETDEV_UP): eth1: link is not ready

``````

$tail var/log/messages
Feb 17 17:45:32 desktop kernel: [36247.036198] __ratelimit: 6 callbacks suppressed
Feb 17 17:45:32 desktop kernel: [36247.036205] eth1: link down
Feb 17 17:45:32 desktop kernel: [36247.036723] ADDRCONF(NETDEV_UP): eth1: link is not ready

```ifconfig is still not showing any transmitted packets, and Wireshark hasn't picked up any on my laptop:

```

$ifconfig
eth1      Link encap:Ethernet  HWaddr 00:e0:a0:00:c6:06  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)**
          Interrupt:16 Memory:fd7ff000-fd7ff0ff 

eth1:avahi Link encap:Ethernet  HWaddr 00:e0:a0:00:c6:06  
          inet addr:169.254.6.87  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:16 Memory:fd7ff000-fd7ff0ff 

```

---

### Post by m3rc on 2010-02-28
I commented out all the config settings in /etc/network/interfaces and tried using Network Manager to manage them. Still nothing. I hate to give up on this for me and anyone in the future who is having problems with this card, but I feel like I've tried everything I know of to get it working and it's all been unsuccessful.

---

### Post by m3rc on 2010-02-28
Here's something interesting though:
when I connect the card to the router, DHCP works fine and I can get online. When I connect to my laptop, there are no packets sent. When I connect the desktop's built-in card to my laptop, theres a ton of packets sent.

So this card works in some cases already, but my intention is to set up a DMZ between the router and modem in which case I need to actually see packets on my laptop to make sure the connection's working.

Do you have any suggestions or even just an explanation for why this card would work with a router but not with a DHCP server on my laptop?

---

