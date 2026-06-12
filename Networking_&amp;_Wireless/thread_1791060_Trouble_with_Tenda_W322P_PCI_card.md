---
title: "Trouble with Tenda W322P PCI card"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by Ammi897 on 2011-06-26
I have recently built a new PC, I am using a Tenda W322P PCI card for my Wireless LAN. I do not understand how to install the Linux drivers onto my PC. I have searched these forums and many others for a solution but I cannot find one. I am new to Linux and do not understand most of the terminal commands, so as new user friendly as possible please. I am currently using a Ethernet connection to connect to the Internet. Any help would be appreciated.

---

### Post by josephmills on 2011-06-26
> **Ammi897 said:**
> I have recently built a new PC, I am using a Tenda W322P PCI card for my Wireless LAN. I do not understand how to install the Linux drivers onto my PC. I have searched these forums and many others for a solution but I cannot find one. I am new to Linux and do not understand most of the terminal commands, so as new user friendly as possible please. I am currently using a Ethernet connection to connect to the Internet. Any help would be appreciated.

Hi there and welcome to ubuntu forums dont know if I can help but will try please open your terminal (ctrl+alt+t) and type in ```
lspci -nn
``` then ```
lsusb
``` then ```
rfkill list all 
``` then this last one takes some time to load ```
sudo lshw -c networks 
``` and then paste the whole thing here thanks   ps when it asks for a password just type it in you will not see it but it is there it is for those nosie  shoulder peepers just press enter after entering the password and it should work

---

### Post by Ammi897 on 2011-06-26
Thanks for replying,
 

 When I do “lspci -nn” I get :
 

```
00:00.0 Host bridge [0600]: ATI Technologies Inc Radeon Xpress 200 (RS480/RS482/RX480/RX482) Chipset - Host bridge [1002:5951] (rev 01)  
 00:02.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI-X Root Port [1002:5a34]  
 00:05.0 PCI bridge [0604]: ATI Technologies Inc RS480 PCI Bridge [1002:5a37]  
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
 00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration [1022:1200]  
 00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Address Map [1022:1201]  
 00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller [1022:1202]  
 00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control [1022:1203]  
 00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] Family 10h Processor Link Control [1022:1204]  
 01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5670] [1002:68d8]  
 01:00.1 Audio device [0403]: ATI Technologies Inc Redwood HDMI Audio [Radeon HD 5600 Series] [1002:aa60]  
 02:06.0 Network controller [0280]: Ralink corp. Device [1814:3062]  
 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)  
 
```When I do “lsusb” I get :
 

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 003: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 
```When I do “rfkill list all” I get
 

```
0: phy0: Wireless LAN  
     Soft blocked: no  
     Hard blocked: no  

``` And when I do “sudo lshw -c networks” I get :
 'CPUID' then it changes to 'PCI (sysfs)' and then it changes back to 'root@ammar-desktop:~# ' (I used the sudo bash command and did the whole thing as root, hope that doesn't make a difference).

---

### Post by MooPi on 2011-06-26
I believe I'm familiar with this device and the chip it uses. Can you give us the results of (from terminal)
```
lsmod
```
I believe it uses the Ralink rt3562 driver and I have written a tutorial on the instalation.  [http://ubuntuforums.org/showthread.php?t=1608095]("http://ubuntuforums.org/showthread.php?t=1608095")
This is mostly from terminal and if you follow each instruction and take your time you should be able to configure the device

---

### Post by Ammi897 on 2011-06-26
From 'lsmod' i get :

```

Module                  Size  Used by
nls_utf8               12493  0 
isofs                  39571  0 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
binfmt_misc            13213  1 
vboxnetadp             13348  0 
vboxnetflt             27855  0 
vboxdrv               234314  2 vboxnetadp,vboxnetflt
usblp                  17827  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_via      56765  1 
arc4                   12473  2 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
rt2800pci              18159  0 
snd_hwdep              13274  1 snd_hda_codec
rt2800lib              43824  1 rt2800pci
crc_ccitt              12595  1 rt2800lib
rt2x00pci              13986  1 rt2800pci
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
rt2x00lib              39075  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
mac80211              257001  3 rt2800lib,rt2x00pci,rt2x00lib
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              156212  2 rt2x00lib,mac80211
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2434640  149 
eeprom_93cx6           12653  1 rt2800pci
ati_agp                13202  0 
soundcore              12600  1 snd
sp5100_tco             13456  0 
i2c_piix4              13095  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
k10temp                12951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
usb_storage            43946  0 
ahci                   21591  3 
uas                    17676  0 
r8169                  46630  0 
libahci                25548  1 ahci
pata_atiixp            12968  0 

```

Thanks for the reply.

---

