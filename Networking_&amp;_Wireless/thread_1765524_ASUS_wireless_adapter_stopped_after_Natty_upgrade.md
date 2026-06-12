---
title: "ASUS wireless adapter stopped after Natty upgrade"
date: 2011-05-23
forum: Networking &amp; Wireless
---

### Post by Fastship on 2011-05-23
Since upgrading to 2.6.38-8 (natty 11.04) from 2.6.35-28 my ASUS 802.11n usb wireless adapter ceased to work. It still  works in 2.6.35-28 so I wondered if someone could give me list of commands I could try in Konsole and make comparisons to see what's wrong.

I bought the Asus adapter to replace the BT Voyager 1055 adapter which I couldn't get to work in 2.6.35-28 but does now work in 11.04! The Asus gives me a much stronger signal though.

In the logs below both adapters have been installed in the computer.

Log for 11.04:
xyx@xyx-Dimension-8400:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1690:0715 Askey Computer Corp. [hex] Name: Voyager 1055 Laptop 802.11g Adapter [Broadcom 4320]
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

xyx@xyx-Dimension-8400:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: phy1: Wireless LAN
        Soft blocked: no
        Hard blocked: no
xyx@xyx-Dimension-8400:~$ 


log for 2.6.35-28, the old version:
As you can see, the Voyager 10055 adapter is not recognised by the rfkill list command:
xyx@xyx-Dimension-8400:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 1690:0715 Askey Computer Corp. [hex] Name: Voyager 1055 Laptop 802.11g Adapter [Broadcom 4320]
Bus 001 Device 002: ID 0b05:1784 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

xyx@xyx-Dimension-8400:~$ rfkill list
0: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no



Cheers.

---

