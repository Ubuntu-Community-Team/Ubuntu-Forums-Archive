---
title: "please help with the wireless connection"
date: 2009-06-22
forum: Networking &amp; Wireless
---

### Post by monkey186 on 2009-06-22
Hello, i normaly use xubuntu where my wireless works fine out of box, but i've just installed debian lenny stable to have a go and can't seem to make wireless work.

It seems that it is recognised by the system?

```
~$ gksu iwconfig
wlan0     IEEE 802.11  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

but i'm not sure how to make it connect, in xubuntu the network manager would alway autodetect the wireless network, how do i make it do the same in lenny?

---

### Post by monkey186 on 2009-06-22
p.s. according to  lspci my wireless card is  Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01)

---

### Post by Iowan on 2009-06-22
I've never used Debian (Lenny in particular)...
Post results of **ifconfig -a** and **lshw -C network**.

---

### Post by monkey186 on 2009-06-25
Its sorted! i had to install wicd and it now connects automatically.

---

