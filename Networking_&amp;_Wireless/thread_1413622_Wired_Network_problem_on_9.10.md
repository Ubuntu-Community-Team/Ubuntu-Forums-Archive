---
title: "Wired Network problem on 9.10"
date: 2010-02-22
forum: Networking &amp; Wireless
---

### Post by michael44 on 2010-02-22
Hi, I'm a complete newbie for Ubuntu, and I'd like some help if possible.

I cannot configure my Wired Network (which is the only connection i've got, apart from a couple of wifi from my neighbours).. I 

At first I was meddling with the Network Manager (right after I checked "Connect to wireless and ethernet networks"), with no success.

Then I found a couple of threads where people said that wicd manager is better than the network manager, so i installed wicd, but again no result.

Then I changed the /etc/network/interfaces, "guessed" my IP, tried restarting, with no result.

After all of this I decided to post a thread here.

Here's the output of ifconfig:

ifconfig

```

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:2f:ac:ac  
          inet6 addr: fe80::e2cb:4eff:fe2f:acac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20984713 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:3
          collisions:0 txqueuelen:1000 
          RX bytes:329624 (329.6 KB)  TX bytes:8357 (8.3 KB)
          Interrupt:36 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2309 (2.3 KB)  TX bytes:2309 (2.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:cd:6e:7a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-25-D3-CD-6E-7A-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Incidentally, can anyone explain how you're supposed to get your IP from that?
I installed Ubuntu 9.10 64bit this morning on my new laptop (i7 processor), and i'm really frustrated that i cannot get this to work.

---

### Post by Iowan on 2010-02-22
The incidentally first: You don't - if there's no IP address... Ordinarily, it'd look more like: ```
eth0      Link encap:Ethernet  HWaddr 00:51:d2:a1:12:11  
          inet addr:192.168.1.11  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::251:d2ff:fea1:1211/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3869 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3675 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3670637 (3.5 MB)  TX bytes:539741 (527.0 KB)
          Interrupt:3 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72280 (70.5 KB)  TX bytes:72280 (70.5 KB)

```If you get a DHCP address, you can edit your */etc/network/interfaces* file to look like:```
auto lo
iface lo inet loopback

auto eth0
inface eth0 inet dhcp

```Restart networking - my era systems used **/etc/init.d/networking restart** - I'm still not familiar with the 
"service" version.

---

### Post by doas777 on 2010-02-22
could you post your interfaces file please?
are there other pcs on the network you are connecting to, and if so, how many? 

if you don't like ifconfig, you can try the 'ip' commands:
```

ip addr
ip address

``` both show your ip, in a somewhat shorter format than ifconfig.

the init.d script Iowan mentioned should work fine, but if not, try:
```
sudo service networking restart
```
it runs the same init.d script, but is a little shorter

---

### Post by Iowan on 2010-02-22
My Karmic machine complains about > restart: unknown instance: when I try ```
sudo service networking restart
```

---

### Post by doas777 on 2010-02-22
> **Iowan said:**
> My Karmic machine complains about  when I try ```
sudo service networking restart
```

interesting. I get this:
```

$ sudo service networking
Usage: /etc/init.d/networking {start|stop|restart|force-reload}

```but you are right, I get the same message when i add 'restart'. 
op: sorry, disregard this command for now. something is obviously not right. my bad.

---

### Post by michael44 on 2010-02-22
Thank you for replying!

However, it's still not working...

Ok, so this is my interfaces file:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

```

After restarting, i get:
```

* Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/e0:cb:4e:2f:ac:ac
Sending on   LPF/eth0/e0:cb:4e:2f:ac:ac
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
receive_packet failed on eth0: Network is down
Terminated
Failed to bring up eth0.

```

and when i restart again, i get:

```

* Reconfiguring network interfaces...                                          
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/e0:cb:4e:2f:ac:ac
Sending on   LPF/eth0/e0:cb:4e:2f:ac:ac
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by doas777 on 2010-02-22
are you sure the cable is snug in the socket?

what is the output of 
```
sudo ethtool eth0
```

---

### Post by Iowan on 2010-02-22
I had a [similar]("http://ubuntuforums.org/showthread.php?t=1156441") problem with Jaunty, but it wasn't an issue on my Karmic box. I've seen reference to threads reporting bugs in dhclient - but haven't seen them myself yet.

---

### Post by michael44 on 2010-02-22
> **doas777 said:**
> 
what is the output of 
```
sudo ethtool eth0
```

```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x0000003f (63)
    Link detected: yes

```

---

### Post by michael44 on 2010-02-23
How can I check whether I've got the right drivers for my Ethernet card? Or whether they are installed at all?

---

### Post by michael44 on 2010-02-23
This is the output i get from lspci:
Is it supposed to be this long?

```

00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 68c0
01:00.1 Audio device: ATI Technologies Inc Device aa60
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
07:00.0 USB Controller: NEC Corporation Device 0194 (rev 03)
08:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)

```

---

### Post by michael44 on 2010-02-23
This is my dhclient.conf. Everythin was commented, apart from two lines, request and require. I uncommented those, and now I get a different response when I restart the network (Network is down, Failed to bring up eth0).

```

send host-name "andare.fugue.com";
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
send dhcp-lease-time 3600;
supersede domain-name "fugue.com home.vix.com";
prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name;
require subnet-mask, domain-name-servers;
timeout 60;
retry 60;
reboot 10;
select-timeout 5;
initial-interval 2;
script "/etc/dhclient-script";
media "-link0 -link1 -link2", "link0 link1";
reject 192.33.137.209;

alias {
  interface "ep0";
  fixed-address 192.5.5.213;
  option subnet-mask 255.255.255.255;
}

lease {
  interface "ep0";
  fixed-address 192.33.137.200;
  medium "link0 link1";
  option host-name "andare.swiftmedia.com";
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.33.137.255;
  option routers 192.33.137.250;
  option domain-name-servers 127.0.0.1;
  renew 2 2000/1/12 00:00:01;
  rebind 2 2000/1/12 00:00:01;
  expire 2 2000/1/12 00:00:01;
}


```

I think i will reinstall karmic, and the install the 9.04 version. Do you think I will have the same problems there?

---

### Post by doas777 on 2010-02-23
the ethtool output looks good so your card is functional and responds to the os via the driver installed.

yes your lspci output will be of some length, usually. 

you can check the exact nic driver with 
```

sudo lshw -C network

```I think Iowan is right about the DHCP bug. I'm out of my element there.

---

### Post by michael44 on 2010-02-23
i have one simple question though:

How would a ubuntu veteran connect to a wired network after a fresh clean install?
Meaning, you installed ubuntu (9.10 in my case), you haven't installed any additional software on it, you haven't even moved your mouse yet. What do you do?

And please answer in the simplest way possible.
Thank You.

---

### Post by Iowan on 2010-02-23
Most of what was in the original (commented) dhclient.conf was sample settings - I suspect your machine has a really weird personality with those settings active... 
I remember a [thread]("http://ubuntuforums.org/showthread.php?t=1412983") that mentioned **dhcpcd** as alternative. I've found a few (14) others that mention **dhcpcd**: [Here's]("http://ubuntuforums.org/showthread.php?t=1249681") one.

---

### Post by michael44 on 2010-02-23
Thank you Iowan!!!!

But, it's not quite working yet.
This is what happens when I run dhcpcd eth0.

```

err, eth0: timed out
err, eth0: lease information file `/var/lib/dhcpcd/dhcpcd-eth0.info'  does not exist
warn, eth0: using IPV4LL address 169.254.213.23
michael@michael-laptop:~$ dhcpcd.sh: interface eth0 has been configured with  new IP=169.254.213.23

```

And the ifconfig shows the following:

```

eth0      Link encap:Ethernet  HWaddr e0:cb:4e:2f:ac:ac  
          inet addr:169.254.213.23  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::e2cb:4eff:fe2f:acac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41970345 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:692316 (692.3 KB)  TX bytes:19069 (19.0 KB)
          Interrupt:36 

```

However, when I start Mozilla, I still get nothing. ping google does't work too.
So, how do I finish the job now?

---

### Post by michael44 on 2010-02-23
Hooray, I'm able to ping localhost.
But I'm still missing something.... What? Could it be that network-manager is causing problems? I tried to connect to eth0 via NM, and I got "Disconnected".

---

### Post by Iowan on 2010-02-23
I'm fortunate that **dhclient** still works for me - so I haven't had the "opportunity" to try **dhcpcd**. The 169.254.213.23 address means that DHCP still didn't work - that's an **avahi** (zeroconf) address that essentially puts the machine in a subnet by itself. So you (we?) still don't get an address via DHCP...

---

### Post by Jive Turkey on 2010-02-24
> **michael44 said:**
> i have one simple question though:

How would a ubuntu veteran connect to a wired network after a fresh clean install?
Meaning, you installed ubuntu (9.10 in my case), you haven't installed any additional software on it, you haven't even moved your mouse yet. What do you do?

And please answer in the simplest way possible.
Thank You.

Simplest answer: plug in a network cable, that's seriously all that is needed most of the time.

A problem I once encountered once dual booting with windows, windows sometimes has the ability to "turn off this adapter to save power" and then when user boots to linux, linux doesn't know to turn it on again.  The fix was to boot into windows and untick that box in the network adapter properties.

---

### Post by michael44 on 2010-02-24
Thank you for your answers people.

@Iowan
Oh well. We'll get there.

@Jive Turkey
This is a new laptop, so there is no windows here. And i intend to keep it that way.

I read somewhere that people were having problems when upgrading to 9.10, and that i should wait for a new release of Karmic, so I downgraded down to Jaunty (that is I installed 9.04 and formatted 9.10).

And now the ifconfig output looks something like:
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7632 (7.6 KB)  TX bytes:7632 (7.6 KB)

pan0      Link encap:Ethernet  HWaddr f2:5a:44:9f:d2:20  
          inet6 addr: fe80::f05a:44ff:fe9f:d220/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:19539 (19.5 KB)

```

There is also pan0:avahi Link, I forgot to copy it...
But why do I have now pan0 instead of eth0?

Also, I read on another thread (not on this website though, but they were having very similar problems) that I should remove the avahi package, and that it is causing all the problems. 

Any thoughts on that?
Cheers

---

### Post by coskierken on 2010-02-24
What are the settings in your router?  Just curious as Karmic installed the drivers to have the nic working and you got an ip address associated to it.  Is the router using DHCP?  I have not problem with this at all and have never, in any version of Ubuntu, connecting to a router via Cat5.  Strange!

---

### Post by doas777 on 2010-02-24
is this DHCP server under your control (a router or whatever) or is it an ISP server?

---

### Post by michael44 on 2010-02-24
i'm connected via dsl modem which was supplied to me by my isp provider...

---

### Post by doas777 on 2010-02-24
> **michael44 said:**
> i'm connected via dsl modem which was supplied to me by my isp provider...

have you thouroughly troubleshot the modem? called the isp etc? usually just unplugging it from power for 10 minutes will help clear up common issues.

---

