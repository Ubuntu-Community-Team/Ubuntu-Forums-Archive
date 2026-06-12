---
title: "Intel WiFi Link 5100 slow Wireless N connectivity"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by dreamingdarkness on 2009-12-08
I recently noticed that wireless performance on my built-in Intel Wireless WiFi Link 5100 dropped from adequate speeds both over local network (laptop->router) and over internet (laptop->router->speed test sites) down to hideously slow - less than 2mbps. The problem appears to be with using wireless N rather than wireless G. 
Other PCs with wireless have no problem with the N wireless in the house. In fact, to get adequate speeds, I have to put the router in b/g only modes - if wireless N is available it auto-selects and bogs down horribly.

Once I move my new router or my old router to wireless G only, my speeds are consistently at where they should be, internet download-wise. However, this does limit me to 54mbps on the local network, with the typical interference issues wireless G experiences as well. 
Not to mention the work wi-fi, which I don't have the option of changing bands with.

Now the gritty details necessary:

sudo lshw -C network:
```
 *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:85:96:e2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.10.101 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:fdffe000-fdffffff

```

Results from dmesg | grep iwl
```
[   17.430392] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   17.430395] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   17.451335] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.451366] iwlagn 0000:03:00.0: setting latency timer to 64
[   17.451458] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   17.505241] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.505330] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[   17.762943] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   17.772318] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-2.ucode
[   17.808056] iwlagn 0000:03:00.0: lbm-iwlwifi-5000-2.ucode firmware file req failed: -2
[   17.808061] iwlagn 0000:03:00.0: firmware: requesting lbm-iwlwifi-5000-1.ucode
[   17.905834] iwlagn 0000:03:00.0: Loaded firmware lbm-iwlwifi-5000-1.ucode, which is deprecated. Please use API v2 instead.
[   17.905840] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   18.047744] Registered led device: iwl-phy0::radio
[   18.047766] Registered led device: iwl-phy0::assoc
[   18.047781] Registered led device: iwl-phy0::RX
[   18.047796] Registered led device: iwl-phy0::TX
```

Note: When I check /lib/firmware, iwlwifi-5000-2 firmware is present:
```
-rw-r--r--  1 root root 345K 2009-11-10 03:21 iwlwifi-5000-2.ucode
```
so I have no idea why the message "the bm-iwlwifi-5000-2.ucode firmware file req failed: -2" prints.

iwconfig results (when connected to wireless in 'B/G mixed' mode):
```
wlan0     IEEE 802.11abgn  ESSID:"Atheros"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:D1:69:2B:1E   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-24 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
iwconfig results (when connected to wireless in 'N' mode)
```
wlan0     IEEE 802.11abgn  ESSID:"Atheros"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:D1:69:2B:1E   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-23 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

I have noted that the 'Bit Rate' settings are fairly frequently low or incorrect. For 802.11g it seems to be more often correct than 802.11n, however. 

ifconfig (wireless N mode)
```
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:85:96:e2  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe85:96e2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:65895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80796868 (80.7 MB)  TX bytes:23654321 (23.6 MB)

```

ifconfig (wireless b/g mixed mode)
```
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:85:96:e2  
          inet addr:192.168.10.101  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::216:eaff:fe85:96e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:80798994 (80.7 MB)  TX bytes:23660010 (23.6 MB)
```

Any thoughts or help would be greatly appreciated - this wireless N bug is irking, since I'd like to start stream from my main PC to my laptop for VLC to do music, TV shows, etc rather than running constant maintenance cleanups on my laptop to have enough HDD space.

Thank you!

---

### Post by aaron552 on 2010-03-08
I am going to bump this thread, since I also have this problem. My PC is a Dell Studio 15, with a Intel Wifi Link 5100 agn. iwconfig frequently displays 0kbps as the bit rate and transfer speeds max out at around 4kBps.

---

### Post by adam814 on 2010-03-08
Hmm...I have the same card, but as I've never tried to use a Wireless-N network I can't say I've experienced the problem.  As for the bit rate being off you can adjust that with iwconfig.  For example:
```
sudo iwconfig wlan0 rate 54M
``` sets the bit rate to 54Mb/s for me.  Sometimes I lower that when trying to connect from further away from the router.

I would assume the same would be valid with Wireless-N, I'll let you know if I get around to giving it a try.

---

### Post by SDERAWI on 2010-04-14
How exactly do you force the wireless to either "G" or "N" in Ubuntu Karmic Koala 9.10

---

### Post by SDERAWI on 2010-04-14
bump

---

### Post by SanchoActual on 2010-04-16
Hi, all.
I have a 5100 AGN and am wondering about making it work at 'N' speeds. I attempted this:

```
sudo iwconfig wlan0 rate 300M
```
and got
```
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wlan0 ; Invalid argument.
```
same error using 150MB. No error when using '54M'


Here is some relevant info:

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Flags: bus master, fast devsel, latency 0, IRQ 33
        Memory at 9e000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```

```

iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"Porcupine"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:D1:C3:66:D0   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-30 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**[COLOR="Red"]NB[/COLOR]: Bit Rate=0 kb/s**
actual speeds seem fine, but can't tell what they are. WiFi Radar confirms it's running in G. Router is a Trendnet N and is set to use G/N. This same laptop connects at between 150-300 Mbps from Vista.

drivers installed:
```
ls -al /lib/firmware | grep 5000
-rw-r--r--  1 root root   12401 2009-11-30 06:29 dvb-fe-xc5000-1.6.114.fw
-rw-r--r--  1 root root  345008 2009-11-30 06:29 iwlwifi-5000-1.ucode
-rw-r--r--  1 root root  353240 2009-11-30 06:29 iwlwifi-5000-2.ucode
```
any way to tell which is in use? I saw steps to force it to use iwlwifi-5000-2.ucode; basically rename to '1' (after renaming '1' to .orig or whatever, and then restarting a couple things.  see:
[http://swiss.ubuntuforums.org/showpost.php?p=8021867&postcount=13](http://swiss.ubuntuforums.org/showpost.php?p=8021867&postcount=13)

Haven't tried it, since I'm not even sure which is in use or what my speeds are. Good to know, though.


My questions are:
* how can I tell at what speed my 5100 AGN is actually running?
* how to make it use N speeds, if that's even possible?

Guess this is a big ol' bump. And a crazy first post ;-)

Nice to be messing with Linux again. Flove Ubuntu so far.


[EDIT 01]
after some more research someone made a real "DUH!" suggestion: see what your router says about your WiFi connection. My Trendnet tells me my Intel 5100 AGN is connecting in the 'N' range (I saw 240, 162 & 108 ). Perhaps the problem is Ubuntu's inability to correctly detect and report N connections. Or it could be HT (high-throughput) setting, though I just read about that and am not yet sure how to find it.

---

### Post by dkeiller on 2010-04-18
Hi,

I'm a not-new, but non-technical user.

My 5100 (on an Asus B50A laptop) loses the connection every 15-30 seconds.

Here's the output of sudo lshw -C network

  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:9c:03:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.17 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:33 memory:fdffe000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:c6:26:b6:48
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.15 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:30 ioport:d800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 02
       serial: 00:22:15:ee:59:76
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:e800(size=256) memory:fcfff000-fcffffff(prefetchable) memory:fcfe0000-fcfeffff(prefetchable) memory:feaf0000-feafffff(prefetchable)

---

### Post by davavanstone on 2010-05-22
did anyone get anywhere with n speeds? I forced my router (wrt320n) to use n only, my laptop connects fine but still 54M connection??

---

### Post by chx1975 on 2010-05-24
It seems like there are a mix of issues in this thread. For the 54M issue, I filed [https://bugs.launchpad.net/bugs/584902](https://bugs.launchpad.net/bugs/584902) . Please help me making that issue complete. Those facing slowness and / or drops please file separate issues. Developers won't see your problem in the forum.

---

### Post by the.dude on 2010-09-10
EDIT:  Of course - about 1/2 hr into using this setup it went bad.  Switched back to G-Mode for now...

----------------------------------------------------------------------

Had the same issue - when using N-mode with and intel 5100 card wireless was practically unusable.

I originally just disabled N-mode by adding the options
```
11n_disable=1 11n_disable50=1
```
to the driver.  This allowed for great G-mode connections - SCP on an ISO was running around 2 megabytes/sec.

But since I had just purchased a new wifi card specifically for N-mode connections I wasn't satisfied with that so I kept poking around...

I believe I now have a fix for it -- The following driver options seem to be working quite well.  These options disable the hardware encryption and uses software instead.  So far there's not much of a CPU load hit.
```
11n_disable=0 11n_disable50=0 swcrypto=1 swcrypto50=1
```

To set this up do the following:

```
# sudo -s "echo 'options iwlagn 11n_disable=0 11n_disable50=0 swcrypto=1 swcrypto50=1' >> /etc/modprobe.d/options.conf"
# sudo modprobe -r iwlagn && sudo modprobe iwlagn
```

After driver was reloaded and connection re-established my SCP of the same ISO was now running at 5 megabytes/sec (2 fold increase).

---

### Post by repatch on 2010-12-17
That worked perfectly, thanks! Now getting n speeds on Linux!

---

### Post by bmosov01 on 2011-01-12
Just tried both of the.dude's suggestions.  I too thought that using the final suggestion had fixed the problem, but similarly to his experience, after about a half hour of browsing the slowness came back.  As far as I can tell, disabling n-mode as per the.dude's first suggestion is working fine.  It is a shame not to have the n speeds, but after months of having slow/no wireless at home, I'm just happy to be able to connect.  Thanks for the workaround!

---

