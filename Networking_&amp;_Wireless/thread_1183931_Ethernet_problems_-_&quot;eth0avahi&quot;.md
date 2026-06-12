---
title: "Ethernet problems - &quot;eth0:avahi&quot;"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by martin_petrov on 2009-06-10
Newbie I'm afraid. I appreciate any help you can give me.

Finally put Ubuntu (dual boot with XP) onto my work laptop at the weekend, and had not noticed any problems until I plugged it into a work network connection on Monday. The network is an external ADSL connection with no firewall, and no specific networking requirements. On the Windows side, I could just plug in and away I went, no worries with IP Address or DNS etc settings.

Ubuntu, however, I got no connectivity anywhere. 

I ran ifconfig and got:

```

eth0      Link encap:Ethernet  HWaddr 00:18:8b:dd:14:49  
          inet6 addr: fe80::218:8bff:fedd:1449/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:197 errors:0 dropped:0 overruns:0 frame:0
          TX packets:85 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13396 (13.0 KB)  TX bytes:7396 (7.2 KB)
          Interrupt:17 

eth0:avahi Link encap:Ethernet  HWaddr 00:18:8b:dd:14:49  
          inet addr:169.254.5.131  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82484 (80.5 KB)  TX bytes:82484 (80.5 KB)


```Having had a google around, I found that "sudo dhclient eth0" was a possible solution, and having run it:

```

[pjohnston@philmobile2 temp]$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:18:8b:dd:14:49
Sending on   LPF/eth0/00:18:8b:dd:14:49
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.1.70 from 192.168.1.254
DHCPREQUEST of 192.168.1.70 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.70 from 192.168.1.254
bound to 192.168.1.70 -- renewal in 33131 seconds.

```I got this:

```

eth0      Link encap:Ethernet  HWaddr 00:18:8b:dd:14:49  
          inet addr:192.168.1.70  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:fedd:1449/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:556 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:345655 (337.5 KB)  TX bytes:31494 (30.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1638 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82484 (80.5 KB)  TX bytes:82484 (80.5 KB)


```And, whoopee, I could connect to the internet.

However, I could find no sensible way to keep this after a reboot. Is there anything I can do for this?

Other points to know: 
I've set my System -> Admin -> Network -> "Wired Connection" to be "DHCP" having read that in another forum, but not really had much rhyme or reason for it.

lspci setting for Ethernet:

```

09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
        Subsystem: Dell Unknown device 01f9
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at f9ef0000 (64-bit, non-prefetchable) [size=64K]
        Expansion ROM at <ignored> [disabled]
        Capabilities: [48] Power Management version 3
        Capabilities: [50] Vital Product Data
        Capabilities: [58] Vendor Specific Information
        Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [d0] Express Endpoint IRQ 0

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation Unknown device 1021
        Flags: bus master, fast devsel, latency 0, IRQ 218
        Memory at f9fff000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [c8] Power Management version 2
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Legacy Endpoint IRQ 0


```Thanks for reading. (and thanks in advance if you can reply with something useful ;) )

---

### Post by doas777 on 2009-06-10
well, one thing you could do, is to add 
```
gksu dhclient eth0
``` to your startup applications.

another thing to try, is to delete the "Wired Connection" profile in network manager and create a new one. 

if that fails, then you can set the interface to use DHCP at boot (not at login) by configuring your /etc/network/interfaces file. [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

good luck

---

### Post by martin_petrov on 2009-06-11
Hey - thanks for the response.

Happily (or annoyingly) whatever playing around I did last night (which I thought was "not very much") might have done something positive since I didn't need to do the dhclient command this morning.

So I'll take what I can for now - though I might well add that command to run automatically if it doesn't.

Thanks,

Martin Petrov

---

