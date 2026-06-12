---
title: "ipw2200 under 9.10"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by brucem9999 on 2009-11-28
I can't get my Intel ipw2200 to work. Here are the particulars per the "How to submit a wireless problem" page:

   Dell Inspirion I6000
   
   
  **ubuntu@ubuntu:~$ lspci -nn | grep 'Wireless'**
  
   
  03:03.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
  
   
  **ubuntu@ubuntu:~$ lspci -vn**
  
   
  03:03.0 0280: 8086:4220 (rev 05)
  
        Subsystem: 8086:2721
  
        Flags: bus master, medium devsel, latency 64, IRQ 17
  
        Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K]
  
        Capabilities: <access denied>
  
        Kernel driver in use: ipw2200
  
        Kernel modules: ipw2200
  
   
   
  **ubuntu@ubuntu:~$ lsusb**
  
  
  Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 004 Device 004: ID 046e:530a Behavior Tech. Computer Corp. 
  
  Bus 004 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
  
  Bus 004 Device 002: ID 046e:5400 Behavior Tech. Computer Corp. 
  
  Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
  
  Bus 001 Device 004: ID 1058:0701 Western Digital Technologies, Inc. 
  
  Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
  
   
  **ubuntu@ubuntu:~$ ifconfig**
  
   
  eth0      Link encap:Ethernet  HWaddr 00:12:3f:ea:43:0b  
  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
  
            Interrupt:18 
  
   
   
  eth1      Link encap:Ethernet  HWaddr 00:13:ce:3f:0c:fa  
  
            inet6 addr: fe80::213:ceff:fe3f:cfa/64 Scope:Link
  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1
  
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:3 errors:0 dropped:3 overruns:0 carrier:0
  
            collisions:0 txqueuelen:1000 
  
            RX bytes:0 (0.0 B)  TX bytes:220 (220.0 B)
  
            Interrupt:17 Base address:0xe000 Memory:dfdfd000-dfdfdfff 
  
   
   
  lo        Link encap:Local Loopback  
  
            inet addr:127.0.0.1  Mask:255.0.0.0
  
            inet6 addr: ::1/128 Scope:Host
  
            UP LOOPBACK RUNNING  MTU:16436  Metric:1
  
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0
  
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
  
            collisions:0 txqueuelen:0 
  
            RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
  
   
   
  **ubuntu@ubuntu:~$ iwconfig**
  
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  eth1      unassociated  ESSID:off/any  
  
            Mode:Managed  Channel=0  Access Point: Not-Associated   
  
            Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
  
            Retry limit:7   RTS thr:off   Fragment thr:off
  
            Power Management:off
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
   
   
  **ubuntu@ubuntu:~$ lsmod**
  
   
  Module                  Size  Used by
  
   
  libipw                 43148  1 ipw2200
  
   
  lib80211                6432  2 ipw2200,libipw
  
   
  **ubuntu@ubuntu:~$ dmesg | grep ipw2200**
  
  
  [   88.874501] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
  
  [   88.874506] ipw2200: Copyright(c) 2003-2006 Intel Corporation
  
  [   88.874612] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
  
  [   88.874711] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
  
  [   88.874757] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
  
  [   91.324330] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
  
   
  **ubuntu@ubuntu:~$ sudo lshw -C network**
  
   
    *-network:0             
  
         description: Ethernet interface
  
         product: BCM4401-B0 100Base-TX
  
         vendor: Broadcom Corporation
  
         physical id: 0
  
         bus info: pci@0000:03:00.0
  
         logical name: eth0
  
         version: 02
  
         serial: 00:12:3f:ea:43:0b
  
         size: 10MB/s
  
         capacity: 100MB/s
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
  
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
  
         resources: irq:18 memory:dfdfe000-dfdfffff
  
    *-network:1
  
         description: Wireless interface
  
         product: PRO/Wireless 2200BG [Calexico2] Network Connection
  
         vendor: Intel Corporation
  
         physical id: 3
  
         bus info: pci@0000:03:03.0
  
         logical name: eth1
  
         version: 05
  
         serial: 00:13:ce:3f:0c:fa
  
         width: 32 bits
  
         clock: 33MHz
  
         capabilities: pm bus_master cap_list ethernet physical wireless
  
         configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
  
         resources: irq:17 memory:dfdfd000-dfdfdfff
  
   
  **ubuntu@ubuntu:~$ iwlist scan**
  
  
  lo        Interface doesn't support scanning.
  
   
   
  eth0      Interface doesn't support scanning.
  
   
   
  eth1      No scan results
  
   
   
  **ubuntu@ubuntu:~$ lsb_release -d**
  
   
  Description:      Ubuntu 9.10
  
   
  **ubuntu@ubuntu:~$ uname -mr**
  
  2.6.31-14-generic i686
  
   
  **ubuntu@ubuntu:~$ sudo /etc/init.d/networking restart**
  
   
  [FONT=Symbol]·[/FONT]Reconfiguring network interfaces...                                   [ OK ] 
  [FONT=Symbol]·[/FONT]
  [FONT=Symbol]·[/FONT] 
  [B]ubuntu@ubuntu:~$ 
[/B]


------------------------------------------------


END OF LISTING


------------------------------------------------


Help, please

---

### Post by chili555 on 2009-11-28
Please let us see:```
[COLOR="Red"]sudo[/COLOR] iwlist eth1 scan
```What happens when you click the Network Manager icon and try to connect?

---

### Post by brucem9999 on 2009-11-29
Per your request:

   To run a command as administrator (user "root"), use "sudo <command>".
  
  See "man sudo_root" for details.
  
   
   
  ubuntu@ubuntu:~$ sudo iwlist eth1 scan
  
  eth1      Scan completed :
  
            Cell 01 - Address: 00:90:4C:5F:00:2A
  
                      ESSID:"CoffeeBeanWiFi"
  
                      Protocol:IEEE 802.11bg
  
                      Mode:Master
  
                      Frequency:2.437 GHz (Channel 6)
  
                      Encryption key:off
  
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
  
                                11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
  
                                48 Mb/s; 54 Mb/s
  
                      Quality=92/100  Signal level=-36 dBm  
  
                      Extra: Last beacon: 72ms ago
  
            Cell 02 - Address: 00:0F:CC:AC:CE:E0
  
                      ESSID:"5314 0454"
  
                      Protocol:IEEE 802.11bg
  
                      Mode:Master
  
                      Frequency:2.437 GHz (Channel 6)
  
                      Encryption key:on
  
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
  
                                11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
  
                                36 Mb/s; 48 Mb/s; 54 Mb/s
  
                      Quality=92/100  Signal level=-36 dBm  
  
                      Extra: Last beacon: 64ms ago
  
            Cell 03 - Address: 00:1E:E5:F8:FF:7B
  
                      ESSID:"MCXLnet"
  
                      Protocol:IEEE 802.11g
  
                      Mode:Master
  
                      Frequency:2.442 GHz (Channel 7)
  
                      Encryption key:on
  
                      Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
  
                                11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
  
                                48 Mb/s; 54 Mb/s
  
                      Quality=59/100  Signal level=-65 dBm  
  
                      IE: WPA Version 1
  
                          Group Cipher : TKIP
  
                          Pairwise Ciphers (1) : TKIP
  
                          Authentication Suites (1) : PSK
  
                      Extra: Last beacon: 96ms ago
  
   
   
  [FONT=&quot]ubuntu@ubuntu:~$ [/FONT]   
I've haven't been able to find Network Manager anywhere in my menu system. Under Places, there's a Network icon, but I can't see where that would help???



A little more background:


I'm trying to get this running under Live CD and I understand I'll have to "redo" this with each reboot. Would I be better of using persistent mode?
I have a casper-cow memory stick, if it would help?? How about a dual-boot system? I just can't make "the big jump" until I get the Internet up.



Thanks for your reply.



I did Unix sys admin for about five years, but never had to deal with communications.

---

### Post by chili555 on 2009-11-29
It looks like your ipw2200 is working well, just waiting for a command to connect! The Network Manager icon is at the top right and will look like the attached. Since you are not connected yet, it may look like an antenna with no bars. Left-click it, look for your network, CoffeeBeanWiFi, perhaps and see if it connects.> Would I be better of using persistent mode?Not especially. If you are connecting to an unencrypted network, like this:> ESSID:"CoffeeBeanWiFi"

Protocol:IEEE 802.11bg

Mode:Master

Frequency:2.437 GHz (Channel 6)

[COLOR="Red"]Encryption key:off[/COLOR]Then it should simply click and connect.

---

### Post by brucem9999 on 2009-11-29
Thanks. I found it. I know I've seen it before when I was looking around for "the manager", but when I go into it and click on the wireless tab, it doesn't show any available networks. If I click on "add", it asks for the SSID, Mode, etc - none of which I have, of course. On that second screen, there is a box labeled "Connect Automatically", which is checked.

I didn't make a copy of the frames I saw because I hadn't looked at your thumbnails until I came back to Windows eMail tomail you back, but it looks different from what you sent me. I wanted to get this off as soon as possible, but I'll restart with Linux and get a thumbnail of what I have and eMail it back to you in the next 1/2 hour or so.

---

### Post by brucem9999 on 2009-11-29
Ah, Ha! The first time I left clicked, I didn't wait long enough ( I'm running off the CD, of course), so I didn't see what you sent me. I then right-clicked and went into the sub menu. I just waited longer this time and I found it. I am now up on Firefox and the Internet thru Linux.

Thank you very, very much.

Case closed!

---

