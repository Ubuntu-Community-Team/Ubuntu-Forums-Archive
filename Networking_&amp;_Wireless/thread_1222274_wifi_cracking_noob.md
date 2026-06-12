---
title: "wifi cracking noob"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by davewickett on 2009-07-24
**wifi cracking noob **  				 					"right this is where i have got too a bit of help would be good"

davewickett@davewickett-laptop:~$ sudo airmon-ng start wifi0 11
[sudo] password for davewickett: 


Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID	Name
3211	NetworkManager
3230	wpa_supplicant
3236	avahi-daemon
3237	avahi-daemon
3824	dhclient
Process with PID 3824 (dhclient) is running on interface ath0


Interface	Chipset		Driver

wifi0		Atheros		madwifi-ng
ath0		Atheros		madwifi-ng VAP (parent: wifi0)
ath1		Atheros		madwifi-ng VAP (parent: wifi0) (monitor mode enabled)

davewickett@davewickett-laptop:~$ sudo xterm -e "airodump-ng -c 11 mon0" &
[1] 4174
davewickett@davewickett-laptop:~$ sudo xterm -e "airodump-ng -c 11 ath1" &
[2] 4188
[1]   Done                    sudo xterm -e "airodump-ng -c 11 mon0"
davewickett@davewickett-laptop:~$ 

"but my packets are colleting really slow" 
"and what do i do next after this step" 
"and is my interfaces ok or not been having problems"

---

