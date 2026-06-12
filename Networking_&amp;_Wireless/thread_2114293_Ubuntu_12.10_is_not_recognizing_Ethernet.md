---
title: "Ubuntu 12.10 is not recognizing Ethernet"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by Soaroz on 2013-02-09
I just installed Ubuntu 12.10 today as a second OS beside Windows 7. I booted it expecting to be able to install Skype, Steam, all of my favorite programs, but instead get an error trying to connect to the ethernet. I have looked at other threads, but none of them helped. I have a desktop with a Gigabyte DS3H MB, integrated ethernet. No wi-fi. I know I need to put in certain terminal commands, which I would like to be specified which ones.

Thanks all.
-Soaroz

---

### Post by praseodym on 2013-02-09
Hi,

please show:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by Soaroz on 2013-02-10
> **praseodym said:**
> Hi,

please show:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
```

```

ross@ubuntu:~$ uname -a
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```

ross@ubuntu:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: Giga-byte Technology Device [1458:e000]
04:00.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev 41)
```

```

ross@ubuntu:~$ lsmod

Module                  Size  Used by

ath9k                 131308  0 

mac80211              539908  1 ath9k

snd_hda_codec_hdmi     32007  1 

parport_pc             32688  0 

ppdev                  17073  0 

rfcomm                 46619  0 

bnep                   18140  2 

bluetooth             209199  10 rfcomm,bnep

lp                     17759  0 

parport                46345  3 parport_pc,ppdev,lp

ath9k_common           14055  1 ath9k

ath9k_hw              395218  2 ath9k,ath9k_common

ath                    23827  3 ath9k,ath9k_common,ath9k_hw

coretemp               13400  0 

kvm                   414070  0 

ghash_clmulni_intel    13180  0 

aesni_intel            51037  0 

cryptd                 20403  2 ghash_clmulni_intel,aesni_intel

aes_x86_64             17208  1 aesni_intel

cfg80211              206566  3 ath9k,mac80211,ath

snd_hda_codec_realtek    77876  1 

snd_hda_intel          33491  5 

snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel

snd_hwdep              13602  1 snd_hda_codec

snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec

microcode              22803  0 

snd_seq_midi           13324  0 

snd_rawmidi            30512  1 snd_seq_midi

snd_seq_midi_event     14899  1 snd_seq_midi

snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event

snd_timer              29425  2 snd_pcm,snd_seq

snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq

joydev                 17457  0 

nouveau               895609  2 

ttm                    83595  1 nouveau

drm_kms_helper         46784  1 nouveau

drm                   275528  4 nouveau,ttm,drm_kms_helper

i2c_algo_bit           13413  1 nouveau

mxm_wmi                12979  1 nouveau

video                  19335  1 nouveau

wmi                    19070  2 nouveau,mxm_wmi

snd                    78734  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

mac_hid                13205  0 

psmouse                95552  0 

serio_raw              13215  0 

soundcore              15047  1 snd

lpc_ich                17061  0 

snd_page_alloc         18484  2 snd_hda_intel,snd_pcm

mei                    40690  0 

hid_generic            12493  0 

usbhid                 46947  0 

hid                   100366  2 hid_generic,usbhid
```

Hope this helps.

---

### Post by praseodym on 2013-02-10
Download these packages:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb)

Save them in "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
```
Reboot. Wired should work now. After that complete the installation:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```

---

### Post by Soaroz on 2013-02-10
> **praseodym said:**
> Download these packages:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23-generic_3.5.0-23.35_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-3.5.0-23_3.5.0-23.35_all.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-cw-3.6-quantal-generic_3.5.0.23.29_amd64.deb)

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-backports-modules-3.5.0/linux-backports-modules-cw-3.6-3.5.0-23-generic_3.5.0-23.9_amd64.deb)

Save them in "Downloads" and install them via:
```

sudo dpkg -i ~/Downloads/*.deb
```Reboot. Wired should work now. After that complete the installation:
```

sudo apt-get install --reinstall linux-headers-generic build-essential dkms
```

I downloaded the packages and it worked after a restart! Problem is, after restarting, my display didn't come as the native 1920x1080 that it automatically did before, nor does it recognize my mouse or keyboard. What did I do wrong?

---

### Post by praseodym on 2013-02-11
Try to reset the BIOS settings.

---

### Post by Soaroz on 2013-02-12
> **praseodym said:**
> Try to reset the BIOS settings.
I tried that, but it didn't work. I guess I could try one more time and report back. Any other suggestions?

Edit: I reset my BIOS the right way by taking out the little battery, and it still didn't fix.

---

### Post by Soaroz on 2013-02-17
Well, I did a fresh reinstall, except with 12.04 thinking that if I go with a LTS version, or just a different version at that, the ethernet would work. I replaced Windows 7 with it, and now I still don't have ethernet again. I am posting from a different computer, and am unable to get any kind of internet to my main computer. I have a USB flash drive that I can use if necessary.
Also, which codes do I need to put down again? It's the same exact computer. I tried installing the files  that you gave me, but since I do not have AMD, but Intel, it didn't work.

---

