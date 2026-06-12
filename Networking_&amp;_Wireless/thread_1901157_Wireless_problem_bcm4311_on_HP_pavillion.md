---
title: "Wireless problem bcm4311 on HP pavillion"
date: 2011-12-27
forum: Networking &amp; Wireless
---

### Post by dave2012 on 2011-12-27
Hi All,
I cannot connect to the wireless network. Please assist. Thanks!

seyi@seyi-HP-Pavilion-dv6000-GA213UA-ABA:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux seyi-HP-Pavilion-dv6000-GA213UA-ABA 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 athlon i386 GNU/Linux

seyi@seyi-HP-Pavilion-dv6000-GA213UA-ABA:~$ lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
--
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Hewlett-Packard Company BCM4311 802.11b/g Wireless LAN Controller [103c:1363]
    Kernel modules: ssb, wl

seyi@seyi-HP-Pavilion-dv6000-GA213UA-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

seyi@seyi-HP-Pavilion-dv6000-GA213UA-ABA:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

seyi@seyi-HP-Pavilion-dv6000-GA213UA-ABA:~$ lsmod
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
nvidia              10390874  43 
snd_hda_codec_conexant    52418  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_intel          28358  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r592                   17808  0 
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35662  2 sm_common,nand
soundcore              12600  1 snd
k8temp                 12905  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
memstick               15857  1 r592
nv_tco                 13399  0 
i2c_nforce2            12906  0 
lib80211               14570  0 
wmi                    18744  1 hp_wmi
binfmt_misc            17292  1 
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
firewire_ohci          35846  0 
sdhci_pci              13658  0 
firewire_core          56937  1 firewire_ohci
hid                    77367  1 usbhid
crc_itu_t              12627  1 firewire_core
sdhci                  27360  1 sdhci_pci
forcedeth              58103  0 
pata_amd               13753  0 
sata_nv                23379  2

---

### Post by wildmanne39 on 2011-12-27
Hi, you will need to have a wired connection to the internet then run this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
Watch for errors, when it is done unplug wired connection and reboot.
Thanks

---

### Post by dave2012 on 2011-12-27
> **wildmanne39 said:**
> Hi, you will need to have a wired connection to the internet then run this command:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```Watch for errors, when it is done unplug wired connection and reboot.
Thanks

I tried the above, installed fwcutter (copied and pasted), re started the laptop but still no wireless connection

---

### Post by wildmanne39 on 2011-12-27
Hi, I think I see the problem please do with wired connection unplugged:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
```
sudo modprobe b43
```
Thanks

---

### Post by dave2012 on 2011-12-27
> **wildmanne39 said:**
> Hi, I think I see the problem please do with wired connection unplugged:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
``````
sudo modprobe b43
```Thanks

THANKS MAN! IT WORKS NOW!!!:popcorn:

---

### Post by wildmanne39 on 2011-12-27
Hi, your welcome! I am glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

### Post by ryconn on 2012-01-02
I'm having similar issues with my HP dv6000. I did have it running previously with Vista, but on installing Ubuntu I had no such luck. I've tried everything up top with no luck.

ryan@ryan-HP-Pavilion-dv6000-GL896UA-ABA:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by wildmanne39 on 2012-01-02
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by EssJohnson on 2012-01-03
```
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:30cf]
    Kernel driver in use: forcedeth
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux birdy-HP-Pavilion-dv9700-Notebook-PC 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 athlon i386 GNU/Linux
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ rfill list all
No command 'rfill' found, did you mean:
 Command 'rfkill' from package 'rfkill' (main)
 Command 'rfile' from package 'radare-common' (universe)
 Command 'sfill' from package 'secure-delete' (universe)
 Command 'rkill' from package 'pslist' (universe)
rfill: command not found
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ rfkill list all
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ rfkill list all
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ lsmod
Module                  Size  Used by
b43                   318816  0 
ssb                    50682  1 b43
mac80211              393459  1 b43
cfg80211              172392  2 b43,mac80211
parport_pc             32114  0 
ppdev                  12849  0 
vesafb                 13489  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
nvidia              10390874  46 
snd_hda_codec_conexant    52418  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
r592                   17808  0 
k8temp                 12905  0 
memstick               15857  1 r592
r852                   17901  0 
sm_common              16737  1 r852
nand                   49706  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
binfmt_misc            17292  1 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
wmi                    18744  1 hp_wmi
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
ahci                   21634  1 
libahci                25727  1 ahci
crc_itu_t              12627  1 firewire_core
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
forcedeth              58103  0 
birdy@birdy-HP-Pavilion-dv9700-Notebook-PC:~$ 
I didn't ask originally but I'm having trouble connecting to wifi too. 

```

---

### Post by wildmanne39 on 2012-01-04
Hi, I do not see a wireless card. You have an internal card right? If not post the output of:
```
lsusb
```
if so make sure the wireless lan is on in the bios.

Please copy and paste all commands for accuracy, try this one again.
```
rfkill list all
```
Thanks

---

### Post by uprvrndn on 2012-01-21
I have the same issue but do not know how to resolve it.  I do not see a response from anyone about not even seeing the network card.

[
root@PetraComputer:~# cat /etc/lsb-release ; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux PetraComputer 3.0.0-15-generic #25-Ubuntu SMP Mon Jan 2 17:44:42 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
root@PetraComputer:~# 
root@PetraComputer:~# lspci -nnk | grep -iA2 net
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
    Subsystem: Hewlett-Packard Company Presario V6133CL [103c:30b7]
    Kernel driver in use: forcedeth
root@PetraComputer:~#
root@PetraComputer:~# rfkill list all
root@PetraComputer:~# 
root@PetraComputer:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
root@PetraComputer:~# root@PetraComputer:~# lsmod
Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
vesafb                 13809  1 
snd_hda_codec_conexant    62197  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_intel          33390  2 
snd_hda_codec         104931  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
nvidia               8107305  37 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72711  0 
snd_timer              29991  2 snd_pcm,snd_seq
videodev               92992  1 uvcvideo
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l2_compat_ioctl32    17083  1 videodev
snd                    68266  13 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
r852                   18277  0 
sm_common              16865  1 r852
nand                   54965  2 r852,sm_common
nand_ids               12723  1 nand
nand_bch               13147  1 nand
r592                   18144  0 
psmouse                73882  0 
bch                    22061  1 nand_bch
nand_ecc               13230  1 nand
soundcore              12680  1 snd
edac_core              53746  0 
serio_raw              13166  0 
memstick               16569  1 r592
mtd                    33181  2 sm_common,nand
k8temp                 13057  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
edac_mce_amd           23709  0 
nv_tco                 13687  0 
i2c_nforce2            13058  0 
wmi                    19256  1 hp_wmi
binfmt_misc            17540  1 
video                  19412  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
sdhci_pci              14032  0 
crc_itu_t              12707  1 firewire_core
sdhci                  32166  1 sdhci_pci
sata_nv                32305  2 
forcedeth              67563  0 
pata_amd               14121  0 
root@PetraComputer:~# 
]

---

### Post by wildmanne39 on 2012-01-21
Hi, is this a laptop? You are right your wireless card did not show up, please check your bios and make sure the wireless lan is on and if possible reseat the card or move it to a new pci slot. 
You should also post the output of:
```
sudo pccardctl ident
```
if it does not show up after doing what I mentioned above.
Thanks

---

