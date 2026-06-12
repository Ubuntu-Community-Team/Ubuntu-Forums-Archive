---
title: "Kismet + Atheros. Whats my source?"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by r3gista on 2009-01-20
Hi all,
I'm a new member but I have been using the site for many months now and found it very useful so thanks to all that help. But now I'm stuck and having trouble finding a solution. I need to edit my kismet.conf to enter a source. ie source=type,interface,name. I dont no what my source is. I have tried using 

source=madwifi_ag,wlan0,madwifi

but that didnt work. Here is the output..

Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.




This is the output of iwconfig.

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"john"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:FC:AF:AE   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality=100/100  Signal level:-60 dBm  Noise level=-103 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.
.


Thanks in advance. Any questions just post and I'll reply ASAP.
--r3gista

---

