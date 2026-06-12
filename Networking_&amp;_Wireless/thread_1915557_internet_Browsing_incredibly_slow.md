---
title: "internet Browsing incredibly slow"
date: 2012-01-26
forum: Networking &amp; Wireless
---

### Post by robtoutant on 2012-01-26
I am not an expert in ubuntu or linux ... however I have set up over 20 different virtualbox installs of linux over the last couple of months and am very impressed with ubuntu. The speed is fantastic on the VB.

I installed for a client ubuntu 11.04 and it ran so fast i decided to use that as my main operating system and run windows XP as a VM.

I first installed ubuntu version 10 LTS  and noticed internet browsing was painfully slow 
internet pages timing out -- or soooooo slow ... pinging is fast
i have a disk drive with my Vista still installed so i rebooted vista to see if my nic was bad ... and Vista web browsing was very fast .... after 20 days of trying to resolve this on my own ( with no luck at all )
i goggled and search form's trying all tips with no luck.

... i decided to re-install kubuntu and same thing.
i  was going with LTS version then upgraded to latest. same thing

i am at my wits end on this one

I am sorry i cannot post much info as i do not fully remember all of the commands

robert@robert-desktop:~$  ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:c0:18:4a:59  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fe18:4a59/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1217328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:693441 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1703481840 (1.7 GB)  TX bytes:58277394 (58.2 MB)
          Interrupt:20 Memory:e5200000-e5220000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:928 errors:0 dropped:0 overruns:0 frame:0
          TX packets:928 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:54585 (54.5 KB)  TX bytes:54585 (54.5 KB)

---

### Post by robtoutant on 2012-01-26
just some more info Intel 82566DC-2 driver e1000e


==========================================================
                                 system         ()
/0                               bus            DG33FB
/0/0                             processor      Intel(R) Core(TM)2 Duo CPU     E6550  @ 2.33GHz
/0/0/1                           memory         4MiB L2 cache
/0/0/3                           memory         32KiB L1 cache
/0/2                             memory         32KiB L1 cache
/0/4                             memory         64KiB BIOS
/0/17                            memory         6GiB System Memory
/0/17/0                          memory         1GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/1                          memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/2                          memory         1GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/17/3                          memory         2GiB DIMM DDR2 Synchronous 800 MHz (1.2 ns)
/0/100                           bridge         82G33/G31/P35/P31 Express DRAM Controller
/0/100/1                         bridge         82G33/G31/P35/P31 Express PCI Express Root Port
/0/100/1/0                       display        NV43 [GeForce 6600 GT]
/0/100/3                         communication  82G33/G31/P35/P31 Express MEI Controller




Any help would be appreciated ... slowness of internet is unuseable ... will have to go back to vista

---

### Post by robtoutant on 2012-01-26
eth0        network        82566DC-2 Gigabit Network Connection

---

### Post by robtoutant on 2012-01-26
MAC Registers
-------------
0x00000: CTRL (Device control register)  0x50100240
      Endian mode (buffers):             little
      Link reset:                        normal
      Set link up:                       1
      Invert Loss-Of-Signal:             no
      Receive flow control:              disabled
      Transmit flow control:             enabled
      VLAN mode:                         enabled
      Auto speed detect:                 disabled
      Speed select:                      1000Mb/s
      Force speed:                       no
      Force duplex:                      no
0x00008: STATUS (Device status register) 0x00080283
      Duplex:                            full
      Link up:                           link config
      TBI mode:                          disabled
      Link speed:                        1000Mb/s
      Bus type:                          PCI
      Bus speed:                         33MHz
      Bus width:                         32-bit
0x00100: RCTL (Receive control register) 0x06038022
      Receiver:                          enabled
      Store bad packets:                 disabled
      Unicast promiscuous:               disabled
      Multicast promiscuous:             disabled
      Long packet:                       enabled
      Descriptor minimum threshold size: 1/2
      Broadcast accept mode:             accept
      VLAN filter:                       disabled
      Canonical form indicator:          disabled
      Discard pause frames:              filtered
      Pass MAC control frames:           don't pass
      Receive buffer size:               4096
0x02808: RDLEN (Receive desc length)     0x00001000
0x02810: RDH   (Receive desc head)       0x0000003F
0x02818: RDT   (Receive desc tail)       0x0000003D
0x02820: RDTR  (Receive delay timer)     0x00000000
0x00400: TCTL (Transmit ctrl register)   0x3103F0FA
      Transmitter:                       enabled
      Pad short packets:                 enabled
      Software XOFF Transmission:        disabled
      Re-transmit on late collision:     enabled
0x03808: TDLEN (Transmit desc length)    0x00001000
0x03810: TDH   (Transmit desc head)      0x00000055
0x03818: TDT   (Transmit desc tail)      0x00000055
0x03820: TIDV  (Transmit delay timer)    0x00000008
PHY type:                                unknown

---

### Post by robtoutant on 2012-01-26
after fighting with this network issue - windows is looking better all the time

---

### Post by shai-tan on 2012-01-26
I had a similar problem, fixed by disabling all ipv6. also deleted ipv6 addresses from interfaces, not sure if that mattered

ref: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

not sure what else I did, tried a lot of different things to finally get it fixed

---

### Post by varunendra on 2012-01-27
Hi *robtoutant*,

First off, Welcome to UbuntuForums :)

Next, something you better be aware of:
There are only a few things worse than posting multiple times in your own thread within 24 hrs. without being answered. THIS IS VERY HARMFUL TO YOUR THREAD! Because with 4 subsequent posts of your own, it will appear in a general search as if has got 4 answers, giving the impression that it 'IS being helped'. So the experts who could otherwise help may prefer to move on without looking at your thread.

That's why, it is recommended to put your question, then patiently wait for at lease 24 hours before posting again. If you really HAVE TO add some info immediately after you have posted, you can edit the existing post to do it.

That said, you haven't committed a crime by multi-posting ;), what I said above is just a recommended way to maximize the chances of getting proper help.



Now onto your internet problem:
Have you tried what shai-tan suggested? (that is - disable IPv6). Some alternate methods to disable it:
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)
If successfully disabled, the *"inet6.."* line won't appear anymore in the output of ifconfig.

If disabling IPv6 doesn't help, please post the outputs of:
```
uname -mr
sudo lshw -C network
lsmod
ifconfig
cat /etc/resolv.conf
cat /etc/network/interfaces
ping -c 4 google.com
```While posting outputs, click on the '**#**' symbol at the top of the box in which you create new posts. This will automatically generate [ code]....[ /code] tags. Copy-paste your outputs in-between those tags. Doing this makes the output appear in a 'code-box' like the one I have created above. It preserves the output formatting and makes it easier to read. Use separate tag-sets for separate outputs.

---

### Post by Revender on 2012-01-28
Thank you varunendra.

[quote=varunendra]Now onto your internet problem:
 Have you tried what shai-tan suggested? (that is - disable IPv6). Some alternate methods to disable it:
[http://www.webupd8.org/2010/05/how-t...untu-1004.html](http://www.webupd8.org/2010/05/how-t...untu-1004.html)
[http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html](http://www.ubuntugeek.com/how-to-dis...in-ubuntu.html)
 If successfully disabled, the "inet6.." line won't appear anymore in the output of ifconfig.[/quote]

Those two links did the job for me. I have issues with Pidgin now, I'm not sure whether Pidgin is in any way related to ipv6 or not, but I hope I will sort it out.

The strange thing is that my motherboard is just few years old (an asus-h61 chipset) and I don't see why it won't support ipv6. A compatibility issue maybe?

---

### Post by varunendra on 2012-01-29
> **Revender said:**
> Thank you varunendra.

Those two links did the job for me.
Glad it worked, and thanks for the feedback, for I wasn't sure myself if those fixes are still relevant. :)

As for any issues with pidgin (or any individual application/service), even with my inadequate knowledge I can say that disabling IPv6 'should have' nothing to do with it if the browsing and lookup speeds are okay. The only case I'm aware of when disabling IPv6 can have negative impact is if your ISP or the domain you are trying to reach, 'exclusively' depend on IPv6 - which is a very rare case.

> **Revender said:**
> The strange thing is that my motherboard is just few years old (an asus-h61 chipset) and I don't see why it won't support ipv6. A compatibility issue maybe?
No it can't be your motherboard (or NIC). As far as I have understood so far (and I'm still not sure), it is actually related with whether your router and/or ISP advertise themselves as IPv6 compatible, and then how they deal with packets when a communication attempt, using IPv6 protocol, is made by your browser or other applications/services.

Of many other explanations I found, this post, although was made in 2005, probably provides the most precise and easy to understand explanation: [http://mandrivausers.org/index.php?/topic/27992-why-does-ipv6-slow-things-down-so-much-solved/page__view__findpost__p__204255](http://mandrivausers.org/index.php?/topic/27992-why-does-ipv6-slow-things-down-so-much-solved/page__view__findpost__p__204255)
> Posted 06 September 2005 - 05:45 PM 					
 					 					 						I think this sums it up quite nicely. It is only one aspect though.
[QUOTE]A short bit about IPv6 addresses:

IPv6 addresses are, compared to IPv4 addresses, really big: 128 bits  against 32 bits. And this provides us just with the thing we need: many,  many IP-addresses: 340,282,266,920,938,463,463,374,607,431,768,211,465  to be precise. Apart from this, IPv6 (or IPng, for IP Next Generation)  is supposed to provide for smaller routing tables on the Internet's  backbone routers, simpler configuration of equipment, better security at  the IP level and better support for QoS.

An example: 2002:836b:9820:0000:0000:0000:836b:9886

 (source  can be found [here]("http://howtos.linuxbroker.com/howtoreader.shtml?file=Adv-Routing-HOWTO.html#LARTC.IPV6-TUNNEL"))

Another aspect is that networks are currently using ipv4 as default, so  the ipv6 sites that are already in use are "translated" into a ipv4  compatible form. This adds to the slowdown. Many network-gurus already  claimed that ipv6 is probably useless and will never be necessary. (ipv6  was started out of fear that the available network adresses wouldn't be  sufficient for the near future).
A third aspect is that some ipv6 servers are configured badly, causing  memory leaks with websites, so that the memory size of pages appears to  be much bigger than it really is. This can cause tremendous slowdowns  and freezing networks (denial of service), forcing a reset of the  machine or the router. 						 						[/QUOTE]

---

