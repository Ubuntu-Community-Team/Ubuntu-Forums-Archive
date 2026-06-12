---
title: "loosing wireless connexion randomly Cubuntu 12.04"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by statquant on 2012-12-02
Hello guys,
I am presently experiencing random deconnexions from my wirless connexion.
It looks like it is more and more frequent (however I have not seen any clear pattern).
This is killing me...

Here is some information:
I hope some of you can help

Machine : Acer Aspire S3

```

statquant@euclide:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation UM67 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Atheros Communications Inc. AR9485 Wireless Network Adapter (rev 01)
statquant@euclide:~$ 

``````

statquant@euclide:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 004: ID 064e:c321 Suyin Corp. 
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 

``````

statquant@euclide:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16895 (16.8 KB)  TX bytes:16895 (16.8 KB)

wlan0     Link encap:Ethernet  HWaddr 74:de:2b:dd:c4:78  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fedd:c478/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:913 errors:0 dropped:0 overruns:0 frame:0
          TX packets:802 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:873218 (873.2 KB)  TX bytes:125826 (125.8 KB)

``````

statquant@euclide:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Bbox-D646D1"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:70:80:01:6C   
          Bit Rate=65 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:71   Missed beacon:0

``````

statquant@euclide:~$ dmesg | grep "wlan"
[   17.495866] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   17.498950] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.072015] wlan0: authenticate with 00:19:70:80:01:6c (try 1)
[   20.269853] wlan0: authenticate with 00:19:70:80:01:6c (try 2)
[   20.272386] wlan0: authenticated
[   20.298682] wlan0: associate with 00:19:70:80:01:6c (try 1)
[   20.302321] wlan0: RX AssocResp from 00:19:70:80:01:6c (capab=0x431 status=0 aid=1)
[   20.302325] wlan0: associated
[   20.307307] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   30.402292] wlan0: no IPv6 routers present

``````

statquant@euclide:~$ sudo lshw -C network
[sudo] password for statquant: 
  *-network               
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 74:de:2b:dd:c4:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-33-generic firmware=N/A ip=192.168.1.3 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0400000-c047ffff memory:afb00000-afb0ffff
statquant@euclide:~$ 

``````

statquant@euclide:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:19:70:80:01:6C
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"Bbox-D646D1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000125fb152bb
                    Extra: Last beacon: 40020ms ago
                    IE: Unknown: 000B42626F782D443634364431
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000000000

``````

statquant@euclide:~$ lsb_release -d
Description:    Ubuntu 12.04.1 LTS

``````

statquant@euclide:~$ uname -mr
3.2.0-33-generic x86_64

``````

statquant@euclide:~$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                                     [ OK ] 
statquant@euclide:~$ 

```Please note that I ran 
```

sudo modprobe -r iwlwifi 
sudo modprobe iwlwifi 11n_disable=1
```which did not help... Thank you if you can help (and even if you cannot :))

---

### Post by statquant on 2012-12-03
up ?
Should I modify my post (sorry if I did something wrong)

---

### Post by mainah on 2012-12-09
I'm having very similar issues.  I've been trying various "fixes" from all over the internet to no avail.  There are some variances, such as a system freeze-up when the wifi dies, etc.

Would it be wise to start my own thread?  For the record, the offending wifi card is an Intel Ultimate N WiFi Link 5300, Ubuntu 12.04 (kernel 3.2.0-29-generic-pae).

Thanks!

---

