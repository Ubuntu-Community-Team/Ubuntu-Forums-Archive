---
title: "Grub has made windows hdd unbootable"
date: 2021-05-04
forum: MINT
---

### Post by i12 on 2021-05-04
I have Mint 19.1 problem but I think its similar to Ubuntu, so I ask.
2 HDD both were bootable, uefi bios. Mint and Windows. And grub made Windows unbootable, I can boot only from grub boot menue. Is it possible to make windows HDD bootable back without reformatting it?

---

### Post by jeremy31 on 2021-05-04
Moved to Mint

---

### Post by yancek on 2021-05-04
You haven't posted enough information for anyone to even begin to think about helping you.  Mint and Ubuntu are similar in many ways.  First, you mention that you have Mint 19.1 but make no mention of which release of windows you are using.  Microsoft has been licensing its windows OS for 35 years so that is significant information.  You indicate you are booting UEFI so if that is the case. you should be able to access the BIOS firmware on the computer and select to boot either Mint or windows.  This method has nothing to do with Grub.  What exactly is it that you thing Grub has done to render windows unbootable?  In your next sentence you state that you can only boot from Grub boot menu.  Those are conflicting statements, unless you mean you can now only boot Mint from Grub.  Clarify please..

---

### Post by i12 on 2021-05-04
Windows is 7 64 bit.

```
linux_user@MS-7850:~$ inxi -Fxz
System:
  Host: MS-7850 Kernel: 4.15.0-20-generic x86_64 bits: 64 compiler: gcc 
  v: 7.3.0 Desktop: Cinnamon 4.0.10 Distro: Linux Mint 19.1 Tessa 
  base: Ubuntu 18.04 bionic 
Machine:
  Type: Desktop Mobo: MSI model: B85-G41 PC Mate(MS-7850) v: 1.0 
  serial: <filter> UEFI: American Megatrends v: 2.8 date: 07/17/2014 
CPU:
  Topology: Dual Core model: Intel Core i3-4150 bits: 64 type: MT MCP 
  arch: Haswell rev: 3 L2 cache: 3072 KiB 
  flags: lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 28000 
  Speed: 1032 MHz min/max: 800/3500 MHz Core speeds (MHz): 1: 978 2: 980 
  3: 982 4: 969 
Graphics:
  Device-1: NVIDIA GK104 [GeForce GTX 760] vendor: Gigabyte driver: nouveau 
  v: kernel bus ID: 01:00.0 
  Display: x11 server: X.Org 1.19.6 driver: nouveau 
  unloaded: fbdev,modesetting,vesa resolution: 1280x1024~60Hz 
  OpenGL: renderer: NVE4 v: 4.3 Mesa 19.0.2 direct render: Yes 
Audio:
  Device-1: Intel 8 Series/C220 Series High Definition Audio 
  vendor: Micro-Star MSI driver: snd_hda_intel v: kernel bus ID: 00:1b.0 
  Device-2: NVIDIA GK104 HDMI Audio vendor: Gigabyte driver: snd_hda_intel 
  v: kernel bus ID: 01:00.1 
  Sound Server: ALSA v: k4.15.0-20-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  vendor: Micro-Star MSI driver: r8169 v: 2.3LK-NAPI port: d000 
  bus ID: 03:00.0 
  IF: enp3s0 state: down mac: <filter> 
Drives:
  Local Storage: total: 2.27 TiB used: 9.24 GiB (0.4%) 
  ID-1: /dev/sda vendor: Seagate model: ST3500418AS size: 465.76 GiB 
  ID-2: /dev/sdb vendor: Western Digital model: WD20EFRX-68EUZN0 
  size: 1.82 TiB 
RAID:
  Hardware-1: VIA VT6421 IDE/SATA Controller driver: sata_via v: 2.6 
  bus ID: 05:00.0 
Partition:
  ID-1: / size: 191.25 GiB used: 9.23 GiB (4.8%) fs: ext4 dev: /dev/sdb2 
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: nouveau temp: 34 C 
  Fan Speeds (RPM): N/A gpu: nouveau fan: 1380 
Info:
  Processes: 196 Uptime: 2m Memory: 7.72 GiB used: 588.1 MiB (7.4%) 
  Init: systemd runlevel: 5 Compilers: gcc: 7.5.0 Shell: bash v: 4.4.20
```

---

### Post by i12 on 2021-05-07
efimanager shows that windows boot manager is inactive. I made it active. And after that i see windows boot option in f11 boot menue, and i can boot from it. But  i  cant change boot sequense using efibootmanager.And i cant with editing bios. Bios editing makes windows boot inactive back.
I use   ~$   efibootmgr -o 0001, 000E,  {my bootlist} 
where 0001 is win boot manager, but efibootmgr writes i write wrongly.

---

### Post by tea for one on 2021-05-07
Have a look at Section [COLOR="#0000FF"]2 Changing Boot Order[/COLOR] of this website:-

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

---

### Post by ActionParsnip on 2021-05-07
Is this a dual boot and want Windows to be the default?

---

### Post by slickymaster on 2021-05-07
Threads merged.

Please do not create duplicate threads, it dilutes the community&#8217;s efforts to provide support and causes confusion.

---

### Post by yancek on 2021-05-07
```
I use   ~$   efibootmgr -o 0001, 000E,  {my bootlist}  
```

Did you use the above command or did you preface it with sudo as required?

Some systems are difficult to change with efibootmgr but you should be able to set either windows or Ubuntu to first boot priority in your BIOS firmware and change on boot if you wish.  If you can't do that you need to read the manual for the particular computer you are using or look it up online, has nothing to do with Ubuntu or Linux.

---

### Post by i12 on 2021-05-08
Of cause with sudo. Any linux will not allow such unless being a superuser.
> Some systems are difficult to change with efibootmgr but you should be  able to set either windows or Ubuntu to first boot priority in your BIOS  firmware and change on boot if you wish.  If you can't do that you need  to read the manual for the particular computer you are using or look it  up online, has nothing to do with Ubuntu or Linux.
When I try to change bootorder in BIOS it makes winbootloader inactive. So strange.

---

### Post by oldfred on 2021-05-08
You show a newer UEFI system, but most Windows 7 installs were BIOS on MBR partitioned drives.
Only about 2012 when Microsoft required vendors to install Windows 8 in UEFI mode to gpt drives did hardware and then a few Windows 7 installs were UEFI.

Post this:
sudo parted -l

UEFI & BIOS are not compatible, once you start booting in one mode or the other from UEFI, you cannot switch modes. Or grub can only boot other installs in same boot mode. 
And grub only boots working Windows. That includes Windows must not be hibernated or need chkdsk.

---

### Post by i12 on 2021-05-08
sudo parted -l
```

&#1052;&#1086;&#1076;&#1077;&#1083;&#1100;: ATA WDC WD20EFRX-68E (scsi)
&#1044;&#1080;&#1089;&#1082; /dev/sdb: 2000GB
&#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1089;&#1077;&#1082;&#1090;&#1086;&#1088;&#1072; (&#1083;&#1086;&#1075;&#1080;&#1095;./&#1092;&#1080;&#1079;&#1080;&#1095;.): 512B/4096B
&#1058;&#1072;&#1073;&#1083;&#1080;&#1094;&#1072; &#1088;&#1072;&#1079;&#1076;&#1077;&#1083;&#1086;&#1074;: gpt
&#1060;&#1083;&#1072;&#1075;&#1080; &#1076;&#1080;&#1089;&#1082;&#1072;: 

&#1053;&#1086;&#1084;&#1077;&#1088;  &#1053;&#1072;&#1095;&#1072;&#1083;&#1086;  &#1050;&#1086;&#1085;&#1077;&#1094;   &#1056;&#1072;&#1079;&#1084;&#1077;&#1088;  &#1060;&#1072;&#1081;&#1083;&#1086;&#1074;&#1072;&#1103; &#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;  &#1048;&#1084;&#1103;                   &#1060;&#1083;&#1072;&#1075;&#1080;
 1     1049kB  538MB   537MB   fat32             EFI System Partition  &#1079;&#1072;&#1075;&#1088;&#1091;&#1079;&#1086;&#1095;&#1085;&#1099;&#1081;, esp
 2     538MB   210GB   210GB   ext4
 3     210GB   2000GB  1790GB  ntfs                                    msftdata

Cant switch bootorder, like efibootmgr refuses to put winbootmgr first
i1@MS-7850:~$ sudo efibootmgr -o 0, 1, F, 10, E, B, 2, 9
Malformed BootOrder order0,
                             ^
i1@MS-7850:~$ sudo efibootmgr 
BootCurrent: 0001
Timeout: 5 seconds
BootOrder: 0001,000F,0000,0010,000E,000B,0002,0009
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0002* UEFI: Built-in EFI Shell 
Boot0009* UEFI: JetFlashTranscend 8GB 1.00
Boot000B* CD/DVD Drive 
Boot000E* Hard Drive 
Boot000F  ubuntu
Boot0010  UEFI OS

```
I can forse it boot windows one time with -n option it boot windows.

---

### Post by oldfred on 2021-05-08
Some require all 4 chars for efibootmgr -o command.
And no space after comma.

You do not have typical Windows install, but since you have Windows UEFI boot entry it looks like an UEFI install.
Windows only installs & boots from gpt partitioned drives with UEFI.

Typical UEFI/gpt Windows partitions:
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

---

