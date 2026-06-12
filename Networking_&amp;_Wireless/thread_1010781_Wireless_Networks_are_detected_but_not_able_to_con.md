---
title: "Wireless Networks are detected but not able to connect"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by sudhar on 2008-12-14
Hi All,

I am new to Linux and I had installed Kubuntu 8.10. now I am facing the problem of wireless connection. Network manager shows the networks including mine. But not able to connect to any.

I tried the already existing Treads to solve the problem. but I am not able to figure it out.. so I am posting a new tread here..

Here is the console outputs from few commands

sudhar@sudhar-laptop:~$ sudo iwlist wlan0 freq
[sudo] password for sudhar:
wlan0     24 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.462 GHz (Channel 11)

sudo lshw -C network
  *-network
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:da:fb:00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:ad:1f:ff
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.100 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 26:80:45:d2:9e:94
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0C:F6:2B:61:E6
                    ESSID:"koets106"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=100/100  Signal level:-35 dBm  Noise level=-86 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000001bed1bac
                    Extra: Last beacon: 8ms ago


Log from /var/log/syslog

Dec 14 10:45:34 sudhar-laptop avahi-daemon[4931]: Interface eth0.IPv4 no longer relevant for mDNS.                                                                                                         
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) starting connection 'Auto koets106'                                                                                               
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  (wlan0): device state change: 3 -> 4                                                                                                                 
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...                                                                                        
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...                                                                                          
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...                                                                                      
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.                                                                                           
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...                                                                                       
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  (wlan0): device state change: 4 -> 5                                                                                                                 
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto koets106' requires no security.  No secrets needed.                                                    
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Config: added 'ssid' value 'koets106'                                                                                                                
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Config: added 'scan_ssid' value '1'                                                                                                                  
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE'                                                                                                                
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.                                                                                         
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  Config: set interface ap_scan to 1                                                                                                                   
Dec 14 10:45:49 sudhar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2                                                                                                  
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3                                                                                                  
Dec 14 10:46:03 sudhar-laptop kernel: [  845.370391] wlan0: authenticate with AP 00:0c:f6:2b:61:e6                                                                                                         
Dec 14 10:46:03 sudhar-laptop kernel: [  845.372431] wlan0: authenticated                                                                                                                                  
Dec 14 10:46:03 sudhar-laptop kernel: [  845.372443] wlan0: associate with AP 00:0c:f6:2b:61:e6                                                                                                            
Dec 14 10:46:03 sudhar-laptop kernel: [  845.375030] wlan0: RX ReassocResp from 00:0c:f6:2b:61:e6 (capab=0x421 status=0 aid=1)                                                                             
Dec 14 10:46:03 sudhar-laptop kernel: [  845.375042] wlan0: associated                                                                                                                                     
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4                                                                                                  
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7                                                                                                  
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'koets106'.
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  (wlan0): device state change: 5 -> 7
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction.
Dec 14 10:46:03 sudhar-laptop dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 14 10:46:03 sudhar-laptop dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 14 10:46:03 sudhar-laptop dhclient: All rights reserved.
Dec 14 10:46:03 sudhar-laptop dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Dec 14 10:46:03 sudhar-laptop dhclient:
Dec 14 10:46:03 sudhar-laptop dhclient: wmaster0: unknown hardware address type 801
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  dhclient started with pid 6609
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 14 10:46:03 sudhar-laptop NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit
Dec 14 10:46:03 sudhar-laptop dhclient: wmaster0: unknown hardware address type 801
Dec 14 10:46:03 sudhar-laptop dhclient: Listening on LPF/wlan0/00:16:ea:da:fb:00
Dec 14 10:46:03 sudhar-laptop dhclient: Sending on   LPF/wlan0/00:16:ea:da:fb:00
Dec 14 10:46:03 sudhar-laptop dhclient: Sending on   Socket/fallback
Dec 14 10:46:06 sudhar-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Dec 14 10:46:08 sudhar-laptop dhclient: DHCPOFFER of 192.168.0.102 from 192.168.0.1
Dec 14 10:46:08 sudhar-laptop dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67
Dec 14 10:46:11 sudhar-laptop dhclient: DHCPREQUEST of 192.168.0.102 on wlan0 to 255.255.255.255 port 67
Dec 14 10:46:19 sudhar-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
Dec 14 10:46:27 sudhar-laptop last message repeated 2 times
Dec 14 10:46:31 sudhar-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 14 10:46:37 sudhar-laptop dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it.
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6609
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled...
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started...
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  (wlan0): device state change: 7 -> 9
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (koets106)
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Marking connection 'Auto koets106' invalid.
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Activation (wlan0) failed.
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete.
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  (wlan0): device state change: 9 -> 3
Dec 14 10:46:48 sudhar-laptop NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Dec 14 10:46:48 sudhar-laptop kernel: [  890.595220] wlan0: disassociating by local choice (reason=3)
Dec 14 10:46:48 sudhar-laptop kernel: [  890.597969] wlan0: authenticate with AP 00:0c:f6:2b:61:e6
Dec 14 10:46:48 sudhar-laptop kernel: [  890.599900] wlan0: authenticated
Dec 14 10:46:48 sudhar-laptop kernel: [  890.599912] wlan0: associate with AP 00:0c:f6:2b:61:e6
Dec 14 10:46:48 sudhar-laptop kernel: [  890.602379] wlan0: RX AssocResp from 00:0c:f6:2b:61:e6 (capab=0x421 status=0 aid=1)
Dec 14 10:46:48 sudhar-laptop kernel: [  890.602389] wlan0: associated
Dec 14 10:46:48 sudhar-laptop kernel: [  890.642652] wlan0: disassociating by local choice (reason=3)

Currently I am able to connect through the ethernet(wired Network)...

Please help to solve the problem...

thanks in Advance..

Sudhar

---

### Post by Sava8420 on 2008-12-14
Is it possible that you are using a range expander on your network?
Post results of:
```
sudo iwconfig wlan0
sudo ifconfig wlan0
```
Also try running:
```
sudo dhclient wlan0
```
Otherwise I'd say it is in setting up your wireless router.  Hook up to it and log onto it's IP through your browser and check everything.

---

### Post by sudhar on 2008-12-15
Hi Sava,

Thanks for the Reply.

I am new to linux and I am not installed anything else(Range expander.. this is the first time I am hearing it :-))

I will try with the router configuration in the ip address..

meanwhile here is the console outputs for the commands u mentioned in the post...

sudo iwconfig wlan0
[sudo] password for sudhar:
wlan0     IEEE 802.11abgn  ESSID:"koets106"
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level:-40 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


sudo ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:16:ea:da:fb:00
          inet6 addr: fe80::216:eaff:feda:fb00/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:500 (500.0 B)  TX bytes:878 (878.0 B)
sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:16:ea:da:fb:00
Sending on   LPF/wlan0/00:16:ea:da:fb:00
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

Thanks..
Sudhar

---

### Post by Sava8420 on 2008-12-16
Try running code:
```
sudo modprobe iwlagn
``` 
Then try connecting to connection.  Also what I meant by Range Expander was like a signal booster device that you plug into your wall.  Gotta go will check back in the AM.

---

### Post by sudhar on 2008-12-16
There is no output for this command.

After  that I tried to connect to my network as well as some other network in the range and It's not connecting to any of the network.

No I am not using any device to increase the signal strength. I am using only the wireless router Sitecom ADSL2+ router 54G turbo 


Thanks for your reply..

Sudhar

---

### Post by Sava8420 on 2008-12-17
Ok, after reviewing the results from your log and from the results of iwconfig it appears to me that your encryption key is not there.  First thing I'd do is right click the network manager icon or go system> pref.> network manager then edit the "auto koets106" and make sure your encryption is set correctly.  This can all be done through the terminal as well and here is a thread that will explain how to setup your network properly through the terminal.  [http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
Hopefully this will get you connected, let me know what happens.

---

### Post by Pelee on 2009-01-09
> **Sava8420 said:**
> Try running code:
```
sudo modprobe iwlagn
```

Same 5100 AGN here, same problem, same "disassociate" message in dmesg. 
Interestingly loading this module seemed to help here.

Either that or I had been misspelling the password multiple times.

Thanks for the suggestion.

---

