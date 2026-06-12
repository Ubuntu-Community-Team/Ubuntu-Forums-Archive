---
title: "LCD brightness can not be changed"
date: 2013-05-25
forum: Multimedia Software
---

### Post by komatta on 2013-05-25
I installed ubuntu-12.04.2-dvd-amd64.iso into emachines E729Z, the note PC. E729Z has Pentium P6100 and Intel HD graphics.

  The install finished successfully, and I applied the latest updates. But LCD brightness can not be changed with X window system nor CUI console, while it can be changed POST and grub screen by the hotkeys, "Fn"+"<-" and "Fn"+"->". The bar appears, expands and contracts on X window system by the hotkeys, but actual brightness does not change. /sys/class/backlight/acpi_video0/brightness varies 0 to 9 by the hotkeys, but actual brightness does not change.

  How can I change LCD brightness on Ubuntu? Please help me.



```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```

```

$ lsmod
Module                  Size  Used by
btrfs                 781017  0 
zlib_deflate           27140  1 btrfs
libcrc32c              12645  1 btrfs
ufs                    75309  0 
qnx4                   13432  0 
hfsplus                89053  0 
hfs                    54783  0 
minix                  36416  0 
ntfs                  101959  0 
msdos                  17333  0 
jfs                   186683  0 
xfs                   852661  0 
reiserfs              249170  0 
ext2                   73799  0 
usblp                  18315  0 
dm_crypt               23126  1 
bnep                   18240  2 
rfcomm                 47562  0 
bluetooth             211812  10 bnep,rfcomm
parport_pc             32867  0 
ppdev                  17114  0 
arc4                   12530  2 
ath9k                 133095  0 
mac80211              555272  1 ath9k
uvcvideo               78117  0 
snd_hda_codec_realtek    79855  1 
videobuf2_core         33025  1 uvcvideo
videodev              125126  2 uvcvideo,videobuf2_core
snd_hda_intel          34063  3 
coretemp               13642  0 
videobuf2_vmalloc      12861  1 uvcvideo
ath9k_common           14054  1 ath9k
snd_hda_codec         135141  2 snd_hda_codec_realtek,snd_hda_intel
ath9k_hw              399752  2 ath9k,ath9k_common
videobuf2_memops       13405  1 videobuf2_vmalloc
ath                    24124  3 ath9k,ath9k_common,ath9k_hw
joydev                 17694  0 
psmouse               102075  0 
cfg80211              208382  3 ath9k,mac80211,ath
snd_hwdep              17765  1 snd_hda_codec
acer_wmi               32845  0 
serio_raw              13216  0 
snd_pcm                97523  2 snd_hda_intel,snd_hda_codec
sparse_keymap          13891  1 acer_wmi
intel_ips              18332  0 
microcode              23030  0 
snd_seq_midi           13325  0 
lpc_ich                17145  0 
snd_rawmidi            30750  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61931  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    83674  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15092  1 snd
snd_page_alloc         18573  2 snd_hda_intel,snd_pcm
mei                    41410  0 
mac_hid                13254  0 
lp                     17800  0 
parport                46563  3 parport_pc,ppdev,lp
ums_realtek            18257  0 
usb_storage            49288  1 ums_realtek
vesafb                 13846  0 
ahci                   25869  2 
libahci                27338  1 ahci
tg3                   156646  0 
i915                  530851  3 
drm_kms_helper         49259  1 i915
drm                   290344  4 i915,drm_kms_helper
i2c_algo_bit           13565  1 i915
mxm_wmi                13022  0 
video                  19653  2 acer_wmi,i915
wmi                    19257  2 acer_wmi,mxm_wmi
```

---

### Post by Toz on 2013-05-25
Hello and welcome to the forums.

Can you supply some more information?

1. The results of this command:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
```

2. The results of this command:
```
cat /proc/cmdline
```

3. The results of this command:
```
lspci  | grep VGA
```

Have you tried any kernel boot parameters? If not, I would suggest trying the **acpi_osi=Linux acpi_backlight=vendor** parameters. See the "Kernel Boot Parameters" link in my signature for more information on how.

---

### Post by komatta on 2013-05-28
"acpi_osi=Linux" solved the problem. Thank you very much.

---

### Post by Toz on 2013-05-28
Glad to hear it worked.
Can you mark this thread as solved by clicking on the "Edit" link in your first post, clicking on the "Go Advanced" link then changing the "Prefix" to "[SOLVED]"? This way, others can easily find this solution.

---

