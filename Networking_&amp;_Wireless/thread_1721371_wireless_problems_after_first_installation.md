---
title: "wireless problems after first installation"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by guysh on 2011-04-04
Hello

I recently installed ubuntu 10 on my Compaq mini 730ej. 
I installed it using the wubi software.
Although it works fine with regular lAN connection, it doesn't recognize any wireless networks - when I click the icon I see a "missing firmware" massage.
Now - I am a linux newbie, so be gentle, but I would very much like to solve this problem since.So what can I do ? 

Thanks

---

### Post by matt_symes on 2011-04-04
Hi

What card is it ? Please post the output of (from a terminal) Applications->Accessories->Terminal

.... case sensitive

```
sudo lshw -C network
lspci -nnk | grep Network
```

Enter your password. It will not be echoed to the screen. This is normal.

This will help us identify your card.

Copy and paste the results back from the terminal to your reply post.

In the reply post wrap the results in code tags. This will make it easier to read. You can do this by highlighting the text to wrap and hitting the # button on the menu above where you type your reply.

Kind regards.

---

### Post by guysh on 2011-04-05
Thank allot

For the first command line I got :

 ```
 *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:feafc000-feafffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:24:81:52:f6:94
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=10.100.102.3 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:feb00000-feb03fff ioport:e000(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:24:2b:ae:65:36
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

```

For the second : 

```
Basic display modes:
-mm		Produce machine-readable output (single -m for an obsolete format)
-t		Show bus tree

Display options:
-v		Be verbose (-vv for very verbose)
-k		Show kernel drivers handling each device
-x		Show hex-dump of the standard part of the config space
-xxx		Show hex-dump of the whole config space (dangerous; root only)
-xxxx		Show hex-dump of the 4096-byte extended config space (root only)
-b		Bus-centric view (addresses and IRQ's as seen by the bus)
-D		Always show domain numbers

Resolving of device ID's to names:
-n		Show numeric ID's
-nn		Show both textual and numeric ID's (names & numbers)
-q		Query the PCI ID database for unknown ID's via DNS
-qq		As above, but re-query locally cached entries
-Q		Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots
-d [<vendor>]:[<device>]			Show only devices with specified ID's

Other options:
-i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>	Look up kernel modules in a given file instead of default modules.pcimap
-M		Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>	Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>	Set PCI access parameter (see `-O help' for a list)
-G		Enable PCI access debugging
-H <mode>	Use direct hardware access (<mode> = 1 or 2)
-F <file>	Read PCI configuration dump from a given file
```

Is that what you need ?

---

### Post by matt_symes on 2011-04-05
Hi

Something went wrong with the last command.

Copy and paste this from here into a terminal. Don't type it :)

```
lspci -nnk | grep -A3 Network
```

Kind regards

---

### Post by guysh on 2011-04-05
Thank for your patience 

here is the output 

```
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:1508]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ss
```

---

### Post by TBABill on 2011-04-05
Since you have internet access via ethernet we can get it going. Many of the BCM4312 Broadcom cards do not work with the b43 driver, which is what your system shows as active. Can you go to System>>Administration>>Additional Drivers (or Hardware if it's Ubuntu 10.04) and select the STA driver and activate it? (And make sure the other is not activated) Then just follow the prompts and restart.

---

### Post by guysh on 2011-04-05
Worked like a charm :) 
Thanks

---

### Post by xXkanfirXx on 2011-04-05
> **TBABill said:**
> Since you have internet access via ethernet we can get it going. Many of the BCM4312 Broadcom cards do not work with the b43 driver, which is what your system shows as active. Can you go to System>>Administration>>Additional Drivers (or Hardware if it's Ubuntu 10.04) and select the STA driver and activate it? (And make sure the other is not activated) Then just follow the prompts and restart.
Hello, I'm a newb too and also having wireless troubles. I have the same wireless card as Guysh. A Broadcom BCM4312. My wireless card turns on, finds networks and connects to them. But if I try to use Firefox or perform any other type of internet related process it doesn't work. I went to "Additional Drivers" and found one driver "Broadcom STA wireless driver" and it says its activated. Any suggestion??

---

### Post by TBABill on 2011-04-06
Your problem is very different than the OP. Do you mean when you open Firefox you can't get to a webpage? Will the machine run updates ok?

---

### Post by xXkanfirXx on 2011-04-06
> **TBABill said:**
> Your problem is very different than the OP. Do you mean when you open Firefox you can't get to a webpage? Will the machine run updates ok?

It won't run updates and when Firefox opens it says "unable to connect".

---

### Post by matt_symes on 2011-04-06
Hi

Open a terminal and type

```
route -n
```

This will (hopefully) produce an output like this.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.4.0      0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.1.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
192.168.57.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet8
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         **192.168.1.1**     0.0.0.0         **UG**    0      0        0 wlan0
```

Look for a line that says UG and look for the IP address near it (in bold above). Ping that IP address.

```
ping -c3 <ip_address>
```

In my case that would be

```
ping -c3 192.168.1.1
```

You should get a response similar to

```
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=1.84 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=1.85 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=1.80 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 1.807/1.833/1.850/0.039 ms
```


If you get a reply (and you should) try pinging

```
ping -c3 8.8.8.8
```

If you get a reply try typing

```
nslookup www.google.com
```

You should get a response similar to

```
Server:         192.168.1.1
Address:        192.168.1.1#53

Non-authoritative answer:
www.google.com  canonical name = www.l.google.com.
Name:   www.l.google.com
Address: 209.85.146.104
Name:   www.l.google.com
Address: 209.85.146.105
Name:   www.l.google.com
Address: 209.85.146.99
Name:   www.l.google.com
Address: 209.85.146.106
Name:   www.l.google.com
Address: 209.85.146.103
Name:   www.l.google.com
Address: 209.85.146.147
```

If that is good try

```
wget www.google.com
```

You should get a response like

```
matthew@matthew-laptop:~/my_documents/colaborative_scripts$ wget www.google.com
--2011-04-07 02:38:56--  http://www.google.com/
Resolving www.google.com... 209.85.146.99, 209.85.146.147, 209.85.146.105, ...
Connecting to www.google.com|209.85.146.99|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.google.co.uk/ [following]
--2011-04-07 02:38:56--  http://www.google.co.uk/
Resolving www.google.co.uk... 209.85.146.106, 209.85.146.104, 209.85.146.103, ...
Reusing existing connection to www.google.com:80.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `index.html'

    [ <=>                                                                                                                                                        ] 9,096       --.-K/s   in 0.03s   

2011-04-07 02:38:56 (326 KB/s) - `index.html' saved [9096]
```

Do any of these steps fail. (Your output will not be exactly the same but should look similar).

Post back.

Kind regards

---

