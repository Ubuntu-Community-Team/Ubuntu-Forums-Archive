---
title: "Wireless Connection on 11.10 not working despite trying everything"
date: 2012-02-25
forum: Networking &amp; Wireless
---

### Post by lossman29 on 2012-02-25
So, I installed Ubuntu 11.10 a few days back and seem to have a serious problem with the wireless connection. I have browsed around the forums and tried a lot of stuff but nothing seems to be working. The wired connection is working fine and gives me speeds of 50mbps. The wireless however gives me Bits/s most of the time. Seems to me like packets are being dropped when I connect the wireless. I have currently disabled my broadcom driver. 

Should I activate the driver again?

Any help would be greatly appreciated.

---

### Post by praseodym on 2012-02-25
Please show the terminal (CTRL+ALT+T) outputs of

```
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by lossman29 on 2012-02-25
Here's the output:

```
06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0510]
	Kernel driver in use: brcmsmac
--
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
	Subsystem: Lenovo Device [17aa:392e]
	Kernel driver in use: r8169

```

```

Module                  Size  Used by
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  4 
bcma                   20219  0 
arc4                   12529  2 
joydev                 17693  0 
snd_hda_codec_conexant    62197  1 
nvidia              11713772  43 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_seq_midi           13324  0 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_rawmidi            30547  1 snd_seq_midi
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ideapad_laptop         13871  0 
sparse_keymap          13890  1 ideapad_laptop
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19412  0 
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
wmi                    19256  0 
psmouse                73882  0 
serio_raw              13166  0 
brcmsmac              631693  0 
brcmutil               17837  1 brcmsmac
mac80211              462046  1 brcmsmac
mei                    41480  0 
cfg80211              199630  2 brcmsmac,mac80211
crc_ccitt              12667  1 brcmsmac
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
ums_realtek            13272  0 
usb_storage            57901  1 ums_realtek
uas                    18027  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
ahci                   26002  4 
libahci                26861  1 ahci
r8169                  52788  0 
```


```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"sMobileNet"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:CA:5C:E8:C0   
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0
```

```
: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by praseodym on 2012-02-25
Hi,

activate the "Broadcom-STA"-driver via "additional drivers". After that open the following file:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
and add the following three new lines:

```
blacklist bcma
blacklist brcmsmac
blacklist brcm80211
```
Save, close the editor, and reboot.

---

### Post by lossman29 on 2012-02-27
Thanks. Problem seems to have been solved.

---

