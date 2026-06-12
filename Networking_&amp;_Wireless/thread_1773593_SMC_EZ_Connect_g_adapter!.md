---
title: "SMC EZ Connect g adapter!"
date: 2011-06-02
forum: Networking &amp; Wireless
---

### Post by Rampo on 2011-06-02
Hi,

I am new to Ubuntu. I just upgraded Ubuntu Netbook on my Dell Latitude D610. I need a wireless USB adapter to use the internet. I decided to make use of the SMC EZ Connect g 802.11g Wireless USB 2.0 Adapter, which I used on Windows XP. Unfortunately Ubuntu recognizes the adapter (lsusb in the terminal). But that's it. No connection to the internet whatsoever or searching for available networks. 
Help me, guys. What should I do to make this adapter work. Drivers? I looked for drivers on the SMC website, couldn't find any.

Model: SMC2862W-G
Part No: 99-012084-449
 
> **Rampo said:**
> lspci
```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller

```
 
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 00:14:22:c4:ba:c9  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:200 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15840 (15.8 KB)  TX bytes:15840 (15.8 KB)

```
 
iwconfig
```

lo        no wireless extensions.
eth0     no wireless extensions.

```
 
lsmod
```

Module                  Size  Used by
p54usb                 11206  0 
p54common              25426  1 p54usb
led_class               2633  1 p54common
mac80211              231541  2 p54usb,p54common
cfg80211              144470  2 p54common,mac80211
binfmt_misc             6599  1 
joydev                  8735  0 
snd_intel8x0           25632  2 
snd_ac97_codec         99227  1 snd_intel8x0
ac97_bus                1014  1 snd_ac97_codec
i915                  290938  4 
snd_pcm                71475  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
pcmcia                 35973  0 
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm                   168054  5 i915,drm_kms_helper
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   5556  0 
yenta_socket           21518  0 
dell_laptop             5730  0 
parport_pc             26058  1 
snd                    49006  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            10566  1 yenta_socket
intel_agp              26360  2 i915
dcdbas                  5402  1 dell_laptop
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
video                  18712  1 i915
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_intel8x0,snd_pcm
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
lp                      7342  0 
parport                31492  3 ppdev,parport_pc,lp
tg3                   123310  0
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:c4:ba:c9
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff

```
 
iwlist scan
```

lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.

```
 
lsb_release -d
```

Description: Ubuntu 10.10

```
 
uname -mr
```

2.6.35-22-generic i686

```

---

### Post by chili555 on 2011-06-02
Ahh! I wish they were all this easy. p54usb devices require firmware that is not installed by default. Can you hook up an ethernet cable and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet cable, reboot and post back to tell us how your wireless is working.

---

### Post by Rampo on 2011-06-03
> **chili555 said:**
> Ahh! I wish they were all this easy. p54usb devices require firmware that is not installed by default. Can you hook up an ethernet cable and open a terminal and do:```
sudo apt-get install linux-firmware-nonfree
```Detach the ethernet cable, reboot and post back to tell us how your wireless is working.
 
I tried this. The result was that my dongle could scan for networks, but it couldn't connect to one. It keeps trying to connect, but it fails to.
 
I even tried 
```

sudo modprobe -r p54usb
sudo modprobe p54usb

```
Same result...

---

### Post by chili555 on 2011-06-03
> It keeps trying to connect, but it fails to.Are there any clues here?```
sudo cat /var/log/syslog | grep -e p54 -e etwork
```Is your network WPA or WPA2 or the dreaded and tricky mixed WPA *and* WPA2 mode? Will it connect with a  static IP address? You can set a static IP by clicking the Network Manager icon, selecting edit connections, select wireless, edit and change DHCP to Manual. Fill in your details and save.

---

### Post by Rampo on 2011-06-03
> **chili555 said:**
> Are there any clues here?```
sudo cat /var/log/syslog | grep -e p54 -e etwork
```Is your network WPA or WPA2 or the dreaded and tricky mixed WPA *and* WPA2 mode? Will it connect with a static IP address? You can set a static IP by clicking the Network Manager icon, selecting edit connections, select wireless, edit and change DHCP to Manual. Fill in your details and save.
 
```

0) Stage 1 of 5 (Device Prepare) started...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): access point 'Auto Nojorono' has security, but secrets are required.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): connection 'Auto Nojorono' has security, and secrets exist.  No new secrets needed.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'ssid' value 'Nojorono'
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'scan_ssid' value '1'
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'psk' value '<omitted>'
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> Config: set interface ap_scan to 1
Jun  3 11:10:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun  3 11:10:12 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  3 11:10:22 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  3 11:10:22 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 11:10:52 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 11:11:11 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): association took too long.
Jun  3 11:11:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 11:11:11 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  3 11:11:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 11:11:26 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): connection 'Auto Nojorono' has security, and secrets exist.  No new secrets needed.
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'ssid' value 'Nojorono'
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'scan_ssid' value '1'
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'psk' value '<omitted>'
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 11:11:28 fredo-Latitude-D610 NetworkManager[532]: <info> Config: set interface ap_scan to 1
Jun  3 11:11:29 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 11:12:29 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): association took too long.
Jun  3 11:12:29 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 11:12:29 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  3 11:12:29 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 11:12:44 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): connection 'Auto Nojorono' has security, and secrets exist.  No new secrets needed.
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'ssid' value 'Nojorono'
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'scan_ssid' value '1'
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'psk' value '<omitted>'
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> Config: set interface ap_scan to 1
Jun  3 12:46:25 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 12:46:38 fredo-Latitude-D610 kernel: [ 6177.794692] usbcore: deregistering interface driver p54usb
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/ieee80211/phy0/rfkill0 disappeared
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): now unmanaged
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 1 (reason 36)
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): deactivating device (reason: 36).
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): cleaning up...
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun  3 12:46:38 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0)
Jun  3 12:46:45 fredo-Latitude-D610 kernel: [ 6184.644901] ieee80211 phy0: p54 detected a LM87 firmware
Jun  3 12:46:45 fredo-Latitude-D610 kernel: [ 6184.644910] p54: rx_mtu reduced from 3240 to 2384
Jun  3 12:46:46 fredo-Latitude-D610 kernel: [ 6185.767162] Registered led device: p54-phy0::assoc
Jun  3 12:46:46 fredo-Latitude-D610 kernel: [ 6185.767227] Registered led device: p54-phy0::tx
Jun  3 12:46:46 fredo-Latitude-D610 kernel: [ 6185.767288] Registered led device: p54-phy0::rx
Jun  3 12:46:46 fredo-Latitude-D610 kernel: [ 6185.767350] Registered led device: p54-phy0::radio
Jun  3 12:46:46 fredo-Latitude-D610 kernel: [ 6185.767439] usbcore: registered new interface driver p54usb
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> found WiFi radio killswitch rfkill1 (at /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/ieee80211/phy0/rfkill1) (driver <unknown>)
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): new 802.11 WiFi device (driver: 'p54usb' ifindex: 4)
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): now managed
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): bringing up device.
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): preparing device.
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): deactivating device (reason: 2).
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0)
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun  3 12:46:46 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) starting connection 'Auto Nojorono'
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): access point 'Auto Nojorono' has security, but secrets are required.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): connection 'Auto Nojorono' has security, and secrets exist.  No new secrets needed.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'ssid' value 'Nojorono'
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'scan_ssid' value '1'
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'psk' value '<omitted>'
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> Config: set interface ap_scan to 1
Jun  3 12:46:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun  3 12:46:48 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  3 12:46:58 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  3 12:46:58 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 12:46:58 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  3 12:47:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  3 12:47:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 12:47:28 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 12:47:47 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): association took too long.
Jun  3 12:47:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 12:47:47 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  3 12:47:47 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 12:48:02 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> radio killswitch /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/ieee80211/phy0/rfkill1 disappeared
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): now unmanaged
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 1 (reason 36)
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): deactivating device (reason: 36).
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): cleaning up...
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Jun  3 12:50:51 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-7/1-7:1.0/net/wlan0, iface: wlan0)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): carrier now ON (device state 2)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 2 -> 3 (reason 40)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) starting connection 'Auto eth0'
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 3 -> 4 (reason 0)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 4 -> 5 (reason 0)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 5 -> 7 (reason 0)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> dhclient started with pid 2119
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun  3 12:51:34 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   address 192.168.178.22
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   prefix 24 (255.255.255.0)
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   gateway 192.168.178.1
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   nameserver '192.168.178.1'
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   domain name 'fritz.box'
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Scheduling stage 5
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Done scheduling stage 5
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Jun  3 12:51:36 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 7 -> 8 (reason 0)
Jun  3 12:51:37 fredo-Latitude-D610 NetworkManager[532]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Jun  3 12:51:37 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) successful, device activated.
Jun  3 12:51:37 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Jun  3 14:35:15 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): carrier now OFF (device state 8, deferring action for 4 seconds)
Jun  3 14:35:19 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): device state change: 8 -> 2 (reason 40)
Jun  3 14:35:19 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): deactivating device (reason: 40).
Jun  3 14:35:19 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): canceled DHCP transaction, DHCP client pid 2119
Jun  3 16:21:06 fredo-Latitude-D610 kernel: [19046.470199] ieee80211 phy1: p54 detected a LM87 firmware
Jun  3 16:21:06 fredo-Latitude-D610 kernel: [19046.470204] p54: rx_mtu reduced from 3240 to 2384
Jun  3 16:21:07 fredo-Latitude-D610 kernel: [19047.499141] Registered led device: p54-phy1::assoc
Jun  3 16:21:07 fredo-Latitude-D610 kernel: [19047.499174] Registered led device: p54-phy1::tx
Jun  3 16:21:07 fredo-Latitude-D610 kernel: [19047.499205] Registered led device: p54-phy1::rx
Jun  3 16:21:07 fredo-Latitude-D610 kernel: [19047.499236] Registered led device: p54-phy1::radio
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> found WiFi radio killswitch rfkill2 (at /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/ieee80211/phy1/rfkill2) (driver <unknown>)
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0)
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): driver supports SSID scans (scan_capa 0x01).
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): new 802.11 WiFi device (driver: 'p54usb' ifindex: 6)
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/3
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): now managed
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 1 -> 2 (reason 2)
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): bringing up device.
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): preparing device.
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): deactivating device (reason: 2).
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant interface state:  starting -> ready
Jun  3 16:21:08 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 2 -> 3 (reason 42)
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) starting connection 'Auto Nojorono'
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): access point 'Auto Nojorono' has security, but secrets are required.
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 16:21:09 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 6 -> 4 (reason 0)
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0/wireless): connection 'Auto Nojorono' has security, and secrets exist.  No new secrets needed.
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'ssid' value 'Nojorono'
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'scan_ssid' value '1'
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Config: added 'psk' value '<omitted>'
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> Config: set interface ap_scan to 1
Jun  3 16:21:10 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  inactive -> scanning
Jun  3 16:21:11 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> associating
Jun  3 16:21:21 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  associating -> disconnected
Jun  3 16:21:21 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Jun  3 16:21:36 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.
Jun  3 16:22:10 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): association took too long.
Jun  3 16:22:10 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): device state change: 5 -> 6 (reason 0)
Jun  3 16:22:10 fredo-Latitude-D610 NetworkManager[532]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  3 16:22:10 fredo-Latitude-D610 NetworkManager[532]: <info> (wlan0): supplicant connection state:  scanning -> disconnected
Jun  3 16:22:25 fredo-Latitude-D610 NetworkManager[532]: <warn> (wlan0): link timed out.

```
 
This is the result of that command you gave me.
 
I am not sure what to fill in once I changed DHCP to manual..

---

### Post by chili555 on 2011-06-03
> <info> ([COLOR="Red"]eth0[/COLOR]): DHCPv4 state changed nbi -> preinit
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> (eth0): DHCPv4 state changed preinit -> bound
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info> Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   address 192.168.178.22
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   prefix 24 (255.255.255.0)
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   gateway 192.168.178.1
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   nameserver '192.168.178.1'
Jun  3 12:51:35 fredo-Latitude-D610 NetworkManager[532]: <info>   domain name 'fritz.box'So, it's busy activating and connecting your wired ethernet, when, in fact, Network Manager is designed to *disallow* a wireless connection if wired is available.  [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)> The computer should use the wired network connection when it's plugged in, but automatically switch to a wireless connection when the user unplugs it and walks away from the desk. Likewise, when the user plugs the computer back in, the computer should switch back to the wired connection. The user should, most times, not even notice that their connection has been managed for themCan you assure me that, at all times you were trying to get the wireless connected, that the ethernet cable was detached?> nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failedI have seen this a few times, but I don't think it's significant. My system connects perfectly on boot and puts out that message, too.> I am not sure what to fill in once I changed DHCP to manual..You might try address 192.168.178.30; netmask 255.255.255.0 and gateway 192.168.178.1. Be sure to also fill in your encryption details. Please try with the ethernet cable detached.

---

### Post by Rampo on 2011-06-03
> **chili555 said:**
> So, it's busy activating and connecting your wired ethernet, when, in fact, Network Manager is designed to *disallow* a wireless connection if wired is available. [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager)Can you assure me that, at all times you were trying to get the wireless connected, that the ethernet cable was detached?I have seen this a few times, but I don't think it's significant. My system connects perfectly on boot and puts out that message, too.You might try address 192.168.178.30; netmask 255.255.255.0 and gateway 192.168.178.1. Be sure to also fill in your encryption details. Please try with the ethernet cable detached.
 
The ethernet cable was detached when I was trying to get the wireless connected.
Ok, I will try what you suggested. Let's hope it works.

---

### Post by Rampo on 2011-06-03
I tried what you said. I filled in those details and tried to get it connected, but no luck unfortunately..

---

### Post by chili555 on 2011-06-03
Any clues here?```
sudo cat /var/log/syslog | grep -e p54 -e etwork
```Thanks.

---

### Post by Rampo on 2011-06-03
> **chili555 said:**
> Any clues here?```
sudo cat /var/log/syslog | grep -e p54 -e etwork
```Thanks.
 
Nope, no clues there.

---

### Post by chili555 on 2011-06-04
Please try an experiment for me. Edit Connections in Network Manager and double-check all settings you've entered, especially the encryption details. Next do:```
sudo rmmod -f p54common
sudo modprobe p54common nohwcrypt=1
```If the module doesn't unload cleanly, you may need to bring down the interface first:```
sudo ifconfig wlan0 down
sudo rmmod -f p54common
sudo modprobe p54common nohwcrypt=1
sudo ifconfig wlan0 up
```Does it connect? If so, we can write a conf file and make it permanent.

---

### Post by Rampo on 2011-06-06
After I used the command:
```
sudop rmmod -f p54common
```
 
It says:
```
ERROR: Removing 'p54common': Resource temporarily unavailable
```

---

### Post by Rampo on 2011-06-08
Could u still help me?

---

### Post by chili555 on 2011-06-08
Let's 'brute strength' it:```
sudo gedit /etc/modprobe.d/p54common.conf
```Add one line:```
options p54common nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot and tell us if the behavior is improved.

---

### Post by Rampo on 2011-06-14
> **chili555 said:**
> Let's 'brute strength' it:```
sudo gedit /etc/modprobe.d/p54common.conf
```Add one line:```
options p54common nohwcrypt=1
```Proofread carefully, save and close gedit. Reboot and tell us if the behavior is improved.
 
Unfortunately, no.... :( :(

---

### Post by chili555 on 2011-06-14
I'm sorry, I'm out of ideas.

---

### Post by Rampo on 2011-06-16
Someone else please?

---

