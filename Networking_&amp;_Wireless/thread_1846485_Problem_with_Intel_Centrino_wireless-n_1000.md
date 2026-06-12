---
title: "Problem with Intel Centrino wireless-n 1000"
date: 2011-09-19
forum: Networking &amp; Wireless
---

### Post by pulsi on 2011-09-19
Hello, I am new to Ubuntu and I have very annoying problem with wireless connection. When I start my notebook(Lenovo ThinkPad Edge E520) wifi is disabled, when I enable it it wont't find any network or it just blink with list of networks.System version is Ubuntu 11.04. When I ran command sudo lshw -C network it says this:


*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: f0:de:f1:64:23:ae
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:41 ioport:4000(size=256) memory:e0404000-e0404fff memory:e0400000-e0403fff
  *-network DISABLED
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:af:48:2a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:44 memory:e1d00000-e1d01fff
I would really apreciate any help.

---

### Post by wildmanne39 on 2011-09-19
Hi, welcome to the forum! please post the results of these commands here:
```
cat /etc/lsb-release; uname -a
```
```
nm-tool
```
```
lspci -nn | grep -e 0280 -e 0200
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
```
sudo iwlist scan
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by anukool_j on 2012-01-23
Hi,

I don't know if pulsi ever resolved the issue, but I have exactly the same problem on very similar hardware (Lenovo Z570, Intel Centrino Wireless-n 1000.)  Specifically, I'm able to see a list of networks, but unable to connect to them. The relevant part of the networkmanager log simply says:

```
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0/wireless): connection 'RESNET-NEW-WARREN' requires no security.  No secrets needed.
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Config: added 'ssid' value 'RESNET-NEW-WARREN'
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Config: added 'scan_ssid' value '1'
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Config: added 'key_mgmt' value 'NONE'
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> Config: set interface ap_scan to 1
Jan 23 20:24:33 anukool NetworkManager[1109]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jan 23 20:24:34 anukool NetworkManager[1109]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Jan 23 20:25:33 anukool NetworkManager[1109]: <warn> Activation (wlan0/wireless): association took too long, failing activation.
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> (wlan0): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11]
Jan 23 20:25:33 anukool NetworkManager[1109]: <warn> Activation (wlan0) failed for access point (RESNET-NEW-WARREN)
Jan 23 20:25:33 anukool NetworkManager[1109]: <warn> Activation (wlan0) failed.
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> (wlan0): deactivating device (reason 'none') [0]
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> Policy set 'Wired connection 1' (eth0) as default for IPv4 routing and DNS.
Jan 23 20:25:33 anukool NetworkManager[1109]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jan 23 20:25:33 anukool NetworkManager[1109]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jan 23 20:25:36 anukool NetworkManager[1109]: <info> Auto-activating connection 'RESNET-NEW-WARREN'.
Jan 23 20:25:36 anukool NetworkManager[1109]: <info> Activation (wlan0) starting connection 'RESNET-NEW-WARREN'
Jan 23 20:25:36 anukool NetworkManager[1109]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]

```This repeats for a long time unless I manually click 'disconnect' in networkmanager to stop it.

I have removed the acer_wmi module and disabled the N radio as suggested in other posts -- without that I'm not able to get wifi to work at all.

I've included the output of all the commands you asked for.

```

anukool@anukool:~$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:e5:0b:37:fa:f6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-15-generic firmware=39.31.5.1 build 35138 latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:43 memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:9b:98:51
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=128.54.244.180 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

``````

anukool@anukool:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux anukool 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

``````

anukool@anukool:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             disconnected
  Default:           no
  HW Address:        74:E5:0B:37:FA:F6

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    &#65533;&#65533;|&#65533;&#65533;&#65533;!+W&#1862;`+&#65533;w&#65533;l&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;iI&#65533;u: Ad-Hoc, 36:3E:F9:32:BD:6B, Freq 2412 MHz, Rate 54 Mb/s, Strength 22
    RESNET-NEW-WARREN: Infra, 00:20:A6:52:B4:FC, Freq 2437 MHz, Rate 54 Mb/s, Strength 35
    Vivato Tech 2:   Infra, 00:0B:33:09:11:20, Freq 2452 MHz, Rate 54 Mb/s, Strength 30 WEP
    HP78FE52:        Ad-Hoc, 02:2E:DE:7C:22:78, Freq 2457 MHz, Rate 11 Mb/s, Strength 27
    RESNET-NEW-WARREN: Infra, 00:20:A6:49:51:13, Freq 2437 MHz, Rate 54 Mb/s, Strength 37
    RESNET-NEW-WARREN: Infra, 00:20:A6:52:B5:33, Freq 2412 MHz, Rate 54 Mb/s, Strength 29
    RESNET-NEW-WARREN: Infra, 00:20:A6:52:B5:2D, Freq 2412 MHz, Rate 54 Mb/s, Strength 25
    RESNET-NEW-WARREN: Infra, 00:20:A6:53:25:DC, Freq 2437 MHz, Rate 54 Mb/s, Strength 52
    HPE710n.8032AE:  Ad-Hoc, 02:20:70:E1:2A:E0, Freq 2437 MHz, Rate 54 Mb/s, Strength 45
    bluwater:        Infra, 00:0F:66:53:42:B6, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:9B:98:51

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         128.54.244.180
    Prefix:          22 (255.255.252.0)
    Gateway:         128.54.244.1

    DNS:             132.239.0.252
    DNS:             128.54.16.2

``````

anukool@anukool:~$ lspci -nn | grep -e 0280 -e 0200
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [8086:0084]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)

``````

anukool@anukool:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``````
          
anukool@anukool:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

``````

anukool@anukool:~$ lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  8 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
dm_crypt               23199  0 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330769  1 
snd_hda_intel          33390  2 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
joydev                 17693  0 
arc4                   12529  2 
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
iwlagn                314213  0 
btusb                  18600  2 
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
bluetooth             166112  23 bnep,rfcomm,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              462092  1 iwlagn
cfg80211              199630  2 iwlagn,mac80211
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rts5139               351143  0 
mei                    41480  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
psmouse                73882  0 
serio_raw              13166  0 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
lp                     17799  0 
ideapad_laptop         13871  0 
parport                46562  3 parport_pc,ppdev,lp
v4l2_compat_ioctl32    17083  1 videodev
sparse_keymap          13890  1 ideapad_laptop
wmi                    19256  0 
i915                  567092  3 
ahci                   26002  3 
libahci                26861  1 ahci
drm_kms_helper         42558  1 i915
r8169                  52788  0 
drm                   236290  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915

``````

anukool@anukool:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:20:A6:52:B4:FC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"RESNET-NEW-WARREN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000000280a037
                    Extra: Last beacon: 332ms ago
                    IE: Unknown: 00115245534E45542D4E45572D57415252454E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010180
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
          Cell 02 - Address: 00:20:A6:49:51:13
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"RESNET-NEW-WARREN"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000033a906d
                    Extra: Last beacon: 392ms ago
                    IE: Unknown: 00115245534E45542D4E45572D57415252454E
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030106
                    IE: Unknown: 050400010102
                    IE: Unknown: 2A0102
                    IE: Unknown: 32041224606C
          Cell 03 - Address: 02:2E:DE:7C:22:78
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"HP78FE52"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Ad-Hoc
                    Extra:tsf=0000025f91a262ec
                    Extra: Last beacon: 168ms ago
                    IE: Unknown: 00084850373846453532
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 06020000
                    IE: Unknown: 0706555320010B14

```

That last output -- iwlist scan -- keeps changing every time I run it, showing different subsets of the available cells.

Thank you!

---

