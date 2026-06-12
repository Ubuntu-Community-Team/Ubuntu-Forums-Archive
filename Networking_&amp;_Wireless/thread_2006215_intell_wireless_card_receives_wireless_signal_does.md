---
title: "intell wireless card receives wireless signal doesn't connect"
date: 2012-06-18
forum: Networking &amp; Wireless
---

### Post by jaredanderson on 2012-06-18
So here is the dl. My wireless card is a Intel Centrino Wireless-N + WiMAX 6150. the wireless card receives a wireless signal from my router but is un-able to connect to the internet. so I searched for drivers and I was in luck turns out that there are linux drivers for intel cards I download the latest compat-wireless file here [http://linuxwireless.org/en/users/Download/stable/](http://linuxwireless.org/en/users/Download/stable/) This page also includes directions on how to install. followed exactly as said seemed to go off without a hitch yet I still have the same problem. any suggestions. Also because I know you want me to say it I am newbie.

---

### Post by wildmanne39 on 2012-06-18
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

### Post by jaredanderson on 2012-06-18
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux jared-Lenovo-V570 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0886] (rev 67)
	Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1315]
	Kernel driver in use: iwlwifi
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Lenovo Device [17aa:3975]
	Kernel driver in use: r8169
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d7 Intel Corp. 
Bus 001 Device 004: ID 5986:0364 Acer, Inc 
Bus 002 Device 003: ID 1c7a:0603 LighTuning Technology Inc. 
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"1111 linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1D:7E:25:7F:4B   
          Bit Rate=1 Mb/s   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:16  Invalid misc:456   Missed beacon:0

eth0      no wireless extensions.

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Module                  Size  Used by
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
rfcomm                 46619  0 
bnep                   18139  2 
parport_pc             32866  0 
ppdev                  17113  0 
bluetooth             204578  10 rfcomm,bnep
joydev                 17693  0 
arc4                   12529  2 
iwlwifi               381775  0 
mac80211              543992  1 iwlwifi
cfg80211              210401  2 iwlwifi,mac80211
compat                 13728  6 rfcomm,bnep,bluetooth,iwlwifi,mac80211,cfg80211
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
i915                  468745  3 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rts5139               351143  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
acer_wmi               28418  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
wmi                    19256  1 acer_wmi
v4l2_compat_ioctl32    17128  1 videodev
psmouse                87692  0 
serio_raw              13211  0 
ideapad_laptop         18234  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
video                  19596  1 i915
mac_hid                13253  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
r8169                  62099  0 

```

---

### Post by wildmanne39 on 2012-06-18
Hi, please post the output of:
```
nm-tool
sudo iwlist scan
iwlist chan
cat /var/lib/NetworkManager/NetworkManager.state
ndiswrapper -l
lsmod | grep iwl
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by jaredanderson on 2012-06-18
```
State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:60:76:76

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.109
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             97.64.168.12
    DNS:             97.64.183.165


- Device: wlan0  [1111 linksys] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             connected
  Default:           no
  HW Address:        40:25:C2:32:77:14

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    PS3-5575119:     Infra, 00:23:4D:83:94:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA
    DEBBY-PC:        Infra, 58:6D:8F:0B:D4:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
    STEWARTHOME:     Infra, 50:67:F0:F0:89:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    JLMS:            Infra, 00:24:93:5D:30:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Belkin.318D:     Infra, 94:44:52:17:C1:8D, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
    SW1IA24:         Infra, 00:19:70:38:19:B6, Freq 2442 MHz, Rate 11 Mb/s, Strength 24
    *1111 linksys:   Infra, 00:1D:7E:25:7F:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA
    home:            Infra, 20:4E:7F:25:68:12, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
    NETGEAR-Guest:   Infra, 22:4E:7F:25:68:13, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             97.64.168.12
    DNS:             97.64.183.165
jared@jared-Lenovo-V570:~$ State: connected (global)
bash: syntax error near unexpected token `('
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$ - Device: eth0  [Auto Ethernet] ------------------------------------------------
-: command not found
jared@jared-Lenovo-V570:~$   Type:              Wired
Type:: command not found
jared@jared-Lenovo-V570:~$   Driver:            r8169
Driver:: command not found
jared@jared-Lenovo-V570:~$   State:             connected
State:: command not found
jared@jared-Lenovo-V570:~$   Default:           yes
Default:: command not found
jared@jared-Lenovo-V570:~$   HW Address:        F0:DE:F1:60:76:76
HW: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   Capabilities:
Capabilities:: command not found
jared@jared-Lenovo-V570:~$     Carrier Detect:  yes
Carrier: command not found
jared@jared-Lenovo-V570:~$     Speed:           100 Mb/s
Speed:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   Wired Properties
Wired: command not found
jared@jared-Lenovo-V570:~$     Carrier:         on
Carrier:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   IPv4 Settings:
IPv4: command not found
jared@jared-Lenovo-V570:~$     Address:         192.168.1.109
Address:: command not found
jared@jared-Lenovo-V570:~$     Prefix:          24 (255.255.255.0)
bash: syntax error near unexpected token `('
jared@jared-Lenovo-V570:~$     Gateway:         192.168.1.1
Gateway:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$     DNS:             97.64.168.12
DNS:: command not found
jared@jared-Lenovo-V570:~$     DNS:             97.64.183.165
DNS:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$ - Device: wlan0  [1111 linksys] ------------------------------------------------
-: command not found
jared@jared-Lenovo-V570:~$   Type:              802.11 WiFi
Type:: command not found
jared@jared-Lenovo-V570:~$   Driver:            iwlwifi
Driver:: command not found
jared@jared-Lenovo-V570:~$   State:             connected
State:: command not found
jared@jared-Lenovo-V570:~$   Default:           no
Default:: command not found
jared@jared-Lenovo-V570:~$   HW Address:        40:25:C2:32:77:14
HW: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   Capabilities:
Capabilities:: command not found
jared@jared-Lenovo-V570:~$     Speed:           1 Mb/s
Speed:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   Wireless Properties
Wireless: command not found
jared@jared-Lenovo-V570:~$     WEP Encryption:  yes
WEP: command not found
jared@jared-Lenovo-V570:~$     WPA Encryption:  yes
WPA: command not found
jared@jared-Lenovo-V570:~$     WPA2 Encryption: yes
WPA2: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   Wireless Access Points (* = current AP)
bash: syntax error near unexpected token `('
jared@jared-Lenovo-V570:~$     PS3-5575119:     Infra, 00:23:4D:83:94:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA
PS3-5575119:: command not found
jared@jared-Lenovo-V570:~$     DEBBY-PC:        Infra, 58:6D:8F:0B:D4:8C, Freq 2462 MHz, Rate 54 Mb/s, Strength 29 WPA2
DEBBY-PC:: command not found
jared@jared-Lenovo-V570:~$     STEWARTHOME:     Infra, 50:67:F0:F0:89:32, Freq 2462 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
STEWARTHOME:: command not found
jared@jared-Lenovo-V570:~$     JLMS:            Infra, 00:24:93:5D:30:60, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
JLMS:: command not found
jared@jared-Lenovo-V570:~$     Belkin.318D:     Infra, 94:44:52:17:C1:8D, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA WPA2
Belkin.318D:: command not found
jared@jared-Lenovo-V570:~$     SW1IA24:         Infra, 00:19:70:38:19:B6, Freq 2442 MHz, Rate 11 Mb/s, Strength 24
SW1IA24:: command not found
jared@jared-Lenovo-V570:~$     *1111 linksys:   Infra, 00:1D:7E:25:7F:4B, Freq 2437 MHz, Rate 54 Mb/s, Strength 66 WPA
*1111: command not found
jared@jared-Lenovo-V570:~$     home:            Infra, 20:4E:7F:25:68:12, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WPA2
home:: command not found
jared@jared-Lenovo-V570:~$     NETGEAR-Guest:   Infra, 22:4E:7F:25:68:13, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA2
NETGEAR-Guest:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$   IPv4 Settings:
IPv4: command not found
jared@jared-Lenovo-V570:~$     Address:         192.168.1.104
Address:: command not found
jared@jared-Lenovo-V570:~$     Prefix:          24 (255.255.255.0)
bash: syntax error near unexpected token `('
jared@jared-Lenovo-V570:~$     Gateway:         192.168.1.1
Gateway:: command not found
jared@jared-Lenovo-V570:~$ 
jared@jared-Lenovo-V570:~$     DNS:             97.64.168.12
DNS:: command not found
jared@jared-Lenovo-V570:~$     DNS:             97.64.183.165
DNS:: command not found
lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.437 GHz (Channel 6)

eth0      no frequency information.

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


Error: unable to find a version of ndiswrapper!

iwlwifi               381775  0 
mac80211              543992  1 iwlwifi
cfg80211              210401  2 iwlwifi,mac80211
compat                 13728  6 rfcomm,bnep,bluetooth,iwlwifi,mac80211,cfg80211

Jun 18 19:44:22 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun 18 19:44:22 jared-Lenovo-V570 wpa_supplicant[1240]: Trying to authenticate with 00:1d:7e:25:7f:4b (SSID='1111 linksys' freq=2437 MHz)
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.192404] wlan0: authenticate with 00:1d:7e:25:7f:4b
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.208623] wlan0: send auth to 00:1d:7e:25:7f:4b (try 1/3)
Jun 18 19:44:22 jared-Lenovo-V570 wpa_supplicant[1240]: Trying to associate with 00:1d:7e:25:7f:4b (SSID='1111 linksys' freq=2437 MHz)
Jun 18 19:44:22 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.211413] wlan0: authenticated
Jun 18 19:44:22 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.213216] wlan0: associate with 00:1d:7e:25:7f:4b (try 1/3)
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.217310] wlan0: RX AssocResp from 00:1d:7e:25:7f:4b (capab=0x411 status=0 aid=4)
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.217316] wlan0: associated
Jun 18 19:44:22 jared-Lenovo-V570 wpa_supplicant[1240]: Associated with 00:1d:7e:25:7f:4b
Jun 18 19:44:22 jared-Lenovo-V570 kernel: [   20.228909] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 18 19:44:22 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: associating -> associated
Jun 18 19:44:23 jared-Lenovo-V570 wpa_supplicant[1240]: WPA: Key negotiation completed with 00:1d:7e:25:7f:4b [PTK=TKIP GTK=TKIP]
Jun 18 19:44:23 jared-Lenovo-V570 wpa_supplicant[1240]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:25:7f:4b completed (auth) [id=0 id_str=]
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: associated -> 4-way handshake
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network '1111 linksys'.
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Beginning IP6 addrconf.
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Jun 18 19:44:24 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Jun 18 19:44:24 jared-Lenovo-V570 dhclient: Listening on LPF/wlan0/40:25:c2:32:77:14
Jun 18 19:44:24 jared-Lenovo-V570 dhclient: Sending on   LPF/wlan0/40:25:c2:32:77:14
Jun 18 19:44:24 jared-Lenovo-V570 dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Jun 18 19:44:27 jared-Lenovo-V570 dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Jun 18 19:44:31 jared-Lenovo-V570 dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Jun 18 19:44:34 jared-Lenovo-V570 kernel: [   32.323359] wlan0: no IPv6 routers present
Jun 18 19:44:40 jared-Lenovo-V570 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
Jun 18 19:44:40 jared-Lenovo-V570 dhclient: DHCPREQUEST of 192.168.1.104 on wlan0 to 255.255.255.255 port 67
Jun 18 19:44:40 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): DHCPv4 state changed preinit -> bound
Jun 18 19:44:40 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 18 19:44:40 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) started...
Jun 18 19:44:41 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): writing resolv.conf to /sbin/resolvconf
Jun 18 19:44:41 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 18 19:44:42 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) successful, device activated.
Jun 18 19:44:42 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 18 19:44:42 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 19:44:42 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 19:44:44 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): IP6 addrconf timed out or failed.
Jun 18 19:44:44 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 18 19:44:44 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 18 19:44:44 jared-Lenovo-V570 NetworkManager[983]: <info> Activation (wlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jun 18 19:45:09 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 19:46:22 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 19:46:22 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 19:51:27 jared-Lenovo-V570 NetworkManager[983]: <info> Policy set '1111 linksys' (wlan0) as default for IPv4 routing and DNS.
Jun 18 20:15:15 jared-Lenovo-V570 NetworkManager[983]: <info> kernel firmware directory '/lib/firmware' changed
Jun 18 20:32:41 jared-Lenovo-V570 wpa_supplicant[1240]: WPA: Group rekeying completed with 00:1d:7e:25:7f:4b [GTK=TKIP]
Jun 18 20:32:41 jared-Lenovo-V570 wpa_supplicant[1240]: WPA: Group rekeying completed with 00:1d:7e:25:7f:4b [GTK=TKIP]
Jun 18 21:02:56 jared-Lenovo-V570 wpa_supplicant[1240]: CTRL-EVENT-DISCONNECTED bssid=00:1d:7e:25:7f:4b reason=4
Jun 18 21:02:56 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): roamed from BSSID 00:1D:7E:25:7F:4B (1111 linksys) to (none) ((none))
Jun 18 21:02:56 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: completed -> scanning
Jun 18 21:02:57 jared-Lenovo-V570 wpa_supplicant[1240]: Trying to authenticate with 00:1d:7e:25:7f:4b (SSID='1111 linksys' freq=2437 MHz)
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.859080] wlan0: authenticate with 00:1d:7e:25:7f:4b
Jun 18 21:02:57 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.865637] wlan0: send auth to 00:1d:7e:25:7f:4b (try 1/3)
Jun 18 21:02:57 jared-Lenovo-V570 wpa_supplicant[1240]: Trying to associate with 00:1d:7e:25:7f:4b (SSID='1111 linksys' freq=2437 MHz)
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.868736] wlan0: authenticated
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.871174] wlan0: associate with 00:1d:7e:25:7f:4b (try 1/3)
Jun 18 21:02:57 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: authenticating -> associating
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.875299] wlan0: RX AssocResp from 00:1d:7e:25:7f:4b (capab=0x411 status=0 aid=3)
Jun 18 21:02:57 jared-Lenovo-V570 kernel: [ 4732.875308] wlan0: associated
Jun 18 21:02:57 jared-Lenovo-V570 wpa_supplicant[1240]: Associated with 00:1d:7e:25:7f:4b
Jun 18 21:02:57 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: associating -> 4-way handshake
Jun 18 21:02:57 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: 4-way handshake -> group handshake
Jun 18 21:02:57 jared-Lenovo-V570 wpa_supplicant[1240]: WPA: Key negotiation completed with 00:1d:7e:25:7f:4b [PTK=TKIP GTK=TKIP]
Jun 18 21:02:57 jared-Lenovo-V570 wpa_supplicant[1240]: CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:25:7f:4b completed (reauth) [id=0 id_str=]
Jun 18 21:02:57 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): supplicant interface state: group handshake -> completed
Jun 18 21:03:02 jared-Lenovo-V570 NetworkManager[983]: <info> (wlan0): roamed from BSSID (none) ((none)) to 00:1D:7E:25:7F:4B (1111 linksys)
``` 
On a side note ndiswrapper originally said it wasn't installed and gave me the apt-get to install it so I entered the command and then it said ndiswrapper couldn't be located after the install.

---

### Post by wildmanne39 on 2012-06-18
Hi, we do not want ndiswrapper installed, I was just checking to make sure it was not, we will probably have to uninstall it after you reboot so check again for ndiswrapper after you reboot with this command.
```
ndiswrapper -l
```
Go into your router settings and change wpa to just wpa2 only if you have that option.

Then do:
```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```

Add one line:

```
options iwlwifi 11n_disable=1
```

Proofread carefully, save and close gedit. Reboot.

---

### Post by jaredanderson on 2012-06-18
Thank you greatly sir. I feel pretty stupid about the ndis thing. yeah everything is working thanks a ton. Seriously super grateful.

---

### Post by wildmanne39 on 2012-06-18
Hi, your welcome! 
Enjoy

---

