---
title: "Problems using wicd"
date: 2011-09-11
forum: Networking &amp; Wireless
---

### Post by fkrogh on 2011-09-11
I am trying to use a wireless access point using WEP 64 bit security.  Since I wasn't getting the usual tools to work, I tried wicd as suggested in another thread here.  This is on a laptop that dual boots to XP which works both wirelessly and with a wired connection.  Under Ubuntu, if I use the usual /etc/init.d/networking start, the wired network works, but I have not found a way to get the wireless to work.  If I stop this and start wicd, then wireless doesn't even come close to working.  The wired connection can ping my gateway (192.168.0.3), but can not ping even a static IP address in the outside world.  Here is what I'm working with.

manager-settings.conf:
[Settings]
wireless_interface = eth1
prefer_wired = False
flush_tool = 0
use_global_dns = False
global_dns_dom = None
always_show_wired_interface = False
global_dns_1 = None
global_dns_2 = None
global_dns_3 = None
backend = external
should_verify_ap = 1
link_detect_tool = 0
dhcp_client = 0
sudo_app = 0
wired_connect_mode = 1
debug_mode = False
wired_interface = eth0
signal_display_type = 0
global_search_dom = None
auto_reconnect = True
wpa_driver = wext

wired-settings.conf:
[wired-default]
afterscript = None
dhcphostname = hplt
dns3 = None
postdisconnectscript = None
search_domain = None
use_static_ip = True
use_static_dns = True
dns2 = 8.8.4.4
dns_domain = mathalacarte
gateway = 192.168.0.3
broadcast = 192.168.0.255
default = True
netmask = 255.255.255.0
ip = 192.168.0.4
beforescript = None
predisconnectscript = None
dns1 = 8.8.8.8

wireless-setting.conf:
ESSID = off/any
Mode = Managed
encryption_method = wep-hex
key = **********  (hidden)
automatic = TRUE
uuse_static_dns = True
uuse_global_dns = False
dns1 = 8.8.8.8
dns2 = 8.8.4.4

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

It isn't critical that I get the wired connection to work, I'm just curious as to why it doesn't.  But I'd really like to get the wireless working.  Any suggestions most welcome.  I'd be happy to supply additional information if it might prove useful.  Thanks,
  Fred

---

### Post by praseodym on 2011-09-11
What hardware is in use?

```
lspci -nnk | grep -iA2 net
lsmod
```
please

---

### Post by fkrogh on 2011-09-11
$ lspci
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:135b]
	Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: e100
m@hplt:/etc/wicd$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:135b]
	Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: e100
m@hplt:/etc/wicd$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:135b]
	Kernel driver in use: iwl3945
--
08:08.0 Ethernet controller [0200]: Intel Corporation PRO/100 VE Network Connection [8086:1092] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:30a5]
	Kernel driver in use: e100


$lsmod
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
nvidia               9377626  31 
snd_hda_codec_conexant    30003  1 
iptable_nat             3752  0 
nf_nat                 16289  1 iptable_nat
nf_conntrack_ipv4      10783  3 iptable_nat,nf_nat
nf_conntrack           63258  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
iptable_mangle          1371  0 
iptable_filter          1302  0 
ip_tables              10460  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               15921  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
arc4                    1165  2 
iwl3945                85550  0 
iwlcore               127415  1 iwl3945
mac80211              231959  2 iwl3945,iwlcore
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3766  0 
sbp2                   19332  0 
hp_wmi                  5223  0 
cfg80211              144694  3 iwl3945,iwlcore,mac80211
tifm_core               6089  1 tifm_7xx1
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee1394               81069  1 sbp2
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
video                  18712  0 
intel_agp              26566  0 
soundcore                880  1 snd
output                  1883  1 video
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6633  0 
firewire_ohci          21234  0 
sdhci                  15922  1 sdhci_pci
e100                   30356  0 
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 e100
Module                  Size  Used by
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
nvidia               9377626  31 
snd_hda_codec_conexant    30003  1 
iptable_nat             3752  0 
nf_nat                 16289  1 iptable_nat
nf_conntrack_ipv4      10783  3 iptable_nat,nf_nat
nf_conntrack           63258  3 iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1117  1 nf_conntrack_ipv4
iptable_mangle          1371  0 
iptable_filter          1302  0 
ip_tables              10460  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               15921  4 iptable_nat,iptable_mangle,iptable_filter,ip_tables
arc4                    1165  2 
iwl3945                85550  0 
iwlcore               127415  1 iwl3945
mac80211              231959  2 iwl3945,iwlcore
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
tifm_7xx1               3766  0 
sbp2                   19332  0 
hp_wmi                  5223  0 
cfg80211              144694  3 iwl3945,iwlcore,mac80211
tifm_core               6089  1 tifm_7xx1
snd                    49038  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee1394               81069  1 sbp2
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket
video                  18712  0 
intel_agp              26566  0 
soundcore                880  1 snd
output                  1883  1 video
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  2 nvidia,intel_agp
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usbhid                 36882  0 
hid                    67742  1 usbhid
sdhci_pci               6633  0 
firewire_ohci          21234  0 
sdhci                  15922  1 sdhci_pci
e100                   30356  0 
firewire_core          46643  1 firewire_ohci
led_class               2633  1 sdhci
crc_itu_t               1383  1 firewire_core
mii                     4425  1 e100

I hope this helps, and thanks for looking at this.  In the meantime I've given up on WEP and decided to use WPA2.  According to the configuration screen of my router (ASUS 520GC which I think is a linksys type).  I have the Authentication method set to WPA2-Personal, which only allows AES for the WPA encryption.  WEP encryption is set to None.

All of this works in windows, but I can't even ping the wireless access point (192.168.1.1) using Ubuntu.  In my network connections, I have Mode: Infrastructure, SSID has the name of the network, BSSID is blank, and MAC address is given, and the MUT is automatic.

IPv4 is set for Automatic DHCP, only IPv4 is used.  The wireless Security is set to WPA & WPA2 Personal, and the password is set correctly.  So there it is.

If there is someway to just get all the needed information into /etc/network/interfaces that would be a godsend.  However see nothing in the man page for interfaces that would allow for input of a key.  Many Thanks, for looking at this.
Fred

---

### Post by fkrogh on 2011-09-12
My problem has been resolved by using wpa_supplicant, see [https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

