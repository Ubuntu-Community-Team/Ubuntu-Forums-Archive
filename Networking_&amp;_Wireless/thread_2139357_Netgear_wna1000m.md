---
title: "Netgear wna1000m"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by nonguru on 2013-04-26
I have a one of those net gear micro USBs (wna1000m) and when I load up Ubuntu 13.04 at the log in screen it will pop up a notification that says disconnected from wireless network, then about 5-10 seconds later it will say wireless connected. My network's name is called "wireless" for anyone who may get confused when reading the logs below. I am no expert at wireless connections but I know that this USB works on windows perfectly fine (dual-booting). Below is a syslog of what I feel is the cause of my wireless not working properly. Can anyone help me here?


```
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 04:25:12 nonguru dhclient: Listening on LPF/wlan0/4c:60:de:5f:fd:48
Apr 26 04:25:12 nonguru dhclient: Sending on   LPF/wlan0/4c:60:de:5f:fd:48
Apr 26 04:25:12 nonguru dhclient: Sending on   Socket/fallback
Apr 26 04:25:12 nonguru dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67 (xid=0x5fe0879f)
Apr 26 04:25:12 nonguru dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Apr 26 04:25:12 nonguru dhclient: bound to 192.168.1.5 -- renewal in 39104 seconds.
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   address 192.168.1.5
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   prefix 24 (255.255.255.0)
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   gateway 192.168.1.1
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   hostname 'nonguru'
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   nameserver '192.168.1.1'
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info>   domain name 'home'
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 26 04:25:12 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 26 04:25:12 nonguru avahi-daemon[998]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.5.
Apr 26 04:25:12 nonguru avahi-daemon[998]: New relevant interface wlan0.IPv4 for mDNS.
Apr 26 04:25:12 nonguru avahi-daemon[998]: Registering new address record for 192.168.1.5 on wlan0.IPv4.
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> Policy set 'wireless' (wlan0) as default for IPv4 routing and DNS.
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> DNS: starting dnsmasq...
Apr 26 04:25:13 nonguru NetworkManager[1026]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 26 04:25:13 nonguru NetworkManager[1026]: <error> [1366975513.533584] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 26 04:25:13 nonguru NetworkManager[1026]: <warn> DNS: plugin dnsmasq update failed
Apr 26 04:25:13 nonguru NetworkManager[1026]: <info> Writing DNS information to /sbin/resolvconf
Apr 26 04:25:13 nonguru dnsmasq[1518]: started, version 2.65 cache disabled
Apr 26 04:25:13 nonguru dnsmasq[1518]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack
Apr 26 04:25:13 nonguru dnsmasq[1518]: DBus support enabled: connected to system bus
Apr 26 04:25:13 nonguru dnsmasq[1518]: warning: no upstream servers configured
```


and this:

```
Apr 26 04:25:26 nonguru nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' took too long; killing it.Apr 26 04:25:33 nonguru NetworkManager[1026]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 26 04:25:33 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.protected: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.25': no such name
Apr 26 04:25:33 nonguru NetworkManager[1026]: <warn> Dispatcher script timed out: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' timed out.
Apr 26 04:25:33 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 26 04:25:33 nonguru NetworkManager[1026]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

The odd thing is that nothing works, but it still says I am connected.

---

### Post by praseodym on 2013-04-26
Please show the outputs of
```

lsusb
lsmod
iwconfig
rfkill list
sudo iwlist scan
```

---

### Post by nonguru on 2013-04-26
Hello praseodym, thanks for assisting me. Here are my outputs as requested :)

**Sidenote**: I noticed that grub screen (purple screen with ubuntu/memtest selections) showed up when I booted up tonight (I was not home all day since the initial post). This grub screen used to never happen since I had a fresh install of Ubuntu 13.04 yesterday. I did not change any files other than opened up the syslog to see what Network Manager was outputting. Also, the wireless seems to work on and off now but it's more functional now than before. An Ubuntu update maybe?


**lsusb:**
```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching HubBus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 002 Device 004: ID 0846:9041 NetGear, Inc. WNA1000M 802.11bgn [Realtek RTL8188CUS]
Bus 002 Device 005: ID 046d:c042 Logitech, Inc. G3 Laser Mouse
```


**lsmod:**
```
Module                  Size  Used byparport_pc             28152  0 
ppdev                  17073  0 
dm_crypt               22820  1 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228619  10 bnep,rfcomm
arc4                   12615  2 
rtl8192cu              67699  0 
rtlwifi                79673  1 rtl8192cu
rtl8192c_common        48779  1 rtl8192cu
mac80211              606457  3 rtlwifi,rtl8192c_common,rtl8192cu
cfg80211              510937  2 mac80211,rtlwifi
coretemp               13355  0 
kvm                   443165  0 
eeepc_wmi              13151  0 
snd_hda_codec_hdmi     36913  1 
asus_wmi               24213  1 eeepc_wmi
sparse_keymap          13890  1 asus_wmi
video                  19390  1 asus_wmi
snd_hda_codec_realtek    78399  1 
snd_hda_intel          39619  6 
microcode              22881  0 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
serio_raw              13215  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
mac_hid                13205  0 
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  22 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mei                    41158  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
ghash_clmulni_intel    13259  0 
radeon                937749  3 
mxm_wmi                13021  0 
i2c_algo_bit           13413  1 radeon
ttm                    83187  1 radeon
wmi                    19070  2 mxm_wmi,asus_wmi
drm_kms_helper         49394  1 radeon
r8169                  67446  0 
aesni_intel            55399  320 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
drm                   286313  5 ttm,drm_kms_helper,radeon
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
ahci                   25731  3 
libahci                31364  1 ahci

```


**iwconfig:**
```
eth0      no wireless extensions.


lo        no wireless extensions.




wlan0     IEEE 802.11bgn  ESSID:"wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:B8:51:B8:EA   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:215   Missed beacon:0





```


**rfkilllist:**
```
0: phy0: Wireless LAN    Soft blocked: no
    Hard blocked: no

```


**sudo iwlist scan:**
```
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.




wlan0     Scan completed :
          Cell 01 - Address: 00:26:B8:51:B8:EA
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"wireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000eda1e4fa92
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 0008776972656C657373
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 200100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101040003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A8C131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706555320010B1B





```

---

### Post by nonguru on 2013-04-27
Attached is the syslog while the connection was looping from offline to online, I tried clicking on the connection a few times as well.

```
Apr 26 21:28:07 nonguru dbus[929]: [system] Activating service name='org.freedesktop.hostname1' (using servicehelper)
Apr 26 21:28:07 nonguru dbus[929]: [system] Successfully activated service 'org.freedesktop.hostname1'
Apr 26 21:28:11 nonguru NetworkManager[1049]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 26 21:28:11 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 26 21:28:11 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 26 21:28:11 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Apr 26 21:28:12 nonguru dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3 (xid=0x61f4ff99)
Apr 26 21:28:15 nonguru dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7 (xid=0x61f4ff99)
Apr 26 21:28:22 nonguru dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10 (xid=0x61f4ff99)
Apr 26 21:28:32 nonguru dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13 (xid=0x61f4ff99)
Apr 26 21:28:36 nonguru NetworkManager[1049]: <warn> (wlan0): DHCPv4 request timed out.
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1863
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) scheduled...
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) started...
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> (wlan0): device state change: ip-config -> failed (reason 'ip-config-unavailable') [70 120 5]
Apr 26 21:28:36 nonguru NetworkManager[1049]: <warn> Activation (wlan0) failed for connection 'wireless'
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv4 Configure Timeout) complete.
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 26 21:28:36 nonguru avahi-daemon[1030]: Withdrawing address record for fe80::4e60:deff:fe5f:fd48 on wlan0.
Apr 26 21:28:36 nonguru avahi-daemon[1030]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::4e60:deff:fe5f:fd48.
Apr 26 21:28:36 nonguru avahi-daemon[1030]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 26 21:28:36 nonguru kernel: [   55.159724] wlan0: deauthenticating from 00:26:b8:51:b8:ea by local choice (reason=3)
Apr 26 21:28:36 nonguru wpa_supplicant[1553]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Apr 26 21:28:36 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: completed -> disconnected
Apr 26 21:28:36 nonguru kernel: [   55.182344] cfg80211: Calling CRDA to update world regulatory domain
Apr 26 21:28:36 nonguru kernel: [   55.184770] cfg80211: World regulatory domain updated:
Apr 26 21:28:36 nonguru kernel: [   55.184772] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:28:36 nonguru kernel: [   55.184773] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:36 nonguru kernel: [   55.184775] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:36 nonguru kernel: [   55.184776] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:36 nonguru kernel: [   55.184777] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:36 nonguru kernel: [   55.184778] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:38 nonguru avahi-daemon[1030]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::4e60:deff:fe5f:fd48.
Apr 26 21:28:38 nonguru avahi-daemon[1030]: New relevant interface wlan0.IPv6 for mDNS.
Apr 26 21:28:38 nonguru avahi-daemon[1030]: Registering new address record for fe80::4e60:deff:fe5f:fd48 on wlan0.*.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Auto-activating connection 'wireless'.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) starting connection 'wireless'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): access point 'wireless' has security, but secrets are required.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): connection 'wireless' has security, and secrets exist.  No new secrets needed.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: added 'ssid' value 'wireless'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: added 'scan_ssid' value '1'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: added 'psk' value '<omitted>'
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> Config: set interface ap_scan to 1
Apr 26 21:28:39 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 21:28:40 nonguru wpa_supplicant[1553]: wlan0: SME: Trying to authenticate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:28:40 nonguru kernel: [   58.666759] wlan0: authenticate with 00:26:b8:51:b8:ea
Apr 26 21:28:40 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 21:28:40 nonguru kernel: [   58.680310] wlan0: send auth to 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:28:40 nonguru wpa_supplicant[1553]: wlan0: Trying to associate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:28:40 nonguru kernel: [   58.716139] wlan0: authenticated
Apr 26 21:28:40 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 21:28:40 nonguru wpa_supplicant[1553]: wlan0: Associated with 00:26:b8:51:b8:ea
Apr 26 21:28:40 nonguru kernel: [   58.718532] wlan0: associate with 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:28:40 nonguru kernel: [   58.722153] wlan0: RX AssocResp from 00:26:b8:51:b8:ea (capab=0x431 status=0 aid=6)
Apr 26 21:28:40 nonguru kernel: [   58.722181] wlan0: associated
Apr 26 21:28:40 nonguru kernel: [   58.722219] cfg80211: Calling CRDA for country: US
Apr 26 21:28:40 nonguru kernel: [   58.724345] cfg80211: Regulatory domain changed to country: US
Apr 26 21:28:40 nonguru kernel: [   58.724347] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:28:40 nonguru kernel: [   58.724348] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Apr 26 21:28:40 nonguru kernel: [   58.724349] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Apr 26 21:28:40 nonguru kernel: [   58.724350] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:40 nonguru kernel: [   58.724351] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:40 nonguru kernel: [   58.724352] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:40 nonguru kernel: [   58.724353] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Apr 26 21:28:40 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 26 21:28:40 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 26 21:28:50 nonguru wpa_supplicant[1553]: wlan0: Authentication with 00:26:b8:51:b8:ea timed out.
Apr 26 21:28:50 nonguru kernel: [   68.728713] wlan0: disassociating from 00:26:b8:51:b8:ea by local choice (reason=3)
Apr 26 21:28:50 nonguru wpa_supplicant[1553]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Apr 26 21:28:50 nonguru kernel: [   68.749094] cfg80211: Calling CRDA to update world regulatory domain
Apr 26 21:28:50 nonguru kernel: [   68.749312] wlan0: deauthenticating from 00:26:b8:51:b8:ea by local choice (reason=3)
Apr 26 21:28:50 nonguru kernel: [   68.753024] cfg80211: World regulatory domain updated:
Apr 26 21:28:50 nonguru kernel: [   68.753028] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:28:50 nonguru kernel: [   68.753031] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:50 nonguru kernel: [   68.753034] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:50 nonguru kernel: [   68.753036] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:50 nonguru kernel: [   68.753038] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:50 nonguru kernel: [   68.753040] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:50 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Apr 26 21:28:50 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
Apr 26 21:28:50 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> need-auth (reason 'supplicant-disconnect') [50 60 8]
Apr 26 21:28:51 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 26 21:28:54 nonguru NetworkManager[1049]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): connection 'wireless' has security, and secrets exist.  No new secrets needed.
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: added 'ssid' value 'wireless'
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: added 'scan_ssid' value '1'
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: added 'psk' value '<omitted>'
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> Config: set interface ap_scan to 1
Apr 26 21:28:54 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 26 21:28:55 nonguru wpa_supplicant[1553]: wlan0: SME: Trying to authenticate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:28:55 nonguru kernel: [   73.389239] wlan0: authenticate with 00:26:b8:51:b8:ea
Apr 26 21:28:55 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 21:28:55 nonguru kernel: [   73.401497] wlan0: send auth to 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:28:55 nonguru wpa_supplicant[1553]: wlan0: Trying to associate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:28:55 nonguru kernel: [   73.423402] wlan0: authenticated
Apr 26 21:28:55 nonguru kernel: [   73.424666] wlan0: associate with 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:28:55 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 21:28:55 nonguru wpa_supplicant[1553]: wlan0: Associated with 00:26:b8:51:b8:ea
Apr 26 21:28:55 nonguru kernel: [   73.458301] wlan0: RX AssocResp from 00:26:b8:51:b8:ea (capab=0x431 status=0 aid=6)
Apr 26 21:28:55 nonguru kernel: [   73.458352] wlan0: associated
Apr 26 21:28:55 nonguru kernel: [   73.458477] cfg80211: Calling CRDA for country: US
Apr 26 21:28:55 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 26 21:28:55 nonguru kernel: [   73.462489] cfg80211: Regulatory domain changed to country: US
Apr 26 21:28:55 nonguru kernel: [   73.462492] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:28:55 nonguru kernel: [   73.462495] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Apr 26 21:28:55 nonguru kernel: [   73.462498] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Apr 26 21:28:55 nonguru kernel: [   73.462500] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:55 nonguru kernel: [   73.462502] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:55 nonguru kernel: [   73.462504] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:28:55 nonguru kernel: [   73.462506] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Apr 26 21:28:55 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 26 21:29:05 nonguru wpa_supplicant[1553]: wlan0: Authentication with 00:26:b8:51:b8:ea timed out.
Apr 26 21:29:05 nonguru kernel: [   83.465645] wlan0: disassociating from 00:26:b8:51:b8:ea by local choice (reason=3)
Apr 26 21:29:05 nonguru wpa_supplicant[1553]: wlan0: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
Apr 26 21:29:05 nonguru kernel: [   83.487923] cfg80211: Calling CRDA to update world regulatory domain
Apr 26 21:29:05 nonguru kernel: [   83.488367] wlan0: deauthenticating from 00:26:b8:51:b8:ea by local choice (reason=3)
Apr 26 21:29:05 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Apr 26 21:29:05 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): disconnected during association, asking for new key.
Apr 26 21:29:05 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> need-auth (reason 'supplicant-disconnect') [50 60 8]
Apr 26 21:29:05 nonguru kernel: [   83.491794] cfg80211: World regulatory domain updated:
Apr 26 21:29:05 nonguru kernel: [   83.491798] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:29:05 nonguru kernel: [   83.491801] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:29:05 nonguru kernel: [   83.491803] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:29:05 nonguru kernel: [   83.491806] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:29:05 nonguru kernel: [   83.491808] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:29:05 nonguru kernel: [   83.491810] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:29:06 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Apr 26 21:29:09 nonguru NetworkManager[1049]: <warn> No agents were available for this request.
Apr 26 21:29:09 nonguru NetworkManager[1049]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Apr 26 21:29:09 nonguru NetworkManager[1049]: <info> Marking connection 'wireless' invalid.
Apr 26 21:29:09 nonguru NetworkManager[1049]: <warn> Activation (wlan0) failed for connection 'wireless'
Apr 26 21:29:09 nonguru NetworkManager[1049]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 26 21:29:09 nonguru NetworkManager[1049]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) starting connection 'wireless'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): access point 'wireless' has security, but secrets are required.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): connection 'wireless' has security, and secrets exist.  No new secrets needed.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: added 'ssid' value 'wireless'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: added 'scan_ssid' value '1'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: added 'psk' value '<omitted>'
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> Config: set interface ap_scan to 1
Apr 26 21:31:12 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: inactive -> scanning
Apr 26 21:31:13 nonguru wpa_supplicant[1553]: wlan0: SME: Trying to authenticate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:31:13 nonguru kernel: [  211.754873] wlan0: authenticate with 00:26:b8:51:b8:ea
Apr 26 21:31:13 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 21:31:13 nonguru kernel: [  211.767090] wlan0: send auth to 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:31:13 nonguru kernel: [  211.970275] wlan0: send auth to 00:26:b8:51:b8:ea (try 2/3)
Apr 26 21:31:14 nonguru kernel: [  212.174112] wlan0: send auth to 00:26:b8:51:b8:ea (try 3/3)
Apr 26 21:31:14 nonguru kernel: [  212.377919] wlan0: authentication with 00:26:b8:51:b8:ea timed out
Apr 26 21:31:14 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Apr 26 21:31:14 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 21:31:37 nonguru NetworkManager[1049]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Apr 26 21:31:37 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> failed (reason 'SSID not found') [50 120 53]
Apr 26 21:31:37 nonguru NetworkManager[1049]: <info> Marking connection 'wireless' invalid.
Apr 26 21:31:37 nonguru NetworkManager[1049]: <warn> Activation (wlan0) failed for connection 'wireless'
Apr 26 21:31:37 nonguru NetworkManager[1049]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Apr 26 21:31:37 nonguru NetworkManager[1049]: <info> (wlan0): deactivating device (reason 'none') [0]
Apr 26 21:31:37 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> disconnected
Apr 26 21:31:37 nonguru NetworkManager[1049]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) starting connection 'wireless'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): access point 'wireless' has security, but secrets are required.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless): connection 'wireless' has security, and secrets exist.  No new secrets needed.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: added 'ssid' value 'wireless'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: added 'scan_ssid' value '1'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: added 'auth_alg' value 'OPEN'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: added 'psk' value '<omitted>'
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> Config: set interface ap_scan to 1
Apr 26 21:32:26 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 21:32:27 nonguru wpa_supplicant[1553]: wlan0: SME: Trying to authenticate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:32:27 nonguru kernel: [  285.561366] wlan0: authenticate with 00:26:b8:51:b8:ea
Apr 26 21:32:27 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 21:32:27 nonguru kernel: [  285.573485] wlan0: send auth to 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:32:27 nonguru kernel: [  285.776834] wlan0: send auth to 00:26:b8:51:b8:ea (try 2/3)
Apr 26 21:32:27 nonguru wpa_supplicant[1553]: wlan0: Trying to associate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:32:27 nonguru kernel: [  285.980643] wlan0: send auth to 00:26:b8:51:b8:ea (try 3/3)
Apr 26 21:32:27 nonguru kernel: [  285.982623] wlan0: authenticated
Apr 26 21:32:27 nonguru kernel: [  285.984619] wlan0: associate with 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:32:27 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 21:32:28 nonguru kernel: [  286.188413] wlan0: associate with 00:26:b8:51:b8:ea (try 2/3)
Apr 26 21:32:28 nonguru kernel: [  286.392235] wlan0: associate with 00:26:b8:51:b8:ea (try 3/3)
Apr 26 21:32:28 nonguru kernel: [  286.596026] wlan0: association with 00:26:b8:51:b8:ea timed out
Apr 26 21:32:28 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associating -> disconnected
Apr 26 21:32:28 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Apr 26 21:32:29 nonguru wpa_supplicant[1553]: wlan0: SME: Trying to authenticate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:32:29 nonguru kernel: [  287.415768] wlan0: authenticate with 00:26:b8:51:b8:ea
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Apr 26 21:32:29 nonguru kernel: [  287.427600] wlan0: send auth to 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:32:29 nonguru wpa_supplicant[1553]: wlan0: Trying to associate with 00:26:b8:51:b8:ea (SSID='wireless' freq=2462 MHz)
Apr 26 21:32:29 nonguru kernel: [  287.465168] wlan0: authenticated
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: authenticating -> associating
Apr 26 21:32:29 nonguru kernel: [  287.467267] wlan0: associate with 00:26:b8:51:b8:ea (try 1/3)
Apr 26 21:32:29 nonguru wpa_supplicant[1553]: wlan0: Associated with 00:26:b8:51:b8:ea
Apr 26 21:32:29 nonguru kernel: [  287.473085] wlan0: RX AssocResp from 00:26:b8:51:b8:ea (capab=0x431 status=0 aid=6)
Apr 26 21:32:29 nonguru kernel: [  287.473139] wlan0: associated
Apr 26 21:32:29 nonguru kernel: [  287.473202] cfg80211: Calling CRDA for country: US
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associating -> associated
Apr 26 21:32:29 nonguru kernel: [  287.477115] cfg80211: Regulatory domain changed to country: US
Apr 26 21:32:29 nonguru kernel: [  287.477118] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Apr 26 21:32:29 nonguru kernel: [  287.477121] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
Apr 26 21:32:29 nonguru kernel: [  287.477124] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
Apr 26 21:32:29 nonguru kernel: [  287.477126] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:32:29 nonguru kernel: [  287.477128] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:32:29 nonguru kernel: [  287.477130] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Apr 26 21:32:29 nonguru kernel: [  287.477132] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Apr 26 21:32:29 nonguru wpa_supplicant[1553]: wlan0: WPA: Key negotiation completed with 00:26:b8:51:b8:ea [PTK=CCMP GTK=CCMP]
Apr 26 21:32:29 nonguru wpa_supplicant[1553]: wlan0: CTRL-EVENT-CONNECTED - Connection to 00:26:b8:51:b8:ea completed (reauth) [id=0 id_str=]
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'wireless'.
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> dhclient started with pid 2726
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Beginning IP6 addrconf.
Apr 26 21:32:29 nonguru avahi-daemon[1030]: Withdrawing address record for fe80::4e60:deff:fe5f:fd48 on wlan0.
Apr 26 21:32:29 nonguru avahi-daemon[1030]: Leaving mDNS multicast group on interface wlan0.IPv6 with address fe80::4e60:deff:fe5f:fd48.
Apr 26 21:32:29 nonguru avahi-daemon[1030]: Interface wlan0.IPv6 no longer relevant for mDNS.
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Apr 26 21:32:29 nonguru dhclient: Internet Systems Consortium DHCP Client 4.2.4
Apr 26 21:32:29 nonguru dhclient: Copyright 2004-2012 Internet Systems Consortium.
Apr 26 21:32:29 nonguru dhclient: All rights reserved.
Apr 26 21:32:29 nonguru dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 26 21:32:29 nonguru dhclient: 
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Apr 26 21:32:29 nonguru dhclient: Listening on LPF/wlan0/4c:60:de:5f:fd:48
Apr 26 21:32:29 nonguru dhclient: Sending on   LPF/wlan0/4c:60:de:5f:fd:48
Apr 26 21:32:29 nonguru dhclient: Sending on   Socket/fallback
Apr 26 21:32:29 nonguru dhclient: DHCPREQUEST of 192.168.1.5 on wlan0 to 255.255.255.255 port 67 (xid=0x77c1d02)
Apr 26 21:32:29 nonguru dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Apr 26 21:32:29 nonguru dhclient: bound to 192.168.1.5 -- renewal in 38784 seconds.
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   address 192.168.1.5
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   prefix 24 (255.255.255.0)
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   gateway 192.168.1.1
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   hostname 'nonguru'
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   nameserver '192.168.1.1'
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info>   domain name 'home'
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Apr 26 21:32:29 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Apr 26 21:32:29 nonguru avahi-daemon[1030]: Joining mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.5.
Apr 26 21:32:29 nonguru avahi-daemon[1030]: New relevant interface wlan0.IPv4 for mDNS.
Apr 26 21:32:29 nonguru avahi-daemon[1030]: Registering new address record for 192.168.1.5 on wlan0.IPv4.
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> (wlan0): device state change: ip-config -> secondaries (reason 'none') [70 90 0]
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> (wlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> Policy set 'wireless' (wlan0) as default for IPv4 routing and DNS.
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> DNS: starting dnsmasq...
Apr 26 21:32:30 nonguru NetworkManager[1049]: <warn> dnsmasq not available on the bus, can't update servers.
Apr 26 21:32:30 nonguru NetworkManager[1049]: <error> [1367037150.565192] [nm-dns-dnsmasq.c:402] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
Apr 26 21:32:30 nonguru NetworkManager[1049]: <warn> DNS: plugin dnsmasq update failed
Apr 26 21:32:30 nonguru NetworkManager[1049]: <info> Writing DNS information to /sbin/resolvconf
Apr 26 21:32:30 nonguru dnsmasq[2730]: started, version 2.65 cache disabled
Apr 26 21:32:30 nonguru dnsmasq[2730]: compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack
Apr 26 21:32:30 nonguru dnsmasq[2730]: DBus support enabled: connected to system bus
Apr 26 21:32:30 nonguru dnsmasq[2730]: warning: no upstream servers configured
Apr 26 21:32:30 nonguru avahi-daemon[1030]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::4e60:deff:fe5f:fd48.
Apr 26 21:32:30 nonguru avahi-daemon[1030]: New relevant interface wlan0.IPv6 for mDNS.
Apr 26 21:32:30 nonguru avahi-daemon[1030]: Registering new address record for fe80::4e60:deff:fe5f:fd48 on wlan0.*.
Apr 26 21:32:44 nonguru NetworkManager[1049]: <info> Activation (wlan0) successful, device activated.
Apr 26 21:32:44 nonguru dbus[929]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Apr 26 21:32:44 nonguru NetworkManager[1049]: <warn> dnsmasq appeared on DBus: :1.72
Apr 26 21:32:44 nonguru NetworkManager[1049]: <info> Writing DNS information to /sbin/resolvconf
Apr 26 21:32:44 nonguru dnsmasq[2730]: setting upstream servers from DBus
Apr 26 21:32:44 nonguru dnsmasq[2730]: using nameserver 192.168.1.1#53
Apr 26 21:32:44 nonguru dbus[929]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Apr 26 21:32:47 nonguru nm-dispatcher.action: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' took too long; killing it.
Apr 26 21:32:54 nonguru NetworkManager[1049]: <info> (wlan0): IP6 addrconf timed out or failed.
Apr 26 21:32:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Apr 26 21:32:54 nonguru NetworkManager[1049]: <warn> Dispatcher script timed out: Script '/etc/NetworkManager/dispatcher.d/01ifupdown' timed out.
Apr 26 21:32:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Apr 26 21:32:54 nonguru NetworkManager[1049]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.

```

---

### Post by praseodym on 2013-04-27
Try to change the encryption mode from "WPA+WPA2" to "WPA2"-only in you router interface.

---

### Post by nonguru on 2013-04-27
[COLOR=#000000][FONT=Verdana]It is currently set at WPA2 from the router, there is no option to do WPA+WPA2 other than from the Ubuntu settings which allows WPA+WPA2 Personal and Enterprise.[/FONT][/COLOR]

---

