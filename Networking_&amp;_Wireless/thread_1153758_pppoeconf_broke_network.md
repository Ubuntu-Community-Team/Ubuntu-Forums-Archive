---
title: "pppoeconf broke network"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by Morphal on 2009-05-09
Installed fresh Jaunty on Samsung R25, everything worked great. Got a wifi connections working to different networks. But when i had to connect to internet via wifi to DSL-modem and pppoe, i used pppoeconf utility to set up a connection. I was set up without problems, found wifi and all steps were done without problems. and internet worked pretty well. but after reboot NEtwork manager stopped detecting any networks, after turning wifi module on nothing happens at all. the same history after i set it up to ethernet connection. Now network manager doesn't react on plugging ethernet cable in.

---

### Post by superprash2003 on 2009-05-09
post output of **sudo iwlist scanning** from the terminal

---

### Post by Morphal on 2009-05-09
alex@alex-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Interface doesn't support scanning : Network is down
vboxnet0  Interface doesn't support scanning.
pan0      Interface doesn't support scanning.

then i did:
alex@alex-laptop:~$ sudo ifconfig wlan0 up
alex@alex-laptop:~$ sudo iwlist scanning
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wmaster0  Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:CE:20:F5
                    ESSID:"HomeWLAN"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/100  Signal level:-75 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: Unknown: 0008486F6D65574C414E
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD090010180200F0000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=00000017f6b46183
                    Extra: Last beacon: 912ms ago
vboxnet0  Interface doesn't support scanning.
pan0      Interface doesn't support scanning.

and:

alex@alex-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          /usr/bin/poff: No pppd is running.  None stopped.
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5
 * if-up.d/mountnfs[dsl-provider]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[dsl-provider]: waiting for interface eth0 before doing NFS mounts
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts

---

### Post by superprash2003 on 2009-05-10
well the wireless seems to be OK, as it is able to view "HOMEWLAN" .. post output of iwconfig and ifconfig . Dont you see the wifi network listed when you click on the networking icon on the top right bar??

---

### Post by Morphal on 2009-05-10
alex@alex-laptop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11abg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.
pan0      no wireless extensions.

alex@alex-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:77:3a:40:2d  
          inet6 addr: fe80::213:77ff:fe3a:402d/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:118 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12291 (12.2 KB)  TX bytes:1812 (1.8 KB)
          Interrupt:22 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:36:21:44  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-36-21-44-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


That is the problem. Everything worked pretty well until pppoeconf :) Now when i click the networking icon both wired and wireless networks are "device not managed". Looks like pppoeconf broke something in network manager options..

---

### Post by superprash2003 on 2009-05-11
check this for your device unmanaged error [http://ubuntuforums.org/showthread.php?t=1028541](http://ubuntuforums.org/showthread.php?t=1028541)

---

### Post by Morphal on 2009-05-11
Thanks a lot! 
It turned out that pppoeconf disabled network manager (donno why?)


Code:
sudo vi /etc/NetworkManager/nm-system-settings.conf

Change "managed=false" to "managed=true"

Code:
sudo killall nm-system-settings

It helped.

---

### Post by lynx93 on 2009-08-10
That didn't work for me:(
I wrote that also in with vi nothing happened just a few blue waves came, when I inserted nano on the place of vi I got this:

What shall I do now?

---

### Post by frederik.nnaji on 2010-04-18
has this issue actually been resolved?
i still see no GTK+ wizard on top of Network Manager 0.8 today.
i also hear reports that pppoeconf still breaks NM's control aka management.. which was mean to be the sole purpose of Network "Manager".

any news there?

---

### Post by tacoee on 2010-05-21
maybe this is helpful. good luck.
[http://ubuntuforums.org/showthread.php?t=1487646&highlight=rp-pppoe](http://ubuntuforums.org/showthread.php?t=1487646&highlight=rp-pppoe)

---

