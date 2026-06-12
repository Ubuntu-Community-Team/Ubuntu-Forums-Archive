---
title: "Intel 3945ABG Wireless will not connect to WEP network"
date: 2010-05-21
forum: Networking &amp; Wireless
---

### Post by Maethoriel on 2010-05-21
Hello everyone,

I have an IBM Thinkpad T60, running Ubuntu 10.04 (Lucid) with a dual boot of Windows XP.  I am having trouble getting it to connect to my home wireless network, which uses WEP.  It connected fine at my university when I first installed Lucid, but has not connected at home.  I can see the network in the panel applet, with a good signal strength, but when I try to connect it repeatedly asks me for my key and never actually connects.  I had this problem shortly before I installed Lucid, though it was working for a long time previously.  I'm not sure what update caused it to stop working because I was at my university at the time, and it works fine there even now, so I didn't realize it right away.

I doubt this is a hardware issue because I can connect to the same network when I boot into Windows.  I have seen posts about similar problems on the forums, but couldn't find any solutions that helped me.

Below is the information the wireless help guide said to post.  Thank you so much for your help!

Machine Brand and Model: 
IBM Thinkpad T60

Wireless Brand, Model, and Wireless Chipset:
lspci -nn | grep 'Wireless'
```
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
```

Check Interface:
ifconfig wlan0
```
wlan0     Link encap:Ethernet  HWaddr 00:13:02:38:fb:0e  
          inet6 addr: fe80::213:2ff:fe38:fb0e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:339 (339.0 B)  TX bytes:579 (579.0 B)
```
iwconfig wlan0
```
wlan0     IEEE 802.11abg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

Check for Modules:
The suggested lsmod | grep "wlan_module_name" didn't find anything... here are the results of just running lsmod.  Sorry it's so long, but I'm not sure what's relevant and what's not.
```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
parport_pc             25962  0 
snd_hda_codec_analog    58566  1 
snd_hda_intel          21877  4 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
fbcon                  35102  72 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
snd_seq_oss            26726  0 
arc4                    1153  2 
vgastate                8961  1 vga16fb
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
iwl3945                68727  0 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
pcmcia                 33024  0 
joydev                  8708  0 
iwlcore               105922  1 iwl3945
nsc_ircc               18220  0 
i915                  282354  4 
snd_timer              19098  2 snd_pcm,snd_seq
thinkpad_acpi          68083  0 
mac80211              204922  2 iwl3945,iwlcore
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
uinput                  6312  0 
yenta_socket           20408  1 
led_class               2864  3 iwl3945,iwlcore,thinkpad_acpi
irda                  186556  1 nsc_ircc
snd                    54148  21 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,thinkpad_acpi,snd_seq_device
psmouse                63245  0 
rsrc_nonstatic         10015  1 yenta_socket
soundcore               6620  1 snd
drm                   162471  5 i915,drm_kms_helper
intel_agp              24177  2 i915
i2c_algo_bit            5028  1 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
agpgart                31724  2 drm,intel_agp
crc_ccitt               1339  1 irda
lp                      7028  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
nvram                   6171  1 thinkpad_acpi
serio_raw               3978  0 
output                  1871  1 video
cfg80211              126485  3 iwl3945,iwlcore,mac80211
parport                32635  3 ppdev,parport_pc,lp
e1000e                119856  0 
ahci                   32008  4
```

Kernel Boot Messages:
dmesg | grep wlan0
```
[43480.171819] wlan0: authenticate with AP 00:1e:e5:f3:f9:34 (try 1)
[43491.926370] wlan0: direct probe to AP 00:1e:e5:f3:f9:34 (try 1)
[43491.928341] wlan0: direct probe responded
[43491.928349] wlan0: authenticate with AP 00:1e:e5:f3:f9:34 (try 1)
[43514.606977] wlan0: deauthenticating from 00:1e:e5:f3:f9:34 by local choice (reason=3)
[43514.642576] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 1)
[43514.840184] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 2)
[43515.040158] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 3)
[43515.043117] wlan0: direct probe responded
[43515.043125] wlan0: authenticate with AP 00:1e:2a:dd:f8:51 (try 1)
[43515.055558] wlan0: authenticated
[43515.055601] wlan0: associate with AP 00:1e:2a:dd:f8:51 (try 1)
[43515.080455] wlan0: RX AssocResp from 00:1e:2a:dd:f8:51 (capab=0x431 status=0 aid=2)
[43515.080463] wlan0: associated
[43518.115722] wlan0: deauthenticated from 00:1e:2a:dd:f8:51 (Reason: 2)
[43519.888228] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 1)
[43520.088181] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 2)
[43520.288161] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 (try 3)
[43520.488104] wlan0: direct probe to AP 00:1e:2a:dd:f8:51 timed out
[45552.568282] wlan0: direct probe to AP 00:1e:e5:f3:f9:34 (try 1)
[45552.570315] wlan0: direct probe responded
[45552.570322] wlan0: authenticate with AP 00:1e:e5:f3:f9:34 (try 1)
[45564.239949] wlan0: direct probe to AP 00:1e:e5:f3:f9:34 (try 1)
[45564.241907] wlan0: direct probe responded
[45564.241915] wlan0: authenticate with AP 00:1e:e5:f3:f9:34 (try 1)
[45575.992372] wlan0: direct probe to AP 00:1e:e5:f3:f9:34 (try 1)
[45575.994332] wlan0: direct probe responded
```

Network Configuration:
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       serial: 00:15:58:2a:9e:05
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=0.5-1 ip=192.168.1.100 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:ee000000-ee01ffff ioport:2000(size=32)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:38:fb:0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:edf00000-edf00fff

```

Scan for Networks:
"linksys" is the one I want to connect to.  "PqyEaM3e7nPWN" is, I believe, my neighbor's network.
iwlist scan
```
wlan0     Scan completed :
          Cell 01 - Address: 00:1E:E5:F3:F9:34
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000008d9b4af8f
                    Extra: Last beacon: 1744ms ago
                    IE: Unknown: 00076C696E6B737973
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD06001018020004
          Cell 02 - Address: 00:1E:2A:DD:F8:51
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"PqyEaM3e7nPWN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000005a446cbd3ad
                    Extra: Last beacon: 3360ms ago
                    IE: Unknown: 000D50717945614D3365376E50574E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706555320010B1B
                    IE: Unknown: 200100
                    IE: Unknown: 2A0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010035FF7F

```

Ubuntu Version: Ubuntu 10.04 LTS

Kernel/architecture: 2.6.32-22-generic i686

Restarting the Network:
sudo /etc/init.d/networking restart
```
 * Reconfiguring network interfaces...                                                                  [ OK ] 

```

---

### Post by klemes on 2010-05-21
Have you tried to connect via wpa_supplicant with the command line?

if not then make a suitable /etc/wpa_supplicant.conf first:

```
network={
     ssid="linksys"
     scan_ssid=1
     key_mgmt=NONE
     wep_key0=XXXXXXXXX
}
```

And then type this to test the connection:

```
wpa_supplicant -c/etc/wpa_supplicant.conf -iwlan0
```

:popcorn:

Add sudo accordingly and/or the -d switch at the end of the comand for debugging purposes.

---

### Post by Maethoriel on 2010-05-22
Hello klemes,

Thanks for the help!  Sorry for the delay replying.

I made the conf file as you suggested, substituting my WEP key in where you put the X's (I figured that's where it was supposed to go?)  It still doesn't seem to be connecting, though I let it run for awhile.  Here are the first 250 lines it outputted with the -d switch.  It seems to be repeating, but I have the whole thing saved and can attach it if you need that.

```
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Priority group 0
   id=0 ssid='linksys'
Interface wlan0 set UP - waiting a second for the driver to complete initialization
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf flags 0x0
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:13:02:38:fb:0e
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
RSN: flushing PMKID list in the driver
Setting scan request: 0 sec 100000 usec
WPS: UUID based on MAC address - hexdump(len=16): 57 7c 51 01 9b 0d 57 a2 aa 80 64 8b 71 f9 3d fd
WPS: Build Beacon and Probe Response IEs
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Version
WPS:  * Wi-Fi Protected Setup State (0)
WPS:  * Response Type (2)
WPS:  * UUID-E
WPS:  * Manufacturer
WPS:  * Model Name
WPS:  * Model Number
WPS:  * Serial Number
WPS:  * Primary Device Type
WPS:  * Device Name
WPS:  * Config Methods (0)
WPS:  * RF Bands (3)
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 297 bytes of scan results (1 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:1e:e5:f3:f9:34 ssid='linksys'
Trying to associate with 00:1e:e5:f3:f9:34 (SSID='linksys' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=13
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 297 bytes of scan results (1 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:1e:e5:f3:f9:34 ssid='linksys'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 01 04
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1e:e5:f3:f9:34
Association info event
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 01 04
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1e:e5:f3:f9:34
Associated with 00:1e:e5:f3:f9:34
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1e:e5:f3:f9:34 completed (auth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1e:e5:f3:f9:34 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
EAPOL: External notification - portValid=0
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 295 bytes of scan results (1 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:1e:e5:f3:f9:34 ssid='linksys'
Trying to associate with 00:1e:e5:f3:f9:34 (SSID='linksys' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=1 key_idx=0 set_tx=1 seq_len=0 key_len=13
wpa_driver_wext_set_drop_unencrypted
State: DISCONNECTED -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
wpa_driver_wext_set_psk
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=ForceAuthorized
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b06 len=8
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b04 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b19 len=8
Received 295 bytes of scan results (1 BSSes)
New scan results available
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1e:e5:f3:f9:34 ssid='linksys' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:1e:e5:f3:f9:34 ssid='linksys'
Already associated with the selected AP.
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8c08 len=32
AssocResp IE wireless event - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 01 04
RTM_NEWLINK: operstate=0 ifi_flags=0x11003 ([UP][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:1e:e5:f3:f9:34
Association info event
resp_ies - hexdump(len=24): 01 08 82 84 8b 96 24 30 48 6c 32 04 0c 12 18 60 dd 06 00 10 18 02 01 04
State: ASSOCIATING -> ASSOCIATED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
Associated to a new BSS: BSSID=00:1e:e5:f3:f9:34
Associated with 00:1e:e5:f3:f9:34
WPA: Association event - clear replay counter
WPA: Clear old PTK
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
EAPOL: External notification - portEnabled=1
EAPOL: SUPP_PAE entering state S_FORCE_AUTH
EAPOL: SUPP_BE entering state IDLE
Cancelling authentication timeout
Removed BSSID 00:1e:e5:f3:f9:34 from blacklist
State: ASSOCIATED -> COMPLETED
CTRL-EVENT-CONNECTED - Connection to 00:1e:e5:f3:f9:34 completed (reauth) [id=0 id_str=]
wpa_driver_wext_set_operstate: operstate 0->1 (UP)
WEXT: Operstate: linkmode=-1, operstate=6
Cancelling scan request
RTM_NEWLINK: operstate=1 ifi_flags=0x11043 ([UP][RUNNING][LOWER_UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x11003 ([UP][LOWER_UP])
WEXT: Operstate: linkmode=-1, operstate=6
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1043 ([UP][RUNNING])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK: operstate=1 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b15 len=20
Wireless event: new AP: 00:00:00:00:00:00
Setting scan request: 0 sec 100000 usec
Added BSSID 00:1e:e5:f3:f9:34 into blacklist
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
State: COMPLETED -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 1->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: SUPP_BE entering state INITIALIZE
```

---

### Post by klemes on 2010-05-22
Not too much helpful the debug output I am afraid.At least I can't make much out of it.It seems it gets connected initially and then suddenly disconnects.I thought that it would well may be some of the quirkiness that network manager is well known of but that test seem to rule out that possibility since you are still unable to connect.However I noticed from the output of your ifconfig command that you don't get assigned an ipv4 IP at all but you do get an ipv6 IP.
Could you try to set manually the IP ,netmask and gateway in the network-manager-applet properties of your wireless connection and see if it connects this way?

---

### Post by Maethoriel on 2010-05-23
Thanks again for your help.  I just tried setting it up with a specified IP address, where the router was configured to assign that IP to the MAC address for my wireless card.  Unfortunately, it still didn't work in Linux, though it worked fine in Windows.

I've also been trying to get ndiswrapper set up, in case maybe it's some problem with the driver.  I'm running into some trouble, though, and that's not working either.  (I found the driver, installed it, added ndiswrapper to load automatically, and blacklisted the other driver, but I'm getting "unknown symbol" errors.)  Since I'm going to be back on the university network for most of this week, I'm planning to undo those changes because it had been working fine at school.  I'll give it another try when I'm home again, which might not be until the weekend.

---

### Post by Smokabowl on 2010-06-14
Having the exact same troubles bro. I'm using iwl3945 in the meantime. Until I can figure out ndisgtk.

---

