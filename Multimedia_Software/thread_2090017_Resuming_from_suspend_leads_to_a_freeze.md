---
title: "Resuming from suspend leads to a freeze"
date: 2012-11-30
forum: Multimedia Software
---

### Post by ldcdc on 2012-11-30
Most of the time resuming works fine (8-9 out of 10), but at times the laptop just crashes/freezes, with the fans going to full throttle (probably because of some program is using lots of CPU). 

I suspect it's the Catalyst video driver that's the cause, because now, with the latest driver, I get a bad video output. The open source driver resumed using only the external monitor, so that's a no go either, but it did not seem to cause the freeze. This all happens in Ubuntu 12.10. Ubuntu Precise did not have this "feature".

Suspend is such a basic feature, I really need to get to the bottom of this.

If there's any logs that would be of help, I'd be happy to provide them, assuming I can find/generate them.

---

### Post by gnusci on 2012-12-01
It can be because the amount of RAM.

---

### Post by 2F4U on 2012-12-01
> If there's any logs that would be of help, I'd be happy to provide them, assuming I can find/generate them.

There is a log dedicated to suspend at /var/log/pm-suspend.log.

---

### Post by ldcdc on 2012-12-01
> It can be because the amount of RAM.

I have 5.5GB of available RAM on this laptop, so, sadly, the solution is not that simple. :(

I'll look for those logs after I get one of those crashes.

---

### Post by ldcdc on 2012-12-01
> **2F4U said:**
> There is a log dedicated to suspend at /var/log/pm-suspend.log.

```
Sat Dec  1 15:31:22 EET 2012: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:

/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux ldcdc-HP-Pavilion-dv6-Notebook-PC 3.5.0-19-generic #30-Ubuntu SMP Tue Nov 13 17:48:01 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
Module                  Size  Used by
pci_stub               12622  1 
vboxpci                23157  0 
vboxnetadp             25670  0 
vboxnetflt             23442  0 
vboxdrv               287189  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  0 
ppdev                  17073  0 
binfmt_misc            17500  1 
dm_crypt               23011  0 
fglrx                5192155  155 
snd_hda_codec_idt      70209  1 
snd_hda_codec_hdmi     32007  1 
arc4                   12529  2 
snd_hda_intel          33491  4 
snd_hda_codec         134212  3 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel
brcmsmac              531848  0 
snd_hwdep              13602  1 snd_hda_codec
mac80211              539908  1 brcmsmac
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
brcmutil               14755  1 brcmsmac
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
kvm_amd                55604  0 
cfg80211              206566  2 brcmsmac,mac80211
snd_timer              29425  2 snd_pcm,snd_seq
kvm                   414070  1 kvm_amd
uvcvideo               76749  0 
joydev                 17457  0 
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
dm_multipath           22828  0 
option                 30008  0 
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
hp_accel               25976  0 
hp_wmi                 18048  0 
cordic                 12535  1 brcmsmac
rts_pstor             433804  0 
snd                    78734  18 snd_hda_codec_idt,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bcma                   35656  1 brcmsmac
psmouse                95552  0 
usb_wwan               20098  1 option
videobuf2_vmalloc      12860  1 uvcvideo
sparse_keymap          13890  1 hp_wmi
mac_hid                13205  0 
usbserial              42355  2 option,usb_wwan
cdc_acm                26935  0 
videobuf2_memops       13368  1 videobuf2_vmalloc
i2c_piix4              13167  0 
lis3lv02d              19829  1 hp_accel
k10temp                13126  0 
microcode              22803  0 
scsi_dh                14554  1 dm_multipath
amd_iommu_v2           19097  1 fglrx
serio_raw              13215  0 
lp                     17759  0 
input_polldev          13896  1 lis3lv02d
parport                46345  3 parport_pc,ppdev,lp
soundcore              15047  1 snd
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
usb_storage            48838  0 
btrfs                 761721  0 
zlib_deflate           26914  1 btrfs
libcrc32c              12644  1 btrfs
dm_raid45              76812  0 
xor                    17152  1 dm_raid45
dm_mirror              22028  0 
dm_region_hash         20806  1 dm_mirror
dm_log                 18529  3 dm_raid45,dm_mirror,dm_region_hash
vesafb                 13797  1 
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
wmi                    19070  1 hp_wmi
pata_atiixp            13204  0 
sdhci_pci              18616  0 
sdhci                  32645  1 sdhci_pci
r8169                  61650  0 
video                  19335  0 
             total       used       free     shared    buffers     cached
Mem:       5575536    3016820    2558716          0     173588    1170700
-/+ buffers/cache:    1672532    3903004
Swap:      7167996          0    7167996

/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:

/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:

/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend:
Having NetworkManager put all interaces to sleep...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:

/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:

/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 

/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:

/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:

/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
ATI Catalyst driver detected, not using quirks.

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:

/usr/lib/pm-utils/sleep.d/99video suspend suspend: disabled.
Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:

/etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
Sat Dec  1 15:31:22 EET 2012: performing suspend
fbcon fb0 state 1
fbcon fb0 state 0
Sat Dec  1 15:31:40 EET 2012: Awake.
Sat Dec  1 15:31:40 EET 2012: Running hooks for resume
Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:

/etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:

/usr/lib/pm-utils/sleep.d/99video resume suspend: disabled.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:

/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:

/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level	= 254

/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:

/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:

/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:

/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.

/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory

/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend:
Having NetworkManager wake interfaces back up...Failed.

/usr/lib/pm-utils/sleep.d/55NetworkManager resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:

/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:

/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:

/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:

/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:

/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:

/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Sat Dec  1 15:31:42 EET 2012: Finished.
```

It would appear that the resuming does finish. Something must be happening right after that though.

---

