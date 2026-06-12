---
title: "Wired ethernet problem in Jaunty"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by MadeTheSwitch on 2009-08-13
Any help would be greatly appreciated.

I am using an Thinkpad X61s. Have had no trouble with it for ages. Today, I came out of suspend mode and the wired ethernet connection stopped working.

The symptom: both link lights are constantly on (not blinking, just on), and there is no ability to connect using eth0. Wireless still works.

**EDIT: note that the lights stay on even if I remove the ethernet cable!**

To make sure it's not a hardware issue, I booted into Windows and it's fine there. Also, I paid attention to the boot process, and the interface works properly (green/link light goes on, neg light blinking) until the Ubuntu "loading" screen pops up (where there is a progress bar). It is at that moment that the neg (orange) light goes on and stays on.

It gets weirded. **ifconfig** shows the interface:

> 
eth0      Link encap:Ethernet  HWaddr 00:16:d3:c8:61:34  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:f8200000-f8220000 


but if I try **ifdown**, I get the following:

> 
ifdown: interface eth0 not configured


and if I try **/etc/init.d/networking restart**

> 
 * Reconfiguring network interfaces...                                   Ignoring unknown interface eth0=eth0.


**/etc/network/interfaces** looks like this:

> 
auto eth0
auto lo
iface lo inet loopback


(no, it's not a DHCP problem; I verified this already by running dhclient, as well as configuring interfaces to enforce this, so the lack of an iface statement with dhcp is not the source; I also set the MTU manually to 1500 in case that was somehow the cause)

lshw -C network gives this:

> 
  *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:16:d3:c8:61:34
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=15.8-10 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:6d:7d:55
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=172.20.120.92 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network:0
       description: Ethernet interface
       physical id: 2
       logical name: virbr0
       serial: 46:ef:af:28:df:6f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.122.1 link=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes


and **lspci** confirms that:

> 
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)


Interestingly, **modprobe eth0** throws up the error:

> 
FATAL: Module eth0 not found.


but I CAN modprobe e1000 and e1000e (comes back with no response but no error either, not sure what that means, it just hands back the prompt).

**dmesg | grep eth0** throws the following:

> 
[    3.759568] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:16:d3:c8:61:34
[    3.759571] 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    3.759609] 0000:00:19.0: eth0: MAC: 5, PHY: 6, PBA No: ffffff-0ff
[   32.856689] ADDRCONF(NETDEV_UP): eth0: link is not ready


Please please please help.

---

### Post by Iowan on 2009-08-13
Your */etc/network/interfaces* has an "auto eth0" line, but no definition.  Dunno if that line is enough to thwart NM management. Try commenting out "auto eth0" and restarting.

---

### Post by MadeTheSwitch on 2009-08-13
> **Iowan said:**
> Your */etc/network/interfaces* has an "auto eth0" line, but no definition.  Dunno if that line is enough to thwart NM management. Try commenting out "auto eth0" and restarting.

Thank you. Tried that already. It makes no difference if that line is in or not.

---

### Post by Iowan on 2009-08-13
Sorry - I guess you DID mention that... although it seems a bit strange.
You mentioned running dhclient - did it confirm IP address? **ifconfig ** looks like eth0 has no address. Strange indeed...

---

### Post by MadeTheSwitch on 2009-08-13
> **Iowan said:**
> Sorry - I guess you DID mention that... although it seems a bit strange.
You mentioned running dhclient - did it confirm IP address? **ifconfig ** looks like eth0 has no address. Strange indeed...

Yes, strange indeed... that is the point :-)

I cannot obtain an IP address for the simple reason that the ethernet interface is "stuck" - it doesn't negotiate. I can't find a way to shut it down even, the lights stay on regardless of what I do until I shut down the machine completely.

Just so I can get that out of the way, here is the result of **dhclient**

> 
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:16:d3:c8:61:34
Sending on   LPF/eth0/00:16:d3:c8:61:34
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only
   ...done.


One thing I don't understand here is what the heck is wmaster0 and how is it related to this at all? the error it throws (unknown hardware address type 801) is very curious too.

---

### Post by MadeTheSwitch on 2009-08-13
I'll add one more note - yesterday this same interface worked perfectly well. I then suspended the machine, turned it on in a place with only wireless (but the lights on the ethernet were off as they should be), suspended over night, took it this morning to a wired network, and the problem appeared.

Nothing changed in the system in between.

---

### Post by MadeTheSwitch on 2009-08-13
Alright, this is fascinating.

The problem corrected itself. 

I shut the laptop down (not suspended, but actual shutdown), left the office I was in, and drove home. An hour and a half later, when I booted it, the problem had disappeared.

I am beginning to wonder if it has something to do with the physical ethernet infrastructure at that particular office. The reason I say that is that it has always been a bit troublesome; most of time, no matter what I do, it would require a reboot to acquire an IP address through the wired ethernet port. Even then, the negotiation process is always FAR longer than anywhere else (a minute instead of a few seconds).

Then I remembered that two months ago I had something somewhat similar happen there; the interface lit up and wouldn't negotiate. At that time a reboot solved the problem which is why I forgot about it.

Is it possible that there is some link between maybe the physical characteristics of that network - maybe the jacks put out a bit of extra juice, or shielding is awkward, or something like that - that would cause the behavior I described above?

This is now one of those "I'm really curious and want to figure it out" moments.

---

### Post by Iowan on 2009-08-14
I'm also curious to learn what's going on... 
(glad it works at home...)

---

### Post by MadeTheSwitch on 2009-08-19
> **Iowan said:**
> I'm also curious to learn what's going on... 
(glad it works at home...)

No one?

A couple more points: the port DID work in Windows at the time, so it would appear not to have been a hardware issue.

Looks like something that got triggered by the interaction between the software (kernel driver maybe) and some unique property of the ethernet link or cable. Any ideas would be greatly appreciated.

---

### Post by MadeTheSwitch on 2009-09-30
Alright folks.

It took me all this time to properly try and duplicate this problem in a consistent manner, because there was literally nothing to work from.

I believe I now have at least a consistent combination of elements that causes this to happen, as follows:

1) low battery (under 1 hour left)
2) several repeated openings and closings of the lid (not rapidly, just in normal course of running the laptop) while in battery mode in order to connect to **more than one** wireless network
3) an attempt to turn off the wireless connection while the lid is closed and the laptop is sleeping in order to connect to a wired network and wake the laptop up
4) (not certain about this) heating; not beyond normal operating parameters but close to them

What seems to happen is that the wired interface falls into a "hardware testing mode".

What seems to solve it is shutting the laptop down, disconnecting the battery, and letting it cool down for 30 minutes before booting it again.

I am completely lost on how to move forward, but this does not happen in Windows under similar conditions (only in Ubuntu).

---

