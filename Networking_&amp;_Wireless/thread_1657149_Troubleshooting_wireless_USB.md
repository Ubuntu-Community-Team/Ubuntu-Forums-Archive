---
title: "Troubleshooting wireless USB"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by faqwad on 2010-12-31
I'm running 10.04 with a wireless USB dongle. Everything - network wise - worked fine until about two weeks ago. Now the wireless connection drops out, sometimes every hour or so, sometimes more frequently. The only way I've found to reestablish the link is to unplug and reconnect the USB dongle. I also have XP installed on the same machine, and this works fine, so I'm guessing that it's not a hardware problem. 

Could someone give me an idea of how to work out what's going on here?

---

### Post by PatchesTheCaveman on 2010-12-31
Hi faqwad!  Sorry you're having trouble with your wireless connection.

To try and see what's going on, we need to collect some information.  Go to Applications > Accessories > Terminal on your top panel, type the following in the black box that appears, and press Enter:
```
sudo lshw -C network
```

Then, copy what appears and paste it into a reply to this thread.

Next, type this and press Enter:
```
ifconfig -a
```
and copy/paste that too.

Then, type in this command and press Enter:
```
sudo iwconfig
```
It will ask you for your password.  Type it in, press Enter, and then copy what appears and paste in your reply.

Finally, type this and press Enter:
```
uname -r
```
and copy/paste the one line that outputs.

With all that, we should be able to figure out what's going on.

---

### Post by faqwad on 2011-01-01
Thanks Patches! Here's that output:  

*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: e0:cb:4e:bb:26:07
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:35 ioport:d800(size=256) memory:fafff000-faffffff(prefetchable) memory:faff8000-faffbfff(prefetchable) memory:fbee0000-fbeeffff(prefetchable)
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:27:19:f1:8a:b1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.65 multicast=yes wireless=IEEE 802.11bg

 ifconfig -a
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:bb:26:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:228 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22569 (22.5 KB)  TX bytes:22569 (22.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:27:19:f1:8a:b1  
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::227:19ff:fef1:8ab1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:828515 (828.5 KB)  TX bytes:283142 (283.1 KB)

lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"priDe"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:24:17:3B:2F:75   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

2.6.32-22-generic

---

### Post by PatchesTheCaveman on 2011-01-01
Try running this from the terminal:
```
sudo iwconfig wlan0 rate 54M
```

---

### Post by faqwad on 2011-01-01
Tried that. It doesn't seem to generate any output - just sits running until I manually kill it.

---

### Post by PatchesTheCaveman on 2011-01-01
That's odd.  It should prompt you for your password.  Once you enter that and press Enter, it should change your wireless configuration and drop you right back at the shell prompt.

Run ```
sudo iwconfig
``` and copy/paste the output so we can see if the changes took effect.

---

