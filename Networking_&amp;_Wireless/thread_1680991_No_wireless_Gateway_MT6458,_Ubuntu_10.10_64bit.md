---
title: "No wireless Gateway MT6458, Ubuntu 10.10 64bit"
date: 2011-02-03
forum: Networking &amp; Wireless
---

### Post by jhargis1012 on 2011-02-03
Hello. I have a Gateway laptop (model MT6458 ). You'll have to bear with me, I'm very inexperienced with Linux in general and especially the command line.

Previously, I was running 10.04 32bit. I wanted to give 64bit a try, so I just fresh installed 10.04 AMD64. With help from you guys, I was able to get my wireless working in the 32 bit version as seen on this thread: [http://ubuntuforums.org/showthread.php?t=1668743](http://ubuntuforums.org/showthread.php?t=1668743). After installing the 64 bit version, I attempted following the same directions as before, but it doesn't seem to be working.

Here's some of what the terminal is telling me:

```
jeremy@jeremy-MT6458:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

```
jeremy@jeremy-MT6458:~$ ndiswrapper -l
netmw14x : invalid driver!
```

```
jeremy@jeremy-MT6458:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)
08:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
08:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
08:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
jeremy@jeremy-MT6458:~$ 
```

```
jeremy@jeremy-MT6458:~$ lsmod
Module                  Size  Used by
ndiswrapper           245044  0 
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11395  0 
snd_hda_codec_si3054     4292  1 
snd_hda_codec_idt      64699  1 
snd_hda_intel          26115  5 
snd_hda_codec         100919  3 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel
pcmcia                 40944  0 
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
radeon                910244  3 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
ttm                    68212  1 radeon
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         32836  1 radeon
yenta_socket           24279  0 
tifm_7xx1               4698  0 
video                  22176  0 
output                  2527  1 video
pcmcia_rsrc            10357  1 yenta_socket
drm                   206230  5 radeon,ttm,drm_kms_helper
snd                    64181  18 snd_hda_codec_si3054,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                62080  0 
tifm_core               7686  1 tifm_7xx1
i2c_algo_bit            6208  1 radeon
serio_raw               4910  0 
edac_core              46822  0 
pcmcia_core            17677  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
k8temp                  4128  0 
edac_mce_amd            9387  0 
i2c_piix4              10047  0 
shpchp                 34910  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
pata_atiixp             4405  2 
sky2                   53371  0 
jeremy@jeremy-MT6458:~$ 

```

I'd appreciate any help you guys can offer as I'm pretty lost. I suspect it's something to do with the fact that I'm in a 64-bit environment now, which requires a windows wireless driver designed for 64-bit? Just a thought. Thanks.

---

### Post by jhargis1012 on 2011-02-03
Update: I found a different driver on another thread. This one is supposed to be 64 bit compatible, but I can't get to the inf file. After unzipping, the setup file is there but it's an .exe file. Tried wine, cabextract, unzip, and unshield to get to the inf. Didn't work.

---

### Post by jhargis1012 on 2011-02-04
Sorry to bump this, but I'd really appreciate any assistance or tips from anyone with experience on these types of issues.

---

### Post by jhargis1012 on 2011-02-07
Again, sorry to bump this, but I'm still having trouble. I have definitely found several instances of the proper files for the 64 bit driver I need after looking around online, but they're always in setup.exe format and unshield, cabextract, wine, etc., never work with them. Anybody have any ideas where I can find the .inf I need?

---

### Post by jhargis1012 on 2011-02-15
Still have not got this working.

As I was attempting to use a Realtek driver for my Marvell device (at this point, I'll try anything!), I realized that my lspci output does not show a device id for the wifi. For ethernet devices, I get:

```

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 2a08 (rev 03)

```

I'm sure it's the second entry, but where is my device id to point ndiswrapper to?

Any assistance would be greatly appreciated.

---

### Post by jhargis1012 on 2011-02-18
Bump

---

### Post by AlaskanPotHead on 2012-06-09
Did you get this fixed? I'm having the same problem with this same computer but with 12.04. I've searched the forums for 2 days now and can't find a solution that works.

---

### Post by SuperStuff on 2012-07-02
Or could someone suggest a replacement wireless card to plug in that Ubuntu recognizes easily.

---

