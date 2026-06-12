---
title: "Wireless issues"
date: 2011-10-25
forum: Networking &amp; Wireless
---

### Post by Fernus on 2011-10-25
Hello you all,

I am new to Linux and so I'm needing a little helping solving this.

I was using 11.04 until two weeks ago and, apart from some graphic card issus, everything was working fine. Then I installed Oneiric 11.10, everything still the same until 5 days ago that, after an update, my wireless connection is having a strange behaviour:
- The nm-applet has the "Enable Networking" and "Enable wireless" grayed out
- I can't disconnect from my current network or connect to another through the applet. Every time I kill the applet and start it again from the command line I get the following error when trying to connect to another network:
> (nm-applet:8124): WARNING **: Failed to add/activate connection: (32) Not authorized to control networking.


- Result of 'lshw -C Network'
> 
 *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 01
       serial: 20:7c:8f:00:20:10
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.0.0-12-generic firmware=N/A ip=192.168.1.10 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f0300000-f030ffff


Thanks in advance for your help.

Cheers,
F

---

### Post by praseodym on 2011-10-25
Hi,

deactivate the hardware encryption for the driver ath9k (this is one line, c/p it):

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
and reboot.

---

### Post by Fernus on 2011-10-26
Hello,

Thanks for your help. But unfortunately it didn't do anything. :(

---

### Post by praseodym on 2011-10-26
Start the tool as root:

```
gksu nm-connection-editor
```

---

### Post by Fernus on 2011-10-26
Thank you for your help. Now I can add a new connection which I couldn't before.

But the problem still stays the same. :(

---

### Post by praseodym on 2011-10-26
Check:

```
iwconfig
lsmod
sudo iwlist scan
rfkill list
lspci -nnk | grep -iA2 net
dmesg | grep ath
```

---

### Post by Fernus on 2011-10-26
Hi again. Here are the outputs. Thanks again.

iwconfig
```
wlan0     IEEE 802.11bgn  ESSID:"FDA-router"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 4C:54:99:7B:E4:64   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=55/70  Signal level=-55 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:1269   Missed beacon:0

```


lsmod
```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  3 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_seq_midi           13324  0 
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
uvcvideo               72711  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
arc4                   12529  2 
videodev               93004  1 uvcvideo
ath9k                 127538  0 
mac80211              310872  1 ath9k
fglrx                2929009  256 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
v4l2_compat_ioctl32    17083  1 videodev
soundcore              12680  1 snd
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath
psmouse                73882  0 
mei                    41480  0 
serio_raw              13166  0 
joydev                 17693  0 
acer_wmi               23948  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
sparse_keymap          13890  1 acer_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
vesafb                 13809  1 
usbhid                 47198  0 
hid                    95463  1 usbhid
video                  19412  0 
wmi                    19256  1 acer_wmi
ahci                   26002  3 
libahci                26861  1 ahci
atl1c                  41643  0
```


sudo iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 4C:54:99:7B:E4:64
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/70  Signal level=-55 dBm  
                    Encryption key:on
                    ESSID:"FDA-router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000017b121f30b
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000A4644412D726F75746572
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706505420010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD140050F204104A000110104400010210080002018C

```


rfkill list
```
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


lspci -nnk | grep -iA2 net
```
03:00.0 Ethernet controller [0200]: Atheros Communications AR8151 v1.0 Gigabit Ethernet [1969:1073] (rev c0)
	Subsystem: Acer Incorporated [ALI] Device [1025:0364]
	Kernel driver in use: atl1c
--
05:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Quanta Microsystems, Inc EM306 802.11bgn (2x2:2) Wireless Half-size Mini PCIe Card [AR9283] [1a32:0306]
	Kernel driver in use: ath9k

```


dmesg | grep ath
```
[   19.941250] ath9k 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.941261] ath9k 0000:05:00.0: setting latency timer to 64
[   20.372301] ath: EEPROM regdomain: 0x65
[   20.372303] ath: EEPROM indicates we should expect a direct regpair map
[   20.372307] ath: Country alpha2 being used: 00
[   20.372308] ath: Regpair used: 0x65
[   20.637282] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   20.637865] Registered led device: ath9k-phy0
[   38.341573] type=1400 audit(1319630611.055:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1097 comm="apparmor_parser"
[   38.342144] type=1400 audit(1319630611.055:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1097 comm="apparmor_parser"

```

---

### Post by praseodym on 2011-10-27
What computer is that? An Acer notebook? If _not_, unload the module acer_wmi

```
sudo rmmod acer_wmi
```
I also recommend pure WPA2-AES encryption instead of mixed WPA/WPA2.

---

