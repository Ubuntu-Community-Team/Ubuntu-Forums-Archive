---
title: "Intel AGN 4965 not working"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by out4trout on 2011-12-07
*NEWBIE* 
I just installed ubuntu 11.1 (clean install) and my wireless card is not working properly.  it is an Intel AGN 4965, in a T61 thinkpad.  It might work a couple minutes then drop.  generally it does not get on the net, and if it does, it is only there for a minute or two.
Any help would be appreciated.
Thank you!

---

### Post by out4trout on 2011-12-07
I have tried many solutions from many different posts and I just cant get it to work.  Anyone have an idea?  what info can I give you?

---

### Post by josephmills on 2011-12-07
Hello there and Welcome to the forum! 

before we can really see what the trouble is we are going to need alot more information could you please open your terminal (ctrl+alt+t) and enter this 
```

sudo lshw -c network && lspci -nn && lsmod && lspci -nn | awk '/Wireless/ {print $11 ,$15}'&& rfkill list all 

```

thanks 
Joseph

---

### Post by out4trout on 2011-12-07
thank you!  here is what came out:

  *-network                
       description: Ethernet interface 
       product: 82566MM Gigabit Network Connection 
       vendor: Intel Corporation 
       physical id: 19 
       bus info: pci@0000:00:19.0 
       logical name: eth0 
       version: 03 
       serial: 00:1e:37:88:1c:77 
       capacity: 1Gbit/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair 
       resources: irq:45 memory:fe000000-fe01ffff memory:fe225000-fe225fff ioport:1840(size=32) 
  *-network 
       description: Wireless interface 
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection 
       vendor: Intel Corporation 
       physical id: 0 
       bus info: pci@0000:03:00.0 
       logical name: wlan0 
       version: 61 
       serial: 00:1d:e0:67:00:41 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=iwl4965 driverversion=3.0.0-13-generic firmware=228.61.2.24 ip=192.168.1.7 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn 
       resources: irq:48 memory:df3fe000-df3fffff 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c) 
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c) 
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) 
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller [8086:2811] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
02:00.0 Memory controller [0580]: Intel Corporation Turbo Memory Controller [8086:444e] (rev 01) 
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4230] (rev 61) 
15:00.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ba) 
15:00.1 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 04) 
15:00.2 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 21) 
15:00.4 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 11) 
15:00.5 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 11) 
Module                  Size  Used by 
nls_iso8859_1          12617  1  
nls_cp437              12751  1  
vfat                   17308  1  
fat                    55577  1 vfat 
usb_storage            44173  1  
uas                    17699  0  
bnep                   17923  2  
rfcomm                 38408  0  
bluetooth             148839  10 bnep,rfcomm 
parport_pc             32114  0  
ppdev                  12849  0  
snd_hda_codec_analog    75090  1  
joydev                 17393  0  
arc4                   12473  2  
pcmcia                 39822  0  
snd_hda_intel          24262  2  
snd_hda_codec          91754  2 snd_hda_codec_analog,snd_hda_intel 
snd_hwdep              13276  1 snd_hda_codec 
psmouse                73673  0  
yenta_socket           27428  0  
pcmcia_rsrc            18367  1 yenta_socket 
r852                   17901  0  
sm_common              16737  1 r852 
nand                   49707  2 r852,sm_common 
nand_ids                8547  1 nand 
nand_bch               13003  1 nand 
bch                    21757  1 nand_bch 
nand_ecc               13070  1 nand 
serio_raw              12990  0  
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec 
mtd                    35852  2 sm_common,nand 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc 
iwl4965               121795  0  
thinkpad_acpi          73942  0  
iwl_legacy             71499  1 iwl4965 
snd_seq_midi           13132  0  
binfmt_misc            17292  1  
snd_rawmidi            25241  1 snd_seq_midi 
snd_seq_midi_event     14475  1 snd_seq_midi 
mac80211              393459  2 iwl4965,iwl_legacy 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28932  2 snd_pcm,snd_seq 
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq 
cfg80211              172392  3 iwl4965,iwl_legacy,mac80211 
snd                    55902  14 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm 
soundcore              12600  1 snd 
nvram                  14029  1 thinkpad_acpi 
tpm_tis                14002  0  
i915                  505108  3  
wmi                    18744  0  
drm_kms_helper         32889  1 i915 
drm                   192226  4 i915,drm_kms_helper 
i2c_algo_bit           13199  1 i915 
video                  18908  1 i915 
lp                     17455  0  
parport                40930  3 parport_pc,ppdev,lp 
sdhci_pci              13658  0  
sdhci                  27360  1 sdhci_pci 
ahci                   21634  2  
libahci                25727  1 ahci 
firewire_ohci          35854  0  
firewire_core          56937  1 firewire_ohci 
crc_itu_t              12627  1 firewire_core 
e1000e                139814  0  
AGN [8086:4230] 
0: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no

---

### Post by out4trout on 2011-12-08
By the way, the computer says that it is connected to the network and there is 100% signal, but i cannot bring up any web pages.  I failed to mention that earlier.

---

### Post by out4trout on 2011-12-08
I am downloading the 64 bit installer now and will install it this afternoon.  maybe there will be some sort of magic that happens.  I will post back when it is complete.

---

### Post by out4trout on 2011-12-08
could not get the 64 bit to install.  so i am still trying to figure out the driver issue for the wireless.  Any thoughts?

---

### Post by out4trout on 2011-12-08
I am now on the internet with the Ethernet card and it seems to work wonderfully.  what can I do to get the wireless up?

---

### Post by linuxman94 on 2011-12-11
Try installing the "linux-backports-modules-headers-oneiric-generic" package.  Open up terminal (search it in the dash) and copy&paste this in:

```
sudo apt-get install linux-backports-modules-headers-oneiric-generic 
```

You'll get a password prompt.  Enter your password and press enter.  You won't see anything on the screen that shows you are entering your password.  This is for security purposes.  After it installs, reboot and try the wireless again.

---

### Post by out4trout on 2011-12-14
Thank you for the reply! 
The install failed, so I tried to download it from the "Ubuntu software center" and that failed as well.  when I attempted to install from the terminal as you instructed here is what I saw on the screen:

scott@scott-ThinkPad-T61:~$ sudo apt-get install linux-backports-modules-headers-oneiric-generic
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-lbm-3.0.0-13-generic
The following NEW packages will be installed:
  linux-backports-modules-headers-oneiric-generic
  linux-headers-lbm-3.0.0-13-generic
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,210 B of archives.
After this operation, 77.8 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/universe linux-headers-lbm-3.0.0-13-generic amd64 3.0.0-13.5 [2,780 B]
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) oneiric-updates/main linux-backports-modules-headers-oneiric-generic amd64 3.0.0.13.15
  404  Not Found [IP: 91.189.88.31 80]
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) oneiric-security/main linux-backports-modules-headers-oneiric-generic amd64 3.0.0.13.15
  404  Not Found [IP: 91.189.92.166 80]
Fetched 2,780 B in 0s (3,976 B/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-headers-oneiric-generic_3.0.0.13.15_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-backports-modules-headers-oneiric-generic_3.0.0.13.15_amd64.deb)  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

What can I do now?

---

### Post by linuxman94 on 2011-12-16
Are you using a wired connection to download the packages instead of relying on the flaky wireless connection?

---

### Post by out4trout on 2011-12-16
Yes.  And it appears to hold signal well and work just fine.

---

### Post by out4trout on 2011-12-18
Ubuntu just downloaded and installed 46 updates or something, and the wireless seems to be working!!!
problem solved!!!
I am pleased!  thank you for all your help along the way!

---

### Post by out4trout on 2011-12-18
interestingly, my wife turned on the laptop upstairs (IBM running xp) and as soon as she got on the Internet, my wireless on the ubuntu machine dropped out.  What would cause that to happen?  It would seem that this may have been the cause of the connectivity problem the whole time!  I have a netgear router if that matters.
What can I do to address the issue?

---

### Post by linuxman94 on 2011-12-19
Glad to hear that the card works now.  

As for the connection issue with the netgear, what is the model number of the router? It should be on the bottom of the router somewhere.

---

### Post by out4trout on 2011-12-19
WNR854T is what I am seeing.

---

