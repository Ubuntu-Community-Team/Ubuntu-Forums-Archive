---
title: "Unable to create wireless ad-hoc access point"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jmmL on 2011-02-25
Everything was working absolutely fine until maybe 4-5 days ago. I create an ad-hoc AP to connect my phone to (so that I can use landline internet with my phone, and not incur data charges).

Now whenever the AP is created it just cycles between "$access_point connection established" and "$access_point Disconnected" every few seconds.

Here is a syslog output:```
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) starting connection 'android'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 26 00:31:24 localhost NetworkManager[809]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0/wireless): connection 'android' requires no security.  No secrets needed.
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Config: added 'ssid' value 'android'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Config: added 'mode' value '1'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Config: added 'frequency' value '2412'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Config: added 'key_mgmt' value 'NONE'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 26 00:31:24 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Feb 26 00:31:24 localhost NetworkManager[809]: <info> Config: set interface ap_scan to 2
Feb 26 00:31:24 localhost wpa_supplicant[971]: Trying to associate with SSID 'android'
Feb 26 00:31:24 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Feb 26 00:31:24 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb 26 00:31:24 localhost wpa_supplicant[971]: Association request to the driver failed
Feb 26 00:31:24 localhost kernel: [12607.019232] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:26 localhost kernel: [12609.126391] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:28 localhost kernel: [12611.181385] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:30 localhost kernel: [12613.230359] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:31 localhost kernel: [12614.049972] wlan0: Creating new IBSS network, BSSID d6:42:6a:2a:5d:34
Feb 26 00:31:31 localhost kernel: [12614.088315] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon
Feb 26 00:31:31 localhost wpa_supplicant[971]: Associated with d6:42:6a:2a:5d:34
Feb 26 00:31:31 localhost wpa_supplicant[971]: CTRL-EVENT-CONNECTED - Connection to d6:42:6a:2a:5d:34 completed (reauth) [id=0 id_str=]
Feb 26 00:31:31 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  associating -> associated
Feb 26 00:31:31 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  associated -> completed
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'android'.
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Feb 26 00:31:31 localhost NetworkManager[809]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Feb 26 00:31:31 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Feb 26 00:31:31 localhost avahi-daemon[818]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.42.43.1.
Feb 26 00:31:31 localhost avahi-daemon[818]: New relevant interface wlan0.IPv4 for mDNS.
Feb 26 00:31:31 localhost avahi-daemon[818]: Registering new address record for 10.42.43.1 on wlan0.IPv4.
Feb 26 00:31:31 localhost kernel: [12614.090451] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert INPUT --in-interface wlan0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --jump REJECT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --out-interface wlan0 --jump REJECT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --in-interface wlan0 --out-interface wlan0 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan0 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --insert FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table nat --insert POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Starting dnsmasq...
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) successful, device activated.
Feb 26 00:31:32 localhost dnsmasq[3774]: junk found in command line
Feb 26 00:31:32 localhost dnsmasq[3774]: FAILED to start up
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Feb 26 00:31:32 localhost NetworkManager[809]: <warn> dnsmasq exited with error: Configuration problem (1)
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): device state change: 8 -> 9 (reason 18)
Feb 26 00:31:32 localhost NetworkManager[809]: <warn> Activation (wlan0) failed for access point (android)
Feb 26 00:31:32 localhost NetworkManager[809]: <warn> Activation (wlan0) failed.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): deactivating device (reason: 0).
Feb 26 00:31:32 localhost avahi-daemon[818]: Withdrawing address record for 10.42.43.1 on wlan0.
Feb 26 00:31:32 localhost avahi-daemon[818]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 10.42.43.1.
Feb 26 00:31:32 localhost avahi-daemon[818]: Interface wlan0.IPv4 no longer relevant for mDNS.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table nat --delete POSTROUTING --source 10.42.43.0/255.255.255.0 --destination ! 10.42.43.0/255.255.255.0 --jump MASQUERADE
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --destination 10.42.43.0/255.255.255.0 --out-interface wlan0 --match state --state ESTABLISHED,RELATED --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --source 10.42.43.0/255.255.255.0 --in-interface wlan0 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface wlan0 --out-interface wlan0 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --out-interface wlan0 --jump REJECT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete FORWARD --in-interface wlan0 --jump REJECT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan0 --protocol udp --destination-port 67 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan0 --protocol tcp --destination-port 67 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan0 --protocol udp --destination-port 53 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Executing: /sbin/iptables --table filter --delete INPUT --in-interface wlan0 --protocol tcp --destination-port 53 --jump ACCEPT
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) starting connection 'android'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  completed -> disconnected
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0/wireless): connection 'android' requires no security.  No secrets needed.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Config: added 'ssid' value 'android'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Config: added 'mode' value '1'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Config: added 'frequency' value '2412'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Config: added 'key_mgmt' value 'NONE'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Feb 26 00:31:32 localhost NetworkManager[809]: <info> Config: set interface ap_scan to 2
Feb 26 00:31:32 localhost wpa_supplicant[971]: Trying to associate with SSID 'android'
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Feb 26 00:31:32 localhost NetworkManager[809]: <info> (wlan0): supplicant connection state:  scanning -> associating
Feb 26 00:31:32 localhost wpa_supplicant[971]: Association request to the driver failed
Feb 26 00:31:32 localhost kernel: [12615.438893] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:34 localhost kernel: [12617.480910] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:37 localhost kernel: [12619.582311] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:38 localhost NetworkManager[809]: <info> (wlan0): device state change: 5 -> 3 (reason 39)
Feb 26 00:31:38 localhost NetworkManager[809]: <info> (wlan0): deactivating device (reason: 39).
Feb 26 00:31:38 localhost NetworkManager[809]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 26 00:31:38 localhost NetworkManager[809]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Feb 26 00:31:38 localhost kernel: [12620.634831] iwlagn 0000:02:00.0: failed to remove IBSS station 00:00:00:00:00:00
``` "android" is the name of the AP.

Here is a more condensed kern.log:```
Feb 26 00:31:24 localhost kernel: [12607.019232] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:26 localhost kernel: [12609.126391] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:28 localhost kernel: [12611.181385] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:30 localhost kernel: [12613.230359] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:31 localhost kernel: [12614.049972] wlan0: Creating new IBSS network, BSSID d6:42:6a:2a:5d:34
Feb 26 00:31:31 localhost kernel: [12614.088315] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon
Feb 26 00:31:31 localhost kernel: [12614.090451] iwlagn 0000:02:00.0: Unable to find TIM Element in beacon
Feb 26 00:31:32 localhost kernel: [12615.438893] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:34 localhost kernel: [12617.480910] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:37 localhost kernel: [12619.582311] wlan0: Trigger new scan to find an IBSS to join
Feb 26 00:31:38 localhost kernel: [12620.634831] iwlagn 0000:02:00.0: failed to remove IBSS station 00:00:00:00:00:00
```

At the moment I'm unable to test if I can connect to a network properly - there are no unsecured wifi APs near me.

I'm not 100% certain what wireless hardware I have, but I'm pretty sure it's the Intel 4965 AGN, using iwlwifi (I think it used to use iwlagn, but this was merged..?).

Is anyone able to create ad-hoc APs with natty? Anyone with similar problems?

---

### Post by ronacc on 2011-02-26
I get the same thing with my "infrastructure" AP every few minutes and to get my connection back I have to go to NM and disable wireless and then re-enable it , then it works for a few more minutes , its been doing this all along for me in natty ,my wireless is realtek rtl8185  .

---

### Post by jmmL on 2011-02-27
That workaround doesn't work for me, unfortunately.

---

### Post by jmmL on 2011-02-27
I wonder if this is a possible kernel regression. I'm pretty sure that this issue only started when I switched to 2.6.38-5, which is based on 2.6.38-rc6. Looking at the [changelog]("http://lwn.net/Articles/429201/") for rc6 I see this: ```
David S. Miller (4):
...
iwlwifi: Delete iwl3945_good_plcp_health.

...
Stanislaw Gruszka (2):
iwl3945: remove plcp check
```
I'm not sure what plcp is though..

I tried booting -4 or -3, but neither would get to the login screen. I think this is due to the new xserver and nvidia changes that came through with -5. I'll try again soon in safe mode.

---

### Post by jmmL on 2011-03-05
The latest update to networkmanager seems to have fixed this issue.

---

