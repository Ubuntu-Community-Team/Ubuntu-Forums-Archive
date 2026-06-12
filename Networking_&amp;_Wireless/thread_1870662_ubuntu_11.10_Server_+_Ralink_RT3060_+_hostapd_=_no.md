---
title: "ubuntu 11.10 Server + Ralink RT3060 + hostapd = no ssid broadcast"
date: 2011-10-27
forum: Networking &amp; Wireless
---

### Post by Ren1601 on 2011-10-27
Hi, 

i need help with a strange problem. I bought a Ralink RT3060 pci wlan device to use it with hostapd. I use the hostapd packages from the ubuntu repositories. The Problem is that hostapd is running without any error outputs, but the ssid is not broadcasted somehow. I can't join the network because i can't find the ssid i configured in hostapd.conf within the wireless network browser of my mac. I don't know if hostapd got stuck because when i start it manually there is no more output printed (see output below).

here is my hostapd.conf

```

interface=wlan0
driver=nl80211
ssid=Testnet
channel=1
hw_mode=g
ieee80211n=1
auth_algs=1
wpa=3
wpa_passphrase=1234567890
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP CCMP
rsn_pairwise=CCMP

```


hostapd -dd hostapd.conf

```

Configuration file: hostapd.conf
nl80211: Add own interface ifindex 3
nl80211: New interface mon.wlan0 created: ifindex=14
nl80211: Add own interface ifindex 14
BSS count 1, BSSID mask 00:00:00:00:00:00 (0 bits)
nl80211: Added 802.11b mode based on 802.11g information
Allowed channel: mode=1 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=1 chan=13 freq=2472 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=1 freq=2412 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=2 freq=2417 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=3 freq=2422 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=4 freq=2427 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=5 freq=2432 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=6 freq=2437 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=7 freq=2442 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=8 freq=2447 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=9 freq=2452 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=10 freq=2457 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=11 freq=2462 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=12 freq=2467 MHz max_tx_power=20 dBm
Allowed channel: mode=0 chan=13 freq=2472 MHz max_tx_power=20 dBm
RATE[0] rate=10 flags=0x1
RATE[1] rate=20 flags=0x1
RATE[2] rate=55 flags=0x1
RATE[3] rate=110 flags=0x1
RATE[4] rate=60 flags=0x0
RATE[5] rate=90 flags=0x0
RATE[6] rate=120 flags=0x0
RATE[7] rate=180 flags=0x0
RATE[8] rate=240 flags=0x0
RATE[9] rate=360 flags=0x0
RATE[10] rate=480 flags=0x0
RATE[11] rate=540 flags=0x0
Completing interface initialization
Mode: IEEE 802.11g  Channel: 1  Frequency: 2412 MHz
Flushing old station entries
Deauthenticate all stations
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=0 set_tx=1 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_nl80211_set_key: ifindex=3 alg=0 addr=(nil) key_idx=3 set_tx=0 seq_len=0 key_len=0
Using interface wlan0 with hwaddr 80:1f:02:08:77:21 and ssid 'Testnet'
Deriving WPA PSK based on passphrase
SSID - hexdump_ascii(len=7):
     54 65 73 74 6e 65 74                              Testnet         
PSK (ASCII passphrase) - hexdump_ascii(len=10): [REMOVED]
PSK (from passphrase) - hexdump(len=32): [REMOVED]
WPA: group state machine entering state GTK_INIT (VLAN-ID 0)
GMK - hexdump(len=32): [REMOVED]
GTK - hexdump(len=32): [REMOVED]
WPA: group state machine entering state SETKEYSDONE (VLAN-ID 0)
wpa_driver_nl80211_set_key: ifindex=3 alg=2 addr=(nil) key_idx=1 set_tx=1 seq_len=0 key_len=32
nl80211: Set beacon (beacon_set=0)
wlan0: Setup of interface done.
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'mon.wlan0' added
Unknown event 5
RTM_NEWLINK: operstate=0 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Unknown event 5

----Output stops here----


```


lsmod:

```
Module                  Size  Used by
appletalk              34448  0 
openafs               768548  2 
ipt_MASQUERADE         12759  1 
xt_conntrack           12760  2 
iptable_nat            13229  1 
nf_nat                 25890  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19716  5 iptable_nat,nf_nat
nf_conntrack           82342  5 ipt_MASQUERADE,xt_conntrack,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
iptable_filter         12810  1 
ip_tables              27473  2 iptable_nat,iptable_filter
x_tables               29846  5 ipt_MASQUERADE,xt_conntrack,iptable_nat,iptable_filter,ip_tables
dm_crypt               23199  1 
arc4                   12529  2 
rt2800pci              18715  0 
rt2800lib              54306  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50325  3 rt2800pci,rt2800lib,rt2x00pci
ppdev                  17113  0 
psmouse                73882  0 
serio_raw              13166  0 
mac80211              306714  3 rt2800lib,rt2x00pci,rt2x00lib
cfg80211              199587  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
parport_pc             36962  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  0 
snd_hda_codec         104802  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_timer              29991  1 snd_pcm
snd                    68182  6 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
i915                  566658  1 
drm_kms_helper         42558  1 i915
drm                   236330  2 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
r8169                  52788  0 

```


lspci:

```

00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
03:00.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R

```


iw list:

```

	Supported interface modes:
		 * IBSS
		 * managed
		 * AP
		 * AP/VLAN
		 * WDS
		 * monitor
		 * mesh point

```


iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  Mode:Master  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon.wlan0  IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```


ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:25:22:be:44:93  
          inet addr:192.168.4.5  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:febe:4493/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:833807 errors:0 dropped:0 overruns:0 frame:0
          TX packets:472384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:948706646 (948.7 MB)  TX bytes:143034193 (143.0 MB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3630 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:307537 (307.5 KB)  TX bytes:307537 (307.5 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr 80-1F-02-08-77-21-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 80:1f:02:08:77:21  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::821f:2ff:fe08:7721/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:104686 (104.6 KB)

```

I really don't know how to solve this. Any help would be appreciated! :)

---

### Post by Ren1601 on 2011-10-27
Hmm no one an idea?

---

### Post by ratcheer on 2011-10-27
Run "sudo lspci -v" and post the output section for the RT3060.

Tim

---

### Post by jawilljr on 2011-10-27
Looks like [this guy is having the same problem.](http://marc.info/?l=linux-wireless&m=131805718207199&w=2)

If it were me I would try the latest compat-wireless.

Jerry

---

### Post by Ren1601 on 2011-10-27
Here is the output for lspci -v

> 
03:00.0 Network controller: Ralink corp. RT3060 Wireless 802.11n 1T/1R
	Subsystem: Edimax Computer Co. Device 7711
	Flags: bus master, slow devsel, latency 32, IRQ 21
	Memory at febf0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci


---

### Post by Ren1601 on 2011-10-27
@ Jerry, where can i find "compat-wireless" ? is it part of the repositories? apt-cache search compat-wireless did not find anything.

---

### Post by jawilljr on 2011-10-27
[Here.](http://linuxwireless.org/en/users/Download)

I would probably go for the latest bleeding edge first.

To install is easy just download and extract it the cd to the source path. Then type these commands

```
./scripts/driver-select rt2x00
make
sudo make install
```

Then reboot.

To uninstall issue these commands:

```
sudo make uninstall
make clean
```

Jerry

---

### Post by Ren1601 on 2011-10-27
That did it! :D Thank you so much Jerry!!!

Here is what i did:

> 
sudo apt-get install build-essential
wget [http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://linuxwireless.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2)
tar xfv compat-wireless-2.6.tar.bz2
cd compat-wireless-2011-10-27
/scripts/driver-select rt2x00
make
sudo make install


to be sure i rebooted and everything worked! :D

---

### Post by jawilljr on 2011-10-27
Great!!! Glad to help.

Jerry

---

### Post by ratcheer on 2011-10-27
I'm happy it worked for you, but that's not what I would have done. I would have just gone to the Ralink website and downloaded the proper driver for the card. But, I guess all's well that ends well.

Tim

---

### Post by jawilljr on 2011-10-27
> **ratcheer said:**
> I'm happy it worked for you, but that's not what I would have done. I would have just gone to the Ralink website and downloaded the proper driver for the card. But, I guess all's well that ends well.

Tim

He is using the Kernel supported driver.  The staging drivers have ben deprecated by [this commit](https://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=fefecc6989b4b24276797270c0e229c07be02ad3)

So for Kernel versions 3.0 and up rt2800usb/pci are the correct drivers.

Also the firmware files on Ralink's site are outdated... they were updated on [this commit](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=commit;h=5c10f3d6a5c76dca943ae68926b602bd0a1eae35)

BTW Oneiric has the correct updated firmware...versions 34 and version 29.

Jerry

---

### Post by ratcheer on 2011-10-27
Except that rt2800pci does not work for many users, including me. I have heard that it might be fixed in the 3.1 kernel.

So, I have to download and install rt2860. Even if it is outdated, at least it works.

Tim

PS - I know this is still true, because every time the kernel is upgraded, rt2800pci is included again, and my network stops working. Then, I have to reinstall rt2860.

---

### Post by tmuehlhoff on 2012-01-13
@ratcheer: sure you've got hostapd working with the ralink drivers ? Tried it recently without success (no AP mode). but the latest compat-wireless as of 2012-01-12 did the trick (not the stock Ubuntu 11.1)
-t

---

