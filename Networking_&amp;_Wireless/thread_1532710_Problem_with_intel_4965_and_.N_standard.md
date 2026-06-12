---
title: "Problem with intel 4965 and .N standard"
date: 2010-07-16
forum: Networking &amp; Wireless
---

### Post by extasy on 2010-07-16
I have a Intel 4965 card with .N standard. however I can't connect to my router with N standard.  have tried a Belkin N Vison and a Linksys 160 NL. When the N only mode i choosen it will not connect. It will however connect in G standard. I'm on a 64 bit system.

sudo iwconfig
[sudo] password for henrik: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"Linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:A3:AE:74   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:a9:6d:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.120 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4000000-f4001fff

Any Idea?

Henrik

---

### Post by extasy on 2010-07-22
No one has an idea?

---

### Post by Max-P on 2010-07-31
Hi,

I'm having the same problem as you. Running Ubuntu Lucid 64 Bits, fresh install.

Exact same outputs and problems,  except my MAC address and my SSID, of course!

```


max-p@max-p-laptop:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 61
       serial: 00:21:5c:06:9c:4f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.100 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f4000000-f4001fff

```

```


wlan0     IEEE 802.11abgn  ESSID:"Max-P"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1E:58:06:02:5D   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Asked on French forums, someone else have the same problem too.

---

### Post by pedro.nariyoshi on 2011-01-16
Check your /etc/modprobe.d/ folder,
you probably have a intel-5300-iwlagn-disable11n.conf file.

Rename it (as root) to intel-53...conf.bak or just delete it.
Then reload the iwlagn module. (Or reboot)


I heard this driver causes trouble, i keep it disabled just in case:
[(https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748)]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/630748")

---

### Post by Max-P on 2011-01-17
Thanks pedro.nariyoshi for your answer, but this topic was kind of outdated. This file is new to Maverick but I had this bug on Lucid. It was fixed meanwhile and I didn't upgrade to Maverick yet just because of this bug. It started to work again on an upgrade I can't remember when. And I can tell it works perfectly on my computer.

Still can be usefull for Maverick users though!

---

### Post by pedro.nariyoshi on 2011-01-18
You are right, I'm sorry.

I figured this problem recently when I upgraded my router. And I ended up sharing even when not necessary... -,-

How did you solve the problem? Did you recompile the driver/kernel?

---

### Post by Max-P on 2011-01-18
No problem ;)

As I said, it just fixed by itself after some package upgrades, new kernel I think, something like that. I had G speeds then after a reboot after an upgrade, I downloaded something and noticed the speed increased. I checked the speed reported by network manager, and I saw a nice 130 MBps, so I was happy.

It's ok to have shared it, at least Maverick users getting on this topic will have the solution.

---

