---
title: "BCM94321MC Broadcom 4321 BCM4321 5 GHz on kernel 3.2.0"
date: 2012-02-11
forum: Networking &amp; Wireless
---

### Post by alfonso78 on 2012-02-11
Hi,

I just bought a mini-PCI express BCM94321MC card.

Ubuntu 11.10 recognized is as a 802.11a/b/g/n card:

```
# lspci -vnn |grep 14e4
01:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)

```

```
# lshw -C network
  *-network
       description: Wireless interface
       product: BCM4321 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: 03
       serial: 00:1f:5b:b7:ce:f5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 ip=192.168.100.168 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:fe600000-fe603fff memory:d0100000-d01fffff

```

Linux by default used the b43 driver:

```
$ lsmod | grep 43
b43                   324292  0
bcma                   25554  1 b43
mac80211              432604  4 b43,rt2800lib,rt2x00pci,rt2x00lib
cfg80211              174734  3 b43,rt2x00lib,mac80211
ssb                    49883  1 b43

```

but I couldn't see the wireless interface in my computer:

```
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:01:2e:36:c1:90
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:273 errors:0 dropped:0 overruns:0 frame:0
          TX packets:211 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:30280 (30.2 KB)  TX bytes:26777 (26.7 KB)
          Interrupt:45 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5066 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:348884 (348.8 KB)  TX bytes:348884 (348.8 KB)

```

```
$ iwconfig
wlan2     IEEE 802.11bg  ESSID:off/any
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

lo        no wireless extensions.

eth1      no wireless extensions.

```

```
$ sudo ifconfig wlan2 up
SIOCSIFFLAGS: No such file or directory

```

after a short research I realized I missed the firmware:

```
$ apt-get install firmware-b43-installer
```

This did the trick...

```
$ sudo ifconfig wlan2 up
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:01:2e:36:c1:90
          inet addr:192.168.100.100  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1185 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1767077 (1.7 MB)  TX bytes:128431 (128.4 KB)
          Interrupt:45 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:628980 (628.9 KB)  TX bytes:628980 (628.9 KB)

wlan2     Link encap:Ethernet  HWaddr 00:1f:5b:b7:ce:f5
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

but "iw list" revealed only 2.4 GHz channels were available and my AP is set to function at 5 GHz to avoid the noise of tens of WiFi APs I have around my flat.

Checking this file: [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
I was sure my card was 2.4 and 5GHz capable (i.e. Dualband)

```
	   BRCM		    PCI		  PCI		  Dell
	  Product Name	  Vendor ID	Device ID	Product ID
          -------------	 ----------	---------   	-----------
          4321 **Dualband**	    0x14e4	0x**4328**  	Dell 1505
          4321 **Dualband**	    0x14e4	0x**4328**  	Dell 1500
          4321 2.4 Ghz	    0x14e4	0x4329  	
          4321 5 Ghz        0x14e4	0x432a  	

```

```
# lspci -n | grep 14e4
01:00.0 0280: 14e4:**4328** (rev 03)
```

Looking here:
[http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices](http://wireless.kernel.org/en/users/Drivers/b43#Supported_devices)

I realized the b43 does not yet support 5GHz for my card.
See [http://wireless.kernel.org/en/users/Drivers/b43#Not_working_yet](http://wireless.kernel.org/en/users/Drivers/b43#Not_working_yet) : **5GHz for N-PHY cards**. This is important, cause maybe when you read this, the support will be there and this little howto will be useless!

So I tried to install the STA drivers from here:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

when I tried to compile I got an error:

```
wl_linux.c:388:2: error: unknown field ândo_set_multicast_listâ specified in initializer
```

so I tried to install a ready-made package:

```
sudo apt-get install bcmwl-kernel-source
```

Sure enough, it didn't work:

```
Error! Bad return status for module build on kernel: 3.2.0-interlaced2+ (i686)
Consult /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log for more information.

```

and inside /var/lib/dkms/bcmwl/5.100.82.38+bdcom/build/make.log the same error:

```
wl_linux.c:332:2: error: unknown field ândo_set_multicast_listâ specified in initializer
```

So I found this: [http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/](http://www.mindwerks.net/2011/11/wireless-bcm4312-3-2-kernel/) with a patch:

```
332c332
<       .ndo_set_multicast_list = wl_set_multicast_list,
---
>       .ndo_set_rx_mode = wl_set_multicast_list,

```

patch -p0 src/wl/sys/wl_linux.c < (name you gave to the file)

so I managed to compile the driver. Then I simply installed it following instructions at [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt) :

```
# lsmod  | grep "b43\|ssb\|bcma\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod bcma
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
```

And here I am, with a BCM4321 connected on a 5 GHz AP having very fast performances.
Next step: I will change AP to go from 802.11a to 802.11n to get much higher speed.

---

### Post by alfonso78 on 2012-03-07
For some reason after the latest updates my wireless driver didn't load anymore.

I simply had to run

```
sudo depmod -a
```

to solve the problem

---

