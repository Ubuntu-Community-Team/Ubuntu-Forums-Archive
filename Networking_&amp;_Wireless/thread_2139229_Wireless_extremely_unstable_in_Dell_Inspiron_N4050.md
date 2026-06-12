---
title: "Wireless extremely unstable in Dell Inspiron N4050"
date: 2013-04-26
forum: Networking &amp; Wireless
---

### Post by silfalqueto on 2013-04-26
Hi there,

I'm having trouble from a long time with my wireless on my notebook, and I don't know what do to. Briefly, this is my case:

-I bought this notebook (Dell Inspiron N4050) with Ubuntu, and changed to Kubuntu later. Also it has dual boot for Windows Vista, wich I rarely use
-It takes a lot of trials on Wicd to connect, even if the wireless signal is strong
-After a lot of trials, when it finally connects, then the connection falls when I try to open the first page on a browser. So I try to connect
 again and then the connection is stable.
-But yesterday, updating the distro, I just can't connect, unless I wire it. After many attempts to connect, the connection is extremely unstable and will fall on the  first first page opening, as before, but now, I can't get a stable connection after this.

I'm not good with Terminal, but I can copy and paste stuff there and follow instructions if anyone can help me. 

thanks in advance

silvia

---

### Post by Kopkins on 2013-04-26
Please post output of ```
lspci | grep -i net
``` 

```
rfkill list
```

```
lsmod
```

Please post the results in [noparse]```

``` tags. [/noparse]

Thanks,

Kopkins

---

### Post by holycow131415 on 2013-04-26
I would advise you to boot into vista to try to surf the net, etc, to eliminate that your wireless card may be dying.

---

### Post by silfalqueto on 2013-05-11
```
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
09:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

```
0: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no
1: phy0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
```

```
Module                  Size  Used by
bnep                   18036  2 
parport_pc             28152  0 
rfcomm                 42641  16 
ppdev                  17073  0 
arc4                   12615  2 
ath9k                 149924  0 
joydev                 17377  0 
coretemp               13355  0 
ath9k_common           14055  1 ath9k
kvm_intel             132891  0 
ath9k_hw              413680  2 ath9k_common,ath9k
snd_hda_codec_hdmi     36913  1 
kvm                   443165  1 kvm_intel
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              606457  1 ath9k
snd_hda_codec_idt      70256  1 
ghash_clmulni_intel    13259  0 
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
aesni_intel            55399  1 
snd_hwdep              13602  1 snd_hda_codec
cfg80211              510937  3 ath,ath9k,mac80211
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ablk_helper            13597  1 aesni_intel
mei                    41158  0 
psmouse                95870  0 
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
dell_laptop            17369  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
dell_wmi               12681  0 
lpc_ich                17061  0 
sparse_keymap          13890  1 dell_wmi
dcdbas                 14397  1 dell_laptop
serio_raw              13215  0 
lp                     17759  0 
btusb                  22474  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
microcode              22881  0 
soundcore              12680  1 snd
bluetooth             228619  22 bnep,btusb,rfcomm
parport                46345  3 lp,ppdev,parport_pc
mac_hid                13205  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
i915                  600351  3 
i2c_algo_bit           13413  1 i915
wmi                    19070  1 dell_wmi
video                  19390  1 i915
drm_kms_helper         49394  1 i915
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  2 
libahci                31364  1 ahci
r8169                  67446  0

```
sorry or the delay, I moved to wired connection and forgot this tread #shame
But I had other problems with my connection, that is too slow by now. I don't have windows anymore, I did a fresh install of Kubuntu today,
and erased it. Wifi seems to be ok now. We tried to use wicd, but it didnt work. I'm using another stuff that I believe is native on kubuntu. 
now my problem is internet speed, it is slow even on wired connection. Should I post another thread?

thanks a lot for your help!

s

---

### Post by wildmanne39 on 2013-05-11
*Thread moved to **Networking & Wireless**.*

---

