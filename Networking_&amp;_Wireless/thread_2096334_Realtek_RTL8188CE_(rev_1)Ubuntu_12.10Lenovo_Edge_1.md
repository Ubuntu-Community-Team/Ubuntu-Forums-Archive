---
title: "Realtek RTL8188CE (rev 1)/Ubuntu 12.10/Lenovo Edge 14&quot;"
date: 2012-12-19
forum: Networking &amp; Wireless
---

### Post by NeilHanlon on 2012-12-19
Two separate (but possibly related) issues:

Wifi works everywhere in my house on 12.10, with no problems -- except for a 5 square foot area in my room. If I move my laptop out of that five square foot area, it works fine. If it's in it, it's a crapshoot. Sometimes it'll work for a half hour without timing out (I've been running a "watch iwlist wlan0 scan", and the Last Beacon just stops updating....), other times, it'll work for 5 seconds after re-authenticating with my network. The area I speak of is on the third floor of my house. My router is in my basement, with it's antennae pointing upwards. The only way I can "fix" it is by turning off wifi and turning it back on (on the laptop).

NOTE: I have no issues with wifi in Windows 7 on the same laptop.

Second issue:

My school uses 802.1x with a self-signed certificate. Same issue as above, but it's everywhere, no matter how close I am to an access point. (or how far away).


Now for some information?

lspci:
```

03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8195
	Flags: bus master, fast devsel, latency 0, IRQ 17
	I/O ports at 2000 [size=256]
	Memory at f0400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 01-91-81-fe-ff-4c-e0-00
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce

```

ifconfig/iwconfig:
```

wlan0     Link encap:Ethernet  HWaddr 60:d8:19:ca:00:3e  
          inet addr:192.168.1.9  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1034  Metric:1
          RX packets:433051 errors:0 dropped:0 overruns:0 frame:0
          TX packets:319146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:369026449 (369.0 MB)  TX bytes:37138262 (37.1 MB)


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off

```

lsmod:
```

rtl8192ce              53594  0 
rtl8192c_common        48779  1 rtl8192ce
rtlwifi                74705  1 rtl8192ce

```

sudo cat /var/log/syslog | grep -e ipw -e firmware -e wpa -e wlan -e etork | tail -n55 :

```

Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0/wireless): access point 'hanlon' has security, but secrets are required.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0/wireless): connection 'hanlon' has security, and secrets exist.  No new secrets needed.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Dec 19 14:36:23 ubuntu NetworkManager[852]: <info> (wlan0): supplicant interface state: inactive -> scanning
Dec 19 14:36:24 ubuntu wpa_supplicant[22567]: wlan0: SME: Trying to authenticate with 30:46:9a:13:78:ff (SSID='hanlon' freq=2412 MHz)
Dec 19 14:36:24 ubuntu kernel: [175479.021974] wlan0: authenticate with 30:46:9a:13:78:ff
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Dec 19 14:36:24 ubuntu wpa_supplicant[22567]: wlan0: Trying to associate with 30:46:9a:13:78:ff (SSID='hanlon' freq=2412 MHz)
Dec 19 14:36:24 ubuntu kernel: [175479.041798] wlan0: send auth to 30:46:9a:13:78:ff (try 1/3)
Dec 19 14:36:24 ubuntu kernel: [175479.043274] wlan0: authenticated
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): supplicant interface state: authenticating -> associating
Dec 19 14:36:24 ubuntu kernel: [175479.057340] wlan0: associate with 30:46:9a:13:78:ff (try 1/3)
Dec 19 14:36:24 ubuntu kernel: [175479.064458] wlan0: RX AssocResp from 30:46:9a:13:78:ff (capab=0x431 status=0 aid=5)
Dec 19 14:36:24 ubuntu kernel: [175479.064597] wlan0: associated
Dec 19 14:36:24 ubuntu kernel: [175479.065627] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 19 14:36:24 ubuntu wpa_supplicant[22567]: wlan0: Associated with 30:46:9a:13:78:ff
Dec 19 14:36:24 ubuntu wpa_supplicant[22567]: wlan0: WPA: Key negotiation completed with 30:46:9a:13:78:ff [PTK=CCMP GTK=CCMP]
Dec 19 14:36:24 ubuntu wpa_supplicant[22567]: wlan0: CTRL-EVENT-CONNECTED - Connection to 30:46:9a:13:78:ff completed (auth) [id=0 id_str=]
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): supplicant interface state: associating -> completed
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'hanlon'.
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Dec 19 14:36:24 ubuntu kernel: [175479.074310] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Dec 19 14:36:24 ubuntu dhclient: Listening on LPF/wlan0/60:d8:19:ca:00:3e
Dec 19 14:36:24 ubuntu dhclient: Sending on   LPF/wlan0/60:d8:19:ca:00:3e
Dec 19 14:36:24 ubuntu dhclient: DHCPREQUEST of 192.168.1.9 on wlan0 to 255.255.255.255 port 67
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Dec 19 14:36:24 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Dec 19 14:36:25 ubuntu NetworkManager[852]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Dec 19 14:36:26 ubuntu NetworkManager[852]: <info> (wlan0): roamed from BSSID 30:46:9A:13:78:FF (hanlon) to (none) ((none))
Dec 19 14:36:26 ubuntu NetworkManager[852]: <info> Policy set 'hanlon' (wlan0) as default for IPv4 routing and DNS.
Dec 19 14:36:26 ubuntu NetworkManager[852]: <info> Activation (wlan0) successful, device activated.
Dec 19 14:36:26 ubuntu NetworkManager[852]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Dec 19 14:54:35 ubuntu wpa_supplicant[22567]: wlan0: WPA: Group rekeying completed with 30:46:9a:13:78:ff [GTK=CCMP]

```

(Earlier, when I was getting this issue, I was getting "Failed to initiate AP Scan" from wpa_supplicant when it timed out... I forgot to save any of those results.)

dmesg | grep rtl

```

[   77.816479] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[   77.988481] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   77.988788] rtlwifi: wireless switch is on
[62061.454727] rtlwifi: wireless switch is on
[139621.682246] rtlwifi: wireless switch is on
[172760.162937] rtlwifi: wireless switch is on
[175084.786405] Modules linked in: snd_hda_codec_hdmi snd_hda_codec_realtek coretemp kvm arc4 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm microcode thinkpad_acpi joydev uvcvideo videobuf2_core snd_seq_midi videodev videobuf2_vmalloc videobuf2_memops snd_rawmidi intel_ips rtl8192ce rtl8192c_common rtlwifi lpc_ich psmouse snd_seq_midi_event mac80211 serio_raw i915 snd_seq cfg80211 snd_timer snd_seq_device drm_kms_helper drm wmi mei i2c_algo_bit snd snd_page_alloc soundcore nvram video rfcomm bnep parport_pc bluetooth ppdev lp parport binfmt_misc mac_hid hid_generic usbhid hid ums_realtek r8169 uas usb_storage
[175474.273821] rtlwifi: wireless switch is on

```

sudo lshw -C network:

```

  *-network               
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 60:d8:19:ca:00:3e
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-19-generic firmware=N/A ip=192.168.1.9 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0400000-f0403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 04:7d:7b:39:ac:2c
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8168d-2.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:3000(size=256) memory:f0804000-f0804fff memory:f0800000-f0803fff memory:f0820000-f083ffff

```

```
&#9581;&#9472;<root@ubuntu>-</var/log>-<3:05PM>-&#9671;
&#9584;&#9472;&#10148; iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 30:46:9A:13:78:FF
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"hanlon"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000147ac4e25d
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000668616E6C6F6E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010002004000
                    IE: Unknown: DD840050F204104A0001101044000102103B000103104700100000000000001000000030469A1378FF1021000D4E6574676561722C20496E632E10230008574E4452333730301024000456314831104200046E6F6E651054000800060050F204000110110015574E44523337303028576972656C65737320415029100800020086103C000103
```

```

&#9581;&#9472;<root@ubuntu>-</var/log>-<3:05PM>-&#9671;
&#9584;&#9472;&#10148; lsb_release -d
Description:	Ubuntu 12.10

```

```

&#9581;&#9472;<root@ubuntu>-</var/log>-<3:06PM>-&#9671;
&#9584;&#9472;&#10148; uname -mr                                                               
3.5.0-19-generic x86_64

```

```

&#9581;&#9472;<root@ubuntu>-</var/log>-<3:06PM>-&#9671;
&#9584;&#9472;&#10148; /etc/init.d/networking restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service networking restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop networking ; start networking. The restart(8) utility is also available.
networking stop/waiting
networking start/running

```

---

### Post by dwb814 on 2012-12-29
Hi,

You need to blacklist some modules do this in the terminal:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```Then at the very bottom of the page, paste these lines in:
```
blacklist rtl8192cu
blacklist rtl8192c_common
blacklist rtlwifi
```Save the file!

Then download the Realtek RTL8188CE driver from here:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#2282](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&ProdID=272&DownTypeID=3&GetDown=false&Downloads=true#2282)

Open a terminal, example: say the download went to your Downloads directory in your home directory. You would do:
```
cd ~/Downloads
unzip (ZIPFILENAME)
cd (NEWDIRECTORY_CREATED)
chmod 755 ./install.sh
sudo ./install.sh
```Then add you correct module like this:
```
sudo gedit /etc/modules
```And add
```
8188ce
```To the bottom of the list, this will make it load automatically at start up, then save the file.
You will need to do the reinstall of the software from Realtek on each kernel update. So keep the file handy.

Reboot and you should be able to connect.

Hope that helps!

---

