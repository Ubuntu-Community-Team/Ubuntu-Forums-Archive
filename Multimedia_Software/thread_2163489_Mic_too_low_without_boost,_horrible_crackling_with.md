---
title: "Mic too low without boost, horrible crackling with boost"
date: 2013-07-18
forum: Multimedia Software
---

### Post by Thee on 2013-07-18
So this has been driving me crazy, I can't have a normal conversation over Skype when I turn the Mic boost off because its so quiet that my voice can barely be heard, and when I turn up the Mic boost, its then loud and good, but then crackling and popping sound can be heard when ever I speak. This is not limited to Skype ofc, it's the same in any application.

My sound card is Realtek ALC892, using Ubuntu 13.04.

I attached my current ALSA mixer settings, and anything set any higher makes the mic crackle.

Anyone got a solution?
Thanks

---

### Post by eXt on 2013-08-19
Same problem here. Did you find any solution?

---

### Post by tgalati4 on 2013-08-19
What kind of computer?  If these are laptops, then the built-in microphone is generally too crappy for telephone calls.  You need a plug-in headset microphone from Plantronics or some recognized vendor if you expect the other party to hear you.  Some microphone ports put out 5VDC to power a dynamic microphone.  If you are using a passive microphone, then you generally will get crappy results.  Dynamic mics have 3 bands on the plug.  You might have to try a few different brands until you find something that works the way you expect.

---

### Post by Thee on 2013-08-19
It's a Desktop computer and I have a headset that works well on Windows, so the hardware is not the problem. I didn't manage to fix my problem, but I did try to live boot a fresh Ubuntu 13.04 and the problem doesn't happen there.
Now only thing that I can guess is, that while upgrading from 12.04 to 13.04 something screwed up, and the way to resolve it is probably to reinstall the entire system, which I'll postpone for now.

---

### Post by tgalati4 on 2013-08-20
Boot the LiveDVD and take a snapshot of the ALSA settings and open a terminal and note the modules that get loaded:

```
lsmod
lsmod | grep snd
```

Perhaps there is a different module being loaded for your Realtek chip than what the LiveDVD loads.

---

### Post by Thee on 2013-08-20
I've set ALSA mixer settings the same way on both Live CD and Desktop, so that isn't the problem.

Here is the output of lsmod | grep snd on LiveCD:

```

snd_hda_codec_hdmi     41193  1 
snd_usb_audio         149964  1 
snd_hda_codec_realtek    47074  1 
snd_usbmidi_lib        25014  1 snd_usb_audio
snd_hda_intel          43836  7 
snd_hda_codec         188691  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_cmipci             44561  2 
snd_mpu401_uart        14169  1 snd_cmipci
snd_opl3_lib           19131  1 snd_cmipci
snd_hwdep              13602  3 snd_usb_audio,snd_hda_codec,snd_opl3_lib
gameport               15435  1 snd_cmipci
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102033  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_cmipci
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  3 snd_pcm,snd_seq,snd_opl3_lib
snd                    69125  36 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cmipci,snd_opl3_lib,snd_seq_midi
soundcore              12680  1 snd

```

on Desktop:

```

snd_cmipci             45102  0 
snd_mpu401_uart        14169  1 snd_cmipci
snd_hda_codec_hdmi     37407  1 
snd_opl3_lib           19391  1 snd_cmipci
snd_hda_codec_realtek    46511  1 
snd_hda_intel          44397  7 
snd_usb_audio         147350  1 
gameport               19699  1 snd_cmipci
snd_hda_codec         190010  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_usbmidi_lib        29477  1 snd_usb_audio
snd_hwdep              13613  3 snd_usb_audio,snd_hda_codec,snd_opl3_lib
snd_pcm               102477  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_cmipci
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30417  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
snd_timer              29989  4 snd_pcm,snd_seq,snd_opl3_lib
snd                    69533  29 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cmipci,snd_opl3_lib
soundcore              12680  1 snd

```


And here is the output of lsmod on LiveCD:

```

Module                  Size  Used by
dm_crypt               22728  0 
snd_hda_codec_hdmi     41193  1 
snd_usb_audio         149964  1 
snd_hda_codec_realtek    47074  1 
dm_multipath           22843  0 
snd_usbmidi_lib        25014  1 snd_usb_audio
scsi_dh                14882  1 dm_multipath
snd_hda_intel          43836  7 
joydev                 17377  0 
snd_hda_codec         188691  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
kvm_amd                59958  0 
kvm                   424842  1 kvm_amd
snd_cmipci             44561  2 
snd_mpu401_uart        14169  1 snd_cmipci
snd_opl3_lib           19131  1 snd_cmipci
snd_hwdep              13602  3 snd_usb_audio,snd_hda_codec,snd_opl3_lib
gameport               15435  1 snd_cmipci
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
serio_raw              13413  0 
microcode              23394  0 
k10temp                13126  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
snd_pcm               102033  5 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_cmipci
edac_core              62277  0 
edac_mce_amd           22617  0 
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_timer              29433  3 snd_pcm,snd_seq,snd_opl3_lib
snd                    69125  36 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cmipci,snd_opl3_lib,snd_seq_midi
soundcore              12680  1 snd
sp5100_tco             13979  0 
parport_pc             32701  0 
ppdev                  17671  0 
i2c_piix4              22106  0 
bnep                   19564  2 
lp                     17759  0 
rfcomm                 69001  0 
parport                42299  3 lp,ppdev,parport_pc
bluetooth             372613  10 bnep,rfcomm
mac_hid                13205  0 
squashfs               47827  1 
overlayfs              27897  1 
nls_iso8859_1          12713  1 
dm_mirror              22056  0 
dm_region_hash         20784  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101225  2 hid_generic,usbhid
usb_storage            62062  1 
radeon                999946  3 
i2c_algo_bit           13413  1 radeon
ttm                    84547  1 radeon
pata_acpi              13038  0 
drm_kms_helper         52692  1 radeon
r8169                  67138  0 
firewire_ohci          40060  0 
drm                   289960  5 ttm,drm_kms_helper,radeon
firewire_core          64364  1 firewire_ohci
pata_atiixp            13242  0 
crc_itu_t              12707  1 firewire_core
pata_jmicron           12758  0 
ahci                   25819  1 
libahci                31898  1 ahci
wmi                    19070  0 

```

and on Desktop:

```

Module                  Size  Used by
arc4                   12573  0 
md4                    12595  0 
nls_utf8               12557  1 
cifs                  451245  2 
fscache                57914  1 cifs
pci_stub               12622  1 
vboxpci                23194  0 
vboxnetadp             25670  0 
vboxnetflt             23479  0 
vboxdrv               320372  3 vboxnetadp,vboxnetflt,vboxpci
bnep                   18258  2 
parport_pc             28284  0 
ppdev                  17106  0 
rfcomm                 47863  0 
bluetooth             251354  10 bnep,rfcomm
snd_cmipci             45102  0 
snd_mpu401_uart        14169  1 snd_cmipci
snd_hda_codec_hdmi     37407  1 
snd_opl3_lib           19391  1 snd_cmipci
snd_hda_codec_realtek    46511  1 
snd_hda_intel          44397  7 
snd_usb_audio         147350  1 
gameport               19699  1 snd_cmipci
snd_hda_codec         190010  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_usbmidi_lib        29477  1 snd_usb_audio
snd_hwdep              13613  3 snd_usb_audio,snd_hda_codec,snd_opl3_lib
snd_pcm               102477  6 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_cmipci
snd_page_alloc         18798  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30417  3 snd_usbmidi_lib,snd_mpu401_uart,snd_seq_midi
snd_seq                61930  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  4 snd_seq,snd_rawmidi,snd_opl3_lib,snd_seq_midi
fglrx                5294837  178 
snd_timer              29989  4 snd_pcm,snd_seq,snd_opl3_lib
snd                    69533  29 snd_hda_codec_realtek,snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_mpu401_uart,snd_seq_device,snd_cmipci,snd_opl3_lib
soundcore              12680  1 snd
kvm_amd                60389  0 
kvm                   452835  1 kvm_amd
joydev                 17613  0 
amd_iommu_v2           19198  1 fglrx
sp5100_tco             13870  0 
wmi                    19256  0 
microcode              22923  0 
mac_hid                13253  0 
edac_core              63023  0 
k10temp                13173  0 
i2c_piix4              13459  0 
edac_mce_amd           22792  0 
serio_raw              13215  0 
binfmt_misc            17540  1 
lp                     17799  0 
parport                46562  3 lp,ppdev,parport_pc
hid_generic            12548  0 
usbhid                 47346  0 
hid                   101248  2 hid_generic,usbhid
firewire_ohci          44864  0 
firewire_core          64836  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
r8169                  68680  0 
ahci                   30063  2 
pata_acpi              13038  0 
libahci                32088  1 ahci
pata_jmicron           12758  0 
pata_atiixp            13242  0 

```


It looks to me that both are loading the same sound modules..

---

