---
title: "Wireless PCI card DWA 510 Ver. A1 does not work on a Karmic"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by franzmaximilian on 2010-03-17
The mentioned PCI card is reported as working out of the box on Intrepid in this Ubuntu document: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI) 

It does not on my Karmic uname -a:
Linux giugi-desktop 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:05:19 UTC 2010 i686 GNU/Linux
This is a clean install on a brand new computer. Nothing else has been added or modified after installation and updates from default repositories (via temporary cable connection).

from lspci -k:
03:05.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
        Kernel driver in use: rt61pci
        Kernel modules: rt61pci

from iwconfig:
wlan0     IEEE 802.11bg  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Tx-Power=16 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

from ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:a0:41:8a
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

from iwlist wlan0 scanning:
lan0     Scan completed :
          Cell 01 - Address: 00:E0:98:50:6B:4A
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=30/70  Signal level=-80 dBm
                    Encryption key:on
                    ESSID:"rete_casa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=00000002fe2ca185
                    Extra: Last beacon: 9156ms ago
                    IE: Unknown: 0009726574655F63617361
                    IE: Unknown: 010482840B16
                    IE: Unknown: 03010A
                    IE: Unknown: 0406000200000000

This means that the card is up and running. Channel # and ESSID are the right ones from the router. I can send commands to the card such as "sudo iwconfig wlan0 channel 10" and the frequency gets changed accordingly. But no way I can manage to get an IP from the router.
The router's log too does not show any trace of attempts to connect.

Any ideas?

---

### Post by bkratz on 2010-03-17
Well it does say

Power Management on   above

Do you have some switch or key combination that is used to enable the wireless?

---

### Post by chili555 on 2010-03-17
When you click on the Network Manager icon at the top right, do you see your network? Can you click it, supply your encryption details and connect?

---

### Post by franzmaximilian on 2010-03-17
> **chili555 said:**
> When you click on the Network Manager icon at the top right, do you see your network? Can you click it, supply your encryption details and connect?

Yes sorry, I did it so many times in the past two days... that I gave it as granted.

I can see my network, give the WEP key and hit connect. Simply, nothing happens after this.

Better to say that the WEP hex key has been checked (and it works fine using Karmic on my wife's eeepc). I also borrowed a laptop from a friend for a test on my network (dual boot WinXP and Karmic) and it connects pretty easily using both OSs. This excludes the router as a troublemaker.

---

### Post by franzmaximilian on 2010-03-17
.

---

### Post by michaelwheatland on 2010-04-08
I am having the same problem. The DWA-510 PCI card using either the RT61pci driver or the ndiswrapper windows driver has problems connecting after entering the WEP key.

From what it looks like the card has powered down to a very low broadcast strength and is unable to connect. I have 2 other computers in the same room and both can connect to the wireless network without problem and at high speed.

Can someone help?

---

### Post by chili555 on 2010-04-08
> From what it looks like the card has powered down to a very low broadcast strengthCan you please show us?```
iwconfig
```

---

