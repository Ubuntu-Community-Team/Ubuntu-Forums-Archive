---
title: "Broadcom BCM4318 : Slow internet with 12.04"
date: 2012-09-27
forum: Networking &amp; Wireless
---

### Post by grumpyjames on 2012-09-27
Hello there.

I've just started using a PCI wireless card to connect to the internet with 12.04 (previously I was fortunate enough to use a trusty piece of copper).

While the installation of the card and detection of networks seems to work, the speed is woeful (this page took five attempts to load). In browsers and in console based downloading, 5k/s is what I'm averaging, with frequent connection timeouts. Other wireless clients on the same network do not suffer at all.

As far as I know I'm using the correct driver for the card - the various documentation suggests I should be using the b43 module, which I am (wireless disappears/reappears when I unload/reload the module via modprobe).

Interestingly, no proprietary driver is shown in jockey (most of the documentation suggests one should be) - this led me to a bug which suggested commenting out the BCMXXX line in the modprobe blacklist might help - this at least seemed to let b43-firmware-installer install something...but that didn't help the situation.

I'm somewhat at my wits end here, so any advice on getting this partially working card up to full speed would be gratefully received.

As requested in the sticky, here's a bundle of console output from various commands:

```

james@waterhouse:~$ lspci | grep oad
04:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

james@waterhouse:~$ ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:18:f3:00:d3:03
          inet addr:192.168.1.72  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:f3ff:fe00:d303/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4071 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4934 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3535276 (3.5 MB)  TX bytes:1010748 (1.0 MB)

james@waterhouse:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"Kinakuta"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:26:44:C7:31:7F
          Bit Rate=36 Mb/s   Tx-Power=20 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:122  Invalid misc:78   Missed beacon:0

james@waterhouse:~$ dmesg | grep -e b43 -e Broadcom
[    2.821910] b43-pci-bridge 0000:04:01.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    5.194440] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[    5.308378] Registered led device: b43-phy0::tx
[    5.308400] Registered led device: b43-phy0::rx
[    5.308423] Registered led device: b43-phy0::assoc
[    5.308445] Registered led device: b43-phy0::radio
[    5.308461] Broadcom 43xx driver loaded [ Features: PNL ]
[    5.840059] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)

james@waterhouse:~$ sudo lshw -C network
PCI (sysfs)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:04:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:22 memory:feafe000-feafffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:18:f3:00:d3:03
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-30-generic firmware=508.1084 ip=192.168.1.72 link=yes multicast=yes wireless=IEEE 802.11bg

james@waterhouse:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:26:44:C7:31:7F
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-38 dBm
                    Encryption key:on
                    ESSID:"Kinakuta"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s                                                                                                                                     
                              24 Mb/s; 36 Mb/s; 54 Mb/s                                                                                                                                                      
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s                                                                                                                                               
                    Mode:Master
                    Extra:tsf=0000000155715b91
                    Extra: Last beacon: 1372ms ago
                    IE: Unknown: 00084B696E616B757461
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0102
                    IE: Unknown: 2F0102
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180204F0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

james@waterhouse:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS

james@waterhouse:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.

james@waterhouse:~$ uname -mr
3.2.0-30-generic x86_64

```

---

### Post by grumpyjames on 2012-09-28
Went with ndiswrapper instead in the end; that seems to work.

---

