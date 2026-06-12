---
title: "Wireless Disabled"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by miika71 on 2009-06-03
Hi ! I have installed 9.04 Netbook Remix on my Aspire On A531h. The tickbox for Enabling Wireless in the Network manager is greyed out.
 
I think it has to do with the WiFi "killswitch" on my hardware. It doesn´t seem to have any effect at all, so propably it is not supported in Ubuntu.
 
I use the standard driver, not the "madwifi" that is also included. 
 
Has anyone experienced the same and know what to do? Can the wifi be enabled/activated with command(s)?
 
BR /miika71, newbie

---

### Post by t0mppa on 2009-06-03
Wouldn't hurt to take a look at your configuration and find what's causing the problem to begin with. Might be it's as simple as bringing the interface up or then not. So, open up a terminal, run **lshw -C network** and post back with the output.

---

### Post by miika71 on 2009-06-03
This is the output from lshw -C:

*-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:23:8b:8b:3b:9c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI firmware=L1e latency=0 module=atl1e multicast=yes
  *-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:e4:3f:4a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:a3:fb:4e:ee:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Another thing worth mentioning, I downloaded RutilT WLAN Manager, and with that applicationit is possible to scan and detect networks using wlan0, but I can not activate it in the Network manager to use it to connect to the networks.So, the interface seem to be alive, but I can not use it.

---

### Post by superprash2003 on 2009-06-03
post output of the following
1)sudo iwlist scanning
2)iwconfig

---

### Post by ddrichardson on 2009-06-03
Is the acer_wmi module loaded?  On some kernels this inhibits the ath5k kernel module.

---

### Post by miika71 on 2009-06-03
Outputs from iwlist and iwconfig:

micke@acer-a531h:~$ sudo iwlist scanning
[sudo] password for micke: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:E7:E8:FB
                    ESSID:"hellgate"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=3/100  Signal level:-99 dBm  Noise level=-101 dBm
                    Encryption key:on
                    IE: Unknown: 000868656C6C67617465
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334C101FFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340600070000000F000000000000000000000000000000
                    IE: Unknown: 2D1A4C101FFFFF000000000000000000000000000004000000000000
                    IE: Unknown: 3D160600030000000F000000000000000000000000000000
                    IE: Unknown: DD790050F204104A0001101044000102103B0001031047001090B7399C3A153EBCB2511173D30CD4B21021000E442D4C696E6B2053797374656D73102300074449522D363135102400024232104200046E6F6E651054000800060050F204000110110011576972656C657373204E20526F75746572100800020004
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000037d82f7180
                    Extra: Last beacon: 1372ms ago
          Cell 02 - Address: 00:15:E9:0D:D.E:4C
                    ESSID:"ryttare2"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=1/100  Signal level:-100 dBm  Noise level=-101 dBm
                    Encryption keyn
                    IE: Unknown: 00087279747461726532
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000031bf348179
                    Extra: Last beacon: 1380ms ago
          Cell 03 - Address: 00:14:6C:96:DE:EC
                    ESSID:"MadameMim"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/100  Signal level:-87 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 00094D6164616D654D696D
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000014eb269f1
                    Extra: Last beacon: 916ms ago
          Cell 04 - Address: 00:01:38:73:6C:1F
                    ESSID:"B2_private_4B"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=10/100  Signal level:-93 dBm  Noise level=-100 dBm
                    Encryption key:on
                    IE: Unknown: 000D42325F707269766174655F3442
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000037d5225e97
                    Extra: Last beacon: 912ms ago
          Cell 05 - Address: 00:90:D0:E0:BF:CC
                    ESSID:"SpeedTouchEB36D6"
                    Mode:Master
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=255/100  Signal level:-102 dBm  Noise level=-101 dBm
                    Encryption key:off
                    IE: Unknown: 00105370656564546F756368454233364436
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD060010180202F0
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000037d5ce3962
                    Extra: Last beacon: 1176ms ago

pan0      Interface doesn't support scanning.

ppp0      Interface doesn't support scanning.

micke@acer-a531h:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"TrollboNet1"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.

micke@acer-a531h:~$

---

### Post by miika71 on 2009-06-03
> **ddrichardson said:**
> Is the acer_wmi module loaded?  On some kernels this inhibits the ath5k kernel module.
Hi, how can I check if the Acer_WMI module is loaded?

---

### Post by ddrichardson on 2009-06-03
> **miika71 said:**
> Hi, how can I check if the Acer_WMI module is loaded?
```
lsmod | grep acer
```If its blank then it isn't that.

---

### Post by miika71 on 2009-06-03
It seem to be there!
What should I do?

micke@acer-a531h:~$ lsmod | grep acer
acer_wmi               24260  0 
led_class              12036  2 ath5k,acer_wmi

---

### Post by ddrichardson on 2009-06-03
You can remove it (temporarily) by```
sudo rmmod acer_wmi
```If it helps then blacklist it.

---

### Post by miika71 on 2009-06-03
Damnit! It worked! Thanks a million! How do I do to blacklist it? Will it then be disabled when I reboot as well?

---

### Post by ddrichardson on 2009-06-03
Edit /etc/modprobe.d/blacklist.conf and add a line:```
blacklist acer_wmi
```

---

### Post by ddrichardson on 2009-06-03
I meant to say, keep an eye on automatic updates because this will likely change in the future.  The acer_wmi module doesn't inhibit on my current kernel (I'd say the number but I can't be nadged to go up stairs, turn it on and type uname -r to find out what the current Arch kernel image is).

---

### Post by miika71 on 2009-06-04
> **ddrichardson said:**
> I meant to say, keep an eye on automatic updates because this will likely change in the future.  The acer_wmi module doesn't inhibit on my current kernel (I'd say the number but I can't be nadged to go up stairs, turn it on and type uname -r to find out what the current Arch kernel image is).
Yeah, I will definet&#314;y keep an eye on this: Anyway, thanks alot for the help! /miika71

---

### Post by ddrichardson on 2009-06-04
Glad it fixed it for you. Its been surprising how many times updates have caused me problems on my Aspire One.

---

