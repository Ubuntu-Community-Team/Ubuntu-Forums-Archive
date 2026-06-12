---
title: "iwconfig, cannot connect from command line"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by SolmyrBhaal on 2009-11-23
Hey All,

I have seen that there is actually quite a few posts already out there on this topic, I.E connecting to a wireless network from the command line.  However, I am battling to get this right.  Please see the steps I am following to get this working.  FYI I have done theses steps and get the same output on two different machines (one without a GUI, which is why I need to do this with the command line) - the only thing that is the same is the wireless card, the access point, and the steps I follow.

My card:  Intel Corporation PRO/Wireless 4965 AG and using Ubuntu 9.04.

So just to get started I am able to connect to the wireless network when I use the GUI, goto the network Icon top right corner click rlc and it connects.  This works for WEP and no security.

My Steps:
[INDENT][I]paladin@paladin-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - **Address: 00:19:70:05:07:54**
                    ESSID:"rlc"
                    **Mode:Master**
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=88/100  Signal level:-44 dBm  Noise level=-127 dBm
                    **Encryption key: off**
                    IE: Unknown: 0003726C63
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000007bcce4c0
                    Extra: Last beacon: 808ms ago
  [/I][/INDENT]In this example I use no security, you can see that encryption is off.
[INDENT][I]paladin@paladin-ubuntu:~$ sudo ifconfig wlan0 down
paladin@paladin-ubuntu:~$ sudo iwconfig wlan0 mode managed essid 'rlc' channel 11 **ap 00:19:70:05:07:54**
paladin@paladin-ubuntu:~$ sudo ifconfig wlan0 up
paladin@paladin-ubuntu:~$ sudo iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"rlc"  
          Mode:Managed  Frequency:2.462 GHz  **Access Point: Not-Associated **  
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/I][/INDENT]As you can see I specify the Access Point in my command but it does not actually come through - I know it works cause if I change the essid it does detect this ("rlc1" instead of "rlc").  Also in the scan you can see that the Mode is detected as master, if I try and set this i get the following error:[INDENT][I]paladin@paladin-ubuntu:~$ sudo ifconfig wlan0 downpaladin@paladin-ubuntu:~$ sudo iwconfig wlan0 mode **Master **essid 'rlc' channel 11 ap 00:19:70:05:07:54
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
[/I][/INDENT]You can also see that the Link Quality Signal Level and Noise Level are also always 0.  Which would tell me that is is not connected to anything.

The next frustrating part is that if I try and set it up to be a secure connection that command also does not go through:
[INDENT]*paladin@paladin-ubuntu:~$ sudo ifconfig wlan0 down*
*paladin@paladin-ubuntu:~$ sudo iwconfig wlan0** key 1234567890** mode managed essid 'rlc' channel 11 ap 00:19:70:05:07:54*
*paladin@paladin-ubuntu:~$ sudo ifconfig wlan0 up*
*paladin@paladin-ubuntu:~$ sudo iwconfig wlan0*
*wlan0     IEEE 802.11abgn  ESSID:"rlc"  *
*          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   *
*          Tx-Power=15 dBm   *
*          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   *
*          **Encryption key: off***
*          Power Management: off*
*          Link Quality:0  Signal level:0  Noise level:0*
*          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0*
*          Tx excessive retries:0  Invalid misc:0   Missed beacon:0*
[/INDENT]Now if i try and get a dhcp assigned IP the following is the output:
[INDENT][I]paladin@paladin-ubuntu:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1f:3b:2a:6b:6b
Sending on   LPF/wlan0/00:1f:3b:2a:6b:6b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
[/I][/INDENT]Now I now this is a long post I am trying to get as much information to you guys as possible so please bear with this last bit of data :P  now as I said earlier I am able to connect with the GUI, when I do this here is the output from iwconfig:
[INDENT][I]wlan0     IEEE 802.11abgn  ESSID:"rlc"  
          Mode:Managed  Frequency:2.462 GHz  **Access Point: 00:19:70:05:07:54   **
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          **Link Quality=100/100  Signal level:-42 dBm  Noise level=-127 dBm**
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
[/I][/INDENT]Any help on this problem will be very appreciated, kinds regards

Louis

---

### Post by kukubau on 2010-05-03
I am having the [COLOR=Red]**exact**[/COLOR] same problem. Can't connect to a wireless access point with no encryption set or otherwise.

Could anyone help???

Thanks

---

