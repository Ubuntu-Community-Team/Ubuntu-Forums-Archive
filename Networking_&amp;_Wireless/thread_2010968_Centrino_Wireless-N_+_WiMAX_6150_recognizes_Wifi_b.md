---
title: "Centrino Wireless-N + WiMAX 6150 recognizes Wifi but doesn't connect"
date: 2012-06-26
forum: Networking &amp; Wireless
---

### Post by 42th on 2012-06-26
So I've installed Ubuntu 12.04 LTS on my laptop that uses a Centrino Wireless-N + WiMAX 6150.  I try to connect to my college campus wifi, which it recognizes, but whenever I put in my login information, it attempts to connect for a while before it spits out the "Wireless Network Authentication Required" screen before it finally disconnects from the wireless.  It does this ad nauseum.  I am able to get a wired connection, which is what I am currently using right now.  

I did try to do my homework on this, which ultimately lead me here.  I've been to [http://intellinuxwireless.org/?n=Info](http://intellinuxwireless.org/?n=Info) to make sure my drivers up to date, and then I found out that since I'm using 12.04, all the drivers should have been up to date anyway.  I also found out that kernels later than 2.6.38 are broken with the Centrino Wireless-N + WiMAX 6150 wireless cards, but since this was a fresh install of Ubuntu and not an upgrade, I didn't think this was a feasible option and that it really apply to me.  So, I'm currently at a loss.

Also, after poking around the forums for a bit, here are my outputs of the following:

```

cat /etc/lsb-release; uname -a 
lspci -nnk | grep -iA2 net 
lsusb 
iwconfig 
rfkill list all 
lsmod

```My outputs: 
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux WLT 3.2.0-25-generic #40-Ubuntu SMP Wed May 23 20:30:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
    Subsystem: Intel Corporation Centrino Wireless-N + WiMAX 6150 BGN [8086:1305]
    Kernel driver in use: iwlwifi
--
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1851]
    Kernel driver in use: atl1c

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 8087:07d6 Intel Corp. 
Bus 001 Device 004: ID 13d3:5710 IMC Networks 

lo        no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no

Module                  Size  Used by
dm_crypt               23125  1 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
joydev                 17693  0 
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
asus_nb_wmi            12710  0 
asus_wmi               24456  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlwifi               332672  0 
mac80211              506816  1 iwlwifi
mac_hid                13253  0 
soundcore              15091  1 snd
psmouse                87692  0 
serio_raw              13211  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
mei                    41616  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
cfg80211              205544  2 iwlwifi,mac80211
v4l2_compat_ioctl32    17128  1 videodev
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
atl1c                  41717  0 
i915                  468745  4 
wmi                    19256  1 asus_wmi
drm_kms_helper         46978  1 i915
drm                   242038  5 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915


```Thank you greatly in advance!

---

### Post by 42th on 2012-06-27
Bump. I need some help please and thanks. :)

---

### Post by chili555 on 2012-06-27
Just to humor an old driver dawg, please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Any improvement? If so, we'll write a quick file to make it persistent.

---

### Post by wildmanne39 on 2012-06-27
Hi, I can tell you things that usually keeps that driver from connecting but it gets harder to fix certain issues when a college comes into play, because it may require changing router settings and such but we will start with the basics.

Does it connect at home?
Please do:
```
echo "blacklist asus_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
```
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
does it connect know? if not post the output of:
```
nm-tool
sudo cat /var/log/syslog | grep -e iwl -e firmware -e wpa -e wlan -e etork | tail -n55
```
Thanks

---

### Post by 42th on 2012-06-27
> **wildmanne39 said:**
> Hi, I can tell you things that usually keeps that driver from connecting but it gets harder to fix certain issues when a college comes into play, because it may require changing router settings and such but we will start with the basics.

Does it connect at home?


I'm apologize, I forgot to mention that I can't connect to any wireless.  I've tried with my home wifi, my friend's wifi, and my campus's wifi and had no such luck. 

> **wildmanne39 said:**
> 
Please do:
```
echo "blacklist asus_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
``````
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

When I did this:
```
sudo modprobe -v iwlwifi
```I got this error message:
```
insmod /lib/modules/3.2.0-25-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.2.0-25-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko lln_disable=1
FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```> **wildmanne39 said:**
> 
does it connect know? if not post the output of:
```
nm-tool
sudo cat /var/log/syslog | grep -e [ -e firmware -e wpa -e wlan -e etork | tail -n55
```Thanks


```

NetworkManager Tool

State: connected (global)

- Device: eth0  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        C8:60:00:4D:50:B9

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

Jun 26 13:39:48 WLT NetworkManager[854]: <info> (wlan0): bringing up device.
Jun 26 13:39:48 WLT NetworkManager[854]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 26 13:49:53 WLT NetworkManager[854]: <info> (wlan0): now unmanaged
Jun 26 13:49:53 WLT NetworkManager[854]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'sleeping') [20 10 37]
Jun 26 13:51:09 WLT kernel: [  626.396863] iwlwifi 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
Jun 26 13:51:09 WLT kernel: [  626.396901] iwlwifi 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xde800004)
Jun 26 13:51:09 WLT kernel: [  626.396909] iwlwifi 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
Jun 26 13:51:09 WLT kernel: [  626.396921] iwlwifi 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100006)
Jun 26 13:51:10 WLT NetworkManager[854]: <info> (wlan0): now managed
Jun 26 13:51:10 WLT NetworkManager[854]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 26 13:51:10 WLT NetworkManager[854]: <info> (wlan0): bringing up device.
Jun 26 13:51:10 WLT NetworkManager[854]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 27 16:36:47 WLT kernel: [   15.845484] iwlwifi 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Jun 27 16:36:47 WLT kernel: [   15.845497] iwlwifi 0000:02:00.0: setting latency timer to 64
Jun 27 16:36:47 WLT kernel: [   15.845703] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
Jun 27 16:36:47 WLT kernel: [   15.845706] iwlwifi 0000:02:00.0: pci_resource_base = ffffc900057bc000
Jun 27 16:36:47 WLT kernel: [   15.845708] iwlwifi 0000:02:00.0: HW Revision ID = 0x67
Jun 27 16:36:47 WLT kernel: [   15.845797] iwlwifi 0000:02:00.0: irq 52 for MSI/MSI-X
Jun 27 16:36:47 WLT kernel: [   15.845835] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
Jun 27 16:36:47 WLT kernel: [   15.846070] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
Jun 27 16:36:47 WLT kernel: [   15.856421] iwlwifi 0000:02:00.0: device EEPROM VER=0x557, CALIB=0x6
Jun 27 16:36:47 WLT kernel: [   15.856425] iwlwifi 0000:02:00.0: Device SKU: 0X150
Jun 27 16:36:47 WLT kernel: [   15.856427] iwlwifi 0000:02:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
Jun 27 16:36:47 WLT kernel: [   15.856578] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
Jun 27 16:36:47 WLT kernel: [   15.922400] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
Jun 27 16:36:47 WLT kernel: [   15.944693] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
Jun 27 16:36:47 WLT kernel: [   16.195544] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
Jun 27 16:36:47 WLT NetworkManager[862]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 27 16:36:47 WLT NetworkManager[862]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Jun 27 16:36:47 WLT NetworkManager[862]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): using nl80211 for WiFi device control
Jun 27 16:36:47 WLT NetworkManager[862]: <warn> (wlan0): driver supports Access Point (AP) mode
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): new 802.11 WiFi device (driver: 'iwlwifi' ifindex: 3)
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/0
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): now managed
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): bringing up device.
Jun 27 16:36:47 WLT NetworkManager[862]: <info> (wlan0): deactivating device (reason 'managed') [2]
Jun 27 16:36:47 WLT kernel: [   16.767952] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 27 16:58:49 WLT NetworkManager[862]:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/pci0000:00/0000:00:1c.1/0000:02:00.0/net/wlan0, iface: wlan0)
Jun 27 16:58:49 WLT NetworkManager[862]: <info> (wlan0): now unmanaged
Jun 27 16:58:49 WLT NetworkManager[862]: <info> (wlan0): device state change: unavailable -> unmanaged (reason 'removed') [20 10 36]
Jun 27 16:58:49 WLT kernel: [ 1336.399337] iwlwifi 0000:02:00.0: PCI INT A disabled
Jun 27 16:59:06 WLT kernel: [ 1353.565218] iwlwifi: Unknown parameter `lln_disable'
Jun 27 16:59:32 WLT kernel: [ 1378.881020] iwlwifi: Unknown parameter `lln_disable'
Jun 27 17:08:44 WLT kernel: [ 1930.078805]  <IRQ>  [<ffffffff810672af>] warn_slowpath_common+0x7f/0xc0
Jun 27 17:08:44 WLT kernel: [ 1930.078826]  [<ffffffff810673a6>] warn_slowpath_fmt+0x46/0x50
Jun 27 17:21:00 WLT NetworkManager[862]: <info> kernel firmware directory '/lib/firmware' changed
Jun 27 17:22:09 WLT kernel: [   17.001380] iwlwifi: Unknown parameter `lln_disable'
Jun 27 17:22:09 WLT kernel: [   17.292539] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
Jun 27 17:22:10 WLT NetworkManager[828]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 27 19:22:40 WLT kernel: [   15.906406] iwlwifi: Unknown parameter `lln_disable'
Jun 27 19:22:40 WLT kernel: [   16.191383] psmouse serio4: elantech: assuming hardware version 3 (with firmware version 0x450f01)
Jun 27 19:22:41 WLT NetworkManager[894]: <info> monitoring kernel firmware directory '/lib/firmware'.
Jun 27 19:42:38 WLT kernel: [ 1212.586899] iwlwifi: Unknown parameter `lln_disable'



```Thank you.

---

### Post by wildmanne39 on 2012-06-27
Hi, I did not see chili555 there when I posted we must have been posting at the same time, I will let him handle this since he was here first and he is the best at these issues.

---

### Post by chili555 on 2012-06-27
Haha! I'm not at all sure I know any more than the Wild Man. Please post:```
cat /etc/modprobe.d/iwlwifi.conf
```If it says anything different than:```
options iwlwifi 11n_disable=1
```...then you'll net to edit the file to make it so:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Amend, proofread and save. Close gedit. Now do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Any errors, warnings, smoke or sparks? Thanks.

---

### Post by 42th on 2012-06-27
Thank you both for your help. :D

> **chili555 said:**
> Haha! I'm not at all sure I know any more than the Wild Man. Please post:```
cat /etc/modprobe.d/iwlwifi.conf
```If it says anything different than:```
options iwlwifi 11n_disable=1
```...then you'll net to edit the file to make it so:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Amend, proofread and save. Close gedit. Now do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi
```Any errors, warnings, smoke or sparks? Thanks.

When I did this:

```
sudo modprobe iwlwifi
```I received the following error message:

```
FATAL: Error inserting iwlwifi (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by chili555 on 2012-06-28
> Unknown symbol in module, or unknown parameter (see dmesg)Let's see *dmesg* then:```
sudo modprobe iwlwifi
dmesg | grep iwl
```Thanks.

---

### Post by 42th on 2012-06-28
My iwlwifi.conf is correct now; '1' and 'l' look similar enough that I didn't notice any difference.  Sorry about that...

but I was able to successfully do:

```
sudo modprobe iwlwifi
```without any errors.

I'm currently testing on my home wifi now.  It recognizes my home wifi and attempts to connect. 
After the Wireless Network Authentication Required screen pops, I enter in my password and it tries to connect for a few minutes before the authentication screen pops up again.

---

### Post by chili555 on 2012-06-28
Let's see if there are any clues in:```
cat /var/log/syslog | grep etwork | tail -n20
```Also, I suspect you'll have better luck if your router is set to WPA2 only, not any mixed mode. Please see attached.

---

### Post by 42th on 2012-06-28
Here you go:
```
Jun 28 16:45:32 WLT NetworkManager[863]: <info> Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Jun 28 16:45:32 WLT NetworkManager[863]: <info> (eth0): DHCPv4 state changed nbi -> preinit
Jun 28 16:45:32 WLT NetworkManager[863]: <info> (eth0): DHCPv4 state changed preinit -> reboot
Jun 28 16:45:32 WLT NetworkManager[863]: <info>   address 192.168.0.100
Jun 28 16:45:32 WLT NetworkManager[863]: <info>   prefix 24 (255.255.255.0)
Jun 28 16:45:32 WLT NetworkManager[863]: <info>   gateway 192.168.0.1
Jun 28 16:45:32 WLT NetworkManager[863]: <info>   nameserver '192.168.0.1'
Jun 28 16:45:32 WLT NetworkManager[863]: <info>   domain name 'launchmodem.com'
Jun 28 16:45:32 WLT NetworkManager[863]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Jun 28 16:45:32 WLT NetworkManager[863]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) started...
Jun 28 16:45:33 WLT NetworkManager[863]: <info> DNS: starting dnsmasq...
Jun 28 16:45:33 WLT NetworkManager[863]: <info> (eth0): writing resolv.conf to /sbin/resolvconf
Jun 28 16:45:34 WLT NetworkManager[863]: <info> (eth0): device state change: ip-config -> activated (reason 'none') [70 100 0]
Jun 28 16:45:34 WLT NetworkManager[863]: <info> Policy set 'Auto Ethernet' (eth0) as default for IPv4 routing and DNS.
Jun 28 16:45:34 WLT NetworkManager[863]: <info> Activation (eth0) successful, device activated.
Jun 28 16:45:34 WLT NetworkManager[863]: <info> Activation (eth0) Stage 5 of 5 (IPv4 Commit) complete.
Jun 28 16:45:53 WLT NetworkManager[863]: <info> (eth0): IP6 addrconf timed out or failed.
Jun 28 16:45:53 WLT NetworkManager[863]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jun 28 16:45:53 WLT NetworkManager[863]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jun 28 16:45:53 WLT NetworkManager[863]: <info> Activation (eth0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
```

---

### Post by chili555 on 2012-06-28
We see eth0, that is, your wired ethernet, connecting perfectly. Please detach the ethernet cable, try to connect with wireless and try again.

---

### Post by 42th on 2012-06-28
I've tried it without the ethernet cable, and it is still not connecting.

I've redone the 
```
cat /var/log/syslog | grep etwork | tail -n20
```without ethernet cable and here's the results, if that'll help.

```
Jun 28 20:25:06 WLT NetworkManager[846]: <info> (wlan0): supplicant interface state: authenticating -> disconnected
Jun 28 20:25:06 WLT NetworkManager[846]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun 28 20:25:09 WLT NetworkManager[846]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun 28 20:25:09 WLT NetworkManager[846]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun 28 20:25:09 WLT NetworkManager[846]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0/wireless): connection 'HOMENET' has security, and secrets exist.  No new secrets needed.
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: added 'ssid' value 'HOMENET'
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: added 'scan_ssid' value '1'
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: added 'auth_alg' value 'OPEN'
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: added 'psk' value '<omitted>'
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun 28 20:25:09 WLT NetworkManager[846]: <info> Config: set interface ap_scan to 1
Jun 28 20:25:11 WLT NetworkManager[846]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun 28 20:25:11 WLT NetworkManager[846]: <info> (wlan0): supplicant interface state: scanning -> authenticating

```

---

### Post by chili555 on 2012-06-28
When you click the Network Manager icon and edit connections, is IPv6 set to Ignore? That seems to be a common Google hit searching for this mysterious listing:> get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failedIs your router reset to WPA2 only?

---

### Post by 42th on 2012-06-29
I, um, don't know how to edit my router. It was set up by someone else.

Also, the IPv6 is set to automatic; I've double checked.

---

### Post by chili555 on 2012-06-30
> Also, the IPv6 is set to automatic; I've double checked.I'm very sorry if I didn't make myself clear. I'm requesting that you set IPv6 to Ignore and *not* automatic.

---

### Post by 42th on 2012-06-30
Oh, sorry. 
I've set the IPv6 setting to ignore now, but it still won't connect.

---

### Post by chili555 on 2012-07-01
May I see:```
cat /sys/module/iwlwifi/parameters/11n_disable
```

---

### Post by 42th on 2012-07-01
Here you go: 
```
1
```

---

### Post by 42th on 2012-07-02
*bump*

---

### Post by chili555 on 2012-07-03
Let's try another driver parameter. Please do:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi swcrypto=1
```If this does not help and if you are unable or unwilling to change the router to WPA2 only, I have no further suggestions.

---

### Post by 42th on 2012-07-04
Sorry for the radio silence, but I've actually managed to track down two different unix admins at my college. 

After some tinkering, they changed my 
```
cat /etc/modprobe.d/iwlwifi.conf
```to read

```
options iwlwifi bt_coex_active=0
```and then they changed my network certificate, so now it works. 
I'm able to connect to wifi now.
They think that it was a combination of the iwlwifi.conf and the network certificate that was causing my issues.

Thank you so much for the help, chili555

---

### Post by chili555 on 2012-07-04
> and the *network certificate* that was causing my issues.
My suspicion as well. Glad it's working in any event.

---

### Post by jwx330 on 2012-11-25
I really hate to bump an old post, but I'm have the exact same problem as the poster here, but I'm not sure how to change the line of code below or how to change the network certificate...Can a noob get a bit of help?

> **42th said:**
> Sorry for the radio silence, but I've actually managed to track down two different unix admins at my college. 

After some tinkering, they changed my 
```
cat /etc/modprobe.d/iwlwifi.conf
```to read

```
options iwlwifi bt_coex_active=0
```and then they changed my network certificate, so now it works. 
I'm able to connect to wifi now.
They think that it was a combination of the iwlwifi.conf and the network certificate that was causing my issues.

Thank you so much for the help, chili555

---

### Post by chili555 on 2012-11-25
The network certificate is set by the usually corporate or university network you are trying to connect to. Is that what you need?

Do you have the same network card? What are your symptoms?

---

### Post by jwx330 on 2012-11-26
Yes, the same wireless card, with the same  symptoms. It will never connect, just keep popping up the screen where you put the network key in. 

This happens trying to access the network at my house. I haven't tried it anywhere else, but I'm pretty sure it would have the same symptoms.

---

### Post by chili555 on 2012-11-26
These will be experimental. They disappear on reboot. The purpose is to find the one driver parameter that works and then apply it to a conf file permanently. Please try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```As the eye doctor says, better, worse or the same? Next try:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi bt_coex_active=N
```Any change? Of course, you could try both:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1 bt_coex_active=N
```

---

### Post by jwx330 on 2012-11-27
I keep getting the following after the first line, I've tried with the wireless enabled and disabled...

```
kandj@kandj-U56E:~$ sudo modprobe -r iwlwifi
FATAL: Module iwlwifi is in use.
```

When I put the second line in, it just does the following.

```
kandj@kandj-U56E:~$ sudo modprobe iwlwifi 11n_disable=1 
kandj@kandj-U56E:~$ 
```

Am I doing something wrong?

---

### Post by chili555 on 2012-11-27
Please try:```
sudo ifconfig wlan0 down
sudo modprobe -r iwlwifi
```If there are no errors, proceed:```
sudo modprobe iwlwifi 11n_disable=1
sudo ifconfig wlan0 up
```Better?

---

### Post by cmacia06 on 2012-11-29
My issue with this card was that it would not reconnect to the network after suspending the laptop (authentication issue). I had tried to remove the module and insert it again with no luck (which used to work). After many attempt at a repair I googled my issue and stumbled onto this thread. I will report that the method the corrected my issue was running the command "sudo gedit /etc/modprobe.d/iwlwifi.conf" and adding "options iwlwifi bt_coex_active=0" to the file. Thank your network administrators for me. :) Now i can say I love to use Ubuntu with this laptop HP dv7 6135dx. It works PERFECTLY on 12.04.

---

### Post by jwx330 on 2012-11-30
Thank you guys so much, I am now posting this using wifi! After trying everything you said chili555 with no different results, I added```
options iwlwifi bt_coex_active=N
``` to the iwlwifi.conf then rebooted and it worked like a charm. 

Now, what did I do exactly? I'm doing my best to try and learn ubuntu, and I would like to have a better under standing of what the problems I run into are and what I do to fix them.

---

### Post by chili555 on 2012-11-30
I'm surprised it had no effect in post #27, but does now. We learn every day.

The parameter tells the driver we don't want bluetooth and wireless to co-exist, presumably running at the same time. How or why it helps, I don't know. If it works, I'll take it!

---

### Post by pauleskey on 2013-05-12
Thanks everyone for the effort on this. I have the same problem with an ASUS but I'm an absolute beginner and don't understand how I would apply this. What are the codes I'd type into the Terminal?

---

### Post by chili555 on 2013-05-13
> **pauleskey said:**
> Thanks everyone for the effort on this. I have the same problem with an ASUS but I'm an absolute beginner and don't understand how I would apply this. What are the codes I'd type into the Terminal?There are several posters here describing slightly different problems. Please tell us *your* exact problem. Open the terminal and run these commands and post the results:```
lspci -nn | grep 0280
uname -r 
arch
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by pauleskey on 2013-05-13
Sorry about being so vague. I have an ASUS U56E-bal7 on which I have installed 12.04 LTS Xubuntu. Post installation the computer detects the Netgear wireless router (but not 5g?) and automatically tries to connect and presents a password prompt. After entering the correct password, the prompt diappears but the connection is not made and the prompt repeats after a short interval. I would like to connect to the internet via wireless through the Netgear router (wndr3700). After some research including this thread I believe the answer is this:

 ```
Note: 'iwlagn' becomes 'iwlwifi' on kernel >=3.1
For those that did not read the upstream bug, the fix for this issue is to:

sudo modprobe -r iwlagn
sudo modprobe iwlagn bt_coex_active=0

To make the change permanent:
gksu gedit /etc/modprobe.d/iwl.conf

Copy/paste this line into the new file:
options iwlagn bt_coex_active=0

Save. Quit.
```

I entered the first two commands with iwlwifi and then the third. At that point the computer stated that a connection via the wireless had been made, but neither the browser nor Thunderbird were able to connect to the internet. I do not understand what the copy/paste command means.... 

The result of your first request is : 02:00.0 Network Controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev67)

The result of your second request is: 3.2.0-37-generic

The result of your third request is : i686

Thanks. I hope that is clearer?

---

### Post by pauleskey on 2013-05-13
I also think this is a solution, but I don't know enough to implement or understand:

```
@Dave using 12.04 I just did

options iwlwifi 11n_disable=1

/etc/modprobe.d/iwlwifi.conf

```

---

### Post by pauleskey on 2013-05-13
Okay got it to work temporarily with first two commands. I do not know how to use the following to make changes permanent:

```

To make the change permanent: gksu gedit /etc/modprobe.d/iwl.conf  Copy/paste this line into the new file: options iwlagn bt_coex_active=0  Save. Quit
```.

I think the gksu should be gsku?

---

### Post by chili555 on 2013-05-13
First, please do:```
gksudo gedit /etc/modprobe.d/iwl.conf
```Whatever is in there now, please change it to:```
options iwlwifi 11n_disable=1
```Proofread carefully, save and close gedit. Reboot.

Can you connect, surf the web, etc. now?

The driver iwlwifi is near to my heart; I am replying with mine right now. Some card/firmware/router combinations, like mine, work beautifully, even at N speeds. Some stubbornly refuse. I have been trying to work out the reasons and, if you wish, after we get you connected smoothly, we could look at router settings and try to restore N. I make no guarantees!

---

### Post by pauleskey on 2013-05-13
okay. One issue resolved. Gedit had not installed. I have installed it. I ran the first command and a dialog box came up with nothing in it. Should I insert the second command you gave?

---

### Post by chili555 on 2013-05-13
Yes, please. After you save and close, let's be certain there are no conflicting files around:```
ls /et/modprobe.d | grep iwl
```If you see nothing except the file you just wrote: iwl.conf, you are good to go. If there is anything else, tell me what it is.

---

### Post by pauleskey on 2013-05-13
done. but changed to /etc/modprobe.d | grep iwl. response was iwl.conf. The iwl was in bold.

---

### Post by pauleskey on 2013-05-13
rebooted and same issue: will not connect. 

Ran : ```
gksudo gedit /etc/modprobe.d/iwl.conf 
```

the following text was in box:

[CODE]options iwlwifi 11n_disable=1[CODE]


A question: should the gedit command have been [CODE] gksudo gedit /etc/modprobe.d/iwlwifi.conf [CODE] 

With the iwl.conf changed to iwlwifi.conf?

---

### Post by pauleskey on 2013-05-13
Thanks. Problem is resolved. I used gedit and pasted 

```
options iwlwifi bt_coex_active=0
```

Connects after numerous reboots and is a very fast connection. No unintended consequences as of yet. Please let me know if you think this may cause problems down the line.... Thanks again. I appreciate it.

---

### Post by chili555 on 2013-05-13
> changed to /etc/modprobe.d | grep iwl. response was iwl.conf. The iwl was in bold. Perfect!> A question: should the gedit command have been  gksudo gedit /etc/modprobe.d/iwlwifi.conf It makes no difference. The system reads the contents of the file and not the title, in this instance. The title simply makes it easier for us, the users, to find and understand.> Please let me know if you think this may cause problems down the lineNot at all. Whatever works!

Glad it's working.

---

### Post by zig2 on 2013-09-08
[SIZE=4]Hi all,
I have recently been looking over the information here and have found some information that will most likely solve this problem temporarily, but i need some assistance making this work on start up. Here is some code in which i typed in to make this whole wifi problem do the equivalent of restarting itself:[/SIZE]
```

sudo rmmod iwldvm
sudo rmmod iwlwifi
sudo modprobe iwlwifi bt_coex_active=0

```
[SIZE=4]This does the equivalent of restarting the wifi process, including the addition of some coding that chili555 wrote up. If someone could please post a method on how to make this automatically happen.

That is all I have for you today.

Good luck, and please reply with the method to automate this process.

Zig[/SIZE]

---

### Post by chili555 on 2013-09-08
Here ya go, Zig:```
sudo -i
echo "options iwlwifi bt_coex_active=0" >> /etc/modprobe.d/iwlwifi.conf
exit
```That's it.

---

### Post by Hector_J._Herrera on 2013-10-01
Hi all, I don't know if its okay to post on an old thread but since i'm having the same card and the same problem I thought I could do it.

I can't connect wireless, it does recognize the signal and i enter the key but does not connect.
I have read and tried all and every step you guys have given with no luck.

Am i doing something wrong? 

> doblehache@Hectoribio:~$ lspci -nn | grep 0280
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N + WiMAX 6150 [8086:0885] (rev 67)
doblehache@Hectoribio:~$ uname -r
3.8.0-31-generic
doblehache@Hectoribio:~$ arch
x86_64 


---

### Post by chili555 on 2013-10-01
> **Hector_J._Herrera said:**
> Hi all, I don't know if its okay to post on an old thread but since i'm having the same card and the same problem I thought I could do it.

I can't connect wireless, it does recognize the signal and i enter the key but does not connect.
I have read and tried all and every step you guys have given with no luck.

Am i doing something wrong?Let's see:```
cat /etc/modprobe.d/iwlwifi.conf
dmesg | grep -e iwl -e wlan
nm-tool
```

---

### Post by Hector_J._Herrera on 2013-10-01
Thanks, here you go: 

> doblehache@Hectoribio:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi bt_coex_active=0
options iwlwifi bt_coex_active=N
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1
doblehache@Hectoribio:~$ dmesg | grep -e iwl -e wlan
[    8.771592] iwlwifi 0000:02:00.0: irq 52 for MSI/MSI-X
[    8.902058] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[   10.365801] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   10.365806] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   10.365808] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   10.365810] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   10.365812] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   10.365815] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[   10.365877] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   10.572913] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.596580] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   15.596735] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   15.877736] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   15.877888] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.085708] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.086988] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 7094.229110] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[ 7094.229868] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[ 7094.436599] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
doblehache@Hectoribio:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 2] -------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             connected
  Default:           yes
  HW Address:        54:04:A6:45:92:EE

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.78
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlwifi
  State:             disconnected
  Default:           no
  HW Address:        40:25:C2:8C:E5:E4

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: wmx0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            i2400m_usb
  State:             unavailable
  Default:           no
  HW Address:        64:D4:DA:65:AD:CC

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

---

### Post by chili555 on 2013-10-02
> doblehache@Hectoribio:~$ cat /etc/modprobe.d/iwlwifi.conf
options iwlwifi bt_coex_active=0
options iwlwifi bt_coex_active=N
options iwlwifi bt_coex_active=0
options iwlwifi 11n_disable=1Wow! That's a busy file! Please do:```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the file to read:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Detach the ethernet, reboot and let us have your report, including:```
dmesg | grep iwl
rfkill list all
```Thanks.

---

### Post by Hector_J._Herrera on 2013-10-03
> **chili555 said:**
> Wow! That's a busy file!

Haha, my bad.

I still can't connect. Here's what i got:

> doblehache@Hectoribio:~$ dmesg | grep iwl
[    8.658792] iwlwifi 0000:02:00.0: irq 52 for MSI/MSI-X
[    8.701538] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[    8.933776] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    8.933777] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    8.933778] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    8.933779] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    8.933779] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    8.933781] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[    8.933844] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    9.111818] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.655905] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.656059] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.936825] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.936978] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   66.445217] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[   84.665694] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  109.769289] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[  206.112517] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
doblehache@Hectoribio:~$ rfkill list all
0: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-wimax: WiMAX
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: i2400m-usb:1-1.1:1.0: WiMAX
    Soft blocked: yes
    Hard blocked: no



---

### Post by chili555 on 2013-10-03
> [ 66.445217] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[ 84.665694] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[ 109.769289] iwlwifi 0000:02:00.0: fail to flush all tx fifo queues
[ 206.112517] iwlwifi 0000:02:00.0: fail to flush all tx fifo queuesInteresting! You seem to have gained a new problem.This awful message wasn't present in your earlier log. Let's try a fix and check the logs again. ```
gksudo gedit /etc/modprobe.d/iwlwifi.conf
```Change the file to read:
```
options iwlwifi 11n_disable=1 bt_coex_active=N
```Proofread, save and close gedit. Detach the ethernet, reboot and let us have your report, including:
```
dmesg | grep iwl
```If the tx fifo queues still appears, let's install the iwlwifi driver from kernel version 3.11. I suggest you download this to your desktop: [http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2](http://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.11-rc3/backports-3.11-rc3-1.tar.bz2) Right-click it and select 'Extract Here.' Now open a terminal and do:

```
cd Desktop/backports-3.11-rc3-1/
make defconfig-iwlwifi
make
sudo make install

```Reboot and, again, let us see:```
dmesg | grep iwl
```

---

### Post by Hector_J._Herrera on 2013-10-03
Still nothing :(

This is what i get after changing iwlwifi.conf and rebooting.
> doblehache@Hectoribio:~$ dmesg | grep iwl
[    8.427782] iwlwifi 0000:02:00.0: irq 51 for MSI/MSI-X
[    8.470601] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926
[    8.878234] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    8.878238] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    8.878239] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    8.878241] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[    8.878242] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[    8.878244] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[    8.878305] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    9.023332] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.535002] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.535156] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.817135] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.817286] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0

---

### Post by Hector_J._Herrera on 2013-10-05
Even if those *tx fifo queues* didn't appeared, and because i couldn't connect, I have installed the iwlwifi driver from the link you provided after ( i hope i haven't messed it up, but i had to try!)

I still can't connect

> doblehache@Hectoribio:~$ dmesg | grep iwl
[    9.241348] iwlwifi 0000:02:00.0: irq 52 for MSI/MSI-X
[    9.314904] iwlwifi 0000:02:00.0: loaded firmware version 41.28.5.1 build 33926 op_mode iwldvm
[    9.937790] iwlwifi 0000:02:00.0: CPTCFG_IWLWIFI_DEBUG enabled
[    9.937792] iwlwifi 0000:02:00.0: CPTCFG_IWLWIFI_DEBUGFS enabled
[    9.937793] iwlwifi 0000:02:00.0: CPTCFG_IWLWIFI_DEVICE_TRACING enabled
[    9.937794] iwlwifi 0000:02:00.0: CPTCFG_IWLWIFI_P2P enabled
[    9.937796] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Wireless-N + WiMAX 6150 BGN, REV=0x84
[    9.937828] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[    9.999026] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.480202] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.480357] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   16.608373] iwlwifi 0000:02:00.0: L1 Disabled; Enabling L0S
[   16.608527] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0

---

### Post by chili555 on 2013-10-06
Does it try? Are you asked for the WPA key? What is the result of:```
cat /var/log/syslog | grep -e wlan -e etwork | tail -n25
```

---

### Post by Hector_J._Herrera on 2013-10-07
Yes it tries but fails to authenticate. It keeps asking for the wep key. 

This is the result:

> doblehache@Hectoribio:~$ cat /var/log/syslog | grep -e wlan -e etwork | tail -n25Oct  7 16:27:42 Hectoribio kernel: [ 1236.529824] wlan0: deauthenticated from a4:b1:e9:91:dc:21 (Reason: 2)
Oct  7 16:27:42 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: 4-way handshake -> disconnected
Oct  7 16:27:42 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Oct  7 16:27:43 Hectoribio kernel: [ 1237.023941] wlan0: authenticate with a4:b1:e9:91:dc:21
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: scanning -> authenticating
Oct  7 16:27:43 Hectoribio kernel: [ 1237.029835] wlan0: send auth to a4:b1:e9:91:dc:21 (try 1/3)
Oct  7 16:27:43 Hectoribio kernel: [ 1237.032760] wlan0: authenticated
Oct  7 16:27:43 Hectoribio kernel: [ 1237.035465] wlan0: associate with a4:b1:e9:91:dc:21 (try 1/3)
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: authenticating -> associating
Oct  7 16:27:43 Hectoribio kernel: [ 1237.038826] wlan0: RX AssocResp from a4:b1:e9:91:dc:21 (capab=0x411 status=0 aid=6)
Oct  7 16:27:43 Hectoribio kernel: [ 1237.051487] wlan0: associated
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: associating -> associated
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <warn> Activation (wlan0/wireless): association took too long.
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <warn> Activation (wlan0/wireless): asking for new secrets
Oct  7 16:27:43 Hectoribio kernel: [ 1237.428463] wlan0: deauthenticating from a4:b1:e9:91:dc:21 by local choice (reason=3)
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <info> (wlan0): supplicant interface state: associated -> disconnected
Oct  7 16:27:43 Hectoribio NetworkManager[959]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <warn> No agents were available for this request.
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <warn> Activation (wlan0) failed for access point (INFINITUM91DC21)
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <info> Marking connection 'INFINITUM91DC21' invalid.
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <warn> Activation (wlan0) failed.
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Oct  7 16:27:49 Hectoribio NetworkManager[959]: <info> (wlan0): deactivating device (reason 'none') [0]

---

### Post by Hector_J._Herrera on 2013-10-22
Well... uhm, i upgraded to 13.10 and problem solved. Works great.

I guess I'll never know what happened.

Thanks anyways! I think i learnt a thing or two :)

---

### Post by jpedromacedosilva on 2013-11-02
Good evening chili555,

I'm having theses kind of issues on my Asus U32U.
My problem is that I don't also have wirless network on my Ubuntu 13.10: if I try to connect it says that my wifi is off because is turned off by a fisical switch.
If I try to press Fn + F3 (the key to switch wifi on/off) it turns on the bluetooth, and if I press once more the bluetooth turns off and it tries to turn the wifi on, but again I get the message that wifi turned off by a physical button.
I'm a newbie at Ubuntu/Linux and the solution to this problem is way beyond my knowledge, so I need your help.

Here are some of the my outputs:

pedro@asus-U32U:~$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath9k
  State:             unavailable
  Default:           no
  HW Address:        DC:85:DE:25:18:1C

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Conexão cabeada 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        50:46:5D:31:6F:57

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


pedro@asus-U32U:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 6320]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 14h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 PCI to PCI Bridge (rev 40)
00:15.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:15.1 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB700/SB800/SB900 PCI to PCI bridge (PCIE port 1)
00:15.2 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 2)
00:15.3 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] SB900 PCI to PCI bridge (PCIE port 3)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 12h/14h Processor Function 7
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
06:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
pedro@asus-U32U:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
pedro@asus-U32U:~$ cat /etc/modprobe.d/iwlwifi.conf
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211



Can you help, because I don't want to go back to Windows 8?

Best Regards.

---

### Post by varunendra on 2013-11-02
Welcome to the forums jpedromacedosilva ! :)
> **jpedromacedosilva said:**
> I'm having theses kind of issues on my **[COLOR="#FF0000"]Asus U32U[/COLOR]**.
....
....
```
0: **[COLOR="#FF0000"]phy0:[/COLOR]** Wireless LAN
    Soft blocked: no
    **[COLOR="#FF0000"]Hard blocked: yes[/COLOR]**
```
Please see this bug report : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)

The workaround : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

If it's not too much trouble for you, I'd request you to please add yourself to the list of "Affected" users on the bug report page. Thanks!

**PS:**
You should use 'Code' tags for posting terminal outputs. It preserves its formatting and makes the post cleaner, more readable. Please follow the "Using Code Tags" link in my signature to see a quice "HowTo" with screenshots. You'd like it. :)

---

### Post by jpedromacedosilva on 2013-11-03
Hello varunendra,

I can't thank you enough!!... The workaround works great, and now I have wifi network working on my Asus.
Sorry for not using 'Code' tags for posting terminal outputs. This was the first time I used the fórum and I was not aware of that.
Next time I sure use it.
Once again, thank you for helping me. You guys are the best.

Best regards

> **varunendra said:**
> Welcome to the forums jpedromacedosilva ! :)

Please see this bug report : [https://bugs.launchpad.net/bugs/1173681](https://bugs.launchpad.net/bugs/1173681)

The workaround : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

If it's not too much trouble for you, I'd request you to please add yourself to the list of "Affected" users on the bug report page. Thanks!

**PS:**
You should use 'Code' tags for posting terminal outputs. It preserves its formatting and makes the post cleaner, more readable. Please follow the "Using Code Tags" link in my signature to see a quice "HowTo" with screenshots. You'd like it. :)

---

### Post by varunendra on 2013-11-04
> **jpedromacedosilva said:**
> Hello varunendra,

I can't thank you enough!!... The workaround works great, and now I have wifi network working on my Asus.
Sorry for not using 'Code' tags for posting terminal outputs. This was the first time I used the fórum and I was not aware of that.
Next time I sure use it.
Once again, thank you for helping me. You guys are the best.

Best regards

You're welcome, and no worries about the code tags.

It seems partly funny and partly embarrassing that I am getting the compliments while the original pioneer of the solution (the dangerous "saw" wielding man, 3 posts above your 1st one ;)) is probably just smiling at all these 'thankful' comments I'm getting. :P

Oh, by the way, thanks for adding your comment at the bug report page. I also hope it was you who added as the 11th user in the "Affect users" list. :)

---

### Post by chili555 on 2013-11-04
>  probably just smiling at all these 'thankful' comments I'm getting.I am smiling indeed! I am smiling because all those tips and tricks I stole many years ago are now being stolen by a great group of people whose interests are not pride or ego, but getting another happy Ubuntu user up and running!

Glad it's working!

---

### Post by jpedromacedosilva on 2013-11-04
I finished saying "Thank you guys"... And here I was including chili555.
And this is indeed a great group of people!
Once again, thanks to both of you for helping me. Finally I am able to run Ubuntu on this latop/netbook without no problems (I just need to tweak the plymouth resolution, because since I installed the ATI proprietary the plymouth is showing in a low resolution, and none of the solutions I found worked).

Best regards.

> **chili555 said:**
> I am smiling indeed! I am smiling because all those tips and tricks I stole many years ago are now being stolen by a great group of people that whose interests are not pride or ego, but getting another happy Ubuntu user up and running!

Glad it's working!

---

