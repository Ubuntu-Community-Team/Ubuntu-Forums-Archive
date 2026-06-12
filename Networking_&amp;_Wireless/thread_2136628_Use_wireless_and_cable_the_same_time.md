---
title: "Use wireless and cable the same time"
date: 2013-04-18
forum: Networking &amp; Wireless
---

### Post by smedia on 2013-04-18
Hello,

i'm using Ubuntu 12.10 with my dell laptop. Sometimes, i want to connect to an dedicated networking device without Internet Connection via cable and use Internet over wifi. But always, when an ethernet link is detected, something disables my wifi. 
rfkill says, it is hard blocked, so it's not possible to enable it again with rfkill. 

In Log, i see the following messages: 

Apr 18 12:30:57 laptop NetworkManager[1308]: <info> Policy set 'Auto-Ethernet' (eth0) as default for IPv4 routing and DNS.
Apr 18 12:30:57 laptop NetworkManager[1308]: <info> Activation (eth0) successful, device activated.
Apr 18 12:30:57 laptop NetworkManager[1308]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 18 12:30:57 laptop dbus[1035]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 18 12:30:57 laptop dbus[1035]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 18 12:30:58 laptop acvpnagent[1721]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Apr 18 12:30:58 laptop avahi-daemon[1243]: Joining mDNS multicast group on interface eth0.IPv6 with address fe80::d6be:d9ff:fe80:c056.
Apr 18 12:30:58 laptop acvpnagent[1721]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Apr 18 12:30:58 laptop avahi-daemon[1243]: New relevant interface eth0.IPv6 for mDNS.
Apr 18 12:30:58 laptop avahi-daemon[1243]: Registering new address record for fe80::d6be:d9ff:fe80:c056 on eth0.*.
Apr 18 12:30:58 laptop acvpnagent[1721]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Apr 18 12:30:58 laptop acvpnagent[1721]: Function: tableCallbackHandler File: RouteMgr.cpp Line: 1681 Invoked Function: recv Return Code: 11 (0x0000000B) Description: unknown 
Apr 18 12:31:01 laptop kernel: [101529.612926] iwlwifi 0000:03:00.0: RF_KILL bit toggled to disable radio.
Apr 18 12:31:01 laptop kernel: [101529.613044] wlan0: deauthenticating from 02:6f:81:fb:ba:c8 by local choice (reason=3)
Apr 18 12:31:01 laptop wpa_supplicant[1513]: rfkill: WLAN hard blocked
Apr 18 12:31:01 laptop NetworkManager[1308]: <info> WiFi now disabled by radio killswitch
Apr 18 12:31:01 laptop NetworkManager[1308]: <info> (wlan0): device state change: activated -> unavailable (reason 'none') [100 20 0]
Apr 18 12:31:01 laptop kernel: [101529.613192] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.613198] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.613201] HW problem - can not stop rx aggregation for tid 0
Apr 18 12:31:01 laptop kernel: [101529.613229] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.613231] HW problem - can not stop rx aggregation for tid 1
Apr 18 12:31:01 laptop kernel: [101529.613237] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.613240] HW problem - can not stop rx aggregation for tid 3
Apr 18 12:31:01 laptop NetworkManager[1308]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 18 12:31:01 laptop kernel: [101529.625028] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.625033] ieee80211 phy0: failed to remove key (0, 02:6f:81:fb:ba:c8) from hardware (-5)
Apr 18 12:31:01 laptop wpa_supplicant[1513]: wlan0: CTRL-EVENT-DISCONNECTED bssid=02:6f:81:fb:ba:c8 reason=3
Apr 18 12:31:01 laptop kernel: [101529.641081] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.641088] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.641101] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.641136] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.641166] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.641169] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.657017] iwlwifi 0000:03:00.0: Not sending command - RF KILL
Apr 18 12:31:01 laptop kernel: [101529.657020] ieee80211 phy0: failed to remove key (2, ff:ff:ff:ff:ff:ff) from hardware (-5)
Apr 18 12:31:01 laptop kernel: [101529.657058] cfg80211: All devices are disconnected, going to restore regulatory settings
Apr 18 12:31:01 laptop kernel: [101529.657060] cfg80211: Restoring regulatory settings
Apr 18 12:31:01 laptop kernel: [101529.657062] cfg80211: Calling CRDA to update world regulatory domain



does anyone know, which process is disabling the wifi chip and how can i stop it from doing this? It looks like wpa_supplicant has something to do with it, but i didn't find any option or script, which is doing it. 
Any suggestions?

---

### Post by TheFu on 2013-04-18
I don't know the answer, but having 2 network cards on the same subnet at the same time is dangerous and asking for problems.  Routing can get all mixed up and I've experienced all sorts of timeouts due to this.  In theory, controlling which interface gets priority should be handled by the "metric" setting (lower is higher priority), but in practice, that didn't seem to work between wired and wifi connections for me.  On my laptop, there seems to be a hardware setting that disabled wifi automatically when the ethernet jack is used.  I haven't looked, but there is probably a BIOS setting controlling it.

Probably not the answer, but worth checking out.

---

### Post by smedia on 2013-04-18
Hi,

interesting point with the bios. I will check that, perhaps, this could explain the mysteria. 

I know, that having 2 network cards in the same network is a problem and that's not, what i want to do. Sometimes, i have to connect to a totally different subnet without an internet connection, so i won't have any routing conflicts.

---

### Post by smedia on 2013-04-22
Hello again,

i've checked my bios settings and indeed, i found a Power Management setting, which disables wifi when detecting an ethernet link. 

Thank you very much for your hint.

---

