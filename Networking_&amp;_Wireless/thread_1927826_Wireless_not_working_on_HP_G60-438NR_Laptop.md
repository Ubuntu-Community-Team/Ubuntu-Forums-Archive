---
title: "Wireless not working on HP G60-438NR Laptop"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by spanishconnector on 2012-02-18
Hi, I installed Lubuntu 11.10 on my **HP G60-438NR** Laptop but can not get the wireless connection to work. It works fine with Vista, but when running Lubuntu the wireless light remains on but not working nor turns off when I press the wireless button.

Typing lspci -v from the terminal shows the following info about my wireless card:

[HTML]02:00.0 Ethernet controller: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) (rev 01)
	Subsystem: Hewlett-Packard Company AR5BXB63 (Foxconn) 802.11bg Mini PCIe NIC
	Physical Slot: 1
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at d2600000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k
[/HTML]

Please help. Thank you in advance.

---

### Post by praseodym on 2012-02-18
Please show additionally:

```
rfkill list
iwconfig
lsmod
```
For the driver ath5k the hardware encryption needs to be deactivated:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by spanishconnector on 2012-02-18
Thank you for your prompt response. Here is the additional output you asked me to get:

rfkill list
[HTML]0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes
[/HTML]

iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
[/HTML]

lsmod
[HTML]Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
arc4                   12473  2 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
uvcvideo               67271  0 
snd_hda_intel          24262  1 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
videodev               85626  1 uvcvideo
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393421  1 ath5k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
cfg80211              172427  3 ath5k,ath,mac80211
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  12 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i915                  509519  2 
wmi                    18744  1 hp_wmi
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0[/HTML]

For the other code you asked me to enter, I got some output too:

echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
[HTML]options ath5k nohwcrypt=1[/HTML]

sudo modprobe -rfv ath5k
[HTML]rmmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/ath/ath.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko[/HTML]

sudo modprobe -v ath5k
[HTML]insmod /lib/modules/3.0.0-16-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/ath/ath.ko 
insmod /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko nohwcrypt=1[/HTML]

I guess I have to reboot, will tell you if it worked. Thanks.

---

### Post by spanishconnector on 2012-02-18
I rebooted but still not working :(

I pressed the wireless button, but doesn't seem to be working yet.

I have read in some forums that one has to uncheck wireless card from a "blacklist" in a config file, do you or anyoune around know anything about that? I really like Lubuntu, just need the wireless to work. Please help!

Anyway, below is my current output (I think it's basically still the same).

rfkill list
[HTML]0: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
[/HTML]

iwconfig
[HTML]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on[/HTML]

lsmod
[HTML]Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  1 
snd_hda_codec          91859  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
arc4                   12473  2 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
uvcvideo               67271  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
videodev               85626  1 uvcvideo
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 145100  0 
wmi                    18744  1 hp_wmi
ath                    19387  1 ath5k
snd                    55902  12 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              393421  1 ath5k
i915                  509519  2 
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
psmouse                73673  0 
video                  18908  1 i915
cfg80211              172427  3 ath5k,ath,mac80211
serio_raw              12990  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0 [/HTML]

---

### Post by praseodym on 2012-02-19
Try:

```
sudo modprobe -rfv ath5k
sudo rmmod hp_wmi
sudo modprobe -v ath5k
```

---

