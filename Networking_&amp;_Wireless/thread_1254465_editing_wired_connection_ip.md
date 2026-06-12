---
title: "editing wired connection ip"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by ab_dev on 2009-08-31
When going into the system->prefs->network conns, all i see is the 'auto eth0' under wired and the edit button is disabled.

I set a static ip on setup and haven't been able to change it since.

details below:

```

$ uname -a
Linux cseven-backups 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

$ lspci -nn | grep 'Ethernet'
00:12.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6102 [Rhine-II] [1106:3065] (rev 78)

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:f2:63:40:86  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:f2ff:fe63:4086/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2515214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1280599 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3583883684 (3.5 GB)  TX bytes:92890274 (92.8 MB)
          Interrupt:23 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:30795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30795 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3346383 (3.3 MB)  TX bytes:3346383 (3.3 MB)

```

---

### Post by x33a on 2009-08-31
add this to your /etc/network/interfaces file
```
auto eth0

iface eth0 inet static

address xxx.xxx.xxx.xxx
netmask xxx.xxx.xxx.xxx
gateway xxx.xxx.xxx.xxx
```

replace the xs with your desired ip addresses.

---

### Post by ktritty on 2009-08-31
I need to manually specify the two DNS servers on one of my workstations at my office.  It runs "regular" Ubuntu 9.04.    How do I do that?  Is that done in interfaces as well, or in some other place?

Thanks!

---

### Post by Iowan on 2009-08-31
I've seen a post with a dns-server line in */etc/network/interfaces*, but dunno if it should be there. Does that machine also have static address - or is it DHCP? If DHCP, you should be able to use the "prepend" line in */etc/dhcp3/dhclient.conf*.

> **ab_dev said:**
> When going into the system->prefs->network conns, all i see is the 'auto eth0' under wired and the edit button is disabled.

I set a static ip on setup and haven't been able to change it since.Right-click on the Network Manager Icon near clock in upper right corner. My laptop has an (active) "Edit connections" option there - whereas the System>Preferences>Network connections edit feature is grayed.

I just (re)discovered that if I click on **auto eth0**  under System>Preferences>Network connections, it "un-grays" the edit option.  Hope this helps...

---

### Post by x33a on 2009-09-01
> **ktritty said:**
> I need to manually specify the two DNS servers on one of my workstations at my office.  It runs "regular" Ubuntu 9.04.    How do I do that?  Is that done in interfaces as well, or in some other place?

Thanks!

if you have static ip, put the dns entries in /etc/resolv.conf in the format
```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```

for dhcp, follow iowan's instructions.

---

### Post by ktritty on 2009-09-01
> **x33a said:**
> if you have static ip, put the dns entries in /etc/resolv.conf in the format
```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```


Thanks!

This worked perfectly. Somehow, the web browsing worked for a week or so after I switched from dhcp to static without this entry.  Now, all is well again.

---

### Post by ab_dev on 2009-09-02
when i click auto eth0 it doesn't un-gray ... strange

&

when i add the static info to the interfaces file, it didn't work out or show the eth0 in network prefs

[I][B]
Edit >>  This all may have something to do with the 'available to all users' checkbox in the network prefs... what's up with that option ![/B][/I]

---

