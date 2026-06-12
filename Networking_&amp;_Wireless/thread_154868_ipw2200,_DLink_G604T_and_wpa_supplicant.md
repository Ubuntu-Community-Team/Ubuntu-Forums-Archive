---
title: "ipw2200, DLink G604T and wpa_supplicant"
date: 2006-04-04
forum: Networking &amp; Wireless
---

### Post by chriscmuir on 2006-04-04
Hi, I was hoping somebody could help me.  I'm fairly new to Ubuntu, have enjoyed it over a couple of other tried Linux distros, and now am trying to get everything working successfully.  My wireless link is my last obstacle, as the Ubuntu Forums have been very useful in solving most issues.

My wireless problem is I'm unable to obtain an internet connection through my DLink G604T modem/router using WPA from my Dell Inspiron 9200 with an Intel 2200 nic.

I'd previously attempted to use WEP with no success either.  WPA suites me fine as I have another PC with a WPA enabled NIC I need to support (it doesn't work to well with WEP), and I require encryption because my local area has a number of neighbours with wireless connections.

There is a fair amount of posts on the forums regards these 3 techologies (G604T, ipw2200 and WPA), some posts having over 50 pages.  Trawling my way through the posts and trying (hacking) the many various solutions has not resulted in success :( 

I've followed the forum post [here]("http://ubuntuforums.org/showthread.php?t=26623&highlight=dell+wireless") to setup the ipw2200 and wpa_supplicant, using the ipw2200 v1.1.0 driver, ipw2200 v2.4 firmware and the ieee80211 v1.1.13 driver.

My /etc/wpa_supplicant.conf is as follows:

```
ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
	ssid="<my_ssid>"
	scan_ssid=1
	proto=WPA
	key_mgmt=WPA-PSK
	psk=<my_hex_psk>
}
```
....where <my_hex_psk> is a 64 character hex string I generated using wpa_passphrase.

On starting wpa_supplicant manually with the following command:

```

sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd

```
I receive the following output:

```

Initializing interface 'eth1' conf '/etc/wpa_supplicant.conf' driver 'ipw'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group=0
eapol_version=1
ap_scan=1
fast_reauth=1
Line: 30 - start of a new network block
ssid - hexdump_ascii(len=8):
     <my_ssid_hex>                           <my_ssid>
scan_ssid=1 (0x1)
proto: 0x1
key_mgmt: 0x2
PSK - hexdump(len=32): [REMOVED]
Priority group 0
   id=0 ssid='<my_ssid>'
Daemonize..

```
ifconfig returns the following output:

```

eth1      Link encap:Ethernet  HWaddr 00:0E:35:C0:25:C5
          inet addr:10.1.1.2  Bcast:10.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:45 errors:18 dropped:55 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:6693 (6.5 KiB)  TX bytes:5325 (5.2 KiB)
          Interrupt:7 Base address:0xe000 Memory:faffc000-faffcfff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2228125 (2.1 MiB)  TX bytes:2228125 (2.1 MiB)


```
iwconfig returns the following output:

```

lo        no wireless extensions.

eth0      no wireless extensions.

Warning: Driver for device eth1 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

eth1      IEEE 802.11g  ESSID:"<my_ssid>"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:11:95:95:63:8A
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:18  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:37   Missed beacon:1

```
The warning message here is a bit suspect but as the ieee80211, ipw2200 and wap_supplicant software I installed is neither version 17 or 18, I'm not sure what it is referring to.

An iwlist eth1 scan reveals the following:

```

Warning: Driver for device eth1 recommend version 18 of Wireless Extension,
but has been compiled with version 17, therefore some driver features
may not be available...

eth1      Scan completed :
          Cell 01 - <another wireless network>
          Cell 02 - <another wireless network
          Cell 03 - Address: 00:11:95:95:63:8A
                    ESSID:"<my_essid>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:22 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Quality=86/100  Signal level=-44 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 4690ms ago

```
Again the warning message.  The iwlist proves I can see my modem/router and WPA encryption is turned on.

And my /etc/network/interfaces file is as follows:

```

auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#	script grep
#	map eth0

#iface eth0 inet static
#address 10.1.1.2
#netmask 255.0.0.0
#gateway 10.1.1.1

iface eth1 inet static
address 10.1.1.2
netmask 255.0.0.0
gateway 10.1.1.1
wireless-essid <my_ssid>

auto eth1

```
Within my interfaces file I've disabled eth0 while attempting to get the wireless to work.  I've also assigned a static IP as I intend to use Oracle XE which makes DHCP a no-no.

I suspect the problem is with my WPA configuration, but not sure given my new exposure to Linux.  As a final point I am able to connect to the modem/router through Windows and another local PC using WPA, ensuring the modem/router is configured correctly.

Any help anybody can provide it resolving this issue would be appreciated.

Regards,

CM.

---

### Post by chriscmuir on 2006-04-06
Not a single reply :(  The ubuntu community isn't as rich as I thought it was.  Or maybe I gave too much information and scared everybody off.

Anyhow, "stumbled" across wifi-radar while installing other software.  Now able to connect.  Performance seems slow compared to Windows but at least it's working.

---

