---
title: "Linksys Card, WPA problems, Hardy"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by vette427 on 2009-07-27
I am totally new to linux (Just installed Ubuntu 8.04.3 LTS, with the kernel 2.6.24-24-generic i686), and having a very difficult time trying to access my network using Network Manager. The machine is a Toshiba Satellite A10-S167. The Wireless Card is a Linksys WPC54G ver. 2. The wireless interface is wlan0. I do have the ndiswrapper module installed, and the driver is ndiswrapper+lstinds. I also have Network-Manager-Gnome, Network-Manager, and bcm43xx-fwcutter installed. The wireless network is a WPA-PSK with DHCP, and it worked fine with the same computer and wireless card on windows xp (albiet slowly). It also works just fine using the Mac OS X airport on a different laptop.
 
When I use Network Manager, it does see the network ssid and other ssids in the area. However, when I try to connect, it just keeps asking me for the password over and over again, and I'm sure it's the right passkey. I've also tried converting it to the Hex equivalent and entering that as well, to no avail.
 
When I try sudo /etc/init.d/networking restart, It returns ```
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval <some number>
``` six times, then returns:
 
```
 
No DCHCPOFFERS received.
No working leases in persistent database - sleeping.
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-up.d/wpasupplicant exited with return code 1

```

---

### Post by vette427 on 2009-07-27
Just a note, I have also tried WiCD with the same results.  It does not connect.  I would prefer to use Network Manager (roaming on) if possible, I like the graphic tool for connecting to different networks, since I use several wireless networks.  On a side note, the wireless card works just fine for unprotected networks, so I know the driver works.  It's just the WPA part that doesn't seem to work for me.

Please help me if anybody can, I would greatly appreciate it.  I have been searching forums and trying different things, and nothing seems to help.

---

### Post by vette427 on 2009-07-27
Also, for what it's worth, here is what is in the file /etc/network/interfaces:
 
```
 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback

```
 
Also, here is what returns using ifconfig. It is the wireless interface (wlan0) that I am interested in setting up:
 
```
 
eth0      Link encap:Ethernet  HWaddr 00:08:0d:a4:0a:61  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fea4:a61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1558506 (1.4 MB)  TX bytes:337549 (329.6 KB)
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1862 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1862 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:93100 (90.9 KB)  TX bytes:93100 (90.9 KB)
wlan0     Link encap:Ethernet  HWaddr 00:0f:66:d0:11:b0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10141 (9.9 KB)  TX bytes:9109 (8.8 KB)
          Interrupt:11 Memory:20020000-20022000 

```
 
Also, here is what i get from the command lspci:
 
```
paul@oldlaptop:/$ lspci
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 83)
01:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

```
 
Also, here is what returns with the command lshw -class network:
 
```
paul@oldlaptop:/$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:a4:0a:61
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.105 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:0f:66:d0:11:b0
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+lstinds driverversion=1.52+Linksys,03/10/2004,6.0.0.18 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g

```
 
Finally, just to show that I do see the wireless network, here is what happens when I type sudo iwlist scan:
 
```
paul@oldlaptop:/$ sudo iwlist scan
[sudo] password for paul: 
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:18:60:F3
                    ESSID:"tofu"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:42/100  Signal level:-69 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:1C:F0:F4:00:30
                    ESSID:"friedfish"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

```
 
It is the "friedfish" network that I am interested in connecting to. Again, every time I try to connect (using Network Manager in roaming mode), and enter my password, it just thinks for a while then asks for the password again. I'm sure the password is right.

---

### Post by alleycatuk on 2009-07-27
Hi,
I'm new to Linux too as of last Saturday but I have a Linksys card in my desktop working ok (enough to post here!) under WPA2 AES/TKIP encryption.

I'm also new to forums so I hope it's ok to post a link to somewhere else. Here's what i found and it got my setup working well.

[http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/](http://www.cyberciti.biz/faq/linux-ndiswrapper-wpa_supplicant-howto/)

Best of luck

Sorry - I forgot to say that I disabled Network-manager as that was preventing wpa_supplicant from connecting.
ps aux | grep NetworkManager   will show you the process id (look for NetworkManager not the process of the grep you just did)
sudo kill -9 <process id number>

---

### Post by vette427 on 2009-07-28
Thanks for the reply alleycatuk! Unfortunately, I still can't get it to work :confused:. First, I did use your advice and kill NetworkManager. I have installed ndiswrapper and wpasupplicant, and put the network info in the wpa_supplicant.conf file. Using iwlist wlan0 scan, it does show my network. However, when I try to connect using:
 
```
 
$ sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext

```
 
it starts out like this:
 
```

 
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'wext' ctrl_interface
'N/A' bridge 'N/A'Configuration file '/etc/wpa_supplicant.conf' ->
'/etc/wpa_supplicant.conf'Reading configuration file
'/etc/wpa_supplicant.conf'ap_scan=1ctrl_interface='/var/run/wpa_supplicant'Priority
group 0   id=0 ssid='friedfish'Initializing interface (2) 'wlan0'EAPOL: SUPP_PAE
entering state DISCONNECTEDEAPOL: KEY_RX entering state
NO_KEY_RECEIVEEAPOL: SUPP_BE entering state INITIALIZEEAP: EAP entering state
DISABLEDEAPOL: External notification - portEnabled=0EAPOL: External notification -
portValid=0ioctl[SIOCSIWPMKSA]: Invalid argumentSIOCGIWRANGE: WE(compiled)
=22 WE(source)=18 enc_capa=0x5  capabilities: key_mgmt 0x5 enc 0x7WEXT:
Operstate: linkmode=1, operstate=5Own MAC address:
00:0f:66:d0:11:b0wpa_driver_wext_set_wpawpa_driver_wext_set_key: alg=0
key_idx=0 set_tx=0 seq_len=0 key_len=0wpa_driver_wext_set_key: alg=0
key_idx=1 set_tx=0 seq_len=0 key_len=0wpa_driver_wext_set_key: alg=0
key_idx=2 set_tx=0 seq_len=0 key_len=0wpa_driver_wext_set_key: alg=0
key_idx=3 set_tx=0 seq_len=0
key_len=0wpa_driver_wext_set_countermeasureswpa_driver_wext_set_drop_unencryptedSetting
scan request: 0 sec 100000 usecAdded interface wlan0RTM_NEWLINK: operstate=0
ifi_flags=0x1002 ()Wireless event: cmd=0x8b06 len=8RTM_NEWLINK: operstate=0
ifi_flags=0x1003 ([UP])RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' addedState:
DISCONNECTED -> SCANNINGStarting AP scan (broadcast SSID)Trying to get current
scan results first without requesting a new scan to speed up initial associationReceived
479 bytes of scan results (2 BSSes)Scan results: 2Selecting BSS from priority group
0Try to find WPA-enabled AP0: 00:1c:f0:f4:00:30 ssid='friedfish' wpa_ie_len=24
rsn_ie_len=0 caps=0x11   selected based on WPA IE   selected WPA AP
00:1c:f0:f4:00:30 ssid='friedfish'Try to find non-WPA APTrying to associate with
00:1c:f0:f4:00:30 (SSID='friedfish' freq=2412 MHz)Cancelling scan requestWPA:
clearing own WPA/RSN IEAutomatic auth_alg selection: 0x1WPA: using IEEE
802.11i/D3.0WPA: Selected cipher suites: group 8 pairwise 8 key_mgmt 2 proto
1WPA: set AP WPA IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00
00 50 f2 02 01 00 00 50 f2 02WPA: clearing AP RSN IEWPA: using GTK TKIPWPA:
using PTK TKIPWPA: using KEY_MGMT WPA-PSKWPA: Set own WPA IE default -
hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50
f2 02No keys have been configured - skip key
clearingwpa_driver_wext_set_drop_unencryptedState: SCANNING ->
ASSOCIATINGwpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)WEXT:
Operstate: linkmode=-1, operstate=5wpa_driver_wext_associateSetting authentication
timeout: 10 sec 0 usecEAPOL: External notification - EAP success=0EAPOL: External
notification - EAP fail=0EAPOL: External notification - portControl=AutoRTM_NEWLINK:
operstate=0 ifi_flags=0x1003 ([UP])Wireless event: cmd=0x8b06
len=8RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])Wireless event:
cmd=0x8b04 len=12RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])Wireless
event: cmd=0x8b1a len=17CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)WEXT:
Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasure

```
 
 
and ends up running through a loop over and over that looks like this:
 
 
```

wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
State: GROUP_HANDSHAKE -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c07 len=59
AssocReq IE wireless event - hexdump(len=51): 00 09 66 72 69 65 64 66 69 73 68 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8c08 len=38
AssocResp IE wireless event - hexdump(len=30): 01 08 82 84 8b 96 8c 98 b0 48 32 04 12 24 60 6c dd 0c 00 03 7f 02 01 01 00 00 02 a3 40 00
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1c:f0:f4:00:30
Association info event
req_ies - hexdump(len=51): 00 09 66 72 69 65 64 66 69 73 68 01 04 82 84 8b 96 32 08 8c 12 98 24 b0 48 60 6c dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
resp_ies - hexdump(len=30): 01 08 82 84 8b 96 8c 98 b0 48 32 04 12 24 60 6c dd 0c 00 03 7f 02 01 01 00 00 02 a3 40 00
WPA: set own WPA/RSN IE - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
State: SCANNING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1c:f0:f4:00:30
No keys have been configured - skip key clearing
Associated with 00:1c:f0:f4:00:30
WPA: Association event - clear replay counter
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - EAP success=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: SUPP_BE entering state IDLE
Setting authentication timeout: 10 sec 0 usec
Cancelling scan request
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RX EAPOL from 00:1c:f0:f4:00:30
Setting authentication timeout: 10 sec 0 usec
IEEE 802.1X RX: version=1 type=3 length=95
  EAPOL-Key type=254
  key_info 0x89 (ver=1 keyidx=0 rsvd=0 Pairwise Ack)
  key_length=32 key_data_length=0
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 01
  key_nonce - hexdump(len=32): 5b e3 bc 53 d1 da 54 49 bb b2 5a d8 e5 b4 96 c3 fa 43 0d 26 32 d0 9b e3 a9 3f 88 c7 1d d7 e9 fb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
State: ASSOCIATED -> 4WAY_HANDSHAKE
WPA: RX message 1 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: Renewed SNonce - hexdump(len=32): b5 20 1e d8 08 c0 9f 57 97 d2 8d 2e 5e 03 d7 41 43 07 09 00 36 12 d7 69 f7 c9 ae c2 07 d2 7f 6b
WPA: PMK - hexdump(len=32): [REMOVED]
WPA: PTK - hexdump(len=64): [REMOVED]
WPA: WPA IE for msg 2/4 - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 2/4
RX EAPOL from 00:1c:f0:f4:00:30
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 02
  key_nonce - hexdump(len=32): 5b e3 bc 53 d1 da 54 49 bb b2 5a d8 e5 b4 96 c3 fa 43 0d 26 32 d0 9b e3 a9 3f 88 c7 1d d7 e9 fb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 7a 8b 55 5f 8a 43 9a e9 2e 04 14 a6 e3 69 34 0f
State: 4WAY_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
Scan timeout - try to get results
Received 479 bytes of scan results (2 BSSes)
Scan results: 2
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:f0:f4:00:30 ssid='friedfish' wpa_ie_len=24 rsn_ie_len=0 caps=0x11
   selected based on WPA IE
   selected WPA AP 00:1c:f0:f4:00:30 ssid='friedfish'
Try to find non-WPA AP
Already associated with the selected AP.
RX EAPOL from 00:1c:f0:f4:00:30
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 03
  key_nonce - hexdump(len=32): 5b e3 bc 53 d1 da 54 49 bb b2 5a d8 e5 b4 96 c3 fa 43 0d 26 32 d0 9b e3 a9 3f 88 c7 1d d7 e9 fb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 4f b1 3b 37 2a 40 93 dc 93 8b 5c c1 66 3f d8 0b
State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:1c:f0:f4:00:30
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 04
  key_nonce - hexdump(len=32): 5b e3 bc 53 d1 da 54 49 bb b2 5a d8 e5 b4 96 c3 fa 43 0d 26 32 d0 9b e3 a9 3f 88 c7 1d d7 e9 fb
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 78 e0 7b 2c 0c b1 4f 85 cd 17 e2 3c 94 ee 38 ef
State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
EAPOL: startWhen --> 0
EAPOL: SUPP_PAE entering state CONNECTING
EAPOL: txStart
WPA: drop TX EAPOL in non-IEEE 802.1X mode (type=1 len=0)
RX EAPOL from 00:1c:f0:f4:00:30
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 04
  key_nonce - hexdump(len=32): 75 60 ef 9d 64 fe 8f eb bd e0 47 fc 05 f6 eb f8 85 db c6 ec 86 a6 7a 9e 6c e8 f6 62 1c 24 81 6d
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): a4 5e dd ad 7f d1 c9 70 89 18 0d a0 8d 76 53 74
State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RX EAPOL from 00:1c:f0:f4:00:30
IEEE 802.1X RX: version=1 type=3 length=119
  EAPOL-Key type=254
  key_info 0x1c9 (ver=1 keyidx=0 rsvd=0 Pairwise Install Ack MIC)
  key_length=32 key_data_length=24
  replay_counter - hexdump(len=8): 00 00 00 00 00 00 00 05
  key_nonce - hexdump(len=32): 75 60 ef 9d 64 fe 8f eb bd e0 47 fc 05 f6 eb f8 85 db c6 ec 86 a6 7a 9e 6c e8 f6 62 1c 24 81 6d
  key_iv - hexdump(len=16): 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
  key_rsc - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_id (reserved) - hexdump(len=8): 00 00 00 00 00 00 00 00
  key_mic - hexdump(len=16): 39 89 5b 98 91 37 d6 e7 e1 be 62 1a 19 01 27 9b
State: GROUP_HANDSHAKE -> 4WAY_HANDSHAKE
WPA: RX message 3 of 4-Way Handshake from 00:1c:f0:f4:00:30 (ver=1)
WPA: IE KeyData - hexdump(len=24): dd 16 00 50 f2 01 01 00 00 50 f2 02 01 00 00 50 f2 02 01 00 00 50 f2 02
WPA: Sending EAPOL-Key 4/4
WPA: Installing PTK to the driver.
WPA: RSC - hexdump(len=6): 00 00 00 00 00 00
wpa_driver_wext_set_key: alg=2 key_idx=0 set_tx=1 seq_len=6 key_len=32
State: 4WAY_HANDSHAKE -> GROUP_HANDSHAKE
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1c:f0:f4:00:30 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT

```
 
Is the last part of that code the problem perhaps, where it says ioctl[SIOCSIWENCODEEXT]: Invalid argument
Driver did not support SIOCSIWENCODEEXT ?
 
Also, I tried using the wpa_gui and it just says:
```

Failed to open control connection to wpa_supplicant.
PING failed -trying to reconnect
PING failed -trying to reconnect

```
 
repeating the ping over and over again. In the gui, for Status, it says 'Could not get status from wpa_supplicant'
 
somehow my wpa_supplicant is not able to do what it's supposed to perhaps?
 
Any more help would be greatly appreciated!

---

### Post by gopchandani on 2009-07-31
I was looking over some more forum posts, I don't see you mentioning in your post that you did following:

sudo modprobe -r acx
echo "blacklist acx" | sudo tee -a /etc/modprobe.d/blacklist

Apparently for this chipset you are using (ACX 111), there is a native linux driver which is attempted for use and posts on the forum suggest that you have to remove that module (modprobe -r) and blacklist it (so that it doesn't start automatically next time you reboot) and then try using NDISWRAPPER with the windows driver you have. You might want to check out these links:

[http://ubuntuforums.org/showthread.php?t=201633](http://ubuntuforums.org/showthread.php?t=201633)
[http://ubuntuforums.org/showthread.php?t=98438](http://ubuntuforums.org/showthread.php?t=98438)

---

