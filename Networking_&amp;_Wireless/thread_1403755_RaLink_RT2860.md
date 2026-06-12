---
title: "RaLink RT2860?"
date: 2010-02-10
forum: Networking &amp; Wireless
---

### Post by ryanmh on 2010-02-10
I got an MSI Wind U100, with a RaLink RT2860 wireless chip. In the corner where the network properties are, there are no wireless connections in the list, even though there are normally about 10 around where I live. I think it may be due to a driver that I don't have. I googled it and found [this thread]("http://ubuntuforums.org/showthread.php?t=728537"), which lead me to [this thread]("http://ubuntuforums.org/showthread.php?t=756260"). But I can't use ndiswrapper because I wiped the hard drive clean of windows and installed Ubuntu. 

I went and downloaded the [appropriate driver]("http://driverscollection.com/H=RT2860&By=Ralink"). Then I did the standard procedure of cd'ing to the directory of it and doing *make && make install*, it compiles, but I get an error when trying to install and the instructions that come with the driver make no sense at all.

So, is there a way to get this working. Using a netbook on ethernet is completely pointless :p

**Nevermind, I reinstalled Ubuntu and it works now.**

---

### Post by chili555 on 2010-02-10
Does it help to do:```
sudo modprobe rt2860sta
```If that doesn't kick your wireless card to life, please post:```
lspci -nn | grep Network
```Thanks.

---

### Post by ryanmh on 2010-02-10
The first command didn't work. Here's the output for the second:

```
02:00.0 Network controller [0280]: RaLink RT2860 [1814:0781]
```

---

### Post by chili555 on 2010-02-10
> The first command didn't work.It didn't?? Please do:```
iwconfig
```Do you now have a wireless interface?

---

### Post by ryanmh on 2010-02-10
It says ra0, so I guess it recognizes it, but it still doesn't work. Also thanks for trying to help. :)

---

### Post by chili555 on 2010-02-10
> but it still doesn't workWhat happens when you left-click the Network Manager icon at the upper right of your desktop? Do you see networks? Can you connect to yours?

---

### Post by ryanmh on 2010-02-11
Nope, there's no networks.

---

### Post by chili555 on 2010-02-11
Please post:```
sudo iwlist ra0 scan
dmesg | grep rt28
```Thanks.

---

### Post by ryanmh on 2010-02-11
For the first command:
```
ra0     No scan results
```

The second:
```
[17.788666] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[17.804796] rt2860 0000:02:00.0 PCI INT A -> GSI 17 (level, low) -> IRQ 17
[17.805390] rt2860 0000:02:00.0: setting latency timer to 64
```

---

### Post by chili555 on 2010-02-12
Please let us see:```
dmesg | grep ra0
rfkill list
```Thanks.

---

### Post by ryanmh on 2010-02-12
```
ra0: no IPv6 routers present
```
Nothing happened for the second command

---

### Post by M.pike on 2010-04-01
Hey guys. I am having the same problem.  Different laptop but the same wireless card.  It did work perfectly until i upgraded to 9.10 since then I can turn the card on and scan for wireless AP's but never detect any even when sitting right next to my own AP that already has other connections to it :S.  As I said it worked previously to upgrading so I am assuming it has something to do with a lack of support in the latest version of the netbook remix.  On a different but related note, my wired connection no longer works either, it registers that there is a connection and can ping local addresses but cannot ping google, i checked with both the IP address a FQDN in case the DNS was being screwy but neither worked, that is a RealTech card (cant remember the model).  Anyways the main problem is wireless since i use that the most and ralink isn't exactly unused by other people.  If i cant fix it i am afraid I will have to go back to slackware :(

---

### Post by chili555 on 2010-04-01
Please let us see:```
iwconfig
lspci -nn | grep Network
```Thanks.

---

