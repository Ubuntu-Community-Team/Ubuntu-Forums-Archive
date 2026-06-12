---
title: "[SOLVED] Sound not working on New Feisty Install"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by PetroToreno on 2007-09-15
I just installed 7.04 last night and the sound wont work. it doesnt even recognize my sound card.

its an onboard intel card. HDA-Intel. i tried the hda-intel feisty guide. but didnt work for me

lsmod output:

```
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36284  1 
udf                    85252  0 
binfmt_misc            12680  1 
rfcomm                 40856  0 
l2cap                  25856  5 rfcomm
bluetooth              55908  4 rfcomm,l2cap
fglrx                 540004  11 
ppdev                  10116  0 
speedstep_lib           6148  0 
cpufreq_powersave       2688  0 
cpufreq_userspace       5408  0 
cpufreq_conservative     8200  0 
cpufreq_ondemand        9228  0 
cpufreq_stats           7360  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
sony_acpi               6284  0 
pcc_acpi               13184  0 
dev_acpi               12292  0 
tc1100_wmi              8068  0 
dock                   10268  0 
asus_acpi              17308  0 
backlight               7040  1 asus_acpi
sbs                    15652  0 
i2c_ec                  6016  1 sbs
i2c_core               22656  1 i2c_ec
battery                10756  0 
container               5248  0 
ac                      6020  0 
video                  16388  0 
button                  8720  0 
nls_utf8                3072  1 
ntfs                  107764  1 
ipv6                  268960  10 
parport_pc             36388  0 
lp                     12452  0 
parport                36936  3 ppdev,parport_pc,lp
snd_hda_intel         262552  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                81028  2 snd_hda_intel,snd_pcm_oss
snd_seq_oss            35072  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
psmouse                38920  0 
serio_raw               7940  0 
usbhid                 26592  0 
usblp                  14848  0 
snd                    56324  8 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm
hid                    27392  1 usbhid
shpchp                 34324  0 
pci_hotplug            32576  1 shpchp
iTCO_wdt               11812  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              26140  1 
agpgart                35400  2 fglrx,intel_agp
pcspkr                  4224  0 
af_packet              23816  2 
tsdev                   8768  0 
evdev                  11008  4 
usb_storage            72256  0 
ext3                  133128  1 
jbd                    59816  1 ext3
mbcache                 9604  1 ext3
libusual               17936  1 usb_storage
sg                     36252  0 
sd_mod                 23428  4 
sr_mod                 17060  1 
cdrom                  37664  1 sr_mod
ata_piix               15492  4 
ata_generic             9092  0 
libata                125720  2 ata_piix,ata_generic
scsi_mod              142348  5 usb_storage,sg,sd_mod,sr_mod,libata
8139too                27648  0 
ehci_hcd               34188  0 
e100                   36232  0 
floppy                 59524  0 
8139cp                 25088  0 
mii                     6528  3 8139too,e100,8139cp
generic                 5124  0 [permanent]
uhci_hcd               25360  0 
usbcore               134280  7 usbhid,usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
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
```

```
cat /proc/asound/cards 
--- no soundcards ---

```

```
lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc RV370 [Radeon X300SE]
03:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:03.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
03:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
```

Any help would be greatly appreciated.

---

### Post by linuxwizard on 2007-09-17
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

[https://help.ubuntu.com/community/DebuggingSoundProblems](https://help.ubuntu.com/community/DebuggingSoundProblems)

Also you may want to look on Launchpad to see if their are any bugs has been reported sound issues or your sound card.

---

### Post by rzrgenesys187 on 2007-09-17
This post worked for me and i'm pretty sure i have the same sound card

[http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177](http://ubuntuforums.org/showthread.php?t=349491&highlight=p105-s6177)

P.S. it may work even if you don't have a toshiba since the file you download is specific for your laptop model.  Let me know how it works

---

### Post by arkara on 2007-09-18
try acpi=off and see if it works it worked on me

---

### Post by lisati on 2007-09-18
Different solutions seem to work for different people. Installing the "updates" did it for my laptop,,,,,,,

---

### Post by rzrgenesys187 on 2007-09-18
> **arkara said:**
> try acpi=off and see if it works it worked on me

The only problem with turning acpi off is that you can't see your battery power and a few other things.  I wouldn't use this except as a last resort personally, no offense was meant.

---

### Post by maryjanua on 2007-09-19
hey i have a desktop which needed that driver.
 check this thread out it may help 
[http://ubuntuforums.org/showthread.php?t=550753](http://ubuntuforums.org/showthread.php?t=550753)
about page 11

---

### Post by PetroToreno on 2007-09-21
i got it working. it was pretty simple and felt stupid that i didn't think of it before.

just had to go to alsamixer and unmute the lines for the 5.1 channels. don't understand why since im not using 5.1
but it did the trick.

---

### Post by linuxwizard on 2007-09-21
Well at least you got it working good to hear. Please mark thread solved.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

