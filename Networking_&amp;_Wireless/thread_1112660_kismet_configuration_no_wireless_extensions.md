---
title: "kismet configuration: no wireless extensions"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by lostbuthappy on 2009-03-31
Hi guys,

I recently decided that my lacking knowledge of networks and what makes them tick is no longer admissible and therefore chose the practical/exciting approach to get started: kismet.

After reading /usr/share/doc/kismet/README.gz I tried to set up /etc/kismet/kismet.conf properly but eventually failed because I don't know which interface to use (nor do I *really* know what an interface actually is). I tried to determine the correct interface with iwconfig, but it says that there're no wireless extensions available for any of the interfaces. I can't test wlan right know since there's no public access available but NetworkManager shows two ap's in the my vicinity and therefore I assume that wlan generally works.

I took a wild guess and specified the interface as eth0, but kismet failed setting up monitor mode. My broadcom bcm4312 internal wnic is supported by kismet (according to README.gz). Out of curiosity I installed the proprietary driver but quickly changed back to what I assume to be bcm43xx.

I really don't know how to pick the right interface, if missing info from iwconfig is indacating a problem or not and if so what to do to solve it, so please forgive me for simply dumping some data and begging for help *beg*.

System:
HP 6735s notebook, Ubuntu 8.10 recently installed w/o aimlessly changed system settings (yet) 

```
dominik@auntlizzy:~$ sudo lspci -v
[...]
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
	Subsystem: Hewlett-Packard Company Device 137d
	Flags: bus master, fast devsel, latency 0, IRQ 5
	Memory at 92000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 21-00-9a-ff-ff-00-31-f7
	Capabilities: [16c] Power Budgeting <?>
	Kernel modules: wl

```

```
dominik@auntlizzy:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```

```
dominik@auntlizzy:~$ sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.
ppp0      no wireless extensions.
```

```
dominik@auntlizzy:~$ cat /etc/kismet/kismet.conf | grep -i ^source=
source=bcm43xx,eth0,BCM4312
```

I hope you can help me out. Thanks in advance,
Dominik

---

### Post by freonchill on 2009-04-01
did you run the kismet via sudo?

---

### Post by lostbuthappy on 2009-04-01
> **freonchill said:**
> did you run the kismet via sudo?
Of course I did.


Edit:
I tried the proprietary driver once more (called "Broadcom STA wireless driver"). The installation process added a new interface eth1:
```
dominik@auntlizzy:~/.nautilus/metafiles$ sudo iwconfig
[...]
eth1      IEEE 802.11bg  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Kismet however was still not willing to work and so I changed the driver once more. The new interface is still there (propably because I did not restart the networking system?) and kismet is still pis... uncooperative. Here is what it says:

```
dominik@auntlizzy:~/.nautilus/metafiles$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (BCM4312): Enabling monitor mode for bcm43xx source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
Done.

```
Does that simply mean that my wnic does not support monitor mode or is there a less final explanation?

---

### Post by saswatnits on 2009-05-09
Even I have the exact same issue. I will be thankful if anyone gives a solution.. Thanks.

---

### Post by Desolator64 on 2009-05-09
I am having a similar problem. I use a rtl8187b network adapter in my laptop and can't get Kismet to work. I think the problem is that most drivers that the companies who make these adapters write don't have monitor mode enabled for legal reasons. You would therefor need to get a cracked driver instead. That's my theory anyway. I can't get a driver for my card that has monitor mode enabled because it's a crappy USB adapter that Toshiba lazily soldered on to their motherboards and sold in mass quantities without any support.

Anyways, good luck to you and I hope I get an answer too.

---

### Post by chili555 on 2009-05-10
> I tried the proprietary driver once more (called "Broadcom STA wireless driver"). The installation process added a new interface eth1:> source=bcm43xx,eth0,BCM4312You need to determine what the driver is matching your wireless interface with:```
sudo lshw -C network
```It will display information about both your wired and wireless devices, but you need the driver= data from your wireless. Then, amend kismet.conf to match. Please confirm, but it ***may*** be:```
source=b43,eth1,Broadcom
```Substitute your findings here.

---

### Post by mikebruns99 on 2009-05-15
Here's mine, Vostro 1500 running Ubuntu 9.04 with a fresh install.

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial:  (removed) 
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.79.10 ip=192.168.1.139 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

---

### Post by mikebruns99 on 2009-05-15
I last used kismet w/ ubuntu a year or two ago on this laptop.  I remember having to use fwcutter.  It looks like Jaunty included the binary driver in the new version.  I'll give backtrack a try.

---

