---
title: "Dell Wireless Broadcom Help / ndiswrapper"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by arottenmind on 2006-06-10
Running Ubuntu 6.06

```
Wireless: 
0000:02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
        Subsystem: Dell Wireless 1350 WLAN Mini-PCI Card
        Flags: bus master, fast devsel, latency 32, IRQ 11
        Memory at fcffc000 (32-bit, non-prefetchable) [size=8K]
```

Ndiswrapper installed via the cd

this is the error i get when trying to add them via ndiswrapper

the .inf files are in my home directory, ive tried it with out the /usr/sbin/ and without the .inf at the end, all ways lead to same error.
```
arottenmind@Laptop:~$ sudo /usr/sbin/ndiswrapper -i /bcmwl5.inf
Installing bcmwl5
couldn't copy /bcmwl5.inf at /usr/sbin/ndiswrapper line 135.
```

I just recently Switch to Ubuntu, from Xandros.. I installed the wireless card in Xandros, via ndiswrapper and those same drivers..

Any help would be greatly apperciated :D Thanks!

:-k 

Here is more info if required

```
arottenmind@Laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arottenmind@Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0F:1F:22:5A:CF
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:fe22:5acf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13179292 (12.5 MiB)  TX bytes:880589 (859.9 KiB)
          Interrupt:7

```

---

### Post by Patsoe on 2006-06-10
```
arottenmind@Laptop:~$ sudo /usr/sbin/ndiswrapper -i /bcmwl5.inf
```

Well, the slash before bcmwl5.inf should go. :)

---

### Post by arottenmind on 2006-06-10
still same error without the slash =/

---

### Post by Patsoe on 2006-06-10
Are the files in a subdir? Are they named in uppercase? It is certainly something like that.

---

### Post by arottenmind on 2006-06-10
[QUOTE=Patsoe]Are the files in a subdir? Are they named in uppercase? It is certainly something like that.[/QUOTE]

arottenmind@Laptop:~$ ls
80211g        bcm43xx.cat  bcmwl5.inf  Desktop   oem3.inf
bcm43xxa.cat  bcmwl5a.inf  bcmwl5.sys  Examples  wl_apsta.o

There is the directory listing 
but it works for some reason even tho, both drivers say invalid driver via ndis. Im not going to complain tho, as long as it works..
Thansk for the help

---

