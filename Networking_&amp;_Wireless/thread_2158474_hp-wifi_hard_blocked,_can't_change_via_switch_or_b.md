---
title: "hp-wifi hard blocked, can't change via switch or bios"
date: 2013-06-29
forum: Networking &amp; Wireless
---

### Post by fginther on 2013-06-29
I have a hard blocked wifi on an HP dv6 laptop (dv6-7014nr) and as a result am unable to use wireless networking:

```
$ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: yes
10: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```
My wireless switch is currently on according to the LED. Toggling it will hard block/unblock the brcmwl-0 wireless device and remove/restore the hci0: bluetooth device, so it is doing something. My BOIS has no settings to manually enable or disable the wifi device. I've also tried restoring my BIOS defaults with no success.

```
$ rfkill unblock all
```

has no effect.

This all started when I tried to disable the bluetooth device via the indicator (while running saucy), all had been working will prior to that. I've since reverted back to raring to try and resolve this. I've even tried the quantal BCM4313 driver.

I've also tried using a USB wifi device (netgear) which shows up under the network indicator as turned off by hardware switch as well. How is it that I can't even add a working device?

Here's the internal wifi info and driver:

```
$ sudo lspci |grep LAN
0a:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
```

```
$ lsmod
Module                  Size  Used by
btusb                  22474  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  12 
bnep                   18036  2 
bluetooth             228619  22 bnep,btusb,rfcomm
dm_crypt               22820  1 
arc4                   12615  0 
rtl8187                60848  0 
mac80211              606411  1 rtl8187
cfg80211              510937  2 mac80211,rtl8187
eeprom_93cx6           13344  1 rtl8187
joydev                 17377  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
coretemp               13355  0 
kvm                   443165  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_hdmi     36913  1 
lib80211_crypt_tkip    17379  0 
snd_hda_codec_idt      70256  1 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
microcode              22881  0 
snd_rawmidi            30180  1 snd_seq_midi
psmouse                95870  0 
serio_raw              13215  0 
rtsx_pci_ms            13011  0 
memstick               16554  1 rtsx_pci_ms
wl                   2573614  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
lib80211               14352  2 wl,lib80211_crypt_tkip
lpc_ich                17061  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
mei                    41158  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
hp_accel               26012  0 
lis3lv02d              20111  1 hp_accel
input_polldev          13896  1 lis3lv02d
mac_hid                13205  0 
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17475  0 
nouveau               939088  1 
i915                  600351  3 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  325 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  4 ghash_clmulni_intel,aesni_intel,ablk_helper
mxm_wmi                13021  1 nouveau
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
ttm                    83187  1 nouveau
i2c_algo_bit           13413  2 i915,nouveau
r8169                  67446  0 
ahci                   25731  3 
libahci                31364  1 ahci
drm_kms_helper         49394  2 i915,nouveau
drm                   286313  7 ttm,i915,drm_kms_helper,nouveau
video                  19390  2 i915,nouveau
wmi                    19070  3 hp_wmi,mxm_wmi,nouveau
```

Is this just an HP hardware bug and I'm just boned?
Thanks.

---

### Post by fginther on 2013-06-29
Ok. It's working now. I did a suspend/resume by closing the lid and when it resumed, everything was unblocked. \o/

Hopefully this will help someone else in the future.

---

