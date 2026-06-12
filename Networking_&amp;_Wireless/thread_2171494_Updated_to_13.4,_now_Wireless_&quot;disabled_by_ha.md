---
title: "Updated to 13.4, now Wireless &quot;disabled by hardwire switch&quot;"
date: 2013-08-31
forum: Networking &amp; Wireless
---

### Post by pat6 on 2013-08-31
Searched all over the forums and no solutions worked.

My first-ever Linux system.  Brand new ASUS 1015E, shipped with 12.4.  Upgraded via wireless to 12.11, no problems.  Upgraded then to 13.4, and upon restart, wifi is disabled.  Network pulldown says "wi-fi is disabled by hardware switch"

There is no hardwire switch - I confirmed that after an hour plus on ASUS chat support.
I've done Fn+F2 multiple times over - no fix.

rfkill list:
0: asus-wlan: Wireless LAN
  Soft blocked: no
  Hard blocked: no

1: phy0: Wireless LAN
  Soft blocked: no
  Hard blocked: yes

Have run rfkill unblock all.  No effect.  If I run rfkill block all, it toggles the soft blocks to "yes" and hard blocked on 1: phy0 to "off."  Toggle again, and it goes back to what it says above.  No worky.

I rebooted several times.  Rebooted with F2 depressed, reset to default, saved, and restarted - still doesn't work.

Any ideas?  I'm about to send this thing back.

---

### Post by praseodym on 2013-08-31
Please show
```

lsmod
```

---

### Post by pat6 on 2013-08-31
lsmod:

greek2us@greek2us-1015E:~$ lsmod
Module                  Size  Used by
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228667  10 bnep,rfcomm
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_realtek    78399  1 
arc4                   12615  2 
joydev                 17377  0 
brcmsmac              550698  0 
coretemp               13355  0 
cordic                 12574  1 brcmsmac
kvm_intel             132891  0 
brcmutil               14755  1 brcmsmac
kvm                   443165  1 kvm_intel
mac80211              606457  1 brcmsmac
ghash_clmulni_intel    13259  0 
cryptd                 20373  1 ghash_clmulni_intel
cfg80211              510937  2 brcmsmac,mac80211
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
videodev              129260  2 uvcvideo,videobuf2_core
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
microcode              22881  0 
i915                  600396  3 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
drm_kms_helper         49394  1 i915
mac_hid                13205  0 
snd                    68876  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
drm                   286028  4 i915,drm_kms_helper
alx                    67960  0 
asus_nb_wmi            12854  0 
psmouse                95905  0 
asus_wmi               24213  1 asus_nb_wmi
sparse_keymap          13890  1 asus_wmi
wmi                    19070  1 asus_wmi
mdio                   13807  1 alx
bcma                   41051  1 brcmsmac
mei                    41158  0 
lpc_ich                17061  0 
soundcore              12680  1 snd
video                  19390  2 i915,asus_wmi
serio_raw              13215  0 
i2c_algo_bit           13413  1 i915
lp                     17759  0 
parport                46345  3 lp,ppdev,parport_pc
ahci                   25731  3 
libahci                31364  1 ahci

---

### Post by pat6 on 2013-08-31
...and if it helps, now when I suspend, it immediately wakes up again with no inputs whatsoever from me.  /crazy

---

### Post by praseodym on 2013-08-31
Please try:
```

sudo modprobe -v asus-laptop wireless=1
```

---

### Post by pat6 on 2013-09-01
It says: insmod /lib/modules/3.8.0-29-generic/kernel/drivers/input/input-polldev.ko 
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/platform/x86/asus-laptop.ko wireless=1
ERROR: could not insert 'asus_laptop': Invalid argument

---

### Post by praseodym on 2013-09-01
Check:
```

modinfo asus-laptop
``````

sudo modprobe -v asus-laptop wlan_status=1
```

---

### Post by pat6 on 2013-09-01
~$ modinfo asus-laptop
filename:       /lib/modules/3.8.0-29-generic/kernel/drivers/platform/x86/asus-laptop.ko
license:        GPL
description:    Asus Laptop Support
author:         Julien Lerouge, Karol Kozimor, Corentin Chary
srcversion:     2D58DD15A1809C7DD5FBF45
alias:          acpi*:ATK0101:*
alias:          acpi*:ATK0100:*
depends:        sparse-keymap,input-polldev
intree:         Y
vermagic:       3.8.0-29-generic SMP mod_unload modversions 
parm:           wapf:WAPF value (uint)
parm:           wled_type:Set the wled type on boot (unknown, led or rfkill). default is unknown (charp)
parm:           bled_type:Set the bled type on boot (unknown, led or rfkill). default is unknown (charp)
parm:           wlan_status:Set the wireless status on boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1 (int)
parm:           bluetooth_status:Set the wireless status on boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1 (int)
parm:           wimax_status:Set the wireless status on boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1 (int)
parm:           wwan_status:Set the wireless status on boot (0 = disabled, 1 = enabled, -1 = don't do anything). default is -1 (int)
parm:           als_status:Set the ALS status on boot (0 = disabled, 1 = enabled). default is 0 (int)

---

### Post by pat6 on 2013-09-01
sudo modprobe -v asus-laptop wlan_status=1
insmod /lib/modules/3.8.0-29-generic/kernel/drivers/platform/x86/asus-laptop.ko wlan_status=1
ERROR: could not insert 'asus_laptop': No such device

Thanks so much for continuing to help me figure this thing out.

---

### Post by praseodym on 2013-09-01
What about:
```

sudo rmmod asus_wmi
sudo rfkill unblock all
```

---

### Post by pat6 on 2013-09-01
Yeah, thanks, but nogo on those either.  So... I did a "F9 reboot" and restored the system to orginal configuration (12.04).  I hadn't done anything except set up Thunderbird, so no major loss of data.  Will wait until 13.11 is a bit more worked out.

Everything works well now.

Thanks again for all the help... it was a valiant effort!
Pat

---

### Post by Jan_Guth on 2014-03-08
I found a workaround for me.

Apparently if I restart my notebook the hardware switch is turned on. (couldn't find another solution)
And if I go to sleep (fn + f1) and back again wifi works like a charm.

Wired.

Asus 1015e / Ubuntu 12.04 - latest updates.

---

