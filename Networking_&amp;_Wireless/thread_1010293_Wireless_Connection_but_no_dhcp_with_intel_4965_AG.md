---
title: "Wireless Connection but no dhcp with intel 4965 AGN"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by pijkie on 2008-12-13
I have recently installed ubuntu 8.10 on my laptop, a lenovo R61 with a build in wireless card model 4965 AGN.

When I try to connect it  authenticates correctly but the connection drops when it seems unable to recieve DHCP response.

In the log of the AP I also see a correct auth. and then a de-auth by the client.

The AP is a linksys WAG325N and the laptop has no problem connecting under windows XP.

[U]
**Extra iformation**[/U]

2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux


**lspci**
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
```

**iwconfig**
```
wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=81/100  Signal level:-53 dBm  Noise level=-127 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

**lsmod grep iwl**
```
iwlagn                 99588  0 
iwlcore                92740  1 iwlagn
rfkill                 17176  4 iwlcore,thinkpad_acpi
led_class              12164  2 iwlcore,thinkpad_acpi
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211

```

**dmesg**
```
[  954.925012] wlan0: authenticate with AP 00:1d:7e:ab:bd:14
[  954.927772] wlan0: authenticated
[  954.927788] wlan0: associate with AP 00:1d:7e:ab:bd:14
[  954.932313] wlan0: RX AssocResp from 00:1d:7e:ab:bd:14 (capab=0x431 status=0 aid=1)
[  954.932329] wlan0: associated
[  954.932430] wlan0 (WE) : Wireless Event too big (366)
[ 1000.219210] wlan0: disassociating by local choice (reason=3)
[ 1034.996974] wlan0: deauthenticated

```

[B]
iwlist scan[/B]
```

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:AB:BD:14
                    ESSID:"pijknet"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=80/100  Signal level:-56 dBm  Noise level=-88 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1A4C1003FFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000007e511d80
                    Extra: Last beacon: 96ms ago


```

**deamon.log**
```
Dec 13 21:34:31 B2-UB-GO bluetoothd[5323]: Starting security manager 0
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) starting connection 'Auto pijknet' 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0/wireless): access point 'Auto pijknet' has security, but secrets are required. 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 5 -> 6 
Dec 13 21:34:34 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec 13 21:34:38 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 0 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 6 -> 4 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto pijknet' has security, and secrets exist.  No new secrets needed. 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'ssid' value 'pijknet' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'psk' value '<omitted>' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'proto' value 'WPA RSN' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'pairwise' value 'TKIP CCMP' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: added 'group' value 'WEP40 WEP104 TKIP CCMP' 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  Config: set interface ap_scan to 1 
Dec 13 21:34:45 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 4 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 5 -> 6 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'pijknet'. 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
Dec 13 21:34:52 B2-UB-GO dhclient: Internet Systems Consortium DHCP Client V3.1.1
Dec 13 21:34:52 B2-UB-GO dhclient: Copyright 2004-2008 Internet Systems Consortium.
Dec 13 21:34:52 B2-UB-GO dhclient: All rights reserved.
Dec 13 21:34:52 B2-UB-GO dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Dec 13 21:34:52 B2-UB-GO dhclient: 
Dec 13 21:34:52 B2-UB-GO dhclient: wmaster0: unknown hardware address type 801
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  dhclient started with pid 6271 
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
Dec 13 21:34:52 B2-UB-GO dhclient: wmaster0: unknown hardware address type 801
Dec 13 21:34:52 B2-UB-GO NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
Dec 13 21:34:52 B2-UB-GO dhclient: Listening on LPF/wlan0/00:13:e8:47:42:6d
Dec 13 21:34:52 B2-UB-GO dhclient: Sending on   LPF/wlan0/00:13:e8:47:42:6d
Dec 13 21:34:52 B2-UB-GO dhclient: Sending on   Socket/fallback
Dec 13 21:34:56 B2-UB-GO dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
Dec 13 21:35:02 B2-UB-GO dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Dec 13 21:35:16 B2-UB-GO dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 16
Dec 13 21:35:32 B2-UB-GO dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Dec 13 21:35:37 B2-UB-GO NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6271 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Activation (wlan0) failed for access point (pijknet) 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Marking connection 'Auto pijknet' invalid. 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Activation (wlan0) failed. 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Dec 13 21:35:38 B2-UB-GO NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 

```

**lshw**
```
  *-network               
       description: Ethernet interface
       product: 82566MC Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:15:58:c9:4b:94
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=0.3-0 ip=172.20.20.103 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:47:42:6d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:f2:da:6d:af:66
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

---

### Post by jwilliams42 on 2008-12-14
I think your issue is the same as bug [https://bugs.launchpad.net/bugs/277634]("https://bugs.launchpad.net/bugs/277634"), which unfortunately does not appear to be receiving much attention. I have the same wireless card, and my connection drops at random times, with similar log messages to yours:

```
Dec 14 19:04:36 i1720 NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Dec 14 19:04:36 i1720 NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 6 
Dec 14 19:04:36 i1720 NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
Dec 14 19:04:36 i1720 NetworkManager: <info>  (wlan0): supplicant connection state change: 6 -> 7 
```

---

### Post by mrp40 on 2008-12-28
I have experienced the same problem after upgrading my HP Compaq 8510w from Hardy to Intrepid. I was able to get the connection working by assigning static IP information, but it would still take a while for the connection to start working (I have to ping my router for ~30secs before it starts working), it would drop out as reported in the bug description above, and it would kernel panic after a while as described in the [Intrepid release notes]("https://wiki.ubuntu.com/IntrepidReleaseNotes").

So I have just installed the *linux-backports-modules-intrepid* package to hopefully fix the kernel panic. After downloading a large file or leaving it on over night it would always crash. Fingers crossed this fixes it...

p.s. Installing *linux-backports-modules-intrepid* doesn't fix the DHCP problem.

---

### Post by doppiaemme on 2008-12-29
Hi to all,
the same problem here with Intrepidamd64 and 4965:
No way to connect to an AP using wep 64 by Networkmanager.
Using cli+iwconfig the card is able to associate to the AP:
tcpdump shows me bpdu from the AP and all the broacast traffic (e.g. arp requests) from other PCs associated to the same AP but no traffic from my wireless card! So dhcp is not working (dhcp requests do not leave the card) and fixed ip too (I don't see the arp request). Of course I'm running tcpdump on the same PC.
I tried a live 32bit distribution that comes with and older kernel and everything worked so the problem can't be the AP or the hardware. I seems that as soon as the card has to send a packet it disassociate from the ap:

wlan0: privacy configuration mismatch and mixed-cell disabled - disassociate

Thanks
MM

---

### Post by doppiaemme on 2008-12-31
:D
sudo apt-get install linux-backports-modules-intrepid linux-backports-modules-intrepid-generic

worked for me: both fixed ip end dhcp are ok now.
I new to ubuntu and I'm not able to understand how backport modules fixed the problem: "modinfo iwlagn" out is just the same ....
MM

---

### Post by rockorequin on 2009-02-24
Is it an 11N network? I had the same problem with an 11N network (see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305338](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/305338)) and the workaround I found is to disable 11N and reload the iwlagn driver:

sudo modprobe -r iwlagn && sudo modprobe iwlagn 11n_disable=1

or to make it permanent, add 'options iwlagn 11n_disable=1' to the /etc/modprobe.d/options file.

---

### Post by MakOwner on 2010-01-03
bumping the thread.

I just upgraded an Lenovo R61 from 9.04 to 9.10 and Wireless doesn't work.

I'll be opening posting following the instructions about "oepning a ticket" shortly.

Can't believe after all this time this is still an issue...

---

### Post by edyesed on 2012-04-08
FWIW, I am having this trouble now in oneiric.  I couldn't figure out why I could connect to wireless all over the place ( work, friend's house ), but not at home.  Turns out it's because I need this module and I have wireless N at the house, but not anywhere else.   Thanks for the tip!

$ lspci : 
   Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)

 $ lsmod | grep wl
iwlagn                314257  0 
mac80211              462046  1 iwlagn
cfg80211              199630  2 iwlagn,mac80211

---

### Post by coffeecat on 2012-04-09
Old thread closed.

---

