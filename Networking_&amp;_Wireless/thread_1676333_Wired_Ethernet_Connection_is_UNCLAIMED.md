---
title: "Wired Ethernet Connection is UNCLAIMED"
date: 2011-01-27
forum: Networking &amp; Wireless
---

### Post by WthIteh on 2011-01-27
On a Lenovo laptop (Ideapad Z360), my wired Ethernet Network Card does not work, while my wireless connection is completely OK. The wired connection was completely OK too but I didn't use it for a long time. There was a lot of changes (install/remove/update) till now and I just test my wired connection recently and detect that it does not work anymore! So I do not know which change is cause of this problem, but it is a supported card for sure, since it works few month ago.
Here is output of *ifconfig*
```

lo        Link encap:Local Loopback  
          inet addr:XXXXXXXXXXXXXX  Mask:255.0.0.0
          inet6 addr: XXXXXXXXXXXX Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr XXXXXXXXXXXXXXXX
          inet addr:XXXXXXXXXX  Bcast:XXXXXXXXX  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXXXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1796 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1785551 (1.7 MB)  TX bytes:448328 (448.3 KB)

```And there is no sign of *eth0* there. And this is output of *ifconfig eth0 up*
```
eth0: ERROR while getting interface flags: No such device
```And content of */etc/network/interfaces* file:
```

auto lo
iface lo inet loopback

```When listing details of this network card with *sudo lshw -C Network*
```

 *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:08:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:3000(size=128)

```it said that network card is UNCLAIMED which probably means I missed the driver somehow!
I checked relevant part of *lspci* for this device and it said:
```

08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Lenovo Device 3965
    Flags: fast devsel, IRQ 16
    Memory at f0400000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 3000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data
    Capabilities: [100] Advanced Error Reporting
    Capabilities: [180] Device Serial Number XXXXXXXXXXXXXXXXXXX
    Kernel modules: atl1c

```It seems that I need *atl1c* kernel module for this card and here is
output of *lsmod | grep atl1c* command:
```
atl1c                  34955  0 
```which seems to be loaded.
I searched a lot of pages but unfortunately could not find any applicable solution.

Any idea?

---

### Post by dineshs on 2011-01-27
Have you seen this
[http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)
[http://ubuntuforums.org/showpost.php?p=10013704&postcount=5](http://ubuntuforums.org/showpost.php?p=10013704&postcount=5)

---

### Post by WthIteh on 2011-01-27
> **dineshs said:**
> Have you seen this
[http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490)
[http://ubuntuforums.org/showpost.php?p=10013704&postcount=5](http://ubuntuforums.org/showpost.php?p=10013704&postcount=5)
I followed first link ([http://ubuntuforums.org/showthread.php?p=9449490](http://ubuntuforums.org/showthread.php?p=9449490))
and download driver from [http://linuxwireless.org/download/compat-wireless-2.6](http://linuxwireless.org/download/compat-wireless-2.6)
and then extract, make, install it, reboot and did a *sudo modprobe atl1c* but
the network card was still UNCLAIMED.

In the second link ([http://ubuntuforums.org/showpost.php?p=10013704&postcount=5](http://ubuntuforums.org/showpost.php?p=10013704&postcount=5))
it speaks about AR81Family but my card is AR8152 v1.1 Fast Ethernet. Should I install it too? If yes, should I remove the driver which was installed from first link before trying the second link?

And thanks for your help.

---

### Post by dineshs on 2011-01-28
AR8152 v1.1 Fast Ethernet is AR81 family.Let us see what happens when you try the second driver

---

### Post by WthIteh on 2011-01-29
> **dineshs said:**
> AR8152 v1.1 Fast Ethernet is AR81 family.Let us see what happens when you try the second driver
I tried to install the second driver, but it failed with following error while doing "make":
```
Makefile:105: *** Linux kernel source not configured - missing autoconf.h.  Stop.
```
Linux source/headers is installed, but I don't know about "not configured".
How could I fix it?

---

### Post by WthIteh on 2011-02-01
I had switched to my previous kernel version, since my latest kernel was patched by the atheros driver and was somehow unstable. Today when I checked it again (*lshw*) I see that eth0 is detected!! I do not know what happened, since I'm using an old kernel. However the wired connection works now! (unknown solution!)\
Thanks all.

---

### Post by WthIteh on 2011-02-02
:confused: It's very confusing.
After some hours, when eth0 was detected there but I was using wireless, TCP stack start preventing connection to some websites (almost all the tried sites!! else of google and ubuntuforums) by sending RST to them.
Checking packets by wireshark:
  Me:  SYN packet to Site
  Site: SYN-ACK to Me
  Me:  RST packet to Site
but there was no difference in flags of SYN-ACK packet for blocked sites and others (like google which in third message I sent it ACK and connection established without problem).
When Internet disabled I leave it for a while. Restarting computer and/or restarting network module did not fix it too.
Today checking it again, the mysterious RST problem was resolved!! and eth0 were not there again :confused:
I could not figure out how eth0 goes there and how it was removed again.
When eth0 was there I checked lshw -C Network and its driver (atl1c) was loaded and in use (detected by lspci).

Any idea about what is going on this Ubuntu box?
Could RST and eth0 problems be related in anyway?

---

### Post by WthIteh on 2011-02-06
I still get time to time (random) reset packets which are generated by my own machine.
They are like:
time ---------- packet
0 ------------- Me: SYN
200 ms ------ Server: SYN ACK
200.1 ms --- Me: RST
So I'm sure that my box is sending reset packets. This occur at random times for most of sites and make Internet unavailable.

Any Idea?

---

