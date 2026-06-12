---
title: "Linksys WPC300N under Ubuntu 8.10"
date: 2009-03-16
forum: Networking &amp; Wireless
---

### Post by kjellerikan on 2009-03-16
Hello,
I'm new to Ubuntu. Have just set up an old Aspire 1300 with AMD Athlon XP 1800+ working since long with the Linksys WPC300N Client and a Linksys WRT610N Router.
Current set-up is a dual boot XP/Ubuntu.
I can see the WLAN SSID and one blue light on the Linksys adapter is on but I can not connect.
WiFi Radar sees my SSID as well as others.
I have run ndiswrapper, which reports the NET5416.INF as the only installed driver.
WiFi Radar report CONNECTED TO IP (169.254.109.228), which is not on my subnet and I'm not connected.
I enter an ASCII Password under the configuration tool in Ubuntu but when I then look at the password it seems to be HEX code and not ASCII. Result is no connection..
I have a feeling I might be over specifying something somewhere. I wonder, where is the base service for the WLAN? Where you are supposed to set up the basic WLAN service..?
Createful for any advice...!

Heres a copy of my scan:
root@kea-laptop:/home/kea# iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:11:95:3A:88:33
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:21:29:D0:F7:02
                    ESSID:""
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:31/100  Signal level:-76 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

Cell 2 is my 2.4 G Wireless Network and the Address: 00:21:29:D0:F7:02 is correct for the 2.4 G WLAN o the Router.
All seem OK to me but I can still not connect to the Wireless network, only to the wired...!


Hello again,
I wonder if there will be a full implementation of the ath9k driver towards the WPC300N Linksys adapter in Ubuntu V9.04? I made a clean install of V9.04 and added Samba as advised by several posts in forums. The radio LED goes sort of on and off and if I look at traces it seem as the WLAN has been on occasionally. But there is no logic at all in the behaviour. I think many are looking for a solution to this problem...

---

### Post by eemitchell24 on 2009-06-16
I am having the same problem with my Linksys WPC300N, except I don't seem to be getting lights from the adapter. I am using a Dell Latitude 810. for **iwlist wlan0 scan** I get the error message "Interface doesn't support scanning", but for **lshw -C network ** it seems to see the PCI card (NetExtreme BCM5751 Gigabit Ethernet PCI Express) but gives it a logical name of **eth0** which does seem right to me.

---

### Post by stussie on 2009-10-25
Same problem but with the latest release 9.10.

At the start the power LED  on the wireless adapter turns for aprox 3 seconds then turns off , the link/activity light is then constantly on :S

Hope this is fixed in the final release.

---

### Post by BoomSchtick on 2009-11-10
I had a hell of a time getting this to work until I found the source code for the STA driver direct from Broadcom.  I downloaded the 32 bit source to my desktop.  It was super simple to compile (only two commands), as noted in the readme.  The readme also walks you through putting the driver in the correct place.  As soon as I disabled NDISWRAPPER (never could get that to work), and made sure that the old driver was disabled (system -> administration -> hardware drivers), the NIC instantly connected up to my wpa protected access point.

I probably spent over 5 hours trying to get the blasted thing to work.  It worked fine in Breezy (I'm on a fresh Karmic install), so doing all this troubleshooting was new to me.  Thank goodness I had an aircard I could use to get online to search with.

Here is a [link]("http://www.broadcom.com/support/802.11/linux_sta.php") to the Broadcom download page for the drivers.  Follow the ReadMe and it's a piece of cake!

---

### Post by BoomSchtick on 2009-11-11
I have to stand corrected... the card worked last night, but one the computer came back up this morning, it would not connect to the network again.  Same symptoms as before.  It will see the network but won't connect to it.  This is soooo frustrating!  This card and aircard worked fine in 9.04 and the network manager gave me NO problems!

---

### Post by kjellerikan on 2009-11-15
New research
Made a clean install of V9.10 and it seems as the ath9k driver is included. However, the system hangs completely after only about one minute,or so, after boot up. It is released after maybe 30 sec but freezes again... until a compleete freeze... Remedy is to unplug the WPC300N adaptor, then the system comes back immediately.
Network tool reports that both LAN and WLAN are active simultaneosly. MAybe this is causing a complete confusion... This seem to be different in V9.10 vs V8. V8 recognised plug-in of the wireless H/W and tried to switch to it. V9 does not...  In V9 if you disable the LAN in favour for WLAN then all your Network connectivity falls... Strange...

---

### Post by kjellerikan on 2009-11-15
Result of ifconfig before the "icetime" fell over the PC again.

kea@kea-ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:19:45:df  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:5ae3:d0e5:0:2c0:9fff:fe19:45df/64 Scope:Global
          inet6 addr: fe80::2c0:9fff:fe19:45df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12468 (12.4 KB)  TX bytes:14783 (14.7 KB)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1778 (1.7 KB)  TX bytes:1778 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:39:01:44:ab  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2002:5ae3:d0e5:0:218:39ff:fe01:44ab/64 Scope:Global
          inet6 addr: fe80::218:39ff:fe01:44ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2433 (2.4 KB)  TX bytes:1156 (1.1 KB)

This seems all correct to me. Clues someone...?

---

### Post by BoomSchtick on 2009-11-16
One final update...
 
The Linksys card seems to be working fine now with the Broadcom driver that I compiled.  I had to make a script in order to get it to load at startup, but I can remove and replug the card and it will come up and work fine.  So I guess that the driver that I mentioned above was the fix for me.
 
Hot swap of my aircard does not seem to be working, but that's probably a unrelated issue for another thread.

---

### Post by kjellerikan on 2009-11-18
Case closed. My WLAN is now working OK from boot up in Ubuntu V9.10. Have not tested hot swap or switching to/from LAN/WLAN but the purpose of this thread is now reached. I did not need to compile anything new. All I did was to search for Linksys and ip4 related issues. It took some time but here we are at last... 
:popcorn:

---

