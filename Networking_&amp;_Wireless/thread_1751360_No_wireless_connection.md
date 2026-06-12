---
title: "No wireless connection"
date: 2011-05-06
forum: Networking &amp; Wireless
---

### Post by alpharhythm on 2011-05-06
Hi all,
I'm new to Ubuntu (and Linux in general) and cannot seem to get my WiFi connected. Don't see anything about a wireless network connection / settings under the network tab on the desktop. Any help would be greatly appreciated. Thanks!

---

### Post by chicoharv on 2011-05-06
You may have to go toa ethernet connection and go to snaptics manager and download some apps and drivers for your  wireless card. I have had trouble getting wireless to work seamlessly with 10.10  so I have not tried the natty yet. If you have broadcom cards it takes a different set of apps. Depending on your motherboard etc it may be propietary to Windows and you may never get it to work. Not sure what natty has improved but I will be downloading in the next few days and try it on my laptop again. Good luck. You might try letting the quorum nknow your make and model of computer, and wreless card you are using.

---

### Post by alpharhythm on 2011-05-06
Dell inspiron 1501... trying to figure out what the wlan adapter is but that is something I am struggling with now that Ubuntu is installed. Is there a command I can run to determine that?

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> Dell inspiron 1501... trying to figure out what the wlan adapter is but that is something I am struggling with now that Ubuntu is installed. Is there a command I can run to determine that?

Hi there and welcome to the forum lets see what kind of hardware you are working with please open your terminal(ctrl+alt+t) then type in 
```
lspci -nn
```
then lets see if there is anything blocking you card 
```
rfkill list all 
```
lets also see if the driver is loaded this one takes some time to load but it will show up
```
sudo lshw -C network
```
and last lets see if there is anything loaded all ready 
```
lsmod 
``` Please paste all things here thanks and once again welcome to Ubuntu Forums :D

---

### Post by alpharhythm on 2011-05-06
Thank you for a prompt response! The details you request are below :)

> **josephmills said:**
> Hi there and welcome to the forum lets see what kind of hardware you are working with please open your terminal(ctrl+alt+t) then type in 
```
lspci -nn
```nick@ublt01:~$ lspci -nn
00:00.0 Host bridge [0600]: ATI Technologies Inc RS480 Host Bridge [1002:5950] (rev 10)
00:01.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a3f]
00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]
00:06.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a38]
00:12.0 SATA controller [0106]: ATI Technologies Inc SB600 Non-Raid-5 SATA [1002:4380]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI0) [1002:4387]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI1) [1002:4388]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI2) [1002:4389]
00:13.3 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI3) [1002:438a]
00:13.4 USB Controller [0c03]: ATI Technologies Inc SB600 USB (OHCI4) [1002:438b]
00:13.5 USB Controller [0c03]: ATI Technologies Inc SB600 USB Controller (EHCI) [1002:4386]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 13)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB600 IDE [1002:438c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB600 PCI to LPC Bridge [1002:438d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS482 [Radeon Xpress 200M] [1002:5975]
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
08:01.0 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
08:01.1 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 01)

then lets see if there is anything blocking you card 
```
rfkill list all 
```nick@ublt01:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no


lets also see if the driver is loaded this one takes some time to load but it will show up
```
sudo lshw -C network
```PCI (sysfs)  

  *-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:b0200000-b0203fff
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:c7:8f:6e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.1.20 latency=64 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:21 memory:b0300000-b0301fff


and last lets see if there is anything loaded all ready 
```
lsmod 
```nick@ublt01:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
b44                    35301  0 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
ssb                    45942  1 b44
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
wl                   2642531  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
joydev                 17322  0 
radeon                896428  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ttm                    65184  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
drm_kms_helper         40745  1 radeon
psmouse                73312  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop            13515  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
k8temp                 12872  0 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
ati_agp                13202  0 
sp5100_tco             13456  0 
i2c_algo_bit           13184  1 radeon
i2c_piix4              13095  0 
shpchp                 32345  0 
dcdbas                 14054  1 dell_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci
pata_atiixp            12968  0 

Please paste all things here thanks and once again welcome to Ubuntu Forums :D

Thanks!

---

### Post by josephmills on 2011-05-06
Make sure you are connected to the internet via cat5(ethernet cable) if you do not have a router then stop and just tell us but is you do  

lets try this open your terminal again and type in 
```
 sudo apt-get install b43-fwcutter 
```
then type in 
```
sudo apt-get install firmware-b43-installer 
```
then 
```
sudo reboot
```
after reboot if you do not have wireless if not please post 
```
dmesg | grep b43 
```
```
lsmod | grep b43 
```
thanks

---

### Post by alpharhythm on 2011-05-06
Performed the steps you listed above while patched into my router (I've been communicating on this forum from Ethernet cable)

Still no wifi :(

Thanks for your help so far!

---

### Post by josephmills on 2011-05-06
please read the end of post #6

---

### Post by alpharhythm on 2011-05-06
> **josephmills said:**
> please read the end of post #6
I did that after reboot as you suggested. Still no connection.

---

### Post by alpharhythm on 2011-05-06
nick@ublt01:~$ dmesg | grep b43
[   19.900594] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
nick@ublt01:~$ lsmod | grep b43
nick@ublt01:~$

---

### Post by josephmills on 2011-05-06
please go to ubuntu software center and then go to edit-->software sources than make sure all are ticked then close software center and ubuntu software center then do a 
```
sudo apt-get update 
```
then 
```
sudo apt-get upgrade 
```
press y when it asks you to 
then go back to post #6 and do all over again this time add a 
```
sudo apt-get  install bcmwl-kernel-source 

``` read it close show us it all thanks

---

### Post by alpharhythm on 2011-05-06
Checked everything under software as you recommended and performed updates. Then repeated step 6 with the addition you made

nick@ublt01:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install firmware-b43-isntaller
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package firmware-b43-isntaller
nick@ublt01:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo reboot


Doing reboot now.

---

### Post by alpharhythm on 2011-05-06
No wireless connection after reboot. So -

nick@ublt01:~$ dmesg | grep b43
[    9.900638] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
nick@ublt01:~$ lsmod | grep b43
nick@ublt01:~$ 

Still no wireless connection. Just to confirm that I am not retarded, it should show up on the network manager drop down menu under wired connections, right?

Also, how can I confirm that the wireless adapter is enabled? Did we do that already? I don't see the wifi light on my laptop illuminated...

---

### Post by josephmills on 2011-05-06
ok go to synaptic package manager and in the search bar type in bcm 
then then unistall(mark for removal ) the bcmwl-kernel-source then press the apply button then lets see a ```
lsmod
``` thanks ** please make sure that the b43 fwcutter is installed and the firmware-b43-installer  is also installed **

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> Checked everything under software as you recommended and performed updates. Then repeated step 6 with the addition you made

nick@ublt01:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install firmware-b43-isntaller
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Unable to locate package firmware-b43-isntaller**
nick@ublt01:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo reboot


Doing reboot now.the part in bold is the trouble   edit 
never mind

---

### Post by alpharhythm on 2011-05-06
Performed removal as you recommended.
  
nick@ublt01:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                896428  3 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b44                    35301  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
ssb                    45942  1 b44
wl                   2642531  0 
sp5100_tco             13456  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13095  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
k8temp                 12872  0 
ati_agp                13202  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  0 
nick@ublt01:~$

---

### Post by alpharhythm on 2011-05-06
> **josephmills said:**
> the part in bold is the trouble   edit 
never mind

Yeah sorry, typo ;)

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> Performed removal as you recommended.

nick@ublt01:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                896428  3 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b44                    35301  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
ssb                    45942  1 b44
wl                   2642531  0 
sp5100_tco             13456  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13095  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
k8temp                 12872  0 
ati_agp                13202  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  0 
nick@ublt01:~$ ^C
nick@ublt01:~$ 
nick@ublt01:~$ clear

nick@ublt01:~$ lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
radeon                896428  3 
snd_seq_midi_event     14475  1 snd_seq_midi
joydev                 17322  0 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
b44                    35301  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
snd_timer              28659  2 snd_pcm,snd_seq
ssb                    45942  1 b44
wl                   2642531  0 
sp5100_tco             13456  0 
drm                   180037  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
i2c_piix4              13095  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73312  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lib80211               14570  1 wl
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
k8temp                 12872  0 
ati_agp                13202  0 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
usbhid                 41704  0 
hid                    77084  1 usbhid
sdhci_pci              13623  0 
libahci                25548  1 ahci
sdhci                  22720  1 sdhci_pci
pata_atiixp            12968  0 
nick@ublt01:~$

arghhh the driver is still not loaded repeat step six now with the the ```
sudo apt-get install bcmwl-kernel-source 
```at the end then reboot tell us how it goes

---

### Post by alpharhythm on 2011-05-06
nick@ublt01:~$ sudo apt-get install b43-fwcutter
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,202 kB of archives.
After this operation, 3,367 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted bcmwl-kernel-source i386 5.100.82.38+bdcom-0ubuntu3 [1,202 kB]
Fetched 1,202 kB in 2s (419 kB/s)                
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 141774 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 2.6.38-8-generic
Building for architecture i686
Building initial module for 2.6.38-8-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
nick@ublt01:~$ sudo reboot

After reboot: no wifi :(

nick@ublt01:~$ dmesg | grep b43
[   19.863062] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
nick@ublt01:~$ lsmod | grep b43
nick@ublt01:~$ 

No wifi :(

In case you need it again...

nick@ublt01:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
joydev                 17322  0 
snd_hwdep              13274  1 snd_hda_codec
binfmt_misc            13213  1 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
b44                    35301  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ssb                    45942  1 b44
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2642531  0 
radeon                896428  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  5 radeon,ttm,drm_kms_helper
soundcore              12600  1 snd
k8temp                 12872  0 
sp5100_tco             13456  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 radeon
lib80211               14570  1 wl
shpchp                 32345  0 
ati_agp                13202  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
pata_atiixp            12968  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci
nick@ublt01:~$ 

Am I a lost cause?

---

### Post by alpharhythm on 2011-05-06
(Updated above post)

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> nick@ublt01:~$ sudo apt-get install b43-fwcutter
[sudo] password for nick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firmware-b43-installer is already the newest version.
The following package was automatically installed and is no longer required:
  dkms
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
nick@ublt01:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 1,202 kB of archives.
After this operation, 3,367 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) natty/restricted bcmwl-kernel-source i386 5.100.82.38+bdcom-0ubuntu3 [1,202 kB]
Fetched 1,202 kB in 2s (419 kB/s)                
Selecting previously deselected package bcmwl-kernel-source.
(Reading database ... 141774 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu3_i386.deb) ...
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3) ...
Loading new bcmwl-5.100.82.38+bdcom DKMS files...
Building only for 2.6.38-8-generic
Building for architecture i686
Building initial module for 2.6.38-8-generic
Done.

wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.38-8-generic/updates/dkms/

depmod....

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
nick@ublt01:~$ sudo reboot

After reboot: no wifi :(

nick@ublt01:~$ dmesg | grep b43
[   19.863062] b43-pci-bridge 0000:05:00.0: setting latency timer to 64
nick@ublt01:~$ lsmod | grep b43
nick@ublt01:~$ 

No wifi :(

In case you need it again...

nick@ublt01:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
joydev                 17322  0 
snd_hwdep              13274  1 snd_hda_codec
binfmt_misc            13213  1 
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
b44                    35301  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
ssb                    45942  1 b44
snd_seq_midi_event     14475  1 snd_seq_midi
wl                   2642531  0 
radeon                896428  3 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
ttm                    65184  1 radeon
drm_kms_helper         40745  1 radeon
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  5 radeon,ttm,drm_kms_helper
soundcore              12600  1 snd
k8temp                 12872  0 
sp5100_tco             13456  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 radeon
lib80211               14570  1 wl
shpchp                 32345  0 
ati_agp                13202  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
pata_atiixp            12968  0 
sdhci_pci              13623  0 
sdhci                  22720  1 sdhci_pci
libahci                25548  1 ahci
nick@ublt01:~$ 

Am I a lost cause?
no it is not a lost cause try 
```
sudo su
echo b43 >> /etc/modules
exit

```
then reboot with out the cat5 cable did it work?

---

### Post by westie457 on 2011-05-06
Hi 'josephmills' has given some good advice. The solution to your problem might be here
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

I had a similar problem and the work around on page 19 worked for me. 

Hope it works for you as well.

Welcome to the very friendly world of Ubuntu.

ps  Forgot to ask which version are you running? 10.10 (Maverick) or 11.04 (Natty)?

---

### Post by alpharhythm on 2011-05-06
I really appreciate your continued effort to help me out with this. I owe you a beer... or two :)

nick@ublt01:~$ sudo su
[sudo] password for nick: 
root@ublt01:/home/nick# echbo b43 >> /etc/modules
No command 'echbo' found, did you mean:
 Command 'echo' from package 'coreutils' (main)
echbo: command not found
root@ublt01:/home/nick# echo b43 >> /etc/modules
root@ublt01:/home/nick# exit

rebooting, be right back.

---

### Post by alpharhythm on 2011-05-06
Ok, so I rebooted and now under the network manager I see wireless networks but its grayed out and it says "wireless is disabled by hardware switch" and I can't connect via ethernet. Ethernet doesn't even show up under the network manager (had to jump onto my PC to reply)

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> Ok, so I rebooted and now under the network manager I see wireless networks but its grayed out and it says "wireless is disabled by hardware switch" and I can't connect via ethernet. Ethernet doesn't even show up under the network manager (had to jump onto my PC to reply)
try 
```
rfkill unblock all 
```
if that wont do it lets see 
```
rfkill list all 
```

---

### Post by alpharhythm on 2011-05-06
> **westie457 said:**
> Hi 'josephmills' has given some good advice. The solution to your problem might be here
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

I had a similar problem and the work around on page 19 worked for me. 

Hope it works for you as well.

Welcome to the very friendly world of Ubuntu.

ps  Forgot to ask which version are you running? 10.10 (Maverick) or 11.04 (Natty)?

Thanks buddy, I'm taking a look at that thread now. I'm running 11.04. Excited to finally get into Linux.

---

### Post by alpharhythm on 2011-05-06
> **josephmills said:**
> try 
```
rfkill unblock all 
```if that wont do it lets see 
```
rfkill list all 
```

Success! But I still don't have ethernet in the network manager menu.

---

### Post by alpharhythm on 2011-05-06
To clarify, I only ran:

rfkill unblock all

Do I need to do

rfkill list all

.. to enable ethernet again?

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> To clarify, I only ran:

rfkill unblock all

Do I need to do

rfkill list all

.. to enable ethernet again?

ok so the b44 and b43 drivers are getting in the way googling brb

---

### Post by josephmills on 2011-05-06
> **alpharhythm said:**
> Success! But I still don't have ethernet in the network manager menu.

lets see what is in the blacklist.conf 
```
cat /etc/modprobe.d/blacklist.conf
```
thanks

---

### Post by alpharhythm on 2011-05-06
nick@ublt01:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
nick@ublt01:~$

---

### Post by josephmills on 2011-05-06
disconnect from your wireless then plug in your cat5 cable does it work? if not try to disable networking altogether then plug in the cat5 cable then enable the networking again still nothing? try to connect to your wireless and do a  ```
nm-tool 
``` this is the part that we need ```
 Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             unavailable
  Default:           no
  HW Address:        

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         off

``` please take out your HW Adress also

---

### Post by alpharhythm on 2011-05-06
Cat5 cable was already plugged in. Tried disabling networking / enabling. Didn't fix. Here is nm-tool info.

- Device: wlan0  [Auto NASNET] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             connected
  Default:           yes
  HW Address:        XX:XX:XX:XX:XX:XX

  Capabilities:
    Speed:           24 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *NASNET:         Infra, 68:7F:74:8B:02:F9, Freq 2452 MHz, Rate 54 Mb/s, Strength 97 WPA
    Alpha:           Infra, E0:91:F5:CB:8F:6E, Freq 2422 MHz, Rate 54 Mb/s, Strength 37 WPA2
    2WIRE181:        Infra, C0:83:0A:11:60:D9, Freq 2457 MHz, Rate 54 Mb/s, Strength 37 WPA WPA2
    sexyisconfirmed: Infra, 30:46:9A:04:19:55, Freq 2422 MHz, Rate 54 Mb/s, Strength 35 WPA WPA2
    G3Records2:      Infra, C0:3F:0E:7D:8A:62, Freq 2422 MHz, Rate 54 Mb/s, Strength 40 WPA WPA2
    2WIRE253:        Infra, 3C:EA:4F:AD:4D:31, Freq 2437 MHz, Rate 54 Mb/s, Strength 40 WPA
    Coleman5:        Infra, 00:24:B2:5D:D9:FB, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WEP
    Braveheart:      Infra, 00:1C:DF:8C:DE:99, Freq 2412 MHz, Rate 54 Mb/s, Strength 41
    2WIRE164:        Infra, B0:E7:54:E3:E0:31, Freq 2457 MHz, Rate 54 Mb/s, Strength 44 WEP
    Oniko:           Infra, F8:1E:DF:FA:97:CD, Freq 2417 MHz, Rate 54 Mb/s, Strength 62 WPA2

  IPv4 Settings:
    Address:         192.168.1.19
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             68.87.68.166
    DNS:             68.87.74.166


nick@ublt01:~$

---

### Post by josephmills on 2011-05-06
```
sudo lshw -C network
```

---

### Post by alpharhythm on 2011-05-06
nick@ublt01:~$ sudo lshw -C network
[sudo] password for nick: 
  *-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:b0200000-b0203fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:b0300000-b0301fff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:16:cf:c2:64:d2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 ip=192.168.1.19 link=yes multicast=yes wireless=IEEE 802.11bg
nick@ublt01:~$ 

If that was supposed to enable ethernet, it didn't work. If not, there's the info that command returned.

* I actually have to go out for the evening. You have been an amazing help. If there is anyway we can pick up on this tomorrow I would REALLY appreciate it. If you don't have time, don't sweat it. At least I have wifi working. You have been a super big help. Thanks man! :)

---

### Post by colmcraven on 2011-05-07
I have a **Dell Inspiron 1501**, with a broadcom **BCM 4311** wireless card. I installed Ubuntu (Natty Narwhall) and had the same problem. I could connect to the internet via ethernet but could not get laptop to recognise wireless card.

I found a fairly simple solution elsewhere that seemed to work for me. While connected via ethernet, using the terminal I downloaded the appropriate firmware and installed.

**Step 1**:

In terminal type:

                                  [SIZE=2][COLOR=#000000][FONT=Courier, serif]~$ sudo apt-get install b43-fwcutter[/FONT][/COLOR][/SIZE]
[SIZE=2] 
                     [/SIZE]             [SIZE=2][COLOR=#000000][FONT=Courier, serif]~$ sudo apt-get install b43-fwcutter firmware-b43-installer[/FONT][/COLOR][/SIZE]
 
**Step 2**:

Then, in >Applications>Additional Drivers, uninstalled the Broadcom STA Wireless Driver.

**Step 3**:

Restart computer.

**Step 4**:

In BIOS setup (press F2 as computer turns on) scroll across in setup menu and set wireless card to enable. Set Wireless hotkey to disable. Save and exit from BIOS setup.

**Step 5**:

Wireless card should work now when Ubuntu loads.


Hope this helps. I'm very new to using Ubuntu but this worked for me.

---

### Post by alpharhythm on 2011-05-07
> **colmcraven said:**
> I have a **Dell Inspiron 1501**, with a broadcom **BCM 4311** wireless card. I installed Ubuntu (Natty Narwhall) and had the same problem. I could connect to the internet via ethernet but could not get laptop to recognise wireless card.

I found a fairly simple solution elsewhere that seemed to work for me. While connected via ethernet, using the terminal I downloaded the appropriate firmware and installed.

**Step 1**:

In terminal type:

                                  [SIZE=2][COLOR=#000000][FONT=Courier, serif]~$ sudo apt-get install b43-fwcutter[/FONT][/COLOR][/SIZE]
[SIZE=2] 
                     [/SIZE]             [SIZE=2][COLOR=#000000][FONT=Courier, serif]~$ sudo apt-get install b43-fwcutter firmware-b43-installer[/FONT][/COLOR][/SIZE]
 
**Step 2**:

Then, in >Applications>Additional Drivers, uninstalled the Broadcom STA Wireless Driver.

**Step 3**:

Restart computer.

**Step 4**:

In BIOS setup (press F2 as computer turns on) scroll across in setup menu and set wireless card to enable. Set Wireless hotkey to disable. Save and exit from BIOS setup.

**Step 5**:

Wireless card should work now when Ubuntu loads.


Hope this helps. I'm very new to using Ubuntu but this worked for me.

Hi there, thanks for the reply. I'd like to test this out but I still can't use my ethernet connection in Ubuntu (see above posts) and I have to run "rfkill unblock all" after reboot to get wifi to work again. Can anyone help me out with this? Paging JosephMills!!

---

