---
title: "Some wireless networks not visible on Ubuntu 11.10"
date: 2012-03-13
forum: Networking &amp; Wireless
---

### Post by xkcdcode on 2012-03-13
I am using Ubuntu 11.10 on a dual-boot Dell Inspiron 1564 laptop (with Windows 7). It has the Broadcom wlan card, for which I have installed the appropriate firmware from the "restricted" repo. It is detecting and connecting to my home WiFi network but at work, it is not even showing the ssid of my work WiFi network. The same work ssid is visible and connectable from the Win 7 on the same laptop :confused: ..... very very strange right? I've tried the ```
iwlist scanning
``` command from the command-line and I can see a lot of other WiFi hotspots but a few are missing which I know are there :o

Has anyone else encountered this issue? How can I resolve this, because I've to do all my development work on Linux. Thanks in advance for any clues to this mystery.

---

### Post by praseodym on 2012-03-13
Which channels are missing? 12 and 13? Maybe its a bug from the driver. Please show
> 
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list

---

### Post by xkcdcode on 2012-03-13
> **praseodym said:**
> Which channels are missing? 12 and 13? Maybe its a bug from the driver. Please show

Well the whole ssid I am looking for is missing ... maybe I understood you wrong ... the output of the commands you mentioned are below:-

```
# lspci -nnk | grep -iA2 net

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Dell Device [1028:0434]
	Kernel driver in use: r8169
```

```
# lsmod
Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
btusb                  18600  0 
bluetooth             166112  11 bnep,rfcomm,btusb
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_realtek   330815  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_hda_intel          33390  2 
joydev                 17693  0 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
wmi                    19256  1 dell_wmi
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    68266  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
lib80211_crypt_tkip    17390  0 
i915                  571251  7 
psmouse                73882  0 
serio_raw              13166  0 
wl                   2568210  0 
intel_ips              18089  0 
drm_kms_helper         42558  1 i915
drm                   236290  3 i915,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
lib80211               14991  2 lib80211_crypt_tkip,wl
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47198  0 
hid                    95463  1 usbhid
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
r8169                  52788  0 
ahci                   26002  2 
libahci                26861  1 ahci

```

```
# iwconfig

eth2      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
# rfkill list


0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

---

### Post by praseodym on 2012-03-14
Deactivate the Broadcom-driver. After that uninstall it, and install the needed firmware for the native b43 driver, it works better from 11.04 and on:

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo depmod -a
wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
sudo modprobe b43
```

---

