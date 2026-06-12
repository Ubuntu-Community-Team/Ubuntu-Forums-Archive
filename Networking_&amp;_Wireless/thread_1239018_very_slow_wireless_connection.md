---
title: "very slow wireless connection"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by arp on 2009-08-13
Hi,

I just installed Ubuntu Jaunty 9.04 on my new laptop and the wireless connection is super slow. I ran a comparison with my old laptop (through a online speed test service) and it is 5x slower!!! (Connecting through the same wireless router and broadband connection!) From iwconfig the "link quality" is 100%.

Any suggestions on how to fix this are very welcome.

Here are the details of my system:

HP EliteBook 2530p

[lshw -C network ]
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: ##########
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.11 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

[lspci -v]
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
        Subsystem: Intel Corporation Device 1211
        Flags: bus master, fast devsel, latency 0, IRQ 2298
        Memory at 94600000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: [c8] Power Management version 3
        Capabilities: [d0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
        Capabilities: [e0] Express Endpoint, MSI 00
        Capabilities: [100] Advanced Error Reporting <?>
        Capabilities: [140] Device Serial Number ########
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn

---

### Post by Crispian Troy on 2009-08-13
The problem is there are no drivers for that card for vista.. Right now you have a generic driver that only enables lower speeds. It looks like you have an atheros chipset card, and they are fairly good at updating their drivers.. Wait a bit and one should come out.

---

### Post by RavanH on 2009-08-13
Does entering the command ```
sudo iwconfig wlan0 rate 54M
``` in a Terminal window change things (you might need to disconnect/reconnect to your access point after the command)?

---

### Post by arp on 2009-08-13
Actually, my wireless router is quite old and the maximum it supports is 11Mb/s, so I doubt that setting the interface speed to 54Mb/s will help. From iwconfig the interface is supposedly working at 11Mb/s, but from the online speed test I got at most 0.2Mb/s!!!

---

### Post by superprash2003 on 2009-08-14
you could try disabling ipv6 [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4) also post output of 
1)iwconfig
2)ifconfig

---

### Post by AmerNewbieInDE on 2009-08-14
seing you also have the intel 5100 try..

sudo modprobe -r iwlagn

sudo modprobe iwlagn 11n_disable=1 11n_disable50=1

i ended up haveing to run that everytime i reloaded, but then i found another link about upgrading the kernel, i now run rc2.6.31 and have no problem

see... [http://ubuntuforums.org/showpost.php?p=7415234&postcount=3](http://ubuntuforums.org/showpost.php?p=7415234&postcount=3)

---

