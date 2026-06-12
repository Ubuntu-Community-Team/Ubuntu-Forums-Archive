---
title: "No LAN after server install"
date: 2010-05-22
forum: Networking &amp; Wireless
---

### Post by batpuncher on 2010-05-22
Hi all, while installing Lucid server i386, the interface works fine (time server connection, downloading additional packages etc) but after the reset the adapter does not connect to the network.

ifconfig returns the correct (static ip) details and I can ifconfig eth0 down/up but the link lights on the card and switch are not on.
I can successfully ping the servers ip and host name, but anything else returns "Destination Host Unreachable"

Also found a thread in these forums by someone with the same problem that I was going to tack this on the end of, but couldn't find it again.  In that one the person solved his issue with adding the noapic command in the grub config, but that doesn't work with me unfortunately.

Hope someone can help, Tim.

---

### Post by Iowan on 2010-05-22
I kinda/sorta remember a similar thread - one that turned off apic AND acpi.

Are you pinging from the server or another machine? Can the server ping other machines (name or IP address?) "Unreachable" could be a routing problem - what are results of **route -n**

---

### Post by albinootje on 2010-05-22
> **batpuncher said:**
> 
I can successfully ping the servers ip and host name, but anything else returns "Destination Host Unreachable"

Please post the output of :
```
lspci
```

---

### Post by batpuncher on 2010-05-22
Iowan: sounds like the thread, I have set acpi=off and noapic in grub already, but not working.  The server can ping itself, but not the switch or further and nothing can ping the server.
route -n produces
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         10.0.0.2        0.0.0.0         UG    100    0        0 eth0
```

server ip is 10.0.0.4 in case I'm missing something.

But if it was just a route/ufw/other problem, wouldn't the link and activity LEDs be doing something?

albinootje: here's the lspci output
```
00:00.0 Host bridge: VIA Technologies, Inc. VT8501 [Apollo MVP4] (rev 04)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8501 [Apollo MVP4 AGP]
00:06.0 Communication controller: Agere Systems LT WinModem
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 19)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 0a)
00:07.4 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 20)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ6832/6833 CardBus Controller (rev 34)
00:0a.1 CardBus bridge: O2 Micro, Inc. OZ6832/6833 CardBus Controller (rev 34)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade/i7d (rev 5d)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

---

### Post by Iowan on 2010-05-22
Link/activity lights can be turned off if the card is software disabled... but if it's showing configuration via **ifconfig -a**, then one must assume it's active. I presume 10.0.0.2 is the router and other machines are in the 10.0.0.X subnet?

---

### Post by batpuncher on 2010-05-22
Yep, that's correct, I've had this computer setup as a mail server before (what I'm trying to do now) with Ubuntu, but that hard drive failed and when I tried reinstalling, I do remember having this problem with an older version (7-8ish I think) so I don't think it's a specific Lucid problem.  But then it comes down to the fact that the interface worked during install, but not after.  Pretty stumped right now.

---

### Post by tgalati4 on 2010-05-22
Shutdown the computer and pull the power cord for 10 min.  It's possible that the card tuners are scrambled and need a cold boot.

---

### Post by albinootje on 2010-05-23
> **batpuncher said:**
> 
```

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```

Hmm. Weird that the leds don't show anything, but you do have ifconfig output for the NIC.

Can you look at the following urls and see whether that might help ?

[http://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue](http://wiki.archlinux.org/index.php/Configuring_Network#Realtek_no_link_.2F_WOL_issue)

[http://wiki.archlinux.org/index.php/Wake-on-LAN#Ensure_that_Wake-on-LAN_is_enabled_and_survives_a_reboot](http://wiki.archlinux.org/index.php/Wake-on-LAN#Ensure_that_Wake-on-LAN_is_enabled_and_survives_a_reboot)

---

