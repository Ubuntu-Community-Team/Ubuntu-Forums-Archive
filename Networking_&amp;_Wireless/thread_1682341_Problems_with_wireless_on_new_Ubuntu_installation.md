---
title: "Problems with wireless on new Ubuntu installation"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by andywhoa on 2011-02-05
I've just installed Ubuntu.  My house isn't wired so I use wireless on all my machines to connect to the internet.

When I start up Ubuntu, I can connect to my wireless router.  After about 3 minutes, I get disconnected.  It refuses to reconnect for several minutes.  If I disable and reenable networking, I can establish a connection again, but the process is repeated.

I'm not really sure what the issue is here.  Any guesses?  This is a desktop and I'm using a Belkin wireless adapter.



Ubuntu 10.10 x64








syslog
> andrew@andrew:~$ tail -f /var/log/syslog
Feb  5 18:17:11 andrew avahi-daemon[1020]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.101.
Feb  5 18:17:11 andrew avahi-daemon[1020]: New relevant interface wlan0.IPv4 for mDNS.
Feb  5 18:17:11 andrew avahi-daemon[1020]: Registering new address record for 192.168.0.101 on wlan0.IPv4.
Feb  5 18:17:12 andrew NetworkManager[1053]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Feb  5 18:17:12 andrew NetworkManager[1053]: <info> Policy set 'Auto enigma' (wlan0) as default for IPv4 routing and DNS.
Feb  5 18:17:12 andrew NetworkManager[1053]: <info> Activation (wlan0) successful, device activated.
Feb  5 18:17:12 andrew NetworkManager[1053]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Feb  5 18:17:14 andrew ntpdate[1798]: adjust time server 91.189.94.4 offset -0.203801 sec
Feb  5 18:17:17 andrew kernel: [   55.290003] wlan0: no IPv6 routers present
Feb  5 18:17:46 andrew pulseaudio[1594]: ratelimit.c: 4 events suppressed



Feb  5 18:22:51 andrew kernel: [  388.580005] No probe response from AP 00:1e:58:39:1a:f5 after 500ms, disconnecting.
Feb  5 18:22:51 andrew wpa_supplicant[1330]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Feb  5 18:22:51 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Feb  5 18:22:51 andrew kernel: [  388.821276] cfg80211: All devices are disconnected, going to restore regulatory settings
Feb  5 18:22:51 andrew kernel: [  388.821280] cfg80211: Restoring regulatory settings
Feb  5 18:22:51 andrew kernel: [  388.821283] cfg80211: Calling CRDA to update world regulatory domain
Feb  5 18:22:51 andrew kernel: [  388.823382] cfg80211: World regulatory domain updated:
Feb  5 18:22:51 andrew kernel: [  388.823384]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  5 18:22:51 andrew kernel: [  388.823386]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:22:51 andrew kernel: [  388.823388]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:22:51 andrew kernel: [  388.823390]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:22:51 andrew kernel: [  388.823392]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:22:51 andrew kernel: [  388.823394]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  5 18:22:51 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Feb  5 18:22:52 andrew wpa_supplicant[1330]: Trying to associate with 00:1e:58:39:1a:f5 (SSID='enigma' freq=2422 MHz)
Feb  5 18:22:52 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb  5 18:22:52 andrew kernel: [  390.392720] wlan0: authenticate with 00:1e:58:39:1a:f5 (try 1)
Feb  5 18:22:53 andrew kernel: [  390.590005] wlan0: authenticate with 00:1e:58:39:1a:f5 (try 2)
Feb  5 18:22:53 andrew kernel: [  390.790005] wlan0: authenticate with 00:1e:58:39:1a:f5 (try 3)
Feb  5 18:22:53 andrew kernel: [  390.990004] wlan0: authentication with 00:1e:58:39:1a:f5 timed out
Feb  5 18:22:58 andrew NetworkManager[1053]: <info> (wlan0): roamed from BSSID 00:1E:58:39:1A:F5 (enigma) to (none) ((none))
Feb  5 18:23:02 andrew wpa_supplicant[1330]: Authentication with 00:1e:58:39:1a:f5 timed out.
Feb  5 18:23:02 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Feb  5 18:23:02 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Feb  5 18:23:04 andrew wpa_supplicant[1330]: Trying to associate with 00:1e:58:39:1a:f5 (SSID='enigma' freq=2422 MHz)
Feb  5 18:23:04 andrew NetworkManager[1053]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb  5 18:23:04 andrew kernel: [  401.872767] wlan0: direct probe to 00:1e:58:39:1a:f5 (try 1)
Feb  5 18:23:04 andrew kernel: [  402.070009] wlan0: direct probe to 00:1e:58:39:1a:f5 (try 2)
Feb  5 18:23:04 andrew kernel: [  402.270005] wlan0: direct probe to 00:1e:58:39:1a:f5 (try 3)
Feb  5 18:23:05 andrew kernel: [  402.470004] wlan0: direct probe to 00:1e:58:39:1a:f5 timed out




route
> andrew@andrew:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

---

### Post by andywhoa on 2011-02-05
Anyone have any ideas? :(

---

### Post by rcayea on 2011-02-05
I don't have an answer but a massive suggestion. Please post the exact model number of your Belkin adapter. Folks will be able to help much more this way.

---

### Post by andywhoa on 2011-02-05
Belkin Wireless N+ USB Adapter

Not sure if it's first or second version

I searched Google and came up with a few links, but nothing has worked so far

---

### Post by andywhoa on 2011-02-06
This computer is in my bedroom.  The wireless router is down the hall.

It would appear that opening my bedroom door makes things better.  With the bedroom door open, I'll stay connected anywhere between 5 minutes and 1 hour.

This still isn't good enough, though.  Usually I don't maintain connection very long and I'll have to turn networking off and back on.  This is particularly annoying when I'm trying to download software for my new install.

:(

---

