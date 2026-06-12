---
title: "Thinkpad x220, Realtkek RTL8188CE, Dynamic Wep ( 802.1x ) problem"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by br0wn on 2011-10-20
Hi everybody!

I think the title is very clear. I cannot connect to 802.1x networks with my Thinkpad x220 with Realtek RTL8188CE wireless card (Thinkpad bgn). I'm using Ubuntu 11.04 and drivers are form the Realtek's site, network uses PEAP and MsCHAPv2.

I'm connecting through nm-applet. That method always worked on my old laptop. I tried with or without certificate, with different versions of phase 2, and so on..

From the log, it seems as I cannot get response from DHCP server. Here's the log from /var/log/syslog:

```


Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) starting connection 'Auto FERwlan'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0/wireless): connection 'Auto FERwlan' has security, and secrets exist.  No new secrets need
ed.
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'ssid' value 'FERwlan'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'scan_ssid' value '1'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'key_mgmt' value 'IEEE8021X'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'password' value '<omitted>'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'eap' value 'PEAP'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'fragment_size' value '1300'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'phase2' value 'auth=MSCHAPV2'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: added 'identity' value 'mb44572'
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> Config: set interface ap_scan to 1
Oct 20 16:51:30 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: Trying to associate with 00:12:80:6e:3b:40 (SSID='FERwlan' freq=2457 MHz)
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): supplicant connection state:  scanning -> associating
Oct 20 16:51:31 br0wn-ubuntu-x220 kernel: [ 4768.121502] wlan0: authenticate with 00:12:80:6e:3b:40 (try 1)
Oct 20 16:51:31 br0wn-ubuntu-x220 kernel: [ 4768.122797] wlan0: authenticated
Oct 20 16:51:31 br0wn-ubuntu-x220 kernel: [ 4768.122813] wlan0: associate with 00:12:80:6e:3b:40 (try 1)
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: Associated with 00:12:80:6e:3b:40
Oct 20 16:51:31 br0wn-ubuntu-x220 kernel: [ 4768.128171] wlan0: RX AssocResp from 00:12:80:6e:3b:40 (capab=0x431 status=0 aid=174)
Oct 20 16:51:31 br0wn-ubuntu-x220 kernel: [ 4768.128191] wlan0: associated
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-EAP-STARTED EAP authentication started
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): supplicant connection state:  associating -> associated
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-EAP-PROPOSED-METHOD vendor=0 method=25
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-EAP-METHOD EAP vendor 0 method 25 (PEAP) selected
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-EAP-PEER-CERT depth=0 subject='/CN=gazda.fer.hr'
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: last message repeated 2 times
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: EAP-MSCHAPV2: Authentication succeeded
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: EAP-TLV: TLV Result - Success - EAP-TLV/Phase2 Completed
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-EAP-SUCCESS EAP authentication completed successfully
Oct 20 16:51:31 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-CONNECTED - Connection to 00:12:80:6e:3b:40 completed (reauth) [id=0 id_str=]
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): supplicant connection state:  associated -> completed
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'FERw
lan'.
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> dhclient started with pid 3930
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: Copyright 2004-2010 Internet Systems Consortium.
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: All rights reserved.
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: For info, please visit https://www.isc.org/software/dhcp/
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: 
Oct 20 16:51:31 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: Listening on LPF/wlan0/ec:55:f9:c3:15:d3
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: Sending on   LPF/wlan0/ec:55:f9:c3:15:d3
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: Sending on   Socket/fallback
Oct 20 16:51:31 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Oct 20 16:51:34 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 16:51:41 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Oct 20 16:51:49 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
Oct 20 16:51:59 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Oct 20 16:52:06 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
Oct 20 16:52:15 br0wn-ubuntu-x220 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <warn> (wlan0): DHCPv4 request timed out.
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 3930
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <warn> Activation (wlan0/wireless): could not get IP configuration for connection 'Auto FERwlan'.
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 7 -> 6 (reason 0)
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0/wireless): asking for new secrets
Oct 20 16:52:16 br0wn-ubuntu-x220 NetworkManager[806]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 6 -> 9 (reason 7)
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <warn> Activation (wlan0) failed for access point (FERwlan)
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <info> Marking connection 'Auto FERwlan' invalid.
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <warn> Activation (wlan0) failed.
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Oct 20 16:52:19 br0wn-ubuntu-x220 NetworkManager[806]: <info> (wlan0): deactivating device (reason: 0).
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.517331] wlan0: deauthenticating from 00:12:80:6e:3b:40 by local choice (reason=3)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.614686] cfg80211: All devices are disconnected, going to restore regulatory settings
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.614701] cfg80211: Restoring regulatory settings
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.614737] cfg80211: Calling CRDA to update world regulatory domain
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622710] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622723] cfg80211: World regulatory domain updated:
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622727] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622735] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622741] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622747] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622753] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 20 16:52:19 br0wn-ubuntu-x220 kernel: [ 4816.622758] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 20 16:52:19 br0wn-ubuntu-x220 wpa_supplicant[1048]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=0


```

I tried from terminal with wpa_supplicant and dhclient but it always hang on DHCPDISCOVER :/ And Google isn't very helpful..

:help:

I'd be very thankful for any help.

---

### Post by br0wn on 2011-10-25
Bump :(

---

### Post by KarboN on 2011-11-16
Same X220, same wireless card, same problem with PEAP MSCHAPv2 at school.

However, I noticed some different effects on WPA2 TKIP at work.  I was downloading at around 3Mo/s (25 mbits) dropping around 225k/s (2mbits), and then going back up.  We're only 5 on the network and I can assure it was not a network congestion issue.

I read quite a lot on the subject.  There seems to have different paths of solution (or rather of problems...).

Some people report problems with PEAP/MSCHAPv2 and the gnome-networkmanager.  Other are complaining about bad driver support.

I tried substituting the kernel driver with ndiswrapper, 32 and 64 bits, none would install.  EDIT: Actually would install, but it won't start.

Will try tomorrow to bypass the gnome-networkmanager and use wpa_supplicant to see if it is any better with the PEAP/MSCHAPv2.

Anyone with relative or total success with this laptop/adapter yet?

---

### Post by br0wn on 2011-12-01
> **KarboN said:**
> Same X220, same wireless card, same problem with PEAP MSCHAPv2 at school.

However, I noticed some different effects on WPA2 TKIP at work.  I was downloading at around 3Mo/s (25 mbits) dropping around 225k/s (2mbits), and then going back up.  We're only 5 on the network and I can assure it was not a network congestion issue.

I read quite a lot on the subject.  There seems to have different paths of solution (or rather of problems...).

Some people report problems with PEAP/MSCHAPv2 and the gnome-networkmanager.  Other are complaining about bad driver support.

I tried substituting the kernel driver with ndiswrapper, 32 and 64 bits, none would install.  EDIT: Actually would install, but it won't start.

Will try tomorrow to bypass the gnome-networkmanager and use wpa_supplicant to see if it is any better with the PEAP/MSCHAPv2.

Anyone with relative or total success with this laptop/adapter yet?

Huh, glad I'm not alone in this problem :) I've also tried to bypass gnome-networkmanager with wpa_supplicant but with no success. I hope you'll have more luck than I did :)

Please post your progress (or even solution) here if you make some, as will I.

---

### Post by frankgerhardt on 2011-12-21
This [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220](http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X220) solved it for me. 

The only difference is that I use the newer linux-image-3.0.0.12-generic instead of the 2.x kernel. 

Now the network and the display resolution are fine.

Frank.

---

