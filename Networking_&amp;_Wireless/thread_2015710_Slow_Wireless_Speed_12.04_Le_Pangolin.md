---
title: "Slow Wireless Speed 12.04 Le Pangolin"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by Nick Burgundy on 2012-07-03
Hello all. So I've been on 12.04 long enough to know that something is no bueno. My wireless speed has been cut in half in the past month. I've tried everything to get it back to normal from unixmen solutions to trolling various threads. Nothing seems to work. I'm perpetually stuck at less than 8 mbps. I've even had the cable company out here twice to check my connection, and well they're not happy with me. Also wife's PC is windows, and she is right now at 20+ mbps. Please help..........

njb@njb-HP-EliteBook-8460p:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux njb-HP-EliteBook-8460p 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

njb@njb-HP-EliteBook-8460p:~$ lspci -nnj | grep -iA2 net
lspci: invalid option -- 'j'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv for very verbose)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>]            Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
njb@njb-HP-EliteBook-8460p:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 138a:003c Validity Sensors, Inc. VFS471 Fingerprint Reader
Bus 002 Device 003: ID 04f2:b230 Chicony Electronics Co., Ltd Integrated HP HD Webcam

njb@njb-HP-EliteBook-8460p:~$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:205  Noise level:172
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

njb@njb-HP-EliteBook-8460p:~$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

njb@njb-HP-EliteBook-8460p:~$ lsmod
Module                  Size  Used by
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_idt      60251  1 
tpm_infineon           17296  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
joydev                 17393  0 
ppdev                  12849  0 
parport_pc             32114  1 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
tpm_tis                18308  0 
hp_accel               25728  0 
lis3lv02d              19268  1 hp_accel
input_polldev          13648  1 lis3lv02d
lib80211_crypt_tkip    17275  0 
wmi                    18744  1 hp_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  414655  3 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wl                   2646601  0 
drm_kms_helper         45466  1 i915
snd                    62064  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   197692  4 i915,drm_kms_helper
uvcvideo               67203  0 
psmouse                72919  0 
soundcore              14635  1 snd
videodev               86588  1 uvcvideo
mac_hid                13077  0 
serio_raw              13027  0 
lib80211               14040  2 lib80211_crypt_tkip,wl
i2c_algo_bit           13199  1 i915
lp                     17455  0 
mei                    36570  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
parport                40930  3 ppdev,parport_pc,lp
video                  19068  1 i915
e1000e                140005  0 
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci

njb@njb-HP-EliteBook-8460p:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [NandJ] --------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        AC:81:12:6A:5F:62

  Capabilities:
    Speed:           58 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    NYOF5:           Infra, 00:26:62:8B:51:24, Freq 2437 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    Theresa:         Infra, 20:4E:7F:1B:B2:DF, Freq 2462 MHz, Rate 0 Mb/s, Strength 27 WPA WPA2
    JZWP1:           Infra, 00:26:62:EA:72:F8, Freq 2462 MHz, Rate 54 Mb/s, Strength 90 WEP
    3IVY1:           Infra, 00:26:B8:32:75:00, Freq 2412 MHz, Rate 54 Mb/s, Strength 50 WEP
    09FX03036238:    Infra, 00:23:97:29:0A:CC, Freq 2452 MHz, Rate 54 Mb/s, Strength 44 WEP
    Honey:           Infra, 00:22:6B:75:CF:97, Freq 2412 MHz, Rate 0 Mb/s, Strength 37 WEP
    *NandJ:          Infra, 30:46:9A:0B:59:00, Freq 2417 MHz, Rate 54 Mb/s, Strength 100 WPA2
    WWVE5:           Infra, 00:26:62:8A:BE:15, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WEP

  IPv4 Settings:
    Address:         192.168.1.3
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        64:31:50:A4:F8:C2

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by Nick Burgundy on 2012-07-03
SORRY GUYS!!!!

After another hour in the forum I found my solution. Wireless speed has tripled.  Please disregard my thread.

[http://ubuntuforums.org/showthread.php?t=1953710&highlight=wireless+turn+off+power+management](http://ubuntuforums.org/showthread.php?t=1953710&highlight=wireless+turn+off+power+management)

---

