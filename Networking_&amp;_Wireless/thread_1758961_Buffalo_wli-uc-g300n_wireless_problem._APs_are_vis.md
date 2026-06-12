---
title: "Buffalo wli-uc-g300n wireless problem. APs are visible but not able to connect."
date: 2011-05-15
forum: Networking &amp; Wireless
---

### Post by MrkS on 2011-05-15
Hi,

I have tried to get familiar with ubuntu and kubuntu few times. With kubuntu I had multi-display problem which I couldn't solve myself. Then I changed to ubuntu 10.04 and 10.10. I did not have multi-display problem but wireless network problem which I could not solve myself either.
I try once more with ubuntu 11.04 but now I try to use your help to progress to avoid many days and evenings wasted time.

So again I have problem to connect to wireless network.
- I can see wireless access points
- When I try to connect one of them after entering router password after a moment I get error to not able to connect and I am asked the password again. (WPA & WPA2)
- Wired network works ok.
- Router is Buffalo WBMR-G125
- Wireless USB adapter is Buffalo WLI-UC-G300n 
- Computer is self made PC with Asus M4 motherboard

Some commands and results:


**2 ) Wireless Brand, Model and Wireless Chipset:**
```
$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 413c:2010 Dell Computer Corp. 
Bus 003 Device 003: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 005: ID 0411:016f MelCo., Inc. **
Bus 001 Device 002: ID 03f0:c202 Hewlett-Packard PhotoSmart 8200 series
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```**3 ) check interface:**
```
$ ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:24:a5:86:49:d5  
          inet6 addr: fe80::224:a5ff:fe86:49d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:18105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1526 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1974743 (1.9 MB)  TX bytes:102113 (102.1 KB)

$ iwconfig
wlan0     Ralink STA  ESSID:""  Nickname:"RT2870STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=86/100  Signal level:-56 dBm  Noise level:-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```**4 ) Check for modules:**
```
$ lsmod | grep "2870"
rt2870sta             410104  1 
crc_ccitt              12595  1 rt2870sta
```**5 ) Kernel boot messages**
```
$ dmesg | grep "2870"
[   11.481375] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[   11.590831] usbcore: registered new interface driver rt2870
```**6 ) Network configuration**
```
$ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       bus info: firewire@1
       logical name: wlan0
       serial: 00:24:a5:86:49:d5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=usb multicast=yes wireless=Ralink STA
```**7 ) Scan for networks:**
```
$ iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:16:01:A2:C9:16
                    Protocol:802.11b/g
                    ESSID:"_mms_"
                    Mode:Managed
                    Channel:1
                    Quality:86/100  Signal level:-56 dBm  Noise level:-53 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
```**8 ) Ubuntu Version: **
```
$ lsb_release -d
Description:    Ubuntu 11.04
```**9 ) Kernel/architecture (including 32 vs. 64 bit): **
```
$ uname -mr
2.6.38-8-generic-pae i686
```**10 ) Restarting the network:**
```
$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
   ...done.
``````
$ nm-tool
- Device: wlan0  [Auto _mms_] --------------------------------------------------
  Type:              802.11 WiFi
  Driver:            usb
  State:             connecting (need authentication)
  Default:           no
  HW Address:        00:24:A5:86:49:D5

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    _mms_:           Infra, 00:16:01:A2:C9:16, Freq 2412 MHz, Rate 54 Mb/s, Strength 81 WPA
```

---

### Post by MrkS on 2011-05-15
Well... The solution was this time very easy. 
I restarted my router box when computer was trying to establish the connection and after that I got connected to Internet.
I cannot remember if I tried this with earlier ubuntus or not...

---

