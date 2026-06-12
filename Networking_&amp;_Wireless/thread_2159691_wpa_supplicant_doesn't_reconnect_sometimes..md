---
title: "wpa_supplicant doesn't reconnect sometimes."
date: 2013-07-04
forum: Networking &amp; Wireless
---

### Post by TT76 on 2013-07-04
Hi everyone:
I run into this problem, and don't know how to solve it. Here is my scenario. The router is set to reboot at 6 am everyday, and then my server sometimes doesn't reconnect to it anymore, I have to unplug the usb wifi dongle and plug back into it to make it work. I have no idea where to look. Could anyone help me?
Here is the syslogs.
The normal one ```
Jul  3 06:00:02 picuntu kernel: [11157.105877] wlan1: deauthenticated from ec:88:8f:82:ea:5c (Reason: 3)
Jul  3 06:00:02 picuntu wpa_supplicant[568]: wlan1: CTRL-EVENT-DISCONNECTED bssid=ec:88:8f:82:ea:5c reason=3
Jul  3 06:00:02 picuntu wpa_action: WPA_IFACE=wlan1 WPA_ACTION=DISCONNECTED
Jul  3 06:00:02 picuntu wpa_action: WPA_ID=0 WPA_ID_STR= WPA_CTRL_DIR=/var/run/wpa_supplicant
Jul  3 06:00:02 picuntu wpa_action: ifdown wlan1
Jul  3 06:00:02 picuntu kernel: [11157.472953] cfg80211: Calling CRDA for country: 
Jul  3 06:00:03 picuntu postfix/master[902]: reload -- version 2.9.6, configuration /etc/postfix
Jul  3 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for 192.168.1.250 on wlan1.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.250.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Interface wlan1.IPv6 no longer relevant for mDNS.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Leaving mDNS multicast group on interface wlan1.IPv6 with address  xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx on wlan1.
Jul  3 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx on wlan1.
Jul  3 06:00:03 picuntu wpa_action: removing sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan1.pid
Jul  3 06:00:04 picuntu kernel: [11158.695692] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jul  3 06:00:05 picuntu ntpd[1389]: Deleting interface #6 wlan1,xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=148, sent=84, dropped=0, active_time=11127 secs
Jul  3 06:00:05 picuntu ntpd[1389]: 2600:3c03:e001:1001::18:3 interface xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx-> (none)
Jul  3 06:00:05 picuntu ntpd[1389]: Deleting interface #5 wlan1, xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=0, sent=0, dropped=0, active_time=11127 secs
Jul  3 06:00:05 picuntu ntpd[1389]: Deleting interface #4 wlan1, xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=0, sent=0, dropped=0, active_time=11127 secs
Jul  3 06:00:05 picuntu ntpd[1389]: Deleting interface #3 wlan1, 192.168.1.250#123, interface stats: received=329, sent=332, dropped=0, active_time=11127 secs
Jul  3 06:00:05 picuntu ntpd[1389]: 91.189.89.199 interface 192.168.1.250 -> (none)
Jul  3 06:00:05 picuntu ntpd[1389]: 24.93.40.100 interface 192.168.1.250 -> (none)
Jul  3 06:00:05 picuntu ntpd[1389]: 18.85.44.118 interface 192.168.1.250 -> (none)
Jul  3 06:00:05 picuntu ntpd[1389]: 71.19.144.130 interface 192.168.1.250 -> (none)
Jul  3 06:00:05 picuntu ntpd[1389]: peers refreshed
Jul  3 06:00:42 picuntu wpa_supplicant[568]: wlan1: SME: Trying to authenticate with ec:88:8f:82:ea:5c (SSID='xxx' freq=2462 MHz)
Jul  3 06:00:42 picuntu kernel: [11196.856320] wlan1: authenticate with ec:88:8f:82:ea:5c (try 1)
Jul  3 06:00:42 picuntu wpa_supplicant[568]: wlan1: Trying to associate with ec:88:8f:82:ea:5c (SSID='xxx' freq=2462 MHz)
Jul  3 06:00:42 picuntu kernel: [11196.923922] wlan1: authenticated
Jul  3 06:00:42 picuntu kernel: [11196.932945] wlan1: associate with ec:88:8f:82:ea:5c (try 1)
Jul  3 06:00:42 picuntu kernel: [11196.936567] wlan1: RX ReassocResp from ec:88:8f:82:ea:5c (capab=0x431 status=0 aid=2)
Jul  3 06:00:42 picuntu kernel: [11196.936580] wlan1: associated
Jul  3 06:00:42 picuntu wpa_supplicant[568]: wlan1: Associated with ec:88:8f:82:ea:5c
Jul  3 06:00:42 picuntu kernel: [11196.972144] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Jul  3 06:00:43 picuntu wpa_supplicant[568]: wlan1: WPA: Key negotiation completed with ec:88:8f:82:ea:5c [PTK=CCMP GTK=CCMP]
Jul  3 06:00:43 picuntu wpa_supplicant[568]: wlan1: CTRL-EVENT-CONNECTED - Connection to ec:88:8f:82:ea:5c completed (reauth) [id=0 id_str=]
Jul  3 06:00:43 picuntu wpa_action: WPA_IFACE=wlan1 WPA_ACTION=CONNECTED
Jul  3 06:00:43 picuntu wpa_action: WPA_ID=0 WPA_ID_STR= WPA_CTRL_DIR=/var/run/wpa_supplicant
Jul  3 06:00:43 picuntu wpa_action: network settings not defined for default in /etc/network/interfaces
Jul  3 06:00:43 picuntu wpa_action: ifup wlan1=default
.....

```

The troubled one ```
Jul  4 06:00:02 picuntu kernel: [97559.077531] wlan1: deauthenticated from ec:88:8f:82:ea:5c (Reason: 3)
Jul  4 06:00:02 picuntu wpa_supplicant[568]: wlan1: CTRL-EVENT-DISCONNECTED bssid=ec:88:8f:82:ea:5c reason=3
Jul  4 06:00:02 picuntu wpa_action: WPA_IFACE=wlan1 WPA_ACTION=DISCONNECTED
Jul  4 06:00:02 picuntu wpa_action: WPA_ID=0 WPA_ID_STR= WPA_CTRL_DIR=/var/run/wpa_supplicant
Jul  4 06:00:02 picuntu wpa_action: ifdown wlan1
Jul  4 06:00:02 picuntu kernel: [97559.465337] cfg80211: Calling CRDA to update world regulatory domain
Jul  4 06:00:02 picuntu postfix/master[902]: reload -- version 2.9.6, configuration /etc/postfix
Jul  4 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for 192.168.1.250 on wlan1.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.250.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Interface wlan1.IPv4 no longer relevant for mDNS.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Interface wlan1.IPv6 no longer relevant for mDNS.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Leaving mDNS multicast group on interface wlan1.IPv6 with addressxxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx on wlan1.
Jul  4 06:00:03 picuntu avahi-daemon[294]: Withdrawing address record for xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx on wlan1.
Jul  4 06:00:03 picuntu wpa_action: removing sendsigs omission pidfile: /run/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan1.pid
Jul  4 06:00:03 picuntu kernel: [97560.769337] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jul  4 06:00:05 picuntu ntpd[3347]: Deleting interface #8 wlan1, xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=3, sent=3, dropped=0, active_time=559 secs
Jul  4 06:00:05 picuntu ntpd[3347]: xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx interface xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx -> (none)
Jul  4 06:00:05 picuntu ntpd[3347]: Deleting interface #6 wlan1, xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=139, sent=145, dropped=0, active_time=86312 secs
Jul  4 06:00:05 picuntu ntpd[3347]: Deleting interface #5 wlan1, fe80::4633:4cff:fe42:210d#123, interface stats: received=0, sent=0, dropped=0, active_time=86312 secs
Jul  4 06:00:05 picuntu ntpd[3347]: Deleting interface #4 wlan1, xxxx:xxx:xxxx:xxxx:xxxx:xxxx:xxxx:xxxx#123, interface stats: received=0, sent=0, dropped=0, active_time=86312 secs
Jul  4 06:00:05 picuntu ntpd[3347]: Deleting interface #3 wlan1, 192.168.1.250#123, interface stats: received=562, sent=580, dropped=0, active_time=86312 secs
Jul  4 06:00:05 picuntu ntpd[3347]: 91.189.89.199 interface 192.168.1.250 -> (none)
Jul  4 06:00:05 picuntu ntpd[3347]: 173.44.32.10 interface 192.168.1.250 -> (none)
Jul  4 06:00:05 picuntu ntpd[3347]: 85.254.216.1 interface 192.168.1.250 -> (none)
Jul  4 06:00:05 picuntu ntpd[3347]: 160.94.245.44 interface 192.168.1.250 -> (none)
Jul  4 06:00:05 picuntu ntpd[3347]: peers refreshed
Jul  4 06:01:33 picuntu ntpd[3347]: frequency file /var/lib/ntp/ntp.drift.TEMP: Permission denied
......

```
here is kernellog```
Jul  3 06:00:02 picuntu kernel: [11157.105877] wlan1: deauthenticated from ec:88:8f:82:ea:5c (Reason: 3)
Jul  3 06:00:02 picuntu kernel: [11157.472953] cfg80211: Calling CRDA for country: US
Jul  3 06:00:04 picuntu kernel: [11158.695692] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jul  3 06:00:42 picuntu kernel: [11196.856320] wlan1: authenticate with ec:88:8f:82:ea:5c (try 1)
Jul  3 06:00:42 picuntu kernel: [11196.923922] wlan1: authenticated
Jul  3 06:00:42 picuntu kernel: [11196.932945] wlan1: associate with ec:88:8f:82:ea:5c (try 1)
Jul  3 06:00:42 picuntu kernel: [11196.936567] wlan1: RX ReassocResp from ec:88:8f:82:ea:5c (capab=0x431 status=0 aid=2)
Jul  3 06:00:42 picuntu kernel: [11196.936580] wlan1: associated
Jul  3 06:00:42 picuntu kernel: [11196.972144] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Jul  4 06:00:02 picuntu kernel: [97559.077531] wlan1: deauthenticated from ec:88:8f:82:ea:5c (Reason: 3)
Jul  4 06:00:02 picuntu kernel: [97559.465337] cfg80211: Calling CRDA to update world regulatory domain
Jul  4 06:00:03 picuntu kernel: [97560.769337] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Jul  4 15:06:04 picuntu kernel: [130322.246274] usb 2-1: USB disconnect, device number 2
......

```

---

