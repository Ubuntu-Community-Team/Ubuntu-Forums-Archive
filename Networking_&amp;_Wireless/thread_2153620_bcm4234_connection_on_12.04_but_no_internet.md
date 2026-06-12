---
title: "bcm4234 connection on 12.04 but no internet"
date: 2013-06-11
forum: Networking &amp; Wireless
---

### Post by asan42 on 2013-06-11
Hello all 
 I have through this forum gotten as far as installing ndiswrapper loading driver and getting connected to wifi. my issue is now i cant seem to stay connected to internet. will only work for about a minute after i first turn my desktop on. wifi connection never fails just no internet available. any suggestions would be greatly appreciated. thank you in advance.

---

### Post by chili555 on 2013-06-12
I highly doubt that ndiswrapper is the best method to get this going. Please open a terminal and run and post:```
lspci -nn -d 14e4:
rfkill list all
```Thanks.

---

### Post by asan42 on 2013-06-13
> **chili555 said:**
> I highly doubt that ndiswrapper is the best method to get this going. Please open a terminal and run and post:```
lspci -nn -d 14e4:
rfkill list all
```Thanks.


```
asan@minepc:~$ lspci -nn -d 14e4:asan@minepc:~$ rfkill list all
asan@minepc:~$ 
```

no output with these codes.  deleted and re-installed but still same deal.

---

### Post by chili555 on 2013-06-13
Very interesting! Let's widen the search:```
lspci -nn
lsusb
```Thanks.

---

### Post by asan42 on 2013-06-13
> **chili555 said:**
> Very interesting! Let's widen the search:```
lspci -nn
lsusb
```Thanks.


```
asan@minepc:~$ lspci -nn00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:02.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0) [1022:9603]
00:06.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) [1022:9606]
00:11.0 SATA controller [0106]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] [1002:4390]
00:12.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:12.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:12.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:13.0 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller [1002:4397]
00:13.1 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller [1002:4398]
00:13.2 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB controller [0c03]: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 0 [1022:1600]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 1 [1022:1601]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 2 [1022:1602]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 3 [1022:1603]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 4 [1022:1604]
00:18.5 Host bridge [0600]: Advanced Micro Devices [AMD] Family 15h Processor Function 5 [1022:1605]
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Device [1002:683d]
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Device [1002:aab0]
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
asan@minepc:~$ lsusb
Bus 002 Device 005: ID 0781:5561 SanDisk Corp. 
Bus 002 Device 004: ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]
Bus 005 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 005 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
asan@minepc:~$ 

```

here is output. i hope this information can help us out. thank you chilli555 for your help.

---

### Post by chili555 on 2013-06-14
> ID 0846:9011 NetGear, Inc. WNDA3100v2 802.11abgn [Broadcom BCM4323]Oh,* that* Broadcom! You had me confused; you said Broadcom BCM4234 and the device is BCM4323. That device does, indeed, only work with ndiswrapper. Let's find out why it isn't:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndiswrapper
```Please post the outcome of each command. Thanks.

---

### Post by asan42 on 2013-06-14
> **chili555 said:**
> Oh,* that* Broadcom! You had me confused; you said Broadcom BCM4234 and the device is BCM4323. That device does, indeed, only work with ndiswrapper. Let's find out why it isn't:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndiswrapper
```Please post the outcome of each command. Thanks.

```
asan@minepc:~$ sudo modprobe ndiswrapper[sudo] password for asan: 
asan@minepc:~$ ndiswrapper -l
bcmwlhigh5 : driver installed
    device (0846:9011) present
asan@minepc:~$ dmesg | grep ndiswrapper
[   20.811451] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   21.930257] ndiswrapper: driver bcmwlhigh5 (Netgear,05/05/2009, 5.10.79.30) loaded
[   22.465742] usbcore: registered new interface driver ndiswrapper
asan@minepc:~$ 

```

here is what i came up with. thank you again for the assistance.

---

### Post by chili555 on 2013-06-14
Perfect so far! Now how about:```
iwconfig
sudo iwlist wlan0 scan
rfkill list all
```

---

### Post by asan42 on 2013-06-14
> **chili555 said:**
> Perfect so far! Now how about:```
iwconfig
sudo iwlist wlan0 scan
rfkill list all
```

```
asan@minepc:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"belkin.991"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 08:86:3B:D4:19:91   
          Bit Rate=104 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:1680   Missed beacon:0


asan@minepc:~$ sudo iwlist wlan0 scan
[sudo] password for asan: 
wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:D4:19:91
                    ESSID:"belkin.991"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A62656C6B696E2E393931
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010AE43846D3DF97E656265FDCB95DF6F021021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323132303847453130383734381054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
          Cell 02 - Address: 0A:86:3B:D4:19:92
                    ESSID:"belkin.991.guests"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001162656C6B696E2E3939312E677565737473
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010AE43846D3DF97E656265FDCB95DF6F021021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323132303847453130383734381054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1F:90:BA:B0:48
                    ESSID:"B47V5"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00054234375635
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000


asan@minepc:~$ rfkill list all
asan@minepc:~$ 

```

this is output. maybe you see something i cant.

---

### Post by chili555 on 2013-06-14
Still looking very good! Now let's see:```
cat /etc/resolv.conf
nm-tool
```

---

### Post by asan42 on 2013-06-14
> **chili555 said:**
> Still looking very good! Now let's see:```
cat /etc/resolv.conf
nm-tool
```

```
asan@minepc:~$ iwconfigeth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11g  ESSID:"belkin.991"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 08:86:3B:D4:19:91   
          Bit Rate=104 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:56/100  Signal level:-60 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:1680   Missed beacon:0


asan@minepc:~$ sudo iwlist wlan0 scan
[sudo] password for asan: 
wlan0     Scan completed :
          Cell 01 - Address: 08:86:3B:D4:19:91
                    ESSID:"belkin.991"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:73/100  Signal level:-49 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 000A62656C6B696E2E393931
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD0E0050F204104A0001101044000102
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010AE43846D3DF97E656265FDCB95DF6F021021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323132303847453130383734381054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
          Cell 02 - Address: 0A:86:3B:D4:19:92
                    ESSID:"belkin.991.guests"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:92/100  Signal level:-37 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 001162656C6B696E2E3939312E677565737473
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DDA20050F204104A00011010440001021041000100103B00010310470010AE43846D3DF97E656265FDCB95DF6F021021001442656C6B696E20496E7465726E6174696F6E616C1023000A46394B3131303520763110240007312E30302E30361042000E31323132303847453130383734381054000800060050F20400011011001D42656C6B696E204E343530444220576972656C65737320526F75746572100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: 00:1F:90:BA:B0:48
                    ESSID:"B47V5"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: Unknown: 00054234375635
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F010100200000


asan@minepc:~$ rfkill list all
asan@minepc:~$ 

```

here is output. i am really stumped with this . thanks for the help.

---

### Post by chili555 on 2013-06-14
Please try again:```
cat /etc/resolv.conf
nm-tool
```

---

### Post by asan42 on 2013-06-14
> **chili555 said:**
> Please try again:```
cat /etc/resolv.conf
nm-tool
```

```
asan@minepc:~$ cat /etc/resolv.conf# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1
search Belkin
asan@minepc:~$ nm-tool


NetworkManager Tool


State: connected (global)


- Device: wlan0  [belkin.991] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connected
  Default:           yes
  HW Address:        10:0D:7F:38:8F:9E


  Capabilities:
    Speed:           144 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    belkin.991.guests: Infra, 0A:86:3B:D4:19:92, Freq 2462 MHz, Rate 54 Mb/s, Strength 100
    *belkin.991:     Infra, 08:86:3B:D4:19:91, Freq 2462 MHz, Rate 54 Mb/s, Strength 84 WPA2
    B47V5:           Infra, 00:1F:90:BA:B0:48, Freq 2412 MHz, Rate 54 Mb/s, Strength 29 WEP
    H87T5:           Infra, 00:7F:28:29:00:D1, Freq 2437 MHz, Rate 54 Mb/s, Strength 34 WPA2


  IPv4 Settings:
    Address:         192.168.2.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1


    DNS:             192.168.2.1




- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        50:E5:49:D1:FB:1B


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




asan@minepc:~$ 

```

sorry doing this off of a usb and got mixed up for a minute.

---

### Post by chili555 on 2013-06-14
We're getting closer! ```
ping -c3 8.8.8.8
ping -c3 www.google.com
ping -c3 74.125.26.105
```Off to lunch; see you later.

---

### Post by asan42 on 2013-06-14
> **chili555 said:**
> We're getting closer! ```
ping -c3 8.8.8.8
ping -c3 www.google.com
ping -c3 74.125.26.105
```Off to lunch; see you later.

```
asan@minepc:~$ ping -c3 8.8.8.8PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=47 time=50.3 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=47 time=45.8 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=47 time=43.9 ms


--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 43.941/46.727/50.355/2.685 ms
asan@minepc:~$ ping -c3 www.google.com
PING www.google.com (74.125.227.84) 56(84) bytes of data.
64 bytes from dfw06s07-in-f20.1e100.net (74.125.227.84): icmp_req=1 ttl=50 time=84.1 ms
64 bytes from dfw06s07-in-f20.1e100.net (74.125.227.84): icmp_req=2 ttl=50 time=83.6 ms
64 bytes from dfw06s07-in-f20.1e100.net (74.125.227.84): icmp_req=3 ttl=50 time=77.3 ms


--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 77.367/81.691/84.105/3.064 ms
asan@minepc:~$ ping -c3 74.125.26.105
PING 74.125.26.105 (74.125.26.105) 56(84) bytes of data.
64 bytes from 74.125.26.105: icmp_req=1 ttl=33 time=106 ms
64 bytes from 74.125.26.105: icmp_req=2 ttl=35 time=125 ms
64 bytes from 74.125.26.105: icmp_req=3 ttl=33 time=204 ms


--- 74.125.26.105 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 106.936/145.806/204.797/42.410 ms
asan@minepc:~$ 

```

this is the output. hope lunch was good chili. hopefully this info gets us closer.

---

### Post by chili555 on 2013-06-14
I see nothing at all wrong here. What happens when you try to open Google with Firefox?

---

### Post by asan42 on 2013-06-14
when i first turn on my desktop and open Firefox it opens Google as the home page no problem. i can surf the internet for about approx one minute then it tells me Firefox cant find server at start.ubuntu.com and stays that way until i turn of completely and turn back on. then same thing.

---

### Post by chili555 on 2013-06-15
Very interesting. Please restart your computer surf the web until it drops out and then lets see if we can tell what's happening under the hood:```
cat /var/log/syslog | grep -e wlan -e ndis | tail -n20
```> Capabilities:
    Speed:           144 Mb/s

Is there any improvement if you turn off N speeds in the router?

---

### Post by asan42 on 2013-06-15
> **chili555 said:**
> Very interesting. Please restart your computer surf the web until it drops out and then lets see if we can tell what's happening under the hood:```
cat /var/log/syslog | grep -e wlan -e ndis | tail -n20
```Is there any improvement if you turn off N speeds in the router?

```
asan@minepc:~$ cat /var/log/syslog | grep -e wlan -e ndis | tail -n20Jun 15 11:43:09 minepc dhclient: DHCPREQUEST of 192.168.2.6 on wlan0 to 255.255.255.255 port 67
Jun 15 11:43:10 minepc avahi-daemon[998]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::120d:7fff:fe38:8f9e.
Jun 15 11:43:10 minepc avahi-daemon[998]: New relevant interface wlan0.IPv6 for mDNS.
Jun 15 11:43:10 minepc avahi-daemon[998]: Registering new address record for fe80::120d:7fff:fe38:8f9e on wlan0.*.
Jun 15 11:43:12 minepc dhclient: DHCPREQUEST of 192.168.2.6 on wlan0 to 255.255.255.255 port 67
Jun 15 11:43:12 minepc NetworkManager[907]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Jun 15 11:43:12 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 15 11:43:12 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 15 11:43:12 minepc avahi-daemon[998]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.2.6.
Jun 15 11:43:12 minepc avahi-daemon[998]: New relevant interface wlan0.IPv4 for mDNS.
Jun 15 11:43:12 minepc avahi-daemon[998]: Registering new address record for 192.168.2.6 on wlan0.IPv4.
Jun 15 11:43:13 minepc NetworkManager[907]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 15 11:43:13 minepc NetworkManager[907]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 15 11:43:13 minepc NetworkManager[907]: <info> Policy set 'belkin.991' (wlan0) as default for IPv4 routing and DNS.
Jun 15 11:43:13 minepc NetworkManager[907]: <info> Activation (wlan0) successful, device activated.
Jun 15 11:43:13 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 15 11:43:29 minepc NetworkManager[907]: <info> (wlan0): IP6 addrconf timed out or failed.
Jun 15 11:43:29 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 15 11:43:29 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 15 11:43:29 minepc NetworkManager[907]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
asan@minepc:~$ 

```

i changed settings on router and got same affect. you think it could be the router? should i change it out?

---

### Post by chili555 on 2013-06-15
> you think it could be the router? should i change it out? I think it's possible but doubtful. How do other devices associated with the same router perform? Perfectly or do they also slow to a crawl? 

Do you have a friend or neighbor you can test with? Does your wireless slow down there, too?

You might edit Network Manager to set IPv6 to 'Ignore;' please see attached.

Frankly, I see nothing to fix here. Your logs look just fine.

---

