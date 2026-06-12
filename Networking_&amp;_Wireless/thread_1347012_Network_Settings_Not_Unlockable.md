---
title: "Network Settings Not Unlockable"
date: 2009-12-05
forum: Networking &amp; Wireless
---

### Post by gregsmith_to on 2009-12-05
I'm looking at the 'Network settings' dialog (8.04LTS, x86_64) and today the 'Unlock' button is grayed out and won't work (normally this only happens when already unlocked, but here everything is read-only). What? Why ?  ?? Nothing appears in /var/log.

Also, what is the best way to get DNS caching set up on this machine? DNSmasq? Tried nscd, didn't seem to work at all.

---

### Post by Iowan on 2009-12-05
I like DNSmasq - especially as DHCP/DNS server.
Is your network working? I could see settings being "unavailable" if there's nothing to configure.

---

### Post by gregsmith_to on 2009-12-06
Network is working OK. lspci says:

```

00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

```

Also, if I select 'network tools', then 'eth0' from the drop box, and push 'configure', it says, 'this interface does not exist'. But that is true, I think, even when the other dialog works. Should there be a /dev/eth0 ? There isn't.

---

### Post by Iowan on 2009-12-06
Check (post) from a terminal: **lshw -C network** That should reveal if the hardware is associated with alias (eth0) and if it has a driver associated.

---

### Post by creat0r on 2009-12-06
gksu gedit /etc/network/interfaces

Replace whatever is there with:

auto lo
iface lo inet loopback

---

### Post by gregsmith_to on 2009-12-07
(1) 
```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:30:1b:bc:45:84
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 duplex=full ip=192.168.1.130 latency=0 link=yes maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:c0:02:20:b5:56
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


```
(the second one is a usb Wifi I don't use)

(2) /etc/network/interfaces currently contains:
```

auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.1.42
netmask 255.255.255.0
gateway 192.168.1.4

auto eth0

```

---

### Post by Iowan on 2009-12-07
Is this a recent occurrance? As **creat0r** hinted, interfaces configured in */etc/network/interfaces* are ignored by Network Manager... although they CAN be configured there. 
To answer the thread title, try the suggestion by **creat0r**. I have some links for setting a static address in Hardy, if required. If the problem is actually internet access, it may be either a gateway or DNS problem. Your gateway is 192.168.1.4? Most routers/modems, etc., use 192.168.X.[COLOR="Red"]1[/COLOR].  */etc/resolv.conf* should contain nameserver addresses.

---

### Post by gregsmith_to on 2009-12-09
Yes, it has been OK in the past, but also has occurred before.

I'll try that suggestion. The router is configured at 192.168.1.4, only because the one I used before it was at 192.168.1.3, etc.

I used to have a static IP on the Hardy machine, but when I got this new 2wire router from the ISP, it was hostile to static addresses - each time an outbound connection came from the machine, it would spend >5 seconds polling the machine to get its host name, and failing (because I think it was using a windows-specific method) before it would let the connection through. When I switched to DHCP it was fine (and since the router also serves local names I didn't need a static IP any more). Right now I'm concerned with trying alternate DNS servers since the sympatico ones have become unreliable. I used the dialog to switch to others, but that only stayed in place for a while ( I suspect until the DHCP lease expired?). Now i'm back to using 192.168.1.4 but I've set the DNS addresses in the router to working ones, that seems fine. But I'd like to be able to change them in this dialog, just to test various DNS servers without having to mess with the router.

---

### Post by Iowan on 2009-12-09
> **gregsmith_to said:**
> (2) /etc/network/interfaces currently contains:
```

auto lo
iface lo inet loopback


iface eth0 inet [COLOR="Red"]dhcp[/COLOR]
[COLOR="Blue"]address 192.168.1.42
netmask 255.255.255.0[/COLOR]
gateway 192.168.1.4

auto eth0

```Looks like a problem here - machine doesn't know whether to get DHCP address or static one...

---

### Post by gregsmith_to on 2009-12-10
Yes, I noticed that. It gets a dynamic one; I assume that the other settings are ignored if dhcp is selected, and are just left over from when it was static (so if I switch back the GUI knows what it was before).

I haven't tried deleting this stuff yet as suggested by creat0r; I'm waiting for when I have time to suffer through reboot cycles. This machine (shuttle SN68PTG6)  has a 'special issue' where often the display fails to detect the monitor at boot time, and ubuntu goes into 'stupid mode' - not only is it VGA resolution but the network interface doesn't work in that mode. Reboots need to be done from power off and *unplugged* for 10 seconds - if I don't actually unplug it there are still lights on inside and the problem tends to occur. I was hoping this would go away when I got a PCIex graphics card to replace the on-board one, but no.

But, when it's up, it works well. Maybe time to look for BIOS upgrades...

---

### Post by Iowan on 2009-12-10
Drifting off-topic a little, but does it have problems if you just restart a service (ie. /etc/init.d/networking restart)?

---

### Post by gregsmith_to on 2010-01-17
OK,  i simplified /etc/network/interfaces as suggested by creat0r. It is now possible to unlock 'network interfaces'.

However, there is still the issue with 'network tools': 
 - dropdown box selects between loopback and eth0
  - select eth0, push configure: 'the interface does not exist' 

(but it does exist and seems to be working fine, other than being inaccessible to the configure tool).

Should there be a /dev/eth0 or a /dev/net/eth0  or something?

---

