---
title: "UDP connectivity disappears after WPA Rescan"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by oliwel on 2008-12-16
Hi Folks,

I am running ibex on a Thinkpad X 300 using iwlagn driver for the builtin card. At home, with a WEP secured network, I never saw problems.

Now, I am on a vacation and tried to connect to the offered unsecured WLAN - it worked without problems BUT after I connect, I am unable to run DNS queries.

Summary:
[LIST]
[*] NetworkManager found SSID and connects
[*] System seems to work
[*] After approx. 10 Seconds, I am unable to reach the DNS Server anymore
[*] Issueing a reconnect, brings back DNS for about 10 Seconds
[/LIST]

Here is what I tracked down:

The daemon.log
```

Dec 17 04:03:30 aurum NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
Dec 17 04:03:30 aurum NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 17 04:03:30 aurum NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
Dec 17 04:03:30 aurum NetworkManager: <info>    address 172.22.220.69 
Dec 17 04:03:30 aurum NetworkManager: <info>    prefix 24 (255.255.255.0) 
Dec 17 04:03:30 aurum NetworkManager: <info>    gateway 172.22.220.1 
Dec 17 04:03:30 aurum NetworkManager: <info>    nameserver '192.168.1.1' 
Dec 17 04:03:30 aurum NetworkManager: <info>    domain name 'nomadix.com' 
Dec 17 04:03:30 aurum NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 17 04:03:30 aurum NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 17 04:03:30 aurum NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 17 04:03:31 aurum NetworkManager: <info>  (wlan0): device state change: 7 -> 8 
Dec 17 04:03:31 aurum NetworkManager: <info>  Policy set 'Sandals' (wlan0) as default for routing and DNS. 
Dec 17 04:03:31 aurum NetworkManager: <info>  Activation (wlan0) successful, device activated. 
Dec 17 04:03:31 aurum NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 17 04:03:53 aurum NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 3 
Dec 17 04:03:53 aurum NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 4 
Dec 17 04:03:53 aurum NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 7 

```

Running a loop with a shortlived "dig" command brings results starting around 04:03:38 and ends with the first connection change message at 04:03:53.

Running the wpa-supplicant in debug mode shows, that it starts a rescan after 10 seconds - even as it does not find new access points, it magically crashes the network. 

As besides DNS even ntp shows the same behaviour, I guess the whole UDP stack is smashed.

Iptables are empty, when I send the DNS queries through a VPN into my home network, they work!

As I dont have access to the infrastructure, I cannot exclude any missbehaviour at the hotels equipment (they run a "nomadix" access system).

Anybody seen such before? Anybody at hand with a simple solution? I guess preventing a rescan should help.

Oliver

---

### Post by oliwel on 2008-12-17
Some additional Info - above applies to a fully patched ibex system as of Dec 5.
When I boot into an older kernel (2.6.24), the system uses another drover iwl4965 and it works!
So it seems to be an issue with the driver. 

Oliver

---

