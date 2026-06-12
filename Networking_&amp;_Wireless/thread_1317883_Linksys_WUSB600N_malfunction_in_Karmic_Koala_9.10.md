---
title: "Linksys WUSB600N malfunction in Karmic Koala 9.10"
date: 2009-11-07
forum: Networking &amp; Wireless
---

### Post by michauko on 2009-11-07
Hello,

I have a Linksys (Cisco) WUSB600N wifi usb key.
Working out-of-the-box in Jaunty 9.04

I upgraded to Karmic Koala.
Now the wifi is detected, associated, I get an IP then..... some bytes are going to the Internet for a few seconds... then it's dead. I'm still connected, but no data can be exchanged.

If I boot back to my old kernel, it's OK.
As my Ubuntu has been upgraded many times (3 or 4 releases), I decided to re-install - I have some other problems I can't get rid of.

So on a fresh Ubuntun 9.10 installation, same thing.


Does anyone have the same problem with this key ? any idea to debug this ; I'm not very familia to wpa_supplicant. But anyway, Networkd-manager was managing all this. Now it's bugged somewhere.
Here's my syslog. When I get back to CTRL-EVENT-SCAN-RESULTS (last line), the wifi's stuck

Kernel is 2.6.31-14-generic.

```
Nov  7 09:48:54 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-SCAN-RESULTS 
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) starting connection 'Auto folie'
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto folie' has security, and secrets exist.  No new secrets needed.
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Config: added 'ssid' value 'folie'
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Nov  7 09:48:54 quadbuntu NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  7 09:48:54 quadbuntu NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  Config: set interface ap_scan to 1
Nov  7 09:48:54 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov  7 09:48:59 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  7 09:49:03 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-SCAN-RESULTS 
Nov  7 09:49:03 quadbuntu wpa_supplicant[1172]: Trying to associate with d2:fa:00:10:98:64 (SSID='folie' freq=2412 MHz)
Nov  7 09:49:03 quadbuntu wpa_supplicant[1172]: Association request to the driver failed
Nov  7 09:49:03 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Nov  7 09:49:03 quadbuntu kernel: [   31.491321] wlan0: direct probe to AP d2:fa:00:10:98:64 try 1
Nov  7 09:49:03 quadbuntu kernel: [   31.493835] wlan0 direct probe responded
Nov  7 09:49:03 quadbuntu kernel: [   31.493840] wlan0: authenticate with AP d2:fa:00:10:98:64
Nov  7 09:49:03 quadbuntu kernel: [   31.495705] wlan0: authenticated
Nov  7 09:49:03 quadbuntu kernel: [   31.495707] wlan0: associate with AP d2:fa:00:10:98:64
Nov  7 09:49:03 quadbuntu kernel: [   31.498831] wlan0: RX AssocResp from d2:fa:00:10:98:64 (capab=0x411 status=0 aid=1)
Nov  7 09:49:03 quadbuntu kernel: [   31.498835] wlan0: associated
Nov  7 09:49:03 quadbuntu wpa_supplicant[1172]: Associated with d2:fa:00:10:98:64
Nov  7 09:49:03 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Nov  7 09:49:03 quadbuntu kernel: [   31.513981] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Nov  7 09:49:04 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  7 09:49:05 quadbuntu avahi-daemon[700]: Registering new address record for fe80::21e:e5ff:fee4:8e5f on wlan0.*.
Nov  7 09:49:10 quadbuntu NetworkManager: <info>  wlan0: link timed out.
Nov  7 09:49:12 quadbuntu wpa_supplicant[1172]: WPA: 4-Way Handshake failed - pre-shared key may be incorrect
Nov  7 09:49:12 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:12 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Nov  7 09:49:12 quadbuntu kernel: [   40.260817] wlan0: deauthenticated (Reason: 1)
Nov  7 09:49:12 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  7 09:49:13 quadbuntu kernel: [   41.260071] wlan0: direct probe to AP d2:fa:00:10:98:64 try 1
Nov  7 09:49:13 quadbuntu kernel: [   41.262359] wlan0 direct probe responded
Nov  7 09:49:13 quadbuntu kernel: [   41.262364] wlan0: authenticate with AP d2:fa:00:10:98:64
Nov  7 09:49:13 quadbuntu kernel: [   41.268109] wlan0: authenticated
Nov  7 09:49:13 quadbuntu kernel: [   41.268111] wlan0: associate with AP d2:fa:00:10:98:64
Nov  7 09:49:13 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:13 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Nov  7 09:49:13 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:13 quadbuntu kernel: [   41.276103] wlan0: deauthenticated (Reason: 6)
Nov  7 09:49:13 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:13 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:14 quadbuntu kernel: [   42.064027] wlan0: no IPv6 routers present
Nov  7 09:49:14 quadbuntu wpa_supplicant[1172]: Authentication with 00:00:00:00:00:00 timed out.
Nov  7 09:49:14 quadbuntu wpa_supplicant[1172]: Failed to initiate AP scan.
Nov  7 09:49:14 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Nov  7 09:49:14 quadbuntu kernel: [   42.276771] wlan0: direct probe to AP d2:fa:00:10:98:64 try 1
Nov  7 09:49:14 quadbuntu kernel: [   42.282522] wlan0 direct probe responded
Nov  7 09:49:14 quadbuntu kernel: [   42.282528] wlan0: authenticate with AP d2:fa:00:10:98:64
Nov  7 09:49:14 quadbuntu kernel: [   42.284291] wlan0: authenticated
Nov  7 09:49:14 quadbuntu kernel: [   42.284295] wlan0: associate with AP d2:fa:00:10:98:64
Nov  7 09:49:14 quadbuntu kernel: [   42.287417] wlan0: RX ReassocResp from d2:fa:00:10:98:64 (capab=0x411 status=0 aid=1)
Nov  7 09:49:14 quadbuntu kernel: [   42.287420] wlan0: associated
Nov  7 09:49:14 quadbuntu wpa_supplicant[1172]: Associated with d2:fa:00:10:98:64
Nov  7 09:49:14 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associated
Nov  7 09:49:16 quadbuntu wpa_supplicant[1172]: Failed to initiate AP scan.
Nov  7 09:49:19 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-SCAN-RESULTS 
Nov  7 09:49:19 quadbuntu wpa_supplicant[1172]: Trying to associate with d2:fa:00:10:98:64 (SSID='folie' freq=2412 MHz)
Nov  7 09:49:19 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> associating
Nov  7 09:49:19 quadbuntu wpa_supplicant[1172]: Association request to the driver failed
Nov  7 09:49:19 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Nov  7 09:49:19 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> disconnected
Nov  7 09:49:23 quadbuntu kernel: [   51.199630] wlan0: authenticate with AP d2:fa:00:10:98:64
Nov  7 09:49:23 quadbuntu kernel: [   51.201269] wlan0: authenticated
Nov  7 09:49:23 quadbuntu kernel: [   51.201272] wlan0: associate with AP d2:fa:00:10:98:64
Nov  7 09:49:23 quadbuntu kernel: [   51.204644] wlan0: RX ReassocResp from d2:fa:00:10:98:64 (capab=0x411 status=0 aid=1)
Nov  7 09:49:23 quadbuntu kernel: [   51.204647] wlan0: associated
Nov  7 09:49:23 quadbuntu wpa_supplicant[1172]: Associated with d2:fa:00:10:98:64
Nov  7 09:49:23 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associated
Nov  7 09:49:24 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Nov  7 09:49:24 quadbuntu kernel: [   51.778032] padlock: VIA PadLock not detected.
Nov  7 09:49:24 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
Nov  7 09:49:25 quadbuntu wpa_supplicant[1172]: WPA: Key negotiation completed with d2:fa:00:10:98:64 [PTK=CCMP GTK=TKIP]
Nov  7 09:49:25 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-CONNECTED - Connection to d2:fa:00:10:98:64 completed (auth) [id=0 id_str=]
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'folie'.
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction (timeout in 45 seconds)
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  dhclient started with pid 1822
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Nov  7 09:49:25 quadbuntu dhclient: Internet Systems Consortium DHCP Client V3.1.2
Nov  7 09:49:25 quadbuntu dhclient: Copyright 2004-2008 Internet Systems Consortium.
Nov  7 09:49:25 quadbuntu dhclient: All rights reserved.
Nov  7 09:49:25 quadbuntu dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Nov  7 09:49:25 quadbuntu dhclient: 
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
Nov  7 09:49:25 quadbuntu NetworkManager: <info>  DHCP: device wlan0 state changed (null) -> preinit
Nov  7 09:49:25 quadbuntu dhclient: Listening on LPF/wlan0/00:1e:e5:e4:8e:5f
Nov  7 09:49:25 quadbuntu dhclient: Sending on   LPF/wlan0/00:1e:e5:e4:8e:5f
Nov  7 09:49:25 quadbuntu dhclient: Sending on   Socket/fallback
Nov  7 09:49:28 quadbuntu dhclient: DHCPREQUEST of 192.168.91.40 on wlan0 to 255.255.255.255 port 67
Nov  7 09:49:28 quadbuntu dhclient: DHCPACK of 192.168.91.40 from 192.168.91.254
Nov  7 09:49:28 quadbuntu dhclient: bound to 192.168.91.40 -- renewal in 378299 seconds.
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> reboot
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Nov  7 09:49:28 quadbuntu NetworkManager: <info>    address 192.168.91.40
Nov  7 09:49:28 quadbuntu NetworkManager: <info>    prefix 24 (255.255.255.0)
Nov  7 09:49:28 quadbuntu NetworkManager: <info>    gateway 192.168.91.254
Nov  7 09:49:28 quadbuntu NetworkManager: <info>    nameserver '212.27.40.240'
Nov  7 09:49:28 quadbuntu NetworkManager: <info>    nameserver '212.27.40.241'
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Nov  7 09:49:28 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Nov  7 09:49:28 quadbuntu avahi-daemon[700]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.91.40.
Nov  7 09:49:28 quadbuntu avahi-daemon[700]: New relevant interface wlan0.IPv4 for mDNS.
Nov  7 09:49:28 quadbuntu avahi-daemon[700]: Registering new address record for 192.168.91.40 on wlan0.IPv4.
Nov  7 09:49:29 quadbuntu NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
Nov  7 09:49:29 quadbuntu NetworkManager: <info>  Policy set 'Auto folie' (wlan0) as default for routing and DNS.
Nov  7 09:49:29 quadbuntu NetworkManager: <info>  Activation (wlan0) successful, device activated.
Nov  7 09:49:29 quadbuntu NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Nov  7 10:49:30 quadbuntu ntpdate[1882]: step time server 91.189.94.4 offset 3600.328115 sec
Nov  7 10:49:36 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-SCAN-RESULTS 
Nov  7 10:50:03 quadbuntu avahi-daemon[700]: Invalid query packet.
Nov  7 10:50:03 quadbuntu avahi-daemon[700]: Invalid query packet.
Nov  7 10:50:04 quadbuntu avahi-daemon[700]: Invalid query packet.
Nov  7 10:50:16 quadbuntu wpa_supplicant[1172]: CTRL-EVENT-SCAN-RESULTS 

```

---

### Post by kwek on 2009-11-09
I can confirm this behaviour with the same device. I am able to ping the local network and even internet. But when opening a http connection the connection drops. This used to be fine in the previous ubuntu. Let me know if i need to provide more information.

---

### Post by michauko on 2009-11-10
Yes, this is it. Then the ping fails too, sometime.
I did not have time to get the chipset manufacturer (rt2870, something like that I guess), and try to download an older/newer module and test. I'll try this later, if no other solution is given.

---

### Post by tlois on 2009-11-12
Did you guys figure this out?  I just ordered a refurbed 600n because I saw a guy said it worked for him out of the box on Ubuntu.  Wish I had found this before I hit "Complete Purchase."

I really want to be able to use the 5ghz network on my new router for movies.  

Thanks for any more info you have.

---

### Post by michauko on 2009-11-13
Hi,
I didn't have time to test, sorry
It's working out of the box..... with Ubutun 9.04. Not with 9.10

---

### Post by tlois on 2009-11-13
OK, thanks.  I found it listed in bugs with Karmic, so hopefully it will be corrected one day.  Not too big a problem- it is an extra for me.  I got it for 25 bucks from a person selling refurbs on amazon.

Do you know if 5ghz networks are seen when it is working with 9,04?  I could not find any confirmation of that.

I wonder if using a different kernel would help??  I have about 4-5 that show up on my laptop before boot.  Will try that when it arrives and let you know if it makes a difference.  I have found that when wireless goes wacky that has helped me in the past for some problems.

---

### Post by michauko on 2009-11-13
On my previous installation, upgraded from Jaunty, I could get the wifi back if I booted on the latest kernel from Jaunty, not Karmic's one.
So yes, you still can use it. But it's a problem on a fresh installation

Can you post the link to the bug, so I/we can follow it ?

Thank you

---

### Post by tlois on 2009-11-13
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/408165)

appears to be more of a general linux bug here.

---

### Post by michauko on 2009-11-15
Hi
I'm getting bored of all this. As some other wifi keys/cards seem to have that kind of problem, I just reinstalled Ubutu 9.04 (jaunty). Back to normal life
If I get a solution in Karmic, I'll tell you. As I won't reinstall it before begin sure the problem is solved, I'll test any solution on a persistant-bootable-karmic-usb-key :)

good luck

---

### Post by tlois on 2009-11-15
yes, know what you mean.  wireless is important for me, because even my desktop can only access our internet via wifi.  are you able to use the 5ghz band on that adapter with ubuntu - have you tried it?  

recently spent way too much on a new netgear router that has 5ghz for streaming video and would like to get my moneys worth out of it.

---

### Post by RegPerrin on 2010-01-25
I have a number of the WUSB600N adapters. I have submitted bug reports to Ubuntu regarding the 'breaking' of the wifi when either upgrading to 9.10 or installing a fresh copy of 9.10.
The concensus of opinion is that the rt2870sta driver as supplied by Ralinktech.com is not compatible with the upgrade.
The solution is NOT to upgrade from 9.04 to 9.10. Not a good not long term solution.
Eventually, the driver issue will be solved, but in the meantime if you either go back to 9.04, or install 9.04 fresh, then follow these instructions, you can have the 5GHz network working properly:
Step 1 - Download the modified driver source RT2870_LinuxSTA_V2.3.0.0 from RALINK  ([http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2))
Step 2 - Extract the .tar to the desktop 
Step 3 - Open a terminal and navigate to the newly created folder 
    * cd Desktop/RT2870_LinuxSTA_V2.3.0.0
Step 4 -   
    * sudo make 
     
Step 5 -  
    * sudo mkdir /etc/Wireless 
    * sudo mkdir /etc/Wireless/RT2870STA 
    * sudo cp RT2870STA.dat /etc/Wireless/RT2870STA/RT2870STA.dat 
 
Step 6 - open the WUSB600N/os/linux folder and type  
    * sudo insmod rt2870sta.ko 
 
The wireless card should now be working. 
 
Secondly, to make sure it uses the driver on reboot: 
 
Copy the .ko file to the kernel modules folder: 
Code: 
    * sudo mkdir /lib/modules/<kernel version>/wireless 
    * sudo cp rt2870sta.ko /lib/modules/<kernel version>/wireless 
 
Edit the modules list 
Code: 
    * sudo gedit /etc/modules 
 
Add the following to the bottom: 
Code: 
    * rt2870sta 
 
Edit the startup script: 
Code: 
    * sudo gedit /etc/rc.local 
 
Add this near the end but before "exit 0" 
Code: 
    * sudo insmod /lib/modules/<kernel version>/wireless/rt2870sta.ko

Reboot, and you should be able to see and connect to all the 5GHz networks.

---

### Post by michauko on 2010-01-25
ok, thank you for this detailed procedure.
I'll just add that one might have to do this after each kernel upgrade.

I'll try this when I can (I don't *need* to upgrade, maybe I'll wait for the next LTS ubuntu release).

Anyway, I guess your answer will help people.

Regards,

---

### Post by RegPerrin on 2010-01-25
I have done the above procedure 8 times (4 fresh installations of 9.04 32-bit, and 4 fresh installations of 9.04 64-bit). 
Immediately after, I got all updates. I did not do the "Upgrade to 9.10" though. 
The WUSB600N continued (and continues) to work properly.
On my wireless test network:

testrig2ub32@testrig2ub32-desktop:~$ iwpriv ra0 show AuthMode
ra0       show:    WPA2PSK
testrig2ub32@testrig2ub32-desktop:~$ iwpriv ra0 show EncrypType
ra0       show:    AES
testrig2ub32@testrig2ub32-desktop:~$ iwpriv ra0 show NetworkType
ra0       show:    Infra
testrig2ub32@testrig2ub32-desktop:~$ iwpriv ra0 get_site_survey
ra0       get_site_survey:
Ch  SSID                             BSSID               Enc     Auth      Siganl(%)W-Mode  NT
56  testing5                         00:24:c4:d9:1d:c0   AES     WPA2PSK   100      11a/n   In

ra0       RT2870 Wireless  ESSID:"testing5"  Nickname:"RT2870STA"
          Mode:Managed  Frequency=5.28 GHz  Access Point: 00:24:C4:D9:1D:C0   
          Bit Rate=270 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-50 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

All seems to be fine.
I am conducting some throughput tests alongside Windows also. At this early stage, the rates do not differ significantly.

---

### Post by RegPerrin on 2010-01-25
Damn stupid smilies

---

