---
title: "Why does wireless hate me?"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by sovelliss06 on 2011-09-02
Running a compaq C700 with the latest ubuntu. My wireless 'sees' networks, and I can try to log into my router, but no matter what I do it won't connect, telling me I have a bad password. The password is correct. The encryption is correct. I'm guessing the driver might be fuggered, which I'm not sure how to fix. I can't find any driver updates for my comp online. I found one thread relating to the subject, but I couldn't download the packages needed for the step-by-step as the files were missing. I just want my wireless... please help...

---

### Post by fdrake on 2011-09-02
lets's just make sure you have all that you need installed
run in the terminal
```

sudo apt-get install --reinstall linux-headers-$(uname -r)
sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
sudo aptitude update
sudo aptitude upgrade

```

then post here the results of these commands please:
```
sudo lshw -c network
sudo iwlist scan
nm-tool
```
what's your networks name?

---

### Post by sovelliss06 on 2011-09-02
I had some problems with the second command line, as it came up with:

raatz@Un-versed:~$ sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-natty-generic

Haven't yet put in the other set of commands. Doing that now... NETGEAR is the name of my wireless network by the way.

The first line

```
raatz@Un-versed:~$ sudo lshw -c network
PCI (sysfs)  
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 01
       serial: 00:1f:3a:6d:ab:fa
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.38-11-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:91300000-9130ffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:1e:ec:1d:a4:51
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.3 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:1000(size=256) memory:91200000-912000ff

The second line gives me

raatz@Un-versed:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:C1:C0:11:AC:81
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption keyff
                    ESSID:"Trinity-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038429ccaa4
                    Extra: Last beacon: 532ms ago
                    IE: Unknown: 000D5472696E6974792D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 02 - Address: C4:3D:C7:5D:F0:AC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-43 dBm  
                    Encryption keyn
                    ESSID:"NETGEAR"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000016ab4b1e68d
                    Extra: Last beacon: 260ms ago
                    IE: Unknown: 00074E455447454152
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700103A0EBDE29A179419D13CCDE25A6200941021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103
                    IE: Unknown: DD090010180201F0050000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406001300000000000000000000000000000000000000
          Cell 03 - Address: C0:C1:C0:11:AC:80
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption keyn
                    ESSID:"Trinity"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000038429cc22e
                    Extra: Last beacon: 536ms ago
                    IE: Unknown: 00075472696E697479
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001700000000000000000000000000000000000000
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010B51BCBAAB559E9C644F5E5105BAC30FB102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180202F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
          Cell 04 - Address: 40:4A:03:E0:83:D5
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption keyn
                    ESSID:"KKAH"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000072d02e73c6
                    Extra: Last beacon: 640ms ago
                    IE: Unknown: 00044B4B4148
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 050C010300000000000000000000
                    IE: Unknown: 2A0103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102
          Cell 05 - Address: 00:26:F2:77:53:D0
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption keyn
                    ESSID:"The_Collective"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000501685dbe3
                    Extra: Last beacon: 312ms ago
                    IE: Unknown: 000E5468655F436F6C6C656374697665
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 06 - Address: 68:7F:74:A3:30:C9
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=23/70  Signal level=-87 dBm  
                    Encryption keyn
                    ESSID:"Cisco19674"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000010aa44ac17
                    Extra: Last beacon: 28ms ago
                    IE: Unknown: 000A436973636F3139363734
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 2F0106
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7A0050F204104A00011010440001021041000100103B000103104700103BD0336C11821D77C48854F820346FA310210005436973636F1023000D4C696E6B7379732045333030301024000776312E302E30341042000234321054000800060050F20400011011000D4C696E6B737973204533303030100800020084
                    IE: Unknown: DD090010180205F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C33FC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B001700000000000000000000000000000000000000

And the last line...

raatz@Un-versed:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             connected
  Default:           yes
  HW Address:        00:1E:EC:1D:A4:51

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        00:1F:3A:6D:AB:FA

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Gary's Net:      Infra, 00:24:B2:0E4:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WEP
    myqwest9660:     Infra, 40:4A:03D:36:4B, Freq 2412 MHz, Rate 54 Mb/s, Strength 18 WPA WPA2
    bailey:          Infra, 00:1E:E5:41:8F:31, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    The_Collective:  Infra, 00:26:F2:77:530, Freq 2437 MHz, Rate 54 Mb/s, Strength 28 WPA WPA2
    LOVE:            Infra, 00:0F:B3:1C:AF:6D, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WEP
    Go Big:          Infra, 00:23:69:9B:213, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    KKAH:            Infra, 40:4A:03:E0:835, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    Trinity-guest:   Infra, C0:C1:C0:11:AC:81, Freq 2412 MHz, Rate 54 Mb/s, Strength 42
    Cisco19674:      Infra, 68:7F:74:A3:30:C9, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA WPA2
    Trinity:         Infra, C0:C1:C0:11:AC:80, Freq 2412 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    NETGEAR:         Infra, C4:3D:C7:5D:F0:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

```
Still won't let me connect. Any ideas?

---

### Post by wildmanne39 on 2011-09-02
Hi which network are you trying to connect too?

---

### Post by sovelliss06 on 2011-09-03
Trying to connect to NETGEAR. Any idea what's wrong with that second command line? My guess is maybe a typo?

---

### Post by wildmanne39 on 2011-09-03
Hi, I have been looking over your information, the command you used is a little different then the one I use.

I do not believe you need to worry about that command your wireless is seeing networks so your driver and firmware is installed and working.

Please post the results of these commands so we can figure out the problem.

```
rfkill list all
```
```
dmesg | grep wlan0
```
```
dmesg | grep ath
```
```
lsmod | grep ath
```
Thank you

---

### Post by sovelliss06 on 2011-09-03
Alright. Here's the whole thing. I appreciate the help.

raatz@Un-versed:~$ rfkill list all
\0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

--

raatz@Un-versed:~$ \dmesg | grep wlan0
[   25.307259] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2565.195451] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2565.247922] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2567.374453] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2567.789439] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2575.314890] ADDRCONF(NETDEV_UP): wlan0: link is not ready

--

raatz@Un-versed:~$ dmesg | grep ath
[    1.304746] device-mapper: multipath: version 1.2.0 loaded
[    1.304750] device-mapper: multipath round-robin: version 1.0.0 loaded
[   24.567494] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.567514] ath5k 0000:01:00.0: setting latency timer to 64
[   24.567593] ath5k 0000:01:00.0: registered as 'phy0'
[   25.072028] ath: EEPROM regdomain: 0x64
[   25.072032] ath: EEPROM indicates we should expect a direct regpair map
[   25.072037] ath: Country alpha2 being used: 00
[   25.072040] ath: Regpair used: 0x64
[   25.252559] Registered led device: ath5k-phy0::rx
[   25.252592] Registered led device: ath5k-phy0::tx
[   25.252605] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[ 2569.952122] ath5k 0000:01:00.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 2569.952153] ath5k 0000:01:00.0: restoring config space at offset 0x4 (was 0x4, writing 0x91300004)
[ 2569.952161] ath5k 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 2569.952171] ath5k 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007)

--

raatz@Un-versed:~$ lsmod | grep ath
ath5k                 144534  0 
ath                    19141  1 ath5k
mac80211              257001  1 ath5k
cfg80211              156212  3 ath5k,ath,mac80211

---

### Post by wildmanne39 on 2011-09-03
Hi, disable encryption in your router then see if you can connect if so then set your router to wpa2 AES not mixed mode or any other option.
Thank you

---

### Post by fdrake on 2011-09-03
> raatz@Un-versed:~$ sudo apt-get install --reinstall linux-backports-modules-wireless-$(less /etc/lsb-release | grep "DISTRIB_CODENAME=" | cut -d "=" -f 2)-$(uname -r | cut -d "-" -f 3)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-natty-generic

Ohh you are using natty, then change the command to this:
```

sudo apt-get install --reinstall linux-backports-modules-cw-2.6.39-natty-generic 
``` Make sure you shout down and start(do not do reboot option) 

@wildmanne39 it looks like the router Netgear has only WAP2 encryption, no mixmode issue in here, but let's just see if he can connect to an open network. 
> 
IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK


> NETGEAR:         Infra, C4:3D:C7:5D:F0:AC, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2

you error dmsg does not say much: try please and post here the following command:
```
less /var/log/syslog | grep "Sep  3" |grep -e wlan0 -e etwork -e ath -e radio | less 
```

---

### Post by wildmanne39 on 2011-09-03
Hi fdrake, I was thinking the same thing about connecting with no encryption.

---

### Post by northd_tech on 2011-09-03
> **fdrake said:**
> 
you error dmsg does not say much: try please and post here the following command:
```
less /var/log/syslog | grep "Sep  3" |grep -e wlan0 -e etwork -e ath -e radio | less 
```

Wow- that's a "fur'ly" dangerous 'plumber" with all those [e]**grep** 'pipes' feeding all back in on themselves without causing a flood somewhere!

In honor of all that **masterful** 'piping' may I dedicate this song to [COLOR=Blue]fdrake[/COLOR]:

**Uneasy Rider (LIVE) 1973-Charlie Daniels **

[http://www.youtube.com/watch?v=5e8fqO245SY](http://www.youtube.com/watch?v=5e8fqO245SY)

[See at ~03:41 in that particular vid (and please forgive Charlie's "un-PC" language, but it was 1973 and the Southern US, or so- and I'm somewhat surprised that I even remembered that "fur'ly dangerous" line this many years/beers later... ;) .  Also, I'm mostly kidding here, but I'm honestly somewhat in awe of [COLOR=Blue]fdrake[/COLOR]- I had forgotten that you could multi-pipe more than 1 or 2 levels of input/output...  =D>]

---

### Post by fdrake on 2011-09-03
:p
like the song!

---

### Post by sovelliss06 on 2011-09-04
[FONT=monospace]To Fdrake

Okay, so when I type in 
[/FONT]
less /var/log/syslog | grep "Sep  3" |grep -e wlan0 -e etwork -e ath -e radio | less
~
~
~
~
~
(END)

And when I try to exit from the terminal it tells me the program is still running, although I let it run for a bit and nothing happened.

To Wildmanne

I don't have access to the router, so I'll have to wait until my roommate gets home, but I'll let you know how it turns out.


Again, thanks for all the help.

---

### Post by fdrake on 2011-09-04
what about:
```

less /var/log/syslog | tail -100 |grep -e wlan0 -e etwork -e ath -e radio | less

```

---

### Post by sovelliss06 on 2011-09-05
Sep  5 11:17:18 Un-versed dhclient: Sending on   LPF/wlan0/00:1f:3a:6d:ab:fa
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> (wlan0): supplicant interface state:  starting -> ready
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info>   address 192.168.1.3
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info>   prefix 24 (255.255.255.0)
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info>   gateway 192.168.1.1
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info>   nameserver '192.168.1.1'
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Scheduling stage 5
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Done scheduling stage 5
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep  5 11:17:18 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Sep  5 11:17:18 Un-versed kernel: [14418.067797] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Sep  5 11:17:18 Un-versed dhclient: receive_packet failed on eth0: Network is down
Sep  5 11:17:18 Un-versed dhclient: receive_packet failed on eth0: Network is down
Sep  5 11:17:18 Un-versed dhclient: send_packet: Network is unreachable
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> Activation (eth0) successful, device activated.
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Sep  5 11:17:19 Un-versed NetworkManager[483]: <info> (eth0): carrier now ON (de:

If I hit the arrow keys new prompts will come up but I can only copy what's in the terminal window. This is the default window.

---

### Post by sovelliss06 on 2011-09-08
Any word? I'm still lost here..

---

### Post by praseodym on 2011-09-08
You can try alternatively the madwifi driver instead of ath5k:

```
sudo apt-get install linux-headers-generic dkms build-essential
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
tar xvf madwifi-hal-0.10.5.6-r4126-20100324.tar.gz
cd madwifi-hal-0.10.5.6-r*
make
sudo make uninstall
sudo make install 
```
After that:

```
gksudo gedit /etc/modprobe.d/blacklist-ath_pci.conf
```

Change to:

```
## Madwifi available
[COLOR="Red"]#[/COLOR] blacklist ath_pci

## ath5k block
blacklist ath5k
```
save, exit and reboot. Check:

```
iwconfig
lsmod | grep ath
dmesg | grep ath
sudo iwlist scan
rfkill list
```

---

