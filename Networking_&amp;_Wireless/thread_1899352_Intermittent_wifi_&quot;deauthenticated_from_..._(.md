---
title: "Intermittent wifi &quot;deauthenticated from ... (Reason: 6)&quot; on Oneiric w/ rtl8192se"
date: 2011-12-23
forum: Networking &amp; Wireless
---

### Post by jglick on 2011-12-23
On an eee-pc 1001pxd using the rtl8192se driver on a 3.0.0 kernel (Oneiric), I sometimes have problems making a wifi connection (to a D-Link DI-524). The network manager prompts for a password (which is stored in the user keyring) and tries again to connect. Sometimes this repeats numerous times, and then may finally succeed. But often the connection is made on the first attempt with no fuss. This is all within a few feet of the AP so the signal strength is fine, and another nearby laptop may be showing an interrupted connection. Disabling and reenabling wifi hardware, or rebooting, does not consistently help.

The kernel log shows blocks like this (omitting the hex for the AP address):

wlan0: authenticate with ... (try 1)
wlan0: authenticated
wlan0: associate with ... (try 1)
wlan0: deauthenticated from ... (Reason: 6)

When the connection finally succeeds:

wlan0: authenticate with ... (try 1)
wlan0: authenticated
wlan0: associate with ... (try 1)
wlan0: RX AssocResp from ... (capab=0x431 status=0 aid=2)
wlan0: associated

I have seen older posts (from 2.x kernel users) implying that this (reason 6 specifically) is a problem with the driver, and responses saying that using compat-wireless-drivers fixes the issue; indeed on a prior Ubuntu release I found that using the 3.x experimental drivers was necessary to avoid wifi dropouts. But Oneiric is already using the 3.0 kernel; do I need to be using an even newer driver, or setting some configuration option?

---

### Post by praseodym on 2011-12-23
Hi,

try pure WPA2-AES encryption. If its not working please show:

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
dmesg | egrep 'rtl8|r8|country'
```

---

### Post by jglick on 2012-05-14
# lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: ASUSTeK Computer Inc. Device [1043:8468]
	Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
	Subsystem: AzureWave Device [1a3b:1107]
	Kernel driver in use: rtl8192se
# lsmod
Module                  Size  Used by
dm_crypt               22528  0 
arc4                   12473  2 
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
rfcomm                 38139  0 
bnep                   17830  2 
snd_hda_codec_realtek   174055  1 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
rtl8192se              94189  0 
snd_seq_midi_event     14475  1 snd_seq_midi
rtlwifi                95804  1 rtl8192se
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
mac80211              436455  2 rtl8192se,rtlwifi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                87213  0 
serio_raw              13027  0 
binfmt_misc            17292  1 
cfg80211              178679  2 rtlwifi,mac80211
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i915                  414568  3 
atl1c                  36718  0 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
wmi                    18744  1 asus_wmi
# iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"REDACTED"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:16:C3:16   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

eth0      no wireless extensions.

# iwlist scan
lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:16:C3:16
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:"REDACTED"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000e55d0d1d8
                    Extra: Last beacon: 428ms ago
                    IE: Unknown: 00066F626C617374
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - <...other networks...>

eth0      Interface doesn't support scanning.

# dmesg | egrep 'rt18|r8|country'
[   19.651681] cfg80211: Calling CRDA for country: EC
[   19.793642] cfg80211: Regulatory domain changed to country: EC

---

### Post by praseodym on 2012-05-14
Is "EC" your country code?

Change the enctyption mode to pure WPA2-AES (CCMP) if possible, and search for a free, fixed channel, see here
[http://en.wikipedia.org/wiki/List_of_WLAN_channels#2.4.C2.A0GHz_.28802.11b.2Fg.2Fn.29](http://en.wikipedia.org/wiki/List_of_WLAN_channels#2.4.C2.A0GHz_.28802.11b.2Fg.2Fn.29).

---

### Post by jglick on 2012-05-14
No, I am in the US. The machine was purchased in the US as well.

To reiterate, WiFi is working fine at the moment on channel 6; the issue was problems getting a connection on the first few tries. Still too early to say whether the problem persists in 12.04 "Precise".

By "pure WPA2" I suppose you are referring to router configuration. I will set that and see if it helps. Thank you for your tips.

---

### Post by jglick on 2012-05-18
The problem does persist, intermittently, in Precise and with the router configured to use just WPA2. Possibly related to problems mentioned in thread ["12.04 eee-pc wifi: sudden RTL8192SE firmware errors"]("http://ubuntuforums.org/showthread.php?t=1980049").

---

### Post by praseodym on 2012-05-18
Change the country code via:

> sudo apt-get install iw
iw reg get
sudo iw reg set US
iw reg get

---

### Post by jglick on 2012-05-31
Interestingly, I sometimes get a broadly similar problem from a different laptop connecting to the same router, also running 12.04 but using iwlwifi:

03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection [8086:4237]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1211]
	Kernel driver in use: iwlwifi

Here again I am repeatedly prompted for a password (stored in keyring so suffices to hit Enter each time), and the connection is made eventually, whereas on other occasions the connection is made immediately with no fuss. In the kernel log, the following block is repeated dozens of times:

NetworkManager[1065]: <info> (wlan0): supplicant interface state: disconnected -> scanning
wpa_supplicant[1226]: Trying to authenticate with <macaddr> (SSID='<myssid>' freq=2437 MHz)
wpa_supplicant[1226]: Trying to associate with <macaddr> (SSID='<myssid>' freq=2437 MHz)
kernel: [349573.948095] wlan0: authenticate with <macaddr> (try 1)
kernel: [349573.951794] wlan0: authenticated
NetworkManager[1065]: <info> (wlan0): supplicant interface state: scanning -> associating
kernel: [349573.952927] wlan0: associate with <macaddr> (try 1)
kernel: [349573.955284] wlan0: RX AssocResp from <macaddr> (capab=0x431 status=43 aid=0)
kernel: [349573.955293] wlan0: <macaddr> denied association (code=43)
wpa_supplicant[1226]: CTRL-EVENT-DISCONNECTED bssid=00:00:00:00:00:00 reason=3
kernel: [349573.957192] wlan0: deauthenticating from <macaddr> by local choice (reason=3)
NetworkManager[1065]: <info> (wlan0): supplicant interface state: associating -> disconnected

Finally it works:

NetworkManager[1065]: <info> (wlan0): supplicant interface state: disconnected -> scanning
wpa_supplicant[1226]: Trying to authenticate with <macaddr> (SSID='<myssid>' freq=2437 MHz)
kernel: [349577.259599] wlan0: authenticate with <macaddr> (try 1)
wpa_supplicant[1226]: Trying to associate with <macaddr> (SSID='<myssid>' freq=2437 MHz)
kernel: [349577.262240] wlan0: authenticated
NetworkManager[1065]: <info> (wlan0): supplicant interface state: scanning -> associating
kernel: [349577.264228] wlan0: associate with <macaddr> (try 1)
kernel: [349577.266626] wlan0: RX AssocResp from <macaddr> (capab=0x431 status=0 aid=1)
kernel: [349577.266634] wlan0: associated
kernel: [349577.271337] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
wpa_supplicant[1226]: Associated with <macaddr>
NetworkManager[1065]: <info> (wlan0): supplicant interface state: associating -> associated
NetworkManager[1065]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
wpa_supplicant[1226]: WPA: Key negotiation completed with <macaddr> [PTK=CCMP GTK=CCMP]
wpa_supplicant[1226]: CTRL-EVENT-CONNECTED - Connection to <macaddr> completed (auth) [id=0 id_str=]
NetworkManager[1065]: <info> (wlan0): supplicant interface state: 4-way handshake -> completed
NetworkManager[1065]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '<myssid>'.
NetworkManager[1065]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager[1065]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager[1065]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
NetworkManager[1065]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
NetworkManager[1065]: <info> dhclient started with pid 6115
NetworkManager[1065]: <info> Activation (wlan0) Beginning IP6 addrconf.
dhclient: .....

and then the link is fine.

---

### Post by praseodym on 2012-06-01
Router firmware is up-to-date?

---

### Post by jglick on 2012-06-04
Yes, the firmware is up to date. The router is rather old so it is possible it has a hardware problem, though that would not explain why connecting is easier under Windows. I will try a new router when I get a chance.

---

