---
title: "Trouble with Atheros AR5007/AR242x wireless card"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by yeats on 2008-12-23
Hello -

I'm setting up Ubuntu on my wife's Toshiba Satellite A215 and all is well except for the wireless card.  I have followed the advice from forum threads here and various sites on the Internet.  The latest thing I have done is install [madwifi-0.9.4]("http://madwifi-project.org/wiki/Releases/0.9.4") from source, following the [how-to]("http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo") on their site.  I get to the point where I do the modprobe ath_pci command, but I'm still not able to see my wireless card with an ifconfig.  My posting here is a last resort, as I am one to try all available avenues before asking for advice!

Relevant information:

- I've installed Hardy Heron i386 because I have found problems with 64-bit ubuntu - if this is the problem, please let me know :-)

lspci shows the card:

```
0e:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

iwconfig only shows eth0 and the loopback:

```
$ iwconfig 

lo        no wireless extensions.

eth0      no wireless extensions.


```

lsmod shows the ath modules:

```
$ lsmod | grep ath

ath_pci               100896  0 

wlan                  206960  1 ath_pci

ath_hal               192592  1 ath_pci

```


Any thoughts?  Thanks for your help.

---

