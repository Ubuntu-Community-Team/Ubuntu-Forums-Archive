---
title: "Wireless Issue &amp; Stumped"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by calivan_mol on 2011-04-30
Ok, just to let those reviewing this know. I have spent hours on the web reviewing suggestions on how to activate and get wireless running on Ubuntu 11.04 32-bit. But now it has boiled down to frustration and just running out of options.

I'm trying to get STA running on a Dell Vostro 1000. I have read the post "[SOLVED] THE beginners solution for fixing up Broadcom BCM43xx and Wireless Cards" pinned to this form, but none of the suggestions are assisting.

Card is confirmed as a 4311 2.4 Ghz
```
# lspci -n | grep 14e4
05:00.0 0280: 14e4:4311 (rev 01)
08:00.0 0200: 14e4:170c (rev 02)

```

When I check Ubuntu's "Additional Drivers" app, I see "Broadcom STA wires driver" as activated and currently in use.

When I look at my network settings ifconfig returns the follow.

```
# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0c:00:a1:23:9f  
          inet addr:192.168.254.2  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fea6:239f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2678 (2.6 KB)  TX bytes:9086 (9.0 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

```

In addition I have check rfkill, everything looks fine there. I do have to unblock a hard block after each reboot though.

```
# rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

Also I have reviewed the lswh information, nothing odd here that I can see.

```

# sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:c0200000-c0203fff

```

All the suggestions I have read on this forum will get me to were it looks like STA is running, but no further. wlan0 never appears on ifconfig -a.

Anyone see something that I missing or need to enable?

Thanks!

**Solution**
Installed Ubuntu 10.10 STA drivers from:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

---

### Post by ChrisGaeth on 2011-04-30
I can confirm this. I am having the exact same issue on the same hardware. Any assistance would e greatly appreciated.

---

### Post by calivan_mol on 2011-05-01
I added my lshw information as well, still no real indication as to why this is failing. Also I confirmed that ssb is blacklisted under /etc/modprobe.d/blacklist-bcm43.conf file.

---

### Post by Dittie on 2011-05-01
Having the same issue with an Acer using broadcom's 4357 wireless.

---

### Post by calivan_mol on 2011-05-02
Alright! Good news, I found a work around. It looks like the STA drivers are bugged for Ubuntu 11.04. The good news is that you can install Ubuntu 10.10 drivers to resolve the issue.

I downloaded the 10.10 drivers from:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

Then installed using the deb package. I'm sure there are better approaches, but this worked well for me.

I ran "ifconfig -a" and found my wireless card listed as eth1. Then ran "sudo iwlist scan" to confirm if the card could see any networks. Success!

---

