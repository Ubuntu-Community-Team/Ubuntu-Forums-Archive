---
title: "Cannot connect to WPA wireless network"
date: 2012-02-13
forum: Networking &amp; Wireless
---

### Post by burkemw3 on 2012-02-13
My ubuntu box cannot connect to a wireless network that is secured with WPA. It can connect to other wireless networks that are unsecured and secured with WPA2. Macs, Androids, and PCs are able to connect to the WPA secured network.

When I select the network, Fluffy, I am prompted for a password then some time goes by then I am prompted for a password again. This process repeats on end.

Yesterday, I was experiencing a similar issue connecting. I read a post about issues with IPv6 and changed the IPv6 Method to Ignore, which allowed the computer to connect. Today, it is unable to connect. All other settings are the default.

I have a ZOTAC GF9300-K-E Motherboard with an onboard VIA VT6656 wireless card. I am running Ubuntu 11.10 with kernel 3.0.0-15. When trying to view the router admin screen, it identifies itself as a WRT54G. I do not have access to the router.

How can I connect to this network?

some outputs:

**tail -f /var/log/syslog | grep NetworkManager** while trying to connect:
```

Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) starting connection 'Fluffy'
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started...
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting...
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0]
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1/wireless): connection 'Fluffy' has security, and secrets exist.  No new secrets needed.
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Config: added 'ssid' value 'Fluffy'
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Config: added 'scan_ssid' value '1'
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Config: added 'psk' value '<omitted>'
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete.
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> Config: set interface ap_scan to 1
Feb 13 21:08:04 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:05 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:06 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:11 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:11 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:12 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:12 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:16 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:16 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:17 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:18 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:22 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:22 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:23 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:23 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:27 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:27 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:28 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:29 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:33 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:33 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:34 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:34 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:38 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:38 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:40 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:40 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:44 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:44 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:45 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:45 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:49 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:49 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:51 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:51 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:08:55 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:08:55 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:08:56 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:08:56 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:09:00 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:09:00 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: disconnected -> scanning
Feb 13 21:09:02 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: scanning -> associating
Feb 13 21:09:02 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: associating -> 4-way handshake
Feb 13 21:09:04 canis-minor NetworkManager[881]: <warn> Activation (eth1/wireless): association took too long.
Feb 13 21:09:04 canis-minor NetworkManager[881]: <info> (eth1): device state change: config -> need-auth (reason 'none') [50 60 0]
Feb 13 21:09:04 canis-minor NetworkManager[881]: <warn> Activation (eth1/wireless): asking for new secrets
Feb 13 21:09:04 canis-minor NetworkManager[881]: <info> (eth1): supplicant interface state: 4-way handshake -> disconnected
Feb 13 21:09:04 canis-minor NetworkManager[881]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Feb 13 21:09:07 canis-minor NetworkManager[881]: <warn> No agents were available for this request.
Feb 13 21:09:07 canis-minor NetworkManager[881]: <info> (eth1): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Feb 13 21:09:07 canis-minor NetworkManager[881]: <warn> Activation (eth1) failed for access point (Fluffy)
Feb 13 21:09:07 canis-minor NetworkManager[881]: <info>
```

**iwconfig**
```
eth1      802.11-a/b/g  ESSID:"Fluffy"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=0/255  
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level:-42 dBm  Noise level:0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**ifconfig**
```
eth1      Link encap:Ethernet  HWaddr 00:12:7b:4c:73:99  
          inet6 addr: fe80::212:7bff:fe4c:7399/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:727 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14581 (14.5 KB)  TX bytes:54262 (54.2 KB)
```

**iwlist** (removed extra cells)
```
eth1      Scan completed :
          Cell 05 - Address: 00:18:39:7D:FA:62
                    ESSID:"Fluffy"
                    Mode:Managed
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-50 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by duckductduck on 2012-12-26
I have the exact same issue with almost the exact same output. I'm running Ubuntu Studio 12.04 with kernel 3.2.0-33.

Are you still having this issue after all this time or have you found a solution?

---

### Post by burkemw3 on 2013-01-09
I don't remember finding a solution to this issue. I am no longer attempting to use this network anymore.

---

