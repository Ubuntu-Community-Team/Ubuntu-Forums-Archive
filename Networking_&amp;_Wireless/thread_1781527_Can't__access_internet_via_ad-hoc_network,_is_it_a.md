---
title: "Can't  access internet via ad-hoc network, is it a driver bug?"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by samy234 on 2011-06-13
Hi,

I want to connect to a wireless open ad-hoc network to have internet access. It worked a while ago (1/2 year or something) but some update must have messed something up so it doesn't work any longer. 

Situation: There is a laptop that is running windows 7 and is connected to the internet via cabel. A open ad-hoc network is configuered with sharing of internet connection, status of the ad-hoc network is "waiting for users to connect". I want to connect with a second laptop that is running ubuntu 11.04. I can find the network and connect to it.

Problem: I cannot get any internet access while being connected to the ad-hoc network. 

So my questions are:
how can i find out if what causes the Problem?
I suspect a driver issue, but I'm not sure.

required information from Howto post a wireless issue:

```
Laptop: Fujitsu Siemens Amilo pi 2530

lspci:
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

ifconfig:
wlan0     Link encap:Ethernet  Hardware Adresse 00:1b:77:78:7e:6a  
          inet Adresse:192.168.137.148  Bcast:192.168.137.255  Maske:255.255.255.0
          inet6-Adresse: fe80::21b:77ff:fe78:7e6a/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:1324 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5909 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:432076 (432.0 KB)  TX bytes:392530 (392.5 KB)

iwconfig wlan0:
wlan0     IEEE 802.11abg  ESSID:"juliaaah"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: A2:70:38:33:60:26   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

lsmod:
iwl3945               152278  0  (i think this is the wireless driver)

dmesg | grep "iwl3945":
[   17.963349] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   17.963353] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   17.963444] iwl3945 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   17.963460] iwl3945 0000:04:00.0: setting latency timer to 64
[   18.052175] iwl3945 0000:04:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   18.052180] iwl3945 0000:04:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.052348] iwl3945 0000:04:00.0: irq 47 for MSI/MSI-X
[   18.159592] iwl3945 0000:04:00.0: loaded firmware version 15.32.2.9
[  140.860282] iwl3945 0000:04:00.0: failed to remove IBSS station 00:00:00:00:00:00
[  278.461519] Modules linked in: binfmt_misc parport_pc ppdev joydev arc4 snd_hda_codec_realtek snd_hda_codec_si3054 snd_hda_intel iwl3945 radeon snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device iwlcore mac80211 ttm snd drm_kms_helper psmouse cfg80211 drm serio_raw soundcore snd_page_alloc lirc_ite8709(C) lirc_dev i2c_algo_bit video lp parport ahci libahci r8169

sudo lshw -C network:
*-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:78:7e:6a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 ip=192.168.137.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:47 memory:f0200000-f0200fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:03:0d:6f:c6:c5
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff

iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: A2:70:38:33:60:26
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-36 dBm  
                    Encryption key:off
                    ESSID:"juliaaah"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=00000004f92823a7
                    Extra: Last beacon: 60ms ago
                    IE: Unknown: 00086A756C6961616168
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010001004000

uname -mr:
2.6.38-8-generic x86_64
```please help

---

### Post by samy234 on 2011-06-27
Help? Anyone?

---

### Post by Shrekster on 2011-07-12
Same problem here. Anyone?

---

### Post by flash63 on 2011-07-12
Hello,
You have created an ad-hoc network with Network-Manager too, that's wrong.

```
wlan0     IEEE 802.11abg  ESSID:"juliaaah"  
          [COLOR="DarkOrange"]Mode:Ad-Hoc[/COLOR]  Frequency:2.457 GHz  Cell: A2:70:38:33:60:26   

```
Delete the profile, and connect easily to the Ad-Hoc Network that you created in Windows. Pay attention to the input of the access key in hex-Code or plain text (ASCII).

---

### Post by samy234 on 2011-08-29
Hi flash, thanks for your reply.
I'm pretty sure I didn't, I just tried to connect to the network via the networkmanager. Anyway I tried It again today and it didn't work. I deleted all wireless network connections configurations in the network manager that I surely do not use, just to be safe.

There never was any access key because its an open network.

this time i wasn't even able to connect to the network like last time, even though it is running and waiting for users to connect.

this is what happens in the syslog when I try to connect:
```
meanSchleppie NetworkManager[844]: <info> Activation (wlan0) starting connection 'Auto juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0/wireless): connection 'Auto juliaaah' requires no security.  No secrets needed.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'ssid' value 'juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'mode' value '1'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: set interface ap_scan to 2
Aug 29 23:12:33 meanSchleppie wpa_supplicant[962]: Trying to associate with SSID 'juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 5 -> 3 (reason 0)
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): deactivating device (reason: 0).
Aug 29 23:12:33 meanSchleppie wpa_supplicant[962]: Association request to the driver failed
Aug 29 23:12:33 meanSchleppie kernel: [ 7636.831709] wlan0: Trigger new scan to find an IBSS to join
Aug 29 23:12:33 meanSchleppie kernel: [ 7636.832790] iwl3945 0000:04:00.0: failed to remove IBSS station 00:00:00:00:00:00
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) starting connection 'Auto juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0/wireless): connection 'Auto juliaaah' requires no security.  No secrets needed.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'ssid' value 'juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'mode' value '1'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: added 'key_mgmt' value 'NONE'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> Config: set interface ap_scan to 2
Aug 29 23:12:33 meanSchleppie wpa_supplicant[962]: Trying to associate with SSID 'juliaaah'
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Aug 29 23:12:33 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  scanning -> associating
Aug 29 23:12:33 meanSchleppie wpa_supplicant[962]: Association request to the driver failed
Aug 29 23:12:33 meanSchleppie kernel: [ 7636.881458] wlan0: Trigger new scan to find an IBSS to join
Aug 29 23:12:34 meanSchleppie kernel: [ 7637.071235] wlan0: Selected IBSS BSSID 46:49:d4:36:60:26 based on configured SSID
Aug 29 23:12:34 meanSchleppie wpa_supplicant[962]: Associated with 46:49:d4:36:60:26
Aug 29 23:12:34 meanSchleppie wpa_supplicant[962]: CTRL-EVENT-CONNECTED - Connection to 46:49:d4:36:60:26 completed (reauth) [id=0 id_str=]
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  associating -> associated
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> (wlan0): supplicant connection state:  associated -> completed
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'juliaaah'.
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 29 23:12:34 meanSchleppie dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Aug 29 23:12:34 meanSchleppie dhclient: Copyright 2004-2010 Internet Systems Consortium.
Aug 29 23:12:34 meanSchleppie dhclient: All rights reserved.
Aug 29 23:12:34 meanSchleppie dhclient: For info, please visit https://www.isc.org/software/dhcp/
Aug 29 23:12:34 meanSchleppie dhclient: 
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> dhclient started with pid 7534
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Aug 29 23:12:34 meanSchleppie NetworkManager[844]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Aug 29 23:12:34 meanSchleppie dhclient: Listening on LPF/wlan0/00:1b:77:78:7e:6a
Aug 29 23:12:34 meanSchleppie dhclient: Sending on   LPF/wlan0/00:1b:77:78:7e:6a
Aug 29 23:12:34 meanSchleppie dhclient: Sending on   Socket/fallback
Aug 29 23:12:34 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Aug 29 23:12:37 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
Aug 29 23:12:42 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
Aug 29 23:12:56 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
Aug 29 23:13:11 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
Aug 29 23:13:18 meanSchleppie dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <warn> (wlan0): DHCPv4 request timed out.
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 7534
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) scheduled...
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) started...
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Timeout) complete.
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) failed (no IP configuration found)
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 7 -> 9 (reason 5)
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <warn> Activation (wlan0) failed for access point (juliaaah)
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Marking connection 'Auto juliaaah' invalid.
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <warn> Activation (wlan0) failed.
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> (wlan0): device state change: 9 -> 3 (reason 0)
Aug 29 23:13:19 meanSchleppie NetworkManager[844]: <info> (wlan0): deactivating device (reason: 0).
```

---

### Post by Timbo337 on 2011-09-13
I had this same issue on my laptop with 11.04, but not with the same laptop and windows XP. My Fios internet has gone out and the technician isn't coming for another week, so I wanted to use wireless tether and my android phone to at least get some internet, albeit slow.

XP could find and connect to the ad hoc server running on the phone just fine, but 11.04 could only see the network in network manager. If I tried to connect, it would give me the "hourglass" icon on the panel, and wouldn't connect. Connecting to a regular wireless AP was no issue, though.

I hated using XP, so I figured out some issues:

Turns out ubuntu 11.04 wasn't setting the dns server in ad hoc mode. Try editing /etc/resolv.conf (it is probably blank except for a comment) and adding

nameserver 192.168.2.254

or whatever the lan IP of your ad hoc server (e.g. my phone is 192.168.2.254). Now try connecting to the network in network manager. Hopefully it works.

---

### Post by Virus666 on 2012-02-20
> **Timbo337 said:**
> I had this same issue on my laptop with 11.04, but not with the same laptop and windows XP. My Fios internet has gone out and the technician isn't coming for another week, so I wanted to use wireless tether and my android phone to at least get some internet, albeit slow.

XP could find and connect to the ad hoc server running on the phone just fine, but 11.04 could only see the network in network manager. If I tried to connect, it would give me the "hourglass" icon on the panel, and wouldn't connect. Connecting to a regular wireless AP was no issue, though.

I hated using XP, so I figured out some issues:

Turns out ubuntu 11.04 wasn't setting the dns server in ad hoc mode. Try editing /etc/resolv.conf (it is probably blank except for a comment) and adding

nameserver 192.168.2.254

or whatever the lan IP of your ad hoc server (e.g. my phone is 192.168.2.254). Now try connecting to the network in network manager. Hopefully it works.

That is definetely not a DNS issue. I have the same WIFI card and the problem is to connect the network; not to get the internet after connecting the network.

My WIFI card:

```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
    Subsystem: Hewlett-Packard Company Compaq 6710b or nx9420 Notebook
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at d8000000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
```

I have made a AD-HOC WIFI network with Windows 7. Then I tried to connect it with my Ubuntu 10.10 Maverick Meerkat and it failed to connect the ad-doc wifi netwrok both without password or with WEP password.

That is a old thread but most of the users have problems with connecting ad-hoc wireless networks, such as hotspots...

Any ideas?

---

### Post by utsab1987 on 2012-03-08
I too have the same problem.
I cant connect to ad hoc wifi network.

Help Please



02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Subsystem: Hewlett-Packard Company Device 1453
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at 90800000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [140] Device Serial Number e0-2a-82-dd-3c-0d-00-00
	Kernel driver in use: rt3090
	Kernel modules: rt3090sta

---

