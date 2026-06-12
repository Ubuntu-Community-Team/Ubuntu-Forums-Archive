---
title: "madwifi-hal wireless on Acer Aspire One"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by ramorrismorris on 2009-01-01
I have  2.6.27-9-generic running on an Acer Aspire One A0A150.  The
kernel is an update from an  earlier kernel installed from USB stick.
In order to use WPA security, I followed the recommendations
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) for fetching, installing,
and configuring the madwifi-hal driver. wpasupplicant 0.6.4-2 is installed.


The result is that the Network Manager seems to vainly try to connect
an interface named ath0, but something has installed an interface
named wifi0, which seems to have more or less the same mac address
(albeit reported 0-filled as reported by ifconfig) and  which also is
reported by ifconfig to be transmitting, whereas ath0 is
not. 

Furthermore, iwconfig (output also below) asserts that wifi0 has
no wireless extensions. The failure seems to be independent of
whether or not the distributed atheros driver is deactivated using
System->HardwareDrivers. It feels like I must either have dueling
drivers, or haven't really installed madwifi-hal. 

Finally note: (1)My Linksys WRT54g v3 WAP is known to work with all
the Windows systems on my network and its configuration is not suspect
(e.g. I have enough IP addresses available, MAC addresses aren't
locked down, etc.) (2)Basically the same behavior happens if I open
the network and no security is involved: the Network Manager still
times out waiting for ath0. (3)Installing the backports and attempting to use the resulting driver also fails to connect to the AP, and subsequently reinstalling the madwfi-hal driver brings no different results than detailed below.

A friend with identical hardware, who followed the same procedure, has
no problem, and so far we have not been able to find any configuration
differences. 

Thanks for any help.
Bob

----


wpa_supplicant.conf
network={
	ssid="milne2"
#        scan_ssid=1 # only needed if your access point uses a hidden ssid
        proto=WPA
        key_mgmt=WPA-PSK
	psk=66e8blahblahblah...
}


output of ifconfig

ath0      Link encap:Ethernet  HWaddr 00:23:4e:23:3a:ca  
          inet6 addr: fe80::223:4eff:fe23:3aca/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4E-23-3A-CA-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:0 (0.0 B)  TX bytes:7406 (7.4 KB)
          Interrupt:18 
-----
output of iwconfig

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

-----
syslog of typical failure

Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) starting connection 'milne2 WPA' 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): device state change: 3 -> 4 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0/wireless): access point 'milne2 WPA' has security, but secrets are required. 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started... 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): device state change: 6 -> 4 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete. 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting... 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): device state change: 4 -> 5 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0/wireless): connection 'milne2 WPA' has security, and secrets exist.  No new secrets needed. 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'ssid' value 'milne2' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Jan  1 12:36:43 heffa NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) complete. 
Jan  1 12:36:43 heffa NetworkManager: <info>  Config: set interface ap_scan to 2 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Jan  1 12:36:43 heffa NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 3 
Jan  1 12:37:43 heffa NetworkManager: <info>  Activation (ath0/wireless): association took too long. 
Jan  1 12:37:43 heffa NetworkManager: <info>  (ath0): device state change: 5 -> 6 
Jan  1 12:37:43 heffa NetworkManager: <info>  Activation (ath0/wireless): asking for new secrets 
Jan  1 12:37:43 heffa NetworkManager: <info>  (ath0): supplicant connection state change: 3 -> 0 
Jan  1 12:37:58 heffa NetworkManager: <info>  ath0: link timed out. 
Jan  1 12:38:50 heffa NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2 
Jan  1 12:42:43 heffa NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: Message did not receive a reply (timeout by message bus). 
Jan  1 12:42:43 heffa NetworkManager: <info>  (ath0): device state change: 6 -> 9 
Jan  1 12:42:43 heffa NetworkManager: <info>  Activation (ath0) failed for access point (milne2) 
Jan  1 12:42:43 heffa NetworkManager: <info>  Marking connection 'milne2 WPA' invalid. 
Jan  1 12:42:43 heffa NetworkManager: <info>  Activation (ath0) failed. 
Jan  1 12:42:43 heffa NetworkManager: <info>  (ath0): device state change: 9 -> 3 
Jan  1 12:42:43 heffa NetworkManager: <info>  (ath0): deactivating device (reason: 0).

---

### Post by Mintux on 2009-01-01
Can't really help you much, but when operating a wireless interface you're supposed to have BOTH wifi0 AND ath0. ath0 is the actual wireless interface used by the system, but you must (for some reason I can't really explain) also have the wifi0 interface configured. The wifi0 having no "wireless extensions" is normal.

Your problem is clearly that the system does not (for whatever reason) manage to configure the interface ath0.

---

### Post by ramorrismorris on 2009-01-06
I have a clear memory that I rebooted my Acer after all my final configuration fiddling, and then tried again to no effect. Nevertheless, when  restarted from hardware cold start, my WPA home router connected flawlessly, with no further configuration.  Absolutely the only thing that makes sense to me is that the previous attempts were ubuntu restarts with no intervening hard shutdown....

---

