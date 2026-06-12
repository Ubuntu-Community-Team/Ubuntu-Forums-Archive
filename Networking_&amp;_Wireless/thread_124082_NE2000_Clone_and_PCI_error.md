---
title: "NE2000 Clone and PCI error"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by Ike Fant on 2006-01-31
Hi,
yesterday i installed Ubuntu from the Installation CD (ubuntu-5.10-install-i386.iso) on an older machine i have, the network card was pluged in, but not connected. Everything works alright, except i can't connect to the net.

I found some advice [here](http://ubuntuforums.org/showthread.php?t=67258) and [here](http://ubuntuforums.org/showthread.php?t=87643), but couldn't work out a sollution.

Some stuff I tried: ```
 lspci | grep -i eth
0000:00:0c.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8029(AS) 
``` so the card has been detected.

but then things aren't as they should be: ```
 sudo ethtool eth0
Settings for eth0:
Cannot get device setting: device not found
Cannot get wake-on-lan settings: device not found
Cannot get message level: device not found
Cannot get link status: device not found
No data available 

```

```
ifconfig eth0
``` also states that the device is not found

So I checked this:
```
lsmod | grep ne2
ne2k_pci   10464   0
8390       9088    1   ne2k_pci

```

I suppose this means, that the driver is there.

Here is the error when I check for the card with dmesg
```
dmesg | grep ne2k
ne2k-pci.c:v1.03 09/22/2003 D. Becker/P. Gortmaker
  http://www.scyld.com/network/ne2k-pci.html
ne2k-pci: I/O resource 0x20 @ 0xde00 busy 
ne2k-pci: probe of 0000:00:0c.0 failed with error -16

```
but i don't know what that means. Can anyone help me out with this?

Thanks,
Ike Fant

---

