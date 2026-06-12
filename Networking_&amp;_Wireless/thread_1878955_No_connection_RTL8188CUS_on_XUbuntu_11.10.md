---
title: "No connection RTL8188CUS on XUbuntu 11.10"
date: 2011-11-10
forum: Networking &amp; Wireless
---

### Post by dimoftheyard on 2011-11-10
Hello forum.

I had wireless working on XUbuntu 10.10 with the internal wireless card of my netbook (broadcom BCM4313 according to NetworkManager). After a while this stopped working due to what seems to be a bios bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577114)), so a bought a EDIMAX EW-7811UN usb wireless adapter with a Realtek RTL8188CUS chip. It did work on 10.10 with the linux driver that came with the stick, but the network was unstable, and the system froze occasionally. So I decided to update to 11.10 where a driver for this adapter was said to be in the kernel (I did uninstall the old driver before the update).
Now my system detects the wireless adapter, but it cannot connect. NetworkManager says "wireless is disabled by hardware switch", but rfkill says it's only "soft blocked"

```
0: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: yes
3: phy1: Wireless LAN
	Soft blocked: yes
	Hard blocked: no

```

lsusb
```
Bus 001 Device 005: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]

```

nmcli nm status
```
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN      
running         disconnected    disabled        disabled   enabled         disabled

```

uname
```
3.0.0-12-generic
```

lsmod
```
Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55577  1 vfat
bnep                   17923  2 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38408  4 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  2 
joydev                 17393  0 
rtl8192cu              97651  0 
rtl8192c_common        69519  1 rtl8192cu
snd_hda_codec_realtek   254125  1 
rtlwifi                95614  1 rtl8192cu
binfmt_misc            17292  1 
mac80211              272785  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              172392  2 rtlwifi,mac80211
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd_hda_intel          24262  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
bcma                   19571  0 
i915                  505108  2 
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         32889  1 i915
drm                   192226  3 i915,drm_kms_helper
ideapad_laptop         13575  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
sparse_keymap          13658  1 ideapad_laptop
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
snd                    55902  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  3 
libahci                25727  1 ahci
r8169                  43104  0 
ums_realtek            13096  0 
usb_storage            44173  2 ums_realtek
uas                    17699  0 

```

This is after I blacklisted brcmsmac and brcmutil, because I feared that the two cards might somehow affect each other.
Thanks in advance

---

### Post by dimoftheyard on 2011-11-19
I followed the steps on [http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/]("http://www.r-statistics.com/2011/11/edimax-ew-7811un-usb-wireless-connecting-to-a-network-on-ubuntu-11-10/"), and now everything works fine.

---

