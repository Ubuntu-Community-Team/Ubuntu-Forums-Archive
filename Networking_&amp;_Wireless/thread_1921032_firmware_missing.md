---
title: "firmware missing"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by xzimppledink on 2012-02-05
Ubuntu 11.1 X 64 is running perfectly except my PCI wireless adapter doesn't work. Error message says "firmware missing". Previous versions didn't have any trouble with wireless. I can make connection with a USB wireless device. I have the same problem with SuSE 64 bit OS. How can I find the firmware?

---

### Post by sanderj on 2012-02-06
> **xzimppledink said:**
> Ubuntu 11.1 X 64 is running perfectly except my PCI wireless adapter doesn't work. Error message says "firmware missing". Previous versions didn't have any trouble with wireless. I can make connection with a USB wireless device. I have the same problem with SuSE 64 bit OS. How can I find the firmware?

I think it would help if you would post & google the relevant line from the command "lspci" to show what pci wifi hardware this about.
Check dmesg and /var/log/syslog for relevant messages. And check lsmod.

Does it work with Ubuntu 11.10 32-bit?

---

### Post by varunendra on 2012-02-06
In order to know what wireless adapter +driver you are using, please run and post output of:
```
lspci -nnk | grep -iA2 net
```
Also-
```
dmesg | grep -iE 'net | wlan'
```

Please wrap the outputs in [ code] and  [ /code] tags by clicking on the **# **symbol at the top of the edit box (in which you create new posts) to generate those tags, the copy-paste the output code in-between those tags. It'll preserve its formatting and make it easily readable.

---

### Post by jkevans on 2012-02-08
I am also having a problem finding the firmware for my wireless.  Here is the output after I ran the codes suggested.

kadene@kadene-Inspiron-8600:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401 100Base-T [14e4:4401] (rev 01)
    Subsystem: Dell Device [1028:8127]
    Kernel driver in use: b44
--
02:03.0 Network controller [0280]: Broadcom Corporation BCM4309 802.11a/b/g [14e4:4324] (rev 03)
    Subsystem: Dell Truemobile 1450 MiniPCI [1028:0003]
    Kernel driver in use: b43-pci-bridge
kadene@kadene-Inspiron-8600:~$ dmesg | grep -iE 'net | wlan'
[    1.684053] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x04, vendor 0x4243)
[    1.752988] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:11:43:5e:6b:51
[   14.817387] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
kadene@kadene-Inspiron-8600:~$ 



Thank you for any help.

---

### Post by cariboo on 2012-02-08
A bump for the move.

---

### Post by varunendra on 2012-02-08
@jkevans,
Please check your original thread where I have replied.

@cariboo,
Nice 'move' (in your new avatar) ;) Oh, and thanks for the 'thread' move too. :P

---

