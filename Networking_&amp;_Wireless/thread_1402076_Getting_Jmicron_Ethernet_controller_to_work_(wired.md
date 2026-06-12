---
title: "Getting Jmicron Ethernet controller to work (wired networking)"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by thisone on 2010-02-08
I just bought a new ASUS laptop with a Jmicron Ethernet Controller and an Atheros wireless network adapter.

I installed Ubuntu 9.10 and got wireless networking working right away. However, wired networking did not work.

```

$ ethtool -i eth0
driver: jme
version: 1.0.4

```

Specs:
```

$ lspci | grep Eth
05:00.5 Ethernet controller: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller (rev 03)

lspci | grep Wir
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```After some research and testing I found a solution (there are some other solutions around, but none of them worked for me).

Download the native drivers from Jmicron's website. The link from Jmicron's website doesn't work as I type this, but I found the correct path after lurking around: [ftp://jmicron.com.tw/jmc2xx/Linux/](ftp://jmicron.com.tw/jmc2xx/Linux/)

There you'll find a readme.txt and the driver.

You may follow the readme or do as I did:

```
[FONT=monospace]
(Download the driver)
$ [/FONT]tar xjvf jme-1.0.5.tbz2
$ cd jme-1.0.5
$ make install
(I ignored the one warning)
$ rmmod jme
$ modprobe jme

```I disabled networking in NetworkManager (right-click the icon -> uncheck "Enable Networking") before I enabled it again.

```

$ ethtool -i eth0
 driver: jme
 version: **1.0.5**
 
```

And it finally works!

---

