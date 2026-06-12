---
title: "Unable to scan or access any wireless networks-Ubuntu 10.04"
date: 2011-06-07
forum: Networking &amp; Wireless
---

### Post by bestsoccerdog on 2011-06-07
Machine is an MSI U130 netbook running Ubuntu 10.04.2 LTS

01:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

interface
```
wlan0     RT2860 Wireless  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```check modules

```
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203376  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  287810  4 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
soundcore               6620  1 snd
psmouse                63245  0 
serio_raw               3978  0 
drm                   162377  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
rt3090sta             674216  0 
agpgart                31724  2 intel_agp,drm
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169

```network configuration
```
*-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff

```scanning:```
*-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt3090 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:16 memory:fe900000-fe90ffff

```architecture:2.6.32-32-generic i686

I realize that Ubuntu recognizes the card, but I'm not sure why it's not picking up any networks that are around and says "disconnected", even though  I've made sure that the wireless network light is enabled on the netbook.

Thanks

---

### Post by chili555 on 2011-06-07
Network interfaces, in your case, wlan0 often show as DISABLED because the wireless switch is set to 'Off' or because the laptop-mode module is not working correctly or even loaded. I see no likely candidates in your *lsmod*. Often, but not always, a module is required to translate the key presses to instructions the kernel recognizes. Let's have a peek. Please run and post:```
rfkill list all
```

---

### Post by bestsoccerdog on 2011-06-07
When I run that command, nothing happens.  It just sets me up for a new command.

---

### Post by chili555 on 2011-06-07
Let's see:```
dmesg | grep -e rt3 -e wlan
sudo cat /var/log/syslog | grep -e rt3 -e wlan
```Thanks.

---

### Post by bestsoccerdog on 2011-06-07
Ok, that command works.

For the first
```
[   13.124651] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned.
[   13.324622] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.324672] rt3090 0000:01:00.0: setting latency timer to 64

```For the second:```
                      p { margin-bottom: 0.08in; }  Jun  7 12:11:55 tim-netbook kernel: [   12.896125] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned. 
 Jun  7 12:11:55 tim-netbook kernel: [   12.934766] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 12:11:55 tim-netbook kernel: [   12.934817] rt3090 0000:01:00.0: setting latency timer to 64 
 Jun  7 12:11:59 tim-netbook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0) 
 Jun  7 12:11:59 tim-netbook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt3090') 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 12:11:59 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 12:12:00 tim-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
 Jun  7 12:12:00 tim-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0) 
 Jun  7 12:12:01 tim-netbook wpa_supplicant[811]: Could not set interface 'wlan0' UP 
 Jun  7 12:32:38 tim-netbook kernel: [   13.338595] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned. 
 Jun  7 12:32:38 tim-netbook kernel: [   13.374697] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 12:32:38 tim-netbook kernel: [   13.374751] rt3090 0000:01:00.0: setting latency timer to 64 
 Jun  7 12:32:39 tim-netbook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0) 
 Jun  7 12:32:39 tim-netbook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt3090') 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
 Jun  7 12:32:39 tim-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0) 
 Jun  7 12:32:39 tim-netbook wpa_supplicant[814]: Could not set interface 'wlan0' UP 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) starting connection 'linksys' 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0) 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0) 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 4) 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) failed. 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0) 
 Jun  7 12:34:07 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) starting connection 'linksys' 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0) 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0) 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 4) 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) failed. 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0) 
 Jun  7 12:34:08 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
 Jun  7 13:01:29 tim-netbook kernel: [   13.226295] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned. 
 Jun  7 13:01:29 tim-netbook kernel: [   13.441230] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 13:01:29 tim-netbook kernel: [   13.441278] rt3090 0000:01:00.0: setting latency timer to 64 
 Jun  7 13:01:31 tim-netbook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0) 
 Jun  7 13:01:31 tim-netbook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt3090') 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
 Jun  7 13:01:31 tim-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0) 
 Jun  7 13:01:31 tim-netbook wpa_supplicant[829]: Could not set interface 'wlan0' UP 
 Jun  7 13:08:37 tim-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 2 (reason 0) 
 Jun  7 13:08:37 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
 Jun  7 13:08:48 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 13:09:37 tim-netbook kernel: [   13.747433] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned. 
 Jun  7 13:09:37 tim-netbook kernel: [   13.825712] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 13:09:37 tim-netbook kernel: [   13.825755] rt3090 0000:01:00.0: setting latency timer to 64 
 Jun  7 13:09:39 tim-netbook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0) 
 Jun  7 13:09:39 tim-netbook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt3090') 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
 Jun  7 13:09:39 tim-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0) 
 Jun  7 13:09:39 tim-netbook wpa_supplicant[809]: Could not set interface 'wlan0' UP 
 Jun  7 13:30:33 tim-netbook NetworkManager: <info>  (wlan0): now unmanaged 
 Jun  7 13:30:33 tim-netbook NetworkManager: <info>  (wlan0): device state change: 3 -> 1 (reason 37) 
 Jun  7 14:58:40 tim-netbook kernel: [ 1271.889288] rt3090 0000:01:00.0: PCI INT A disabled 
 Jun  7 14:58:40 tim-netbook kernel: [ 1272.466513] rt3090 0000:01:00.0: restoring config space at offset 0xf (was 0x1ff, writing 0x10b) 
 Jun  7 14:58:40 tim-netbook kernel: [ 1272.466545] rt3090 0000:01:00.0: restoring config space at offset 0x4 (was 0x0, writing 0xfe900000) 
 Jun  7 14:58:40 tim-netbook kernel: [ 1272.466558] rt3090 0000:01:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10) 
 Jun  7 14:58:40 tim-netbook kernel: [ 1272.466572] rt3090 0000:01:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100007) 
 Jun  7 14:58:40 tim-netbook kernel: [ 1272.644801] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 14:58:41 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 14:58:41 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 14:58:41 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 14:58:41 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 14:58:41 tim-netbook wpa_supplicant[809]: Could not set interface 'wlan0' UP 
 Jun  7 15:03:00 tim-netbook kernel: [   13.124651] rt3090sta: module is from the staging directory, the quality is unknown, you have been warned. 
 Jun  7 15:03:00 tim-netbook kernel: [   13.324622] rt3090 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 Jun  7 15:03:00 tim-netbook kernel: [   13.324672] rt3090 0000:01:00.0: setting latency timer to 64 
 Jun  7 15:03:01 tim-netbook NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0) 
 Jun  7 15:03:01 tim-netbook NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found. 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00). 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'rt3090') 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): now managed 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2) 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): bringing up device. 
 Jun  7 15:03:01 tim-netbook NetworkManager: <info>  (wlan0): deactivating device (reason: 2). 
 Jun  7 15:03:02 tim-netbook NetworkManager: <info>  (wlan0): supplicant manager state:  down -> idle 
 Jun  7 15:03:02 tim-netbook NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 0) 
 Jun  7 15:03:02 tim-netbook wpa_supplicant[803]: Could not set interface 'wlan0' UP 
 
```

Thanks

---

### Post by chili555 on 2011-06-07
> Could not set interface 'wlan0' UPI am suspicious that either the wireless switch has the radio turned off or that Network Manager has disallowed wireless in favor of wired. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themYour reply looks like you have, even temporarily, a wired ethernet connection. If you detach the cable and wait a few moments for Network Manager to notice the change in state, do you see networks when you click the NM icon? Are the messages the same without the ethernet cable attached after this?> [COLOR="Red"]Jun  7 15:03:02[/COLOR] tim-netbook wpa_supplicant[803]: Could not set interface 'wlan0' UPBefore you detach the ethernet, please do:```
sudo apt-get install rfkill
sudo rfkill list all
```

---

### Post by bestsoccerdog on 2011-06-07
Even after installing the rfkill package, the command is not bringing up anything.  I was using a wired connection, but even after disconnecting it, the results in terminal are the same.  Whilst the Ethernet is disconnected, under wireless networks it still says disconnected.  There are no networks under it.  I think it may be disabled, since even when I disable the wireless networks with the keyboard shortcut, I get the same results.  Would I need to install and boot into Windows to maybe enable it?  Thanks for all your help by the way.

---

### Post by chili555 on 2011-06-07
> Would I need to install and boot into Windows to maybe enable it? I don't think so.

Is there a change in the status of Wireless in Network Manager when you press the wireless keyboard shortcut? What specific message does this give us?```
sudo iwlist wlan0 scan
```

---

### Post by bestsoccerdog on 2011-06-07
There is no change in status when I switch the wireless on and off.  After running that command, I just get "wlan0 No scan results."

---

### Post by chili555 on 2011-06-07
I'll have to work on this tomorrow; see you then.

---

### Post by bestsoccerdog on 2011-06-07
After some tedious googling, I found this link, which solved the problem. I think it was a driver issue, even though it showed the driver as installed.

[http://ubuntuforums.org/showthread.php?t=1503122](http://ubuntuforums.org/showthread.php?t=1503122)

Thank you very much for all your help.  It's nice to see a community that offers to help new users so much. Thanks again.

---

