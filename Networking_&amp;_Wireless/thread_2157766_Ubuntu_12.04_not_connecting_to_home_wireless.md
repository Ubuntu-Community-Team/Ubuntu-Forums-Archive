---
title: "Ubuntu 12.04 not connecting to home wireless"
date: 2013-06-26
forum: Networking &amp; Wireless
---

### Post by javeitch on 2013-06-26
Hi all,

I'm hoping someone can help me. I have recently bought a new Toshiba Portege ultrabook and installed Ubuntu 12.04 on it. Everything worked pretty much out of the box, except for the fact that the laptop will not connect to our home wireless (it does connect with the Ethernet cable and and all of the other laptops in the house connect to the home wireless - one has lucid lynx and the other is a mac running a windows operating system). My new laptop has not had any trouble connecting to any other wireless in any random place that I have been, just the wireless at home. 

I'm not that savvy when it comes to IT, but having read some other threads, I figure the outputs from the following commands would be useful:  



 ```
iwconfig
```  

```

lo        no wireless extensions.  

 

 usb0      no wireless extensions.  
 

 wlan0     IEEE 802.11abgn  ESSID:"Undercover Surveillance Van"   
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1D:92:1C:E9:B2    
           Bit Rate=1 Mb/s   Tx-Power=15 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  

           Power Management:on  
           Link Quality=56/70  Signal level=-54 dBm   
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0  
           Tx excessive retries:0  Invalid misc:2   Missed beacon:0  
 

 eth0      no wireless extensions.  

```
 
```

 sudo lshw -C network  

```
 
```

   *-network                

        description: Ethernet interface  
        product: 82579LM Gigabit Network Connection  
        vendor: Intel Corporation  

        physical id: 19  

        bus info: pci@0000:00:19.0  

        logical name: eth0  

        version: 04  
        serial: b8:6b:23:94:5d:12  
        width: 32 bits  
        clock: 33MHz  
        capabilities: pm msi cap_list ethernet physical  
        configuration: broadcast=yes driver=e1000e latency=0 multicast=yes  
        resources: irq:20 memory:e0600000-e061ffff memory:e063b000-e063bfff ioport:2080(size=32)  
   *-network  
        description: Wireless interface  
        product: Centrino Advanced-N 6235  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: wlan0  
        version: 24  
        serial: c8:f7:33:ee:89:b4  
        width: 64 bits  
        clock: 33MHz  
        capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-44-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn  
        resources: irq:45 memory:e0400000-e0401fff  
   *-network  
        description: Ethernet interface  
        physical id: 3  
        logical name: usb0  
        serial: 02:15:e0:ec:01:00  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=cdc_ncm driverversion=04-Aug-2011 firmware=CDC NCM link=no multicast=yes
```
 
```

 sudo -rfkill list all
```
 
```

 0: Toshiba Bluetooth: Bluetooth  
     Soft blocked: yes  
     Hard blocked: no  
 1: phy0: Wireless LAN  

     Soft blocked: no  
     Hard blocked: no  
 388: hci0: Bluetooth  
     Soft blocked: yes  

     Hard blocked: no  

```

I would appreciate and help or suggestions - this is driving me mad!

---

### Post by varunendra on 2013-06-26
Welcome to the forums javeitch !

Please follow the "Wireless Script" link in my signature below and post back the results as asked in the linked post. Thanks !

---

### Post by javeitch on 2013-06-26
Hi Varun,

Thanks for your speedy response! Below is the contents of the wireless-info.txt file (I had to use the ethernet cable to connect and the wireless connection that I am trying to connect to is called 'Undercover Surveillance Van').
 
```
*************** info trace ***************

***** uname -a *****

Linux jenny 3.2.0-44-generic #69-Ubuntu SMP Thu May 16 17:35:01 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

***** lspci *****

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Toshiba America Info Systems Device [1179:0002]
    Kernel driver in use: e1000e
--
02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi

***** lsusb *****

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b369 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 08ff:168b AuthenTec, Inc. 
Bus 002 Device 004: ID 0930:1319 Toshiba Corp. 
Bus 001 Device 004: ID 8087:07da Intel Corp. 

***** iwconfig *****

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

***** rfkill *****

0: Toshiba Bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

iwlwifi               401125  0 
mac80211              506862  1 iwlwifi
cfg80211              205774  2 iwlwifi,mac80211

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: ttyACM0 --------------------------------------------------------------
  Type:              Mobile Broadband (GSM)
  Driver:            cdc_acm
  State:             disconnected
  Default:           no

  Capabilities:


- Device: usb0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            cdc_ncm
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Duoplus:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA
    Undercover Surveillance Van: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 84 WEP


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         10.0.0.102
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.2

    DNS:             10.0.0.2



***** NetworkManager.state *****

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

auto lo
iface lo inet loopback


***** iwlist *****

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:on
                    ESSID:"Undercover Surveillance Van"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000039e653a1b8
                    Extra: Last beacon: 3124ms ago
                    IE: Unknown: 001B556E646572636F766572205375727665696C6C616E63652056616E
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
          Cell 02 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"Duoplus"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000feb7d243
                    Extra: Last beacon: 2748ms ago
                    IE: Unknown: 000744756F706C7573
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00


***** resolv.conf *****

nameserver 127.0.0.1

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    1.932284] iwlwifi 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.932315] iwlwifi 0000:02:00.0: setting latency timer to 64
[    1.932364] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[    1.932365] iwlwifi 0000:02:00.0: pci_resource_base = ffffc9000509c000
[    1.932367] iwlwifi 0000:02:00.0: HW Revision ID = 0x24
[    1.932632] iwlwifi 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.932740] iwlwifi 0000:02:00.0: Detected 6035 Series 2x2 AGN/BT, REV=0xB0
[    1.932919] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    1.949276] iwlwifi 0000:02:00.0: device EEPROM VER=0x756, CALIB=0x6
[    1.949280] iwlwifi 0000:02:00.0: Device SKU: 0X1f0
[    1.949282] iwlwifi 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[    1.960122] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    2.055232] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[    2.082247] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    2.359867] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.366407] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[    2.658557] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[    2.665101] iwlwifi 0000:02:00.0: Radio type=0x2-0x1-0x0
[    2.770209] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    2.771266] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   10.317997] wlan0: authenticate with <MAC address removed> (try 1)
[   10.320659] wlan0: authenticated
[   10.321103] wlan0: associate with <MAC address removed> (try 1)
[   10.323916] wlan0: RX AssocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   10.323919] wlan0: associated
[   10.328007] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   20.522700] wlan0: no IPv6 routers present
[   55.314338] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[   61.217301] wlan0: authenticate with <MAC address removed> (try 1)
[   61.219831] wlan0: authenticated
[   61.220284] wlan0: associate with <MAC address removed> (try 1)
[   61.222740] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[   61.222742] wlan0: associated
[   71.578747] wlan0: no IPv6 routers present
[  106.187399] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  112.139212] wlan0: authenticate with <MAC address removed> (try 1)
[  112.142298] wlan0: authenticated
[  112.142650] wlan0: associate with <MAC address removed> (try 1)
[  112.145040] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  112.145045] wlan0: associated
[  122.411113] wlan0: no IPv6 routers present
[  157.087529] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)
[  163.069322] wlan0: authenticate with <MAC address removed> (try 1)
[  163.071946] wlan0: authenticated
[  163.073154] wlan0: associate with <MAC address removed> (try 1)
[  163.075598] wlan0: RX ReassocResp from <MAC address removed> (capab=0x411 status=0 aid=3)
[  163.075609] wlan0: associated
[  173.243544] wlan0: no IPv6 routers present
[  208.037858] wlan0: deauthenticating from <MAC address removed> by local choice (reason=3)

****************** done ******************
```

---

### Post by varunendra on 2013-06-26
First of all, please use 'Code' tags to wrap commands and their outputs. Follow the "Code Tags example" link in my sig. to see an elaborated example of using it. Then edit your above post to wrap the output part in the code tags to make the output more readable. You'll like the way it looks after that :)

Onto the problem -
Please try :
```
sudo iwconfig wlan0 power off
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi swcrypto=1
```
This will work much better if you also change the encryption in the router from WEP to WPA2-PSK (AES).

The swcrypto=1 option is temporary and will be lost on reboot. We can make it permanent if it seems to help. If it doesn't (even after changing the encryption in the router), post back and we'll try something else.

---

### Post by javeitch on 2013-06-27
Thanks

FIrst problem is that I get an error when I run iwconfig wlan0 power off:

```


  	 	 	 	   iwconfig wlan0 power off 

 

 Error for wireless request "Set Power Management" (8B2C) :  
     SET failed on device wlan0 ; Operation not permitted.  


```

---

### Post by varunendra on 2013-06-27
Did you try it with "sudo" ?

And the next two commands do not depend upon the first one, so try them anyway.

---

### Post by javeitch on 2013-06-27
stupid! Didn't try with sudo.

Seems to have worked! How do I make the last command permanent?

Many many thanks

---

### Post by varunendra on 2013-06-27
> **javeitch said:**
> Seems to have worked!
Yippeee !

> How do I make the last command permanent?
Do this in the terminal -
```
echo "options iwlwifi swcrypto=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```

This will create a configuration file for the driver that will make it load with the "swcrypto=1" option automatically.

If the fix seems to be stable and permanent, please consider marking the thread as [SOLVED].

---

### Post by javeitch on 2013-06-27
Totally sorted - how long do I wait to check that the solution is stable before marking as solved? 

Thanks again!

---

### Post by varunendra on 2013-06-27
> **javeitch said:**
> Totally sorted - how long do I wait to check that the solution is stable before marking as solved?

Depends on how often do you think the variables (signal strength, traffic congestion due to neighbourhood networks, your location, workload, etc.) change, and how often you shutdown/reboot. Generally, a couple of days.. :)

---

### Post by javeitch on 2013-06-30
So, I've given it a couple of days and even after making the swcrypto=1 line permanent, my laptop stopped connecting - it worked for the first and second reboot but not after that. However, what seems to kick-start the wireless connection is the "sudo iwconfig wlan0 power off" line. This seems (touch wood!) to be quite reliable. Why would this be and what would cause such a problem? 

Thanks.

---

### Post by varunendra on 2013-07-01
> **javeitch said:**
> However, what seems to kick-start the wireless connection is the "sudo iwconfig wlan0 power off" line. This seems (touch wood!) to be quite reliable. Why would this be and what would cause such a problem?

Notebook wireless adapters often have a power saving mode to save battery power. It is supposed to kick in when there is no traffic (when the network is idle), and return to full (or optimal) power mode as soon as a traffic starts (network becomes active). However, certain driver/firmware bugs seem to fail to return (the device, or themselves) to active mode once they go to the idle mode.

The "iwconfig <interface> power off" command tries to turn this automatic power management off on the mentioned interface, thus offering better stability at the cost of power saving feature. It is supposed to be permanent (although I'm not very sure about this), but the intel drivers seem to have their own power management techniques, so one has to use the above command on each boot (or when required) if these inbuilt power management techniques don't work well with the OS.

Hope this gives a rough explanation of what happens and why. But this is just my own understanding, and I may be incorrect at some points.

That being said, if you think that the "power off" command makes it stable, you can make it run automatically at startup. Just add it to the "/etc/rc.local" file, above "exit 0" line :

[INDENT]1) Open the /etc/rc.local file as root -
```
gksu gedit /etc/rc.local
```

2) Insert this line just above the last line "exit 0" :
```
sleep 20 && iwconfig wlan0 power off
```
It is very important that the "exit 0" line remains the last line in the file ! Proofread, save and close the file.[/INDENT]

Since this file is run (at boot time) with root permissions, "sudo" is not needed. The "sleep 20" part makes sure that the command is run 20 seconds later after executing the file, thus allowing enough time for the wireless adapter to get ready. It may not be needed, but just to be extra sure..

Keep us posted if anything interesting happens. :)

---

### Post by javeitch on 2013-07-01
Thank you for that explanation. I appreciate all the help.

---

