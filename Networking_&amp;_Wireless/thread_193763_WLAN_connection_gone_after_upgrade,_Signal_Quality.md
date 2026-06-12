---
title: "WLAN connection gone after upgrade, Signal Quality:0/100"
date: 2006-06-10
forum: Networking &amp; Wireless
---

### Post by ToneDispenser on 2006-06-10
Hello board,

I upgraded to dapper from breezy 1 week ago and everything works really great,
except for my WLAN connection.

I compiled a kernel, since my synaptics touchpad was spewing interrupts and the mouse pointer jumped all over the desktop randomly. The only thing I changed were in the synaptics.c,
so everything else is still vanilla 2.6.15.7
I also compiled ndiswrapper against kernel 2.6.15-23-686, but it woudln't work with that kernel either (but i had the jumpy mouse pointer back).

I use ndiswrapper 1.17 which is seems to be set up correctly:
```
$ ndiswrapper -l
Installed drivers:
mrv8335         driver installed, hardware present

```
my wlan chipset PCI-ID is 11ab:1faa (rev 03) and the marvell driver is the right driver...
I used the same driver in breezy and everything worked fine.

The ndiswrapper module is also loaded and there are no error messages in dmesg.
(led is also blinking on my PCMCIA wlan card)
```

$ dmesg | grep ndis
[4294692.241000] ndiswrapper version 1.17 loaded (preempt=yes,smp=no)
[4294692.735000] ndiswrapper: driver mrv8335 (Marvell,02/22/2005,3.1.1.7) loaded[4294692.740000] ndiswrapper: using irq 11
[4294693.294000] wlan0: ndiswrapper ethernet device 00:40:f4:d5:f1:9b using driver mrv8335, 11AB:1FAA.5.conf

```

I moved the Kernel Module for the Marvell WLAN chipset 'mrv8k' from /lib/modules/[etc] to a different location,
so it's definitely not being loaded (modprobe -l confirms that).

I want to use 'network manager' to configure my network interfaces,
so the only two lines in my /etc/network/interfaces are
```
auto lo
iface lo inet loopback
```

However, I'm unable to connect to my WLAN.
```
$ iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:04:0E:1D:A3:DF
                    ESSID:"StayOut"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-80 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```

the gnome applet for the network manager reports the same thing.
my wlan is being listed, but the bar which indicates the quality of the signal
is empty. It also picks up a wlan signal from the neighborhood, but it's the same there.

```
$ iwconfig wlan0
wlan0     IEEE 802.11FH  ESSID:off/any
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm
          RTS thr:2346 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Thanks for any hints/tips/ideas!

---

### Post by ToneDispenser on 2006-06-11
Help anybody? :(

---

### Post by Irish on 2006-06-11
I'm having a roughly similar problem with the Dell TrueMobile 1180. I upgraded to Dapper (using my wireless connection, ironically) and when I finished installing it I couldn't get my WLAN connection to stay active - let alone pick up a signal. I've talked to a few other people that have lost their wireless support right after upgrading to Dapper, but I haven't found anyone yet who's been able to fix it or find an explanation.

If I find anything I'll post it here. :-(

---

### Post by ToneDispenser on 2006-06-11
I'm finally able to connect using the Network Manager.
Signal quality is still 0/100, but I'm able to connect.
I'm quite sure I could see the signal quality working when I used ndiswrapper 1.5 or so.

Versions 1.16, 1.17 and the bleeding edge from svn didn't connect.
1.15 does... :)

---

### Post by ToneDispenser on 2006-06-11
hmmm.. the gnome network manager applet says that signal is 100%.

iwlist wlan0 scan still reports quality:0/100

---

### Post by Irish on 2006-06-11
Blacklisted/removed bcm43xx.ko and reinstalled drivers with ndiswrapper. Everything works fine now.

---

