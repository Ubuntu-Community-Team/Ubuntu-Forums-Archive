---
title: "Sound before login,but no more after"
date: 2007-05-20
forum: Multimedia &amp; Video
---

### Post by icechen1 on 2007-05-20
Hello,I just complied ALSA 1.0.14rc4(utils,lib,driver),all went smoothly but now i only get sound at the login screen,not after.
I make sure i am in the audio group.
ISPCI:
> icechen1@icechen1-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

grep 'audio' /etc/group
> icechen1@icechen1-laptop:~$ grep 'audio' /etc/group
audio : x:29:icechen1

ismod:
> 
icechen1@icechen1-laptop:~$ lsmod
Module                  Size  Used by
snd_rtctimer            4768  1 
binfmt_misc            12680  1 
ipv6                  268704  12 
rfcomm                 40856  0 
l2cap                  25728  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
nfs                   240876  0 
nfsd                  218992  17 
exportfs                6912  1 nfsd
lockd                  64904  3 nfs,nfsd
sunrpc                161340  12 nfs,nfsd,lockd
ppdev                  10116  0 
i915                   24448  3 
drm                    81044  4 i915
cpufreq_userspace       5408  0 
cpufreq_stats           7360  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9228  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8200  0 
tc1100_wmi              8068  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
sony_acpi               6284  0 
video                  16388  0 
sbs                    15652  0 
i2c_ec                  5888  1 sbs
i2c_core               22784  1 i2c_ec
dock                   10268  0 
button                  8720  0 
battery                10756  0 
container               5248  0 
ac                      6020  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
af_packet              23816  4 
nls_utf8                3072  2 
ntfs                  107764  2 
fuse                   46612  1 
sbp2                   23812  0 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel         244632  1 
joydev                 10816  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
pcmcia                 39212  0 
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35200  0 
sr_mod                 17060  0 
cdrom                  37664  1 sr_mod
sky2                   43528  0 
snd_seq_midi            9728  0 
snd_rawmidi            25984  1 snd_seq_midi
snd_seq_midi_event      8576  2 snd_seq_oss,snd_seq_midi
snd_seq                54000  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24196  3 snd_rtctimer,snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           194608  0 
psmouse                38920  0 
serio_raw               7940  0 
tifm_7xx1              10240  0 
tifm_core               9856  1 tifm_7xx1
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
yenta_socket           27532  1 
rsrc_nonstatic         14080  1 yenta_socket
pcmcia_core            40852  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    56324  14 snd_rtctimer,snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
intel_agp              25116  1 
agpgart                35400  3 drm,intel_agp
tsdev                   8768  0 
evdev                  11008  8 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
sg                     36252  0 
sd_mod                 23428  5 
usbhid                 26592  0 
hid                    27392  1 usbhid
ata_piix               15492  0 
ata_generic             9092  0 
ohci1394               36528  0 
ieee1394              299448  2 sbp2,ohci1394
ehci_hcd               34188  0 
ahci                   22020  4 
libata                125720  3 ata_piix,ata_generic,ahci
scsi_mod              142348  5 sbp2,sr_mod,sg,sd_mod,libata
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  5 ndiswrapper,usbhid,ehci_hcd,uhci_hcd
thermal                14856  0 
processor              31048  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3584  1 fbcon
font                    9216  1 fbcon
bitblit                 6912  1 fbcon
softcursor              3200  1 bitblit
vesafb                  9220  0 
capability              5896  0 
commoncap               8192  1 capability
icechen1@icechen1-laptop:~$ 

Also,the sound card is a hda-intel(snd-hda-intel) with Sigmatel STAC92XX

---

### Post by icechen1 on 2007-05-20
Bump,someone help please... :(:(:(:(:(:(:(

---

### Post by shad0w_walker on 2007-05-20
Can you still get sound through OSS? It maybe that there is something wrong with your ALSA install. Im not sure if the login screen uses ALSA or OSS but it is possible it uses OSS as it is the only thing accessing the sound card.

If all else fails i would recommend reinstalling the version of ALSA in the ubuntu repos. Atleast if that version does not work its a known version and there is a lot more experience and knowledge on how it works with ubuntu.

---

### Post by icechen1 on 2007-05-20
> **shad0w_walker said:**
> Can you still get sound through OSS? It maybe that there is something wrong with your ALSA install. Im not sure if the login screen uses ALSA or OSS but it is possible it uses OSS as it is the only thing accessing the sound card.

If all else fails i would recommend reinstalling the version of ALSA in the ubuntu repos. Atleast if that version does not work its a known version and there is a lot more experience and knowledge on how it works with ubuntu.
I forgot to say that when i do sudo frozen-bubble,it has sound but if i remove the sudo it dosen't have sound

---

### Post by shifuimam on 2007-05-20
Do you have more than one sound card? For instance, does your computer have integrated sound on the motherboard, as well as a PCI sound card? I had this same problem, and I think I found the solution today. I have a Dell PowerEdge with integrated Intel sound and a Turtle Beach 5.1 surround sound card - Ubuntu sees a total of seven output interfaces, and it would randomly select one to be default. Sometimes I would have sound, and sometimes I wouldn't.

I fixed it in the config manager. Do a gconf-editor from the terminal. Once the window opens up, navigate to desktop > gnome > sound and you can change the default mixer device. I figured out the hw numbers by looking in VLC Media Player at the sound settings. You also need to change the "audiosrc" setting in system > gstreamer > default.

Hope that helps!

---

### Post by icechen1 on 2007-05-20
I decided to uninstall the alsa i complied and restore to the old one,how to do it?


> **shifuimam said:**
> Do you have more than one sound card? For instance, does your computer have integrated sound on the motherboard, as well as a PCI sound card? I had this same problem, and I think I found the solution today. I have a Dell PowerEdge with integrated Intel sound and a Turtle Beach 5.1 surround sound card - Ubuntu sees a total of seven output interfaces, and it would randomly select one to be default. Sometimes I would have sound, and sometimes I wouldn't.

I fixed it in the config manager. Do a gconf-editor from the terminal. Once the window opens up, navigate to desktop > gnome > sound and you can change the default mixer device. I figured out the hw numbers by looking in VLC Media Player at the sound settings. You also need to change the "audiosrc" setting in system > gstreamer > default.

Hope that helps!

I only have a hda-intel card.

---

