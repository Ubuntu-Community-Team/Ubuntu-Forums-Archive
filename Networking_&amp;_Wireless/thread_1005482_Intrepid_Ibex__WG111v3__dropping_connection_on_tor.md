---
title: "Intrepid Ibex / WG111v3 / dropping connection on torrents"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by patv on 2008-12-08
New to Linux. Most everything worked out of the box, but having problems with my WLAN adapter dropping connection to my router, but _only_ when running a torrent client.

I've filled in the suggested form below as best I'm able:


1 ) Machine Brand and Model (PC/Laptop):
Dell desktop Dimension 5150 (was originally factory installed WinXP). Ubuntu 8.10 now installed, fully auto patched to date. Onboard NIC disabled, only using USB wireless adapter.


2 ) Wireless Brand, Model and Wireless Chipset:
NetGear, Inc. WG111v3 802.11g Adapter [realtek RTL8187B] 

This actually worked out of the box on my Ubuntu 8.10 install, although the Wiki suggested that it wouldn't: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear#USB)


3 ) check interface:
ifconig:
wlan0     Link encap:Ethernet  HWaddr 00:1b:2f:cd:82:14  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::21b:2fff:fecd:8214/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:3843 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:3714 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:2718196 (2.7 MB)  TX bytes:507000 (507.0 KB) 

iwconfig:
wlan0     IEEE 802.11bg  ESSID:"XXXX"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:F1:A6:46   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off 
          Link Quality=80/100  Signal level:-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 


4 ) Check for modules:
Module                  Size  Used by 
usbcore               148848  10 rtl8187,snd_usb_audio,snd_usb_lib,usblp,usb_storage,libusual,usbhid,ehci_hcd,uhci_hcd 


5 ) Kernel boot messages
[   54.429254] wlan0: authenticate with AP 00:1b:2f:f1:a6:46 
[   54.430760] wlan0: authenticated 
[   54.430769] wlan0: associate with AP 00:1b:2f:f1:a6:46 
[   54.433638] wlan0: RX AssocResp from 00:1b:2f:f1:a6:46 (capab=0x411 status=0 aid=2) 
[   54.433647] wlan0: associated 
[  366.544015] wlan0: no IPv6 routers present 


6 ) Network configuration
  *-network:0             
       description: Wireless interface 
       physical id: 1 
       logical name: wlan0 
       serial: 00:1b:2f:cd:82:14 
       capabilities: ethernet physical wireless 
       configuration: broadcast=yes ip=192.168.0.2 multicast=yes wireless=IEEE 802.11bg 
  *-network:1 DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 42:41:ed:a8:ca:d1 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 


7 ) Scan for networks:
wlan0     Scan completed : 
          Cell 01 - Address: 00:1B:2F:F1:A6:46 
                    ESSID:"XXXX" 
                    Mode:Master 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=72/100  Signal level:-35 dBm  
                    Encryption key:on 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s 
                              48 Mb/s; 54 Mb/s 
                    Extra:tsf=00000004a5277234 
                    Extra: Last beacon: 60ms ago 


8 ) Ubuntu Version:
Description:	Ubuntu 8.10 


9 ) Kernel/architecture (including 32 vs. 64 bit):
2.6.27-9-generic i686 


10 ) Restarting the network:
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0. 
                                                                         [ OK ] 


---
The problem with my adapter only shows up (so far) in torrent applications. I've tried both the pre-installed Transmission client, and Deluge. After a few minutes of using either, my PC loses network connectivity – I can't even browse to my local router. The adapter will then not reconnect to the WLAN without a _reboot_ of the PC.

Any help gratefully received. Thanks.

---

### Post by sosostris on 2009-04-02
I seem to have exactly the same problem on my Intrepid setup. 
Everything works fine as long as I don't start a torrent client. I am also connected via a RTL8187B.
Doing 
  sudo /etc/init.d/NetworkManager restart 

will fix the broken connection without reboot.
I have also tried wicd, which behaved exactly the same as NetworkManager. In this case a restart of wicd fixed the broken connection, so it must be some underlying module.
There cannot be a correlation to the network load, as streaming videos or downloading files works fine.

---

### Post by patv on 2009-04-02
I'm afraid that I never did get this problem resolved. I even went down the route of installing the NDIS drivers, but that didn't fix matters. If you do find a workaround, I'd be grateful to know about it!

Cheers, a frustrated *buntu user.

---

### Post by sosostris on 2009-04-17
[http://wiki.ubuntuusers.de/Linux_Wireless](http://wiki.ubuntuusers.de/Linux_Wireless)

solved the problem for me.

---

