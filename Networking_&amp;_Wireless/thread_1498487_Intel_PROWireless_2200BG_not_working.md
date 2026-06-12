---
title: "Intel PRO/Wireless 2200BG not working"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by nlocnilretsim on 2010-05-31
I'm running Ubuntu 9.10 on a Gateway M520 laptop, and after failing to get the Broadcom wireless chip that came with it working I swapped it out for an Intel PRO/Wireless 2200BG.  Unfortunately, I haven't been able to get wireless to work.  The chip doesn't appear to be turned on (it is detected though), and the hotkey to switch wireless on/off (Fn+F2) doesn't work in Ubuntu.  I also am not sure if I have the proper drivers to get the chip working with Ubuntu, and I'm not sure how to figure that out.

Since I've noticed it's asked for a lot, here's the output for iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth2      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Any help would be appreciated.  I've only been using Linux for a few months, and this is the first troubleshooting I've had to do, and after trying to find a solution for this problem online, I'm at a loss.

Thanks

---

### Post by mikewhatever on 2010-05-31
To verify if the driver is loaded, post the output of **sudo lshw -C network**

---

### Post by nlocnilretsim on 2010-06-01
Here's the output of [B]sudo lshw -C network:

  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:12:44:35
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=152.228.242.173 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:19 memory:e00fc000-e00fdfff memory:24000000-2401ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth2
       version: 05
       serial: 00:13:ce:db:dc:27
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:18 memory:e00fe000-e00fefff
[/B]
Thanks, one problem down, so it looks like the driver is there, but I can't get the wireless card to turn on.

Suggestions?

---

### Post by mikewhatever on 2010-06-02
Try the following command:
```
sudo ifconfig eth2 up
```

---

### Post by nlocnilretsim on 2010-06-02
> **mikewhatever said:**
> Try the following command:
```
sudo ifconfig eth2 up
```

I tried it, and it didn't seem to have any effect.

---

### Post by mikewhatever on 2010-06-02
Right, so let's start from the beginning. What happens when you click the network manager applet in the panel? Do you see your network, or any network? Can you also post the output of the following:
```
cat /etc/network/interfaces
```

---

### Post by nlocnilretsim on 2010-06-03
Well, the network manager doesn't detect any wireless networks. It just says "disconnected,"

and here's the output for cat /etc/network/interfaces:

```
auto lo
iface lo inet loopback
```

---

### Post by mikewhatever on 2010-06-03
Odd indeed. I'll go ask google about it. Meanwhile, try the following:
nm-tools
sudo iwlist eth2 scan

---

### Post by nlocnilretsim on 2010-06-04
nm-tool:

```
- Device: eth2 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:13:CE:DB:DC:27

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
```and sudo iwlist eth2 scan:

```
eth2      No scan results
```

---

### Post by krelverehan on 2011-04-21
I am having similar problems with my toshiba laptop with the same 2200BG wireless card. I can see the wireless networks... But when I try to connect to any of them it informs me that I am disconnected from the wireless network before I have a chance to enter any password information.

I feel like I am sooooo close to having wireless working. The funny thing is that the wireless worked from the boot cd when I was trying it out...

Here is some common info:

```
**krel@little-nams:~$ nm-tool**

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:11:2F:16:54:28

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             disconnected
  Default:           no
  HW Address:        00:0E:35:39:D7:03

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    internet free internet: Infra, 00:25:9C:54:BF:0A, Freq 2412 MHz, Rate 54 Mb/s, Strength 95 WPA2
    internet free internet: Infra, E0:CB:4E:FE:21:0C, Freq 2412 MHz, Rate 54 Mb/s, Strength 61 WPA2
    Parker:          Infra, 34:EF:44:0B:D7:31, Freq 2447 MHz, Rate 54 Mb/s, Strength 42
    Jeggings:        Infra, 00:14:D1:3F:A9:20, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2
```

```
**krel@little-nams:~$ sudo lshw -C network**
[sudo] password for krel: 
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:39:d7:03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:fe8fd000-fe8fdfff
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VM (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:11:2f:16:54:28
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.140 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:fe8fe000-fe8fefff ioport:cc00(size=64)
```


```
**krel@little-nams:~$ cat /etc/network/interfaces **
auto lo
iface lo inet loopback
```

```
**krel@little-nams:~$ sudo iwlist eth2 scan**
eth2      Interface doesn't support scanning.
```

```
**krel@little-nams:~$ sudo iwlist eth1 scan**
eth1      Scan completed :
          Cell 01 - Address: 00:25:9C:54:BF:0A
                    ESSID:"internet free internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=95/100  Signal level=-32 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 172ms ago
          Cell 02 - Address: E0:CB:4E:FE:21:0C
                    ESSID:"internet free internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=64/100  Signal level=-62 dBm  
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 196ms ago
          Cell 03 - Address: 34:EF:44:0B:D7:31
                    ESSID:"Parker"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    Extra: Last beacon: 72ms ago
```

This all being said, my wired connection works, and it isn't a problem with the wireless signal, because many other devices in the house are connecting fine from the the router at much greater distances, and the laptop could connect to the wireless network using the boot CD before I installed...

Any help would be greatly appreciated!

-KV

---

### Post by chili555 on 2011-04-21
You have a wired connection:>        configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A [COLOR="Red"]ip=192.168.1.140[/COLOR] latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:fe8fe000-fe8fefff ioport:cc00(size=64)Network Manager is designed to disallow a wireless connection if wired is available: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themPlease detach the ethernet cable and try again.

---

### Post by krelverehan on 2011-04-21
> **chili555 said:**
> You have a wired connection:Network Manager is designed to disallow a wireless connection if wired is available: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)Please detach the ethernet cable and try again.

I just tried with it unplugged and it does the same thing (even after a restart without the wired network). It automaticly tells me that I am disconnected right after I try to join a network.

It reads:
> Wireless network disconnected - you are now offline

---

### Post by chili555 on 2011-04-21
Please run and post, with the ethernet cable disconnected:```
rfkill list all
dmesg | grep ipw
```Thanks.

---

### Post by krelverehan on 2011-04-21
> **chili555 said:**
> Please run and post, with the ethernet cable disconnected:```
rfkill list all
dmesg | grep ipw
```Thanks.


```
**krel@little-nams:~$ rfkill list all**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```
```
**krel@little-nams:~$ dmesg | grep ipw**
[   15.901126] libipw: 802.11 data/management/control stack, git-1.1.13
[   15.901130] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.935431] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   15.935434] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   15.935572] ipw2200 0000:01:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.940025] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   16.311774] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
```

---

### Post by chili555 on 2011-04-21
Wonderful! Everything looks perfect...'cept it won't work.> Cell 01 - Address: 00:25:9C:54:BF:0A
                    ESSID:"internet free internet"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
Is this the cell you are trying to connect with? I wonder if there is a problem because there are spaces in the name.

Googling...

Are you asked for the WPA password?

---

### Post by krelverehan on 2011-04-21
> **chili555 said:**
> Wonderful! Everything looks perfect...'cept it won't work.Is this the cell you are trying to connect with? I wonder if there is a problem because there are spaces in the name.

Googling...

Are you asked for the WPA password?

This is the cell, yes. And no, the window to enter the password only briefly appears for a nanosecond before closing and a notification window tells me I am offline. And also, it does the exact same nonsense when I try to connect to any other network, it just tells my I am offline right after I click on it, without asking for a  password.... Maybe it is a software problem... Would trying wifi radar or another problem possibly fix it?

-KV

---

### Post by josephmills on 2011-04-21
I am verry new at all this myself but could we please see a ```
lsmod | grep ipw 
``` also could you go to ** system-->preferences-->password and encryption keys  **then delete any old ones that might be getting in the way

---

### Post by krelverehan on 2011-04-21
> **josephmills said:**
> I am verry new at all this myself but could we please see a ```
lsmod | grep ipw 
``` also could you go to ** system-->preferences-->password and encryption keys  **then delete any old ones that might be getting in the way

Old passwords are deleted...

```
**krel@little-nams:~$ lsmod | grep ipw**
ipw2200               145664  0 
libipw                 46641  1 ipw2200
cfg80211              156212  2 ipw2200,libipw
lib80211               14570  2 ipw2200,libipw
```

---

### Post by krelverehan on 2011-04-21
Good new! I was able to connect to my wireless network!

With some messing around all I had to do was to manually add the connection by right clicking the network icon in the taskbar >> edit connections >> wireless tab >> + add >> and entering the SSID and the wpa2 password, and letting the rest sort it out.

Apparently some software malfunction wouldn't allow to just to connect by clicking the network on the drop-down list... I bet there is a fancy way to do it by terminal, which would bypass using the sloppy GUI altogether, but I have no such skills.


Thanks for all your patience!

-KV

---

