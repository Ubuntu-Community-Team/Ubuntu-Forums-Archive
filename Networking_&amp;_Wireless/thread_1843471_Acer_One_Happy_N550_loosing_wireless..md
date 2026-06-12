---
title: "Acer One Happy N550 loosing wireless."
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by Jasonindaskyz on 2011-09-13
I have installed Ubuntu 11.4 on my Acer One Happy n550 netbook and keep having issues with my wireless connection.  It seems to work fine when I first open the lid to the netbook.  After a while of browsing the web will stop loading new pages.  (my browser will just sit there wheel of death when a link is clicked)  My wireless icon in the top corner shows a full signal.  If I close the laptop and put it to sleep and the reopen it everything seems to work just fine.  However if I just disconnect from the network and reconnect no change. 

Thanks 

Sorry I am a noob when it come to ubuntu. 

Below information that I have used to try and solve my issues no luck.  


02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at 56000000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: <access denied>
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2011-09-13
Hello,

please show the following terminal outputs:

```
iwconfig
iwlist chan
sudo iwlist scan
route -n
cat /etc/resolv.conf
```

---

### Post by Jasonindaskyz on 2011-09-13
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"dlink"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 5C:D9:98:1F:DC:CE   
          Bit Rate=72.2 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:245  Invalid misc:42   Missed beacon:0

---

### Post by Jasonindaskyz on 2011-09-13
lo        no frequency information.

eth0      no frequency information.

wlan0     11 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Current Frequency=2.412 GHz (Channel 1)

jasonindaskyz@jasonindaskyz-AOHAPPY:~$ sudo iwlist scan
[sudo] password for jasonindaskyz: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 5C:D9:98:1F:DC:CE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000185a25041d7
                    Extra: Last beacon: 64ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B0506000A127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706555300010B10
                    IE: Unknown: DD7B0050F204104A00011010440001011041000100103B000103104700100AAE5EDD9E3C3FFEE87F5CD9981FDCCF10210006442D4C696E6B102300074449522D3831351024000830303030303030301042000830303030303030301054000800060050F2040001101100074449522D383135100800020086103C000103
          Cell 02 - Address: 00:23:97:B8:D0:2A
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"09FX10065839"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000520adc9b35f
                    Extra: Last beacon: 252ms ago
                    IE: Unknown: 000C303946583130303635383339
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
          Cell 03 - Address: 00:18:39:5D:05:BA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"StealThisInternetIfYouDare"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000048e10002af2
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 001A537465616C54686973496E7465726E65744966596F7544617265
                    IE: Unknown: 010882848B9624B0486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32048C129860
                    IE: Unknown: DD090010180200F4010000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

jasonindaskyz@jasonindaskyz-AOHAPPY:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
jasonindaskyz@jasonindaskyz-AOHAPPY:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1
jasonindaskyz@jasonindaskyz-AOHAPPY:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.0.1

---

### Post by praseodym on 2011-09-13
You can update the driver for your wireless device with:

```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
Reboot after that. I recommend to change the encryption mode from "none" to WPA2-AES (CCMP) if possible. Maybe changing the channel to 11 will help, too.

Do these problems only occur if you use suspend or hibernate? If so, please post:

```
lsmod | grep -iE 'usb|1394|hci|ndiswr|forced|8139|hid|802' 
```

---

