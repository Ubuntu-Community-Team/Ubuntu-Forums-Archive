---
title: "Re: wireless connection very unstable"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by newboyo on 2010-11-01
Hi all,

Use a Thinkpad 410 with a realtek card under Karmic 64 bit. Since my net work is iffy, tried out some of the commands mentioned by the 'Wizard who helps". 

here is the output of my

**lshw -C Network**

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 00:26:2d:fc:d9:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=0.12-1 latency=0 multicast=yes
       resources: irq:34 memory:f2400000-f241ffff memory:f2425000-f2425fff ioport:1820(size=32)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:69:53:11
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0018.1025.2010 firmware=63 ip=192.168.1.8 latency=0 multicast=yes wireless=802.11bg
       resources: irq:17 ioport:3000(size=256) memory:f2000000-f2003fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

**lspci -nn**
00:00.0 Host bridge [0600]: Intel Corporation Arrandale DRAM Controller [8086:0044] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation Arrandale PCI Express x16 Root Port [8086:0045] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:16.3 Serial controller [0700]: Intel Corporation 5 Series/3400 Series Chipset KT Controller [8086:3b67] (rev 06)
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b07] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0a6c] (rev a2)
01:00.1 Audio device [0403]: nVidia Corporation Device [10de:0be3] (rev a1)
03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8172] (rev 10)
0d:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
0d:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
0d:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
ff:00.0 Host bridge [0600]: Intel Corporation QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Device [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Device [8086:2d13] (rev 02)

**lsusb**
Bus 001 Device 005: ID 04f9:022a Brother Industries, Ltd 
Bus 001 Device 004: ID 17ef:480f Lenovo 
Bus 001 Device 003: ID 147e:2016 Upek Biometric Touchchip/Touchstrip Fingerprint Sensor
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 004: ID 17ef:1003 Lenovo 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

**uname -a**
Linux newboyo-laptop 2.6.31-22-generic #67-Ubuntu SMP Sat Oct 16 18:51:35 UTC 2010 x86_64 GNU/Linux

**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11bg  ESSID:"WL_QWERTY"  Nickname:"rtl8191SEVA2"
          Mode:Managed  Frequency=2.432 GHz  Access Point: 90:E6:BA:EE:87:9B   
          Bit Rate=54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management period:0us  mode:All packets received
          Link Quality=62/100  Signal level=-71 dBm  Noise level=-101 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

---

### Post by pytheas22 on 2010-11-02
How is your network iffy, specifically?  Does the connection drop completely?  Does the computer still say you're connected but you can't load web pages or download files?  Is it just slower than you think it should be (i.e., slower than on your other computers)?  Is it only on one particular network that you have problems, or on all of them?  It would also be useful to see the output of:

```

sudo iwlist scan
```

in order to know more information about how your network is configured.

There are different solutions that might help, but it would be good to get a better idea of exactly which problems you're experiencing before trying something.

---

### Post by newboyo on 2010-11-02
Thanks for having a look. My connection is generally stable, but all of a sudden downloads (especially of torrents) becomes a crawl. Other times, the connection will drop and won't reconnect. The only solution then is to reboot.

the scan wanted by you follows -



wlan0     Scan completed :
          Cell 01 - Address: 94:44:52:42:C3:2A
                    ESSID:"xxxx1"
                    Protocol:IEEE802.11N-24G
                    Mode:Master
                    Channel:2
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 11 9 12 18 24 36 48 54 
                    Quality:42  Signal level:0  Noise level:165
                    IE: Unknown: DD270050F204104A000110104400010210470010775B6680BFDE11D38D2F94445242C32A103C000101
                    Extra: Last beacon: 138ms ago
          Cell 02 - Address: 90:E6:BA:EE:87:9B
                    ESSID:"MINE"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality=62/100  Signal level=-70 dBm  Noise level=-101 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 79ms ago
          Cell 03 - Address: 34:EF:44:84:53:29
                    ESSID:"BELL167"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality:61  Signal level:0  Noise level:156
                    Extra: Last beacon: 75ms ago
          Cell 04 - Address: 00:03:2F:3A:07:42
                    ESSID:"Kari"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54 
                    Quality:60  Signal level:0  Noise level:156
                    Extra: Last beacon: 62ms ago
          Cell 05 - Address: 00:22:2D:50:32:FA
                    ESSID:"Salama"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:5
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 22 24 36 48 54 
                    Quality:42  Signal level:0  Noise level:165
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 98ms ago
          Cell 06 - Address: 00:14:D1:69:D9:4A
                    ESSID:"GalaGala"
                    Protocol:IEEE802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 11 6 9 12 18 24 36 48 54 
                    Quality:100  Signal level:0  Noise level:136
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    Extra: Last beacon: 6ms ago

vboxnet0  Interface doesn't support scanning.


My connection is cell2 called MINE.

Rgds and thanks 

New

p.s I considered changing the channel, but when I scanned on the router - it said channel 5 was the strongest.

---

### Post by pytheas22 on 2010-11-03
Thanks for the information.  It looks like there are two other routers operating on the same channel with a relatively high signal strength, so interference from those could be at least part of the problem.  I'd see if changing the channel would help.

I have no idea how the router determines which channel it thinks is the strongest, but if it's a typical consumer-class router designed for people who don't know much about computers, I wouldn't be surprised if it totally makes it up.

Beyond that, changing the encryption (from WPA1 to WPA2) is always also worth a try.

If none of the above helps, the next thing I'd do would be to recompile the driver using the latest source code from [http://linuxwireless.org](http://linuxwireless.org), or try ndiswrapper in place of the native Linux driver.  But hopefully that won't be necessary and just changing some of your router's settings will do the trick.

---

### Post by jdkchem on 2010-11-04
Are you using the proprietary Nvidia driver?  I have a similar problem that shows up if I use the Nvidia driver.  No proprietary drive, no problems.

---

### Post by newboyo on 2010-11-08
Thank you all.

I did change the channel, speed improved somewhat. Deactivating NVIDIA mucked up graphics, so I reactivated it.

Nothing else to report now.

rgds

---

### Post by TBABill on 2010-11-08
Can you post the output of ```
sudo lshw -C network
``` That will help identify exactly which device you are working with.

---

