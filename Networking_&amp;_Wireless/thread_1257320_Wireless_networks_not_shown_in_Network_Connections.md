---
title: "Wireless networks not shown in Network Connections (but shown in Terminal!)"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by rok.geo on 2009-09-03
Hello,

Totally new to ubuntu and linux in general. Did my very best of trying to get this working ... after the whole day I'm resorting to the community in hope for some guidance.

PROBLEM: Cannot connect to the internet through a wireless network card.

WIRELESS NETWORK PCI CARD: Canyon CN-*WF511*

I've set a dual boot (XP professional/Ubuntu 9.04) on my old PC. Downloaded drivers from the internet to get the network card working in XP - worked perfectly. After installing ubuntu there was no internet "from-the-box" so I've started googling.

After installing ndiswrapper/ndisgtk from the live CD (followed abyssius' instructions [here]("http://ubuntuforums.org/showthread.php?t=905069")) I've installed this network card's xp drivers (rt2500) only to find the Wireless Network Drivers program saying (after successfully installing the driver): "Hardware present: No".

"Enable Networking" and "Enable Wireless" are both enabled!

Like stated in the title I get 0 wireless networks shown in Network Connection app. I dug deeper so I've started typing things into the Terminal :)


$ lspci
 ```
    
....
02:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
....
  
```$ sudo lshw -c network
```
    *-network               
           description: Wireless interface
    **       product: RT2561/RT61 802.11g PCI**
           vendor: RaLink
           physical id: 6
           bus info: pci@0000:02:06.0
    **       logical name: wmaster0**
           version: 00
           serial: 00:0e:2e:bd:61:ab
           width: 32 bits
           clock: 33MHz
           capabilities: pm bus_master cap_list logical ethernet physical wireless
           configuration: broadcast=yes **driver=rt61pci** latency=32 module=rt61pci multicast=yes wireless=IEEE 802.11bg
      ***-network DISABLED**
           description: Ethernet interface
           physical id: 1
           logical name: pan0
           serial: 62:26:11:d2:85:50
           capabilities: ethernet physical
           configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
    
```$ ifconfig
```
    lo        Link encap:Local Loopback  
            inet addr:127.0.0.1  Mask:255.0.0.0 
            inet6 addr: ::1/128 Scope:Host 
            UP LOOPBACK RUNNING  MTU:16436  Metric:1 
            RX packets:4 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:4 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:0 
            RX bytes:276 (276.0 B)  TX bytes:276 (276.0 B) 
   
  wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:bd:61:ab  
            UP BROADCAST MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
   
  wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-BD-61-AB-00-00-00-00-00-00-00-00-00-00  
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
            RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
            TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
            collisions:0 txqueuelen:1000 
            RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
  
```$ iwconfig
 ```
    lo        no wireless extensions. 
   
  wmaster0  no wireless extensions. 
   
  wlan0     IEEE 802.11bg  ESSID:"MLWI-FI"  
            Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
            Tx-Power=5 dBm   
            Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
            Power Management:off 
            Link Quality:0  Signal level:0  Noise level:0 
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
   
  [FONT=&quot]pan0      no wireless extensions.[/FONT]
```$ iwlist scan
```
    lo        Interface doesn't support scanning.
     
   
  wmaster0  Interface doesn't support scanning.
     
   
  wlan0     No scan results




pan0  Interface doesn't support scanning.
    
```However! .. [with sudo added]("http://xkcd.com/149/"):

$ sudo iwlist scan
```
    lo        Interface doesn't support scanning.
     
   
  wmaster0  Interface doesn't support scanning.
     
   
  wlan0     Scan completed :
              Cell 01 - Address: 00:1A:92:50:99:D5
                        ESSID:"MLWI-FI"
                        Mode:Master
                        Channel:6
                        Frequency:2.437 GHz (Channel 6)
                        Quality=53/100  Signal level:-42 dBm  
                        Encryption key:off
                        IE: Unknown: 00074D4C57492D4649
                        IE: Unknown: 010882848B962430486C
                        IE: Unknown: 030106
                        IE: Unknown: 2A0100
                        IE: Unknown: 2F0100
                        IE: Unknown: 32040C121860
                        IE: Unknown: DD06001018020001
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                                  24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                                  12 Mb/s; 48 Mb/s
                        Extra:tsf=0000066fb9e9fef9
                        Extra: Last beacon: 7360ms ago
              Cell 02 - Address: 00:16:01:2E:77:DB
                        ESSID:"0016012E77DA"
                        Mode:Master
                        Channel:1
                        Frequency:2.412 GHz (Channel 1)
                        Quality=51/100  Signal level:-50 dBm  
                        Encryption key:on
                        IE: Unknown: 000C303031363031324537374441
                        IE: Unknown: 010482848B96
                        IE: Unknown: 030101
                        IE: Unknown: 2A0104
                        IE: Unknown: 2F0104
                        IE: Unknown: 32080C1218243048606C
                        IE: Unknown: DD060010180202F1
                        IE: WPA Version 1
                            Group Cipher : CCMP
                            Pairwise Ciphers (1) : CCMP
                            Authentication Suites (1) : PSK
                        Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                                  9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                                  48 Mb/s; 54 Mb/s
                        Extra:tsf=00000011e44e81cf
    [FONT=&quot]                    Extra: Last beacon: 7420ms ago[/FONT]   


....... + 7 more networks..




    pan0      Interface doesn't support scanning.
  
  
  
```Okay ... so the device is still DISABLED but it can find networks.. to which I'm unable to connect.. :confused:
[SIZE=2]
So I've tried to connect to my "target" network 0016012E77DA (secured) and to my neighbor's unsecured  MLWI-FI directlly from the Terminal. No success (not sure if correct commands were used?):[/SIZE][FONT=&quot]

[/FONT]```
    rok@rok-desktop:~$ sudo iwconfig wmaster0 essid 0016012E77DA key s:xxxxxxxxx

    Error for wireless request "Set ESSID" (8B1A) :
        SET failed on device wmaster0 ; Operation not supported.
    rok@rok-desktop:~$ sudo iwconfig wmaster0 essid MLWI-FI
    Error for wireless request "Set ESSID" (8B1A) :
        SET failed on device wmaster0 ; Operation not supported.
    
```What surprised me the most was that the scan found wireless networks on wlan0 whereas the logical name for my card (according to $ sudo lshw -c network) is not wlan0 but wmaster0. After reading all these posts and guides I reckon the correct logical name should be wlan0 .. maybe this is the mistake?

I know I could just go and buy a compatible USB thingy ... it's just that it became personal :) ... I mean, I can't give up with my first linux problem now can I?

I hope I've missed something elementary here..  Any thoughts or suggestions on this much appreciated!

---

### Post by rok.geo on 2009-09-03
Some more info before retiring for tonight..

I guess the following from [this thread]("http://ubuntuforums.org/showthread.php?t=686856&page=2") is related:

> please copy and paste the output of:
     Code:
     cat /etc/network/interfaces 
**For network-manager to work with the wlan0 adapter there should be nothing more than "auto wlan0" in the above file. **
However I wonder how much you have done to your Ubuntu install to get it to work.My result is:

```
$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```... which is not good I suppose.

But consulting this (as psyburn suggested): [https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61) doesn't seem like the right idea as this fix was supposedly already included into ubuntu 8.10 release..

I've also tried to enable wlan0 (and wmaster0) with ifconfig ($ sudo ifconfig wlan0 up) but this just puts me into a new line ... giving me no results..

---

### Post by rok.geo on 2009-09-04
Re-installed ubuntu, used ndisgtk to install windows drivers, works like a charm. I must have screwed something up the first time.. Consider this one solved.

---

