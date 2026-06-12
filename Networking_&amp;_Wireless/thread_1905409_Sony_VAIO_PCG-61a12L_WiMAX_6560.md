---
title: "Sony VAIO PCG-61a12L WiMAX 6560"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by valroadie on 2012-01-06
Hello,
After looking tirelessly for the past 3 days, I have found, and tried everything I could on these forums to get my wireless working. I will post the required terminal reports and see if anyone out there can give me a simplified walk-through to help me get my wireless working. 
I am having problems obv. with my wireless not working, I can enable it with the enable wireless menu drop-box, but it turns off 2 seconds after I enable it. I appreciate the help, and I hope I have given you enough information for a lead to success. 


$ lspci
 
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N + WiMAX 6150 (rev 67)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
09:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)

```
No need for $ lsusb as it is not USB

$ ifconfig 

```
eth0      Link encap:Ethernet  HWaddr 78:84:3c:a1:31:32  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::7a84:3cff:fea1:3132/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1355 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1102 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1449444 (1.4 MB)  TX bytes:164516 (164.5 KB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

$ iwconfig 

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

$ lsmod

```
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_conexant    62197  1 
arc4                   12529  2 
acer_wmi               23948  0 
sparse_keymap          13890  1 acer_wmi
psmouse                73882  0 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
joydev                 17693  0 
snd_hwdep              13668  1 snd_hda_codec
serio_raw              13166  0 
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
sony_laptop            45393  0 
snd_seq_midi_event     14899  1 snd_seq_midi
iwlagn                314213  0 
wmi                    19256  1 acer_wmi
mac80211              462092  1 iwlagn
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              199587  2 iwlagn,mac80211
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
rts_pstor             445246  0 
i915                  566827  2 
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  1 
libahci                26861  1 ahci
atl1c                  41643  0 

```

$ sudo lswh -C network 

```
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N + WiMAX 6150
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 67
       serial: 40:25:c2:60:ef:38
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-14-generic firmware=41.28.5.1 build 33926 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:41 memory:d2500000-d2501fff
  *-network
       description: Ethernet interface
       product: AR8151 v2.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: c0
       serial: 78:84:3c:a1:31:32
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.10 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:d1400000-d143ffff ioport:2000(size=128)

```

$ lsb_release 

```
Description:	Ubuntu 11.10

```

$ sudo /etc/init.d/networking restart

```
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                   [ OK ] 

```

---

### Post by wildmanne39 on 2012-01-06
Hi, try this please if it works we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f iwlagn
sudo modprobe iwlagn 11n_disable=1
sudo ifconfig wlan0 up

```
Do not reboot.
Thanks

---

### Post by valroadie on 2012-01-06
Great! It turns the wireless card on, but the wireless networks option is still greyed so I cannot connect.

---

### Post by wildmanne39 on 2012-01-06
Hi, let's make that change permanent, then we will go from there.
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add a single line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot and see if it works if not please show.
```
nm-tool
rfkill list all
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75
```
Thanks

---

### Post by valroadie on 2012-01-06
Did not make it turn on, or stay on. 

$ nm-tool 

```
NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        40:25:C2:60:EF:38

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        78:84:3C:A1:31:32

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.10
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



```

$ rf kill all

```
0: sony-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: sony-wimax: WiMAX
	Soft blocked: no
	Hard blocked: no
2: acer-wireless: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

$ sudo iwlist scan 

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down


```

$ sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n75

```
Jan  6 18:39:23 ubuntu kernel: [ 1571.402483] iwlagn 0000:02:00.0: setting latency timer to 64
Jan  6 18:39:23 ubuntu kernel: [ 1571.402515] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Jan  6 18:39:23 ubuntu kernel: [ 1571.413098] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Jan  6 18:39:23 ubuntu kernel: [ 1571.413100] iwlagn 0000:02:00.0: Device SKU: 0X9
Jan  6 18:39:23 ubuntu kernel: [ 1571.413102] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Jan  6 18:39:23 ubuntu kernel: [ 1571.413118] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Jan  6 18:39:23 ubuntu kernel: [ 1571.413206] iwlagn 0000:02:00.0: irq 41 for MSI/MSI-X
Jan  6 18:39:23 ubuntu kernel: [ 1571.415402] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Jan  6 18:39:23 ubuntu kernel: [ 1571.415713] ieee80211 phy2: Selected rate control algorithm 'iwl-agn-rs'
Jan  6 18:39:23 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Jan  6 18:39:23 ubuntu NetworkManager[971]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 5)
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): now managed
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): bringing up device.
Jan  6 18:39:23 ubuntu NetworkManager[971]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  6 18:39:38 ubuntu kernel: [ 1586.158190] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jan  6 18:40:27 ubuntu kernel: [ 1634.987201] Modules linked in: iwlagn bnep rfcomm bluetooth parport_pc ppdev lp parport binfmt_misc snd_hda_codec_hdmi snd_hda_codec_conexant arc4 acer_wmi sparse_keymap psmouse snd_hda_intel snd_hda_codec joydev snd_hwdep serio_raw snd_pcm uvcvideo videodev v4l2_compat_ioctl32 snd_seq_midi snd_rawmidi sony_laptop snd_seq_midi_event wmi mac80211 snd_seq snd_timer snd_seq_device cfg80211 snd soundcore snd_page_alloc mei(C) rts_pstor(C) i915 drm_kms_helper drm i2c_algo_bit video usbhid hid ahci libahci atl1c [last unloaded: iwlagn]
Jan  6 18:40:27 ubuntu kernel: [ 1634.987252]  <IRQ>  [<ffffffff8105e7ef>] warn_slowpath_common+0x7f/0xc0
Jan  6 18:40:27 ubuntu kernel: [ 1634.987258]  [<ffffffff8105e8e6>] warn_slowpath_fmt+0x46/0x50
Jan  6 18:41:26 ubuntu kernel: [ 1693.430500] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
Jan  6 18:41:26 ubuntu kernel: [ 1693.496075] iwlagn 0000:02:00.0: Not sending command - RF KILL
Jan  6 18:41:26 ubuntu kernel: [ 1693.496079] iwlagn 0000:02:00.0: Error sending REPLY_RXON: enqueue_hcmd failed: -5
Jan  6 18:41:26 ubuntu kernel: [ 1693.496082] iwlagn 0000:02:00.0: Error clearing ASSOC_MSK on BSS (-5)
Jan  6 18:41:37 ubuntu kernel: [ 1704.491990] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
Jan  6 18:50:42 ubuntu kernel: [   33.726732] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Jan  6 18:50:42 ubuntu kernel: [   33.726736] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Jan  6 18:50:42 ubuntu kernel: [   33.726791] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  6 18:50:42 ubuntu kernel: [   33.726802] iwlagn 0000:02:00.0: setting latency timer to 64
Jan  6 18:50:42 ubuntu kernel: [   33.726836] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Jan  6 18:50:42 ubuntu kernel: [   33.737450] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Jan  6 18:50:42 ubuntu kernel: [   33.737453] iwlagn 0000:02:00.0: Device SKU: 0X9
Jan  6 18:50:42 ubuntu kernel: [   33.737456] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Jan  6 18:50:42 ubuntu kernel: [   33.742374] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Jan  6 18:50:42 ubuntu kernel: [   33.742470] iwlagn 0000:02:00.0: irq 41 for MSI/MSI-X
Jan  6 18:50:42 ubuntu kernel: [   34.113020] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Jan  6 18:50:42 ubuntu kernel: [   34.115137] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jan  6 18:50:42 ubuntu NetworkManager[967]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Jan  6 18:50:42 ubuntu NetworkManager[967]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): now managed
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): bringing up device.
Jan  6 18:50:42 ubuntu NetworkManager[967]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  6 18:50:44 ubuntu avahi-daemon[965]: Withdrawing workstation service for wlan0.
Jan  6 18:55:31 ubuntu kernel: [  323.713994] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.
Jan  6 18:55:32 ubuntu kernel: [  324.216783] iwlagn 0000:02:00.0: RF_KILL bit toggled to enable radio.
Jan  6 18:56:33 ubuntu kernel: [   33.732583] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
Jan  6 18:56:33 ubuntu kernel: [   33.732587] iwlagn: Copyright(c) 2003-2011 Intel Corporation
Jan  6 18:56:33 ubuntu kernel: [   33.732645] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan  6 18:56:33 ubuntu kernel: [   33.732657] iwlagn 0000:02:00.0: setting latency timer to 64
Jan  6 18:56:33 ubuntu kernel: [   33.732689] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Jan  6 18:56:33 ubuntu kernel: [   33.743367] iwlagn 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Jan  6 18:56:33 ubuntu kernel: [   33.743370] iwlagn 0000:02:00.0: Device SKU: 0X9
Jan  6 18:56:33 ubuntu kernel: [   33.743372] iwlagn 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Jan  6 18:56:33 ubuntu kernel: [   33.819711] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Jan  6 18:56:33 ubuntu kernel: [   33.819836] iwlagn 0000:02:00.0: irq 42 for MSI/MSI-X
Jan  6 18:56:33 ubuntu kernel: [   33.957984] iwlagn 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Jan  6 18:56:33 ubuntu kernel: [   33.960555] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jan  6 18:56:33 ubuntu NetworkManager[940]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0)
Jan  6 18:56:33 ubuntu NetworkManager[940]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlagn' ifindex: 3)
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): now managed
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): bringing up device.
Jan  6 18:56:33 ubuntu NetworkManager[940]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jan  6 18:56:34 ubuntu avahi-daemon[933]: Withdrawing workstation service for wlan0.

```

Thank you

---

### Post by wildmanne39 on 2012-01-06
Hi, please do this it is a problem.
```
echo "blacklist acer-wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
You may have to reboot.
thanks

---

### Post by valroadie on 2012-01-06
Awesome! Works wonderful now sir. 
I can connect to the internet and the wireless card stays on upon reboot. 
Thank you so much!

---

### Post by wildmanne39 on 2012-01-06
Hi, your welome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

