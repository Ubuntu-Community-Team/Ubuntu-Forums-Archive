---
title: "Broadcom 4312/Ubuntu 8.10/Dell Inspiron 1525: Very slow internet after updates"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by sadwings on 2009-03-10
Hi,

I have Ubuntu 8.10 on my Dell Inspiron 1525.

Internet access via the wireless card was great both during the install and for a month afterwards.

I have the Broadcom STA driver and it shows as enabled.

After my first update using "Update Manager" (there were a lot and I just let Ubuntu update everything on the list), my wireless internet slowed to a crawl.  It is now slow whether I'm browsing, using apt-get or cpan, etc... I have to plug into the router when I need to do anything requiring internet access.

The wireless DOES work, it's just terribly slow and as I've said, it DID work just fine until recently.

I'd appreciate any ideas.  I can usually mash my way through these sorts of issues, but I'm not network literate at all and I am pretty much vexed here.

**Machine Brand and Model:**
> Dell Inspiron 1525

**lspci**
> 0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

**ifconfig**
> eth0      Link encap:Ethernet  HWaddr 00:23:ae:14:7c:f5
          inet6 addr: fe80::223:aeff:fe14:7cf5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4381 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4875245 (4.8 MB)  TX bytes:1273385 (1.2 MB)
          Interrupt:16

eth1      Link encap:Ethernet  HWaddr 00:24:2b:34:d0:7f
          inet addr:192.168.1.3  Bcast:192.168.1.255 Mask:255.255.255.0
          inet6 addr: fe80::224:2bff:fe34:d07f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4917 errors:0 dropped:0 overruns:0 frame:33868
          TX packets:5024 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3498526 (3.4 MB)  TX bytes:1161223 (1.1 MB)
          Interrupt:17 Base address:0xc000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:85 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:11041 (11.0 KB)  TX bytes:11041 (11.0 KB)

# This is what iwconfig looks like after I boot.
**iwconfig**
> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated

pan0      no wireless extensions.

# I have seen eth1 look like this, but it's not something I can get to happen at will and I don't think it was working well even then.> 
eth1      IEEE 802.11bg  ESSID:"QQDL0"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:90:E4:B5:B2
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-35 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

# I looked through dmesg output, these lines are the only ones that looked relevant to me.
**dmesg  | grep eth**
> [    3.462455] sky2 eth0: addr 00:23:ae:14:7c:f5
[    4.261552] Driver 'sd' needs updating - please use bus_type methods
[    4.487021] Driver 'sr' needs updating - please use bus_type methods
[   12.004514] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.12
[   25.852982] sky2 eth0: enabling interface
[   25.855775] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.244083] eth1: no IPv6 routers present
[ 5771.293054] eth1: no IPv6 routers present

**sudo lshw -C network**
>   *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:23:ae:14:7c:f5
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:24:2b:34:d0:7f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.27.12 ip=192.168.1.3 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:b7:e9:c9:62:90
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



# There were more cell number entries, but all pointed to network names other than mine.  QQDL0 is my router.
**sudo iwlist scan**
> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:90:E4:B5:B2
                    ESSID:"QQDL0"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-24 dBm  Noise level:-85 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s



**lsb_release -d**
> Description:    Ubuntu 8.10


**uname -mr**
> 2.6.27-11-generic i686


**sudo /etc/init.d/networking restart**
>  * Reconfiguring network interfaces...
Ignoring unknown interface eth1=eth1.

---

### Post by saechen on 2009-03-10
Bump. 

Am seeing the same behavior. Was thinking maybe related to update to wicd, but now maybe not.

---

### Post by sadwings on 2009-03-11
Any ideas based on the outputs of the commands?

I brought the laptop to work today, I'll try the hotspot at the cafe downstairs and see if I get a better conncetion and at least rule my router out as the cause.

---

### Post by sadwings on 2009-03-11
Ok, I'm at the coffee shop at work and my wireless is smoking fast.

So I'm happy, but still vexed.  Any advice or pointers to where I should go for information on troubleshooting my home network would be greatly appreciated.

I may just move into the coffee shop here, this is pretty swell. ;)

---

### Post by pmatos on 2009-04-30
Hi Guys,

I got an XPS1330 with 
broadcom corporation bcm4312 802.11 b/g rev 01

and ubuntu 9.04 detects the STA Broadcom driver but damn it sometimes gets slow and even 5 meters from the router, the connection is only 50-80% sometimes dropping to 20% and losing connection.

Is there any solution to this issue? Interestingly enough the STA driver recognizes my card as a 4315 instead of 4312, this might be it!

Cheers,

Paulo Matos

---

### Post by bobe84 on 2009-04-30
Maybe powersaving feature is causing problems...
Let's see:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-36 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
After this line:
```
sudo iwconfig eth1 power off
```
powersaving is turned off, latency on link drops from 80ms to 2ms maximum...

output from iwconfig:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-35 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
I got also 4312 rev 1

Hope this solves some troubles...

---

### Post by OMIGHTY1 on 2009-04-30
I've heard that Broadcom wireless cards are terrible for Linux.

---

### Post by pmatos on 2009-05-01
> **bobe84 said:**
> Maybe powersaving feature is causing problems...
Let's see:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-36 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
After this line:
```
sudo iwconfig eth1 power off
```
powersaving is turned off, latency on link drops from 80ms to 2ms maximum...

output from iwconfig:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-35 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
I got also 4312 rev 1

Hope this solves some troubles...

Thanks, I will try that, how are you measuring the latency?

---

### Post by pmatos on 2009-05-01
> **OMIGHTY1 said:**
> I've heard that Broadcom wireless cards are terrible for Linux.

Why? Why is there no good driver for them?

---

### Post by pmatos on 2009-05-01
> **bobe84 said:**
> Maybe powersaving feature is causing problems...
Let's see:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-36 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
After this line:
```
sudo iwconfig eth1 power off
```
powersaving is turned off, latency on link drops from 80ms to 2ms maximum...

output from iwconfig:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-35 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
I got also 4312 rev 1

Hope this solves some troubles...

Not really, I think it got worse in fact. How do you measure the latency?
EDIT Do you use any specialised web service or you just ping/traceroute several hosts?

---

### Post by sir_nasty on 2009-05-01
I have a dell mini 9 with BCM4315 and shows my wireless controller version as 5.10.79.10, perhaps you should see if there's another update....

---

### Post by pmatos on 2009-05-01
> **sir_nasty said:**
> I have a dell mini 9 with BCM4315 and shows my wireless controller version as 5.10.79.10, perhaps you should see if there's another update....

That's exactly my version! I assume your card is a BCM4312 and not a 4315?

---

### Post by bobe84 on 2009-05-01
I ping my wifi router, or ping some computer in that LAN
This is with "powersaving"```

root@titan:~# iwconfig eth1 power on
root@titan:~# ping 192.168.2.38
PING 192.168.2.38 (192.168.2.38) 56(84) bytes of data.
64 bytes from 192.168.2.38: icmp_seq=1 ttl=64 time=41.5 ms
64 bytes from 192.168.2.38: icmp_seq=2 ttl=64 time=63.2 ms
64 bytes from 192.168.2.38: icmp_seq=3 ttl=64 time=86.3 ms
64 bytes from 192.168.2.38: icmp_seq=4 ttl=64 time=108 ms
64 bytes from 192.168.2.38: icmp_seq=5 ttl=64 time=28.9 ms
64 bytes from 192.168.2.38: icmp_seq=6 ttl=64 time=52.7 ms
64 bytes from 192.168.2.38: icmp_seq=7 ttl=64 time=72.9 ms
64 bytes from 192.168.2.38: icmp_seq=8 ttl=64 time=96.3 ms
^C
--- 192.168.2.38 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7010ms
rtt min/avg/max/mdev = 28.997/68.830/108.367/25.663 ms
root@titan:~# 

``` 

Without:

```

root@titan:~# iwconfig eth1 power off
root@titan:~# ping 192.168.2.38
PING 192.168.2.38 (192.168.2.38) 56(84) bytes of data.
64 bytes from 192.168.2.38: icmp_seq=1 ttl=64 time=1.01 ms
64 bytes from 192.168.2.38: icmp_seq=2 ttl=64 time=1.15 ms
64 bytes from 192.168.2.38: icmp_seq=3 ttl=64 time=1.02 ms
64 bytes from 192.168.2.38: icmp_seq=4 ttl=64 time=1.05 ms
64 bytes from 192.168.2.38: icmp_seq=5 ttl=64 time=1.01 ms
64 bytes from 192.168.2.38: icmp_seq=6 ttl=64 time=1.11 ms
^C
--- 192.168.2.38 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 1.013/1.064/1.159/0.058 ms
root@titan:~# 


```
As you can see it has big impact for me, hope you solve problem, if not maybe you should try b43 driver works a little slower that this driver (wl) but connects much faster to networks(wl driver conects very slow for me at least) and also u can do "monitoring" :P

---

### Post by bobe84 on 2009-05-01
I forgot to mention...
My card id is 14e4:4312, but dmesg from b43 driver gives this:
```

[  325.999465] b43-phy0: Broadcom 4311 WLAN found

```

---

### Post by sir_nasty on 2009-05-02
mine doesn't show that at all... granted I may have a different version of ubuntu.  But yes mine is a b4312 (dell mini 9) and shows the previously posted driver but not that entry... any luck with resolving this issue yet?

---

### Post by pmatos on 2009-05-04
> **bobe84 said:**
> Maybe powersaving feature is causing problems...
Let's see:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Managementmode:All packets received**
          Link Quality=5/5  Signal level=-36 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
After this line:
```
sudo iwconfig eth1 power off
```
powersaving is turned off, latency on link drops from 80ms to 2ms maximum...

output from iwconfig:
```

eth1      IEEE 802.11abg  ESSID:"bobe-kuci"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:0F:ED:F5:42
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          **Power Management:off**
          Link Quality=5/5  Signal level=-35 dBm  Noise level=-98 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```
I got also 4312 rev 1

Hope this solves some troubles...

It also gets a lot faster here with power management off but link quality is far from good even near the router. Anyway, for now, how do you turn it off each time you start ubuntu? Any init script line I should add somewhere?

Cheers,

Paulo Matos

---

