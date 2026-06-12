---
title: "SD card contents not seen by Xubuntu"
date: 2013-05-22
forum: Multimedia Software
---

### Post by dkolars on 2013-05-22
Xubuntu 12.04, Xorg ver. 1.11.3...

Have many SD cards for camera (Nikon Coolpix L22)... recently returned from vacation with about 9 cards full of video and pics (8 Gb, 16 Gb, 32 Gb sizes)... downloaded all the data to my computer the first week of May.  No problem.  

Now, took 5 pics on a 32 Gb card to e-mail to someone...  formatted card in camera before taking pics, can see pics on camera just fine.   Pull out SD card, put into reader, plug into USB port (just like always) and have to click on the desktop icon to mount card  -- used to be that Krusader ( now Version 2.4.0-beta1) would automatically show the card, but it doesn't now.  Once I've done that, Krusader now shows the card mounted.  But, it shows no pictures in the DCIM/100NIKON directory where they should be, and shows NO pictures in any sub-directory.  So, have no way to transfer the pics to my system!  Connecting the camera via its USB cable is a joke as nothing happens and there appears to be no way to direct connect this camera to Linux...

I've recently upgraded to the latest Xubuntu kernel... perhaps this is the problem?

Not a good week for electronics... just got a Samsung Galaxy Note II and discover that I can't simply connect it via USB as I've always done with my phone, but have to use WiF FTP on phone and Filezilla on computer in order to transfer files via FTP...

And technology makes our lives easier, how, again???

All thoughts/help greatly appreciated.

---

### Post by dentaku65 on 2013-05-23
Hi,
unplug and plug back the camera, then in terminal launch these commands:
```
lsusb
gvfs-mount -l
dmesg | tail -25
```
Post the outputs

---

### Post by dkolars on 2013-05-23
dk@Desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 04b8:000f Seiko Epson Corp. 
Bus 001 Device 003: ID 1a40:0201 Terminus Technology Inc. Hub
Bus 002 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 012: ID 04b0:031c Nikon Corp. 
Bus 001 Device 004: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 005: ID 046d:0826 Logitech, Inc. 
Bus 001 Device 006: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 007: ID 059b:0370 Iomega Corp. 
Bus 001 Device 008: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 009: ID 4971:ce12 SimpleTech 
Bus 001 Device 010: ID 0bc2:2120 Seagate RSS LLC 
Bus 001 Device 011: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge

dk@Desktop:~$ gvfs-mount -l
Drive(0): 1.5 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): HD5
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): HD5 -> file:///media/HD5
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(1): CD/DVD Drive
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): Audio Disc
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
Drive(2): 1.0 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): HD2
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): HD2 -> file:///media/HD2
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(3): 1.0 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): HD3
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): HD3 -> file:///media/HD3
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(4): 1.5 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): HD7
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): HD7 -> file:///media/HD7
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Drive(5): 1.0 TB Hard Disk
  Type: GProxyDrive (GProxyVolumeMonitorGdu)
  Volume(0): HD4
    Type: GProxyVolume (GProxyVolumeMonitorGdu)
    Mount(0): HD4 -> file:///media/HD4
      Type: GProxyMount (GProxyVolumeMonitorGdu)
Volume(0): NIKON DSC COOLPIX L22-PTP
  Type: GProxyVolume (GProxyVolumeMonitorGPhoto2)

dk@Desktop:~$ dmesg | tail -25
[ 9149.662464] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.40 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=29587 PROTO=TCP SPT=443 DPT=51543 WINDOW=0 RES=0x00 RST URGP=0 
[ 9158.708221] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.72 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=27938 PROTO=TCP SPT=443 DPT=34891 WINDOW=0 RES=0x00 RST URGP=0 
[ 9158.708577] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.72 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=27939 PROTO=TCP SPT=443 DPT=34891 WINDOW=0 RES=0x00 RST URGP=0 
[ 9189.623503] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=199.30.80.32 DST=192.168.2.5 LEN=52 TOS=0x00 PREC=0x20 TTL=47 ID=36289 DF PROTO=TCP SPT=80 DPT=48798 WINDOW=40 RES=0x00 ACK FIN URGP=0 
[ 9199.003822] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=199.30.80.32 DST=192.168.2.5 LEN=52 TOS=0x00 PREC=0x20 TTL=47 ID=12151 DF PROTO=TCP SPT=80 DPT=48906 WINDOW=33 RES=0x00 ACK FIN URGP=0 
[ 9205.651543] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.79 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=43493 PROTO=TCP SPT=443 DPT=50176 WINDOW=0 RES=0x00 RST URGP=0 
[ 9205.652237] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.79 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=43495 PROTO=TCP SPT=443 DPT=50176 WINDOW=0 RES=0x00 RST URGP=0 
[ 9205.652524] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.79 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=43496 PROTO=TCP SPT=443 DPT=50176 WINDOW=0 RES=0x00 RST URGP=0 
[ 9207.651875] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.133.95 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=45 ID=41725 PROTO=TCP SPT=443 DPT=51891 WINDOW=0 RES=0x00 RST URGP=0 
[ 9207.652252] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.133.95 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=45 ID=41726 PROTO=TCP SPT=443 DPT=51891 WINDOW=0 RES=0x00 RST URGP=0 
[ 9207.652590] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.133.95 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=45 ID=41727 PROTO=TCP SPT=443 DPT=51891 WINDOW=0 RES=0x00 RST URGP=0 
[ 9225.317370] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=199.30.80.32 DST=192.168.2.5 LEN=52 TOS=0x00 PREC=0x20 TTL=47 ID=25351 DF PROTO=TCP SPT=80 DPT=48907 WINDOW=33 RES=0x00 ACK FIN URGP=0 
[10012.346875] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.41 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=36058 PROTO=TCP SPT=443 DPT=52771 WINDOW=0 RES=0x00 RST URGP=0 
[10012.347201] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.41 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=36059 PROTO=TCP SPT=443 DPT=52771 WINDOW=0 RES=0x00 RST URGP=0 
[10012.353431] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.41 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=53 ID=36060 PROTO=TCP SPT=443 DPT=52771 WINDOW=0 RES=0x00 RST URGP=0 
[12572.928472] FAT-fs (sdc1): error, fat_free_clusters: deleting FAT entry beyond EOF
[12572.928477] FAT-fs (sdc1): Filesystem has been set read-only
[36614.569719] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.209 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=49 ID=9200 PROTO=TCP SPT=443 DPT=53526 WINDOW=0 RES=0x00 RST URGP=0 
[36615.527863] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=173.194.46.74 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=48446 PROTO=TCP SPT=443 DPT=58162 WINDOW=0 RES=0x00 RST URGP=0 
[36616.519037] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.99 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=19782 PROTO=TCP SPT=443 DPT=41921 WINDOW=0 RES=0x00 RST URGP=0 
[36616.519380] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.99 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=19783 PROTO=TCP SPT=443 DPT=41921 WINDOW=0 RES=0x00 RST URGP=0 
[36616.519686] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.99 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=19784 PROTO=TCP SPT=443 DPT=41921 WINDOW=0 RES=0x00 RST URGP=0 
[36884.289881] [UFW BLOCK] IN=eth0 OUT= MAC=54:04:a6:b6:bf:90:08:86:3b:81:15:ec:08:00 SRC=74.125.225.111 DST=192.168.2.5 LEN=40 TOS=0x00 PREC=0x20 TTL=51 ID=16708 PROTO=TCP SPT=443 DPT=35299 WINDOW=0 RES=0x00 RST URGP=0 
[38793.940164] usb 2-4.3: USB disconnect, device number 11
[38829.100184] usb 2-5: new high-speed USB device number 12 using ehci_hcd

---

### Post by dentaku65 on 2013-05-23
Seems that the filesystem of SD card is corrupted
> [12572.928472] FAT-fs (sdc1): error, fat_free_clusters: deleting FAT entry beyond EOF
[12572.928477] FAT-fs (sdc1): Filesystem has been set read-only
This may be depended by unplug the sd card without unmount or because there are many big files for FAT system type
You could try to fix it with dosfsck (assuming that the SD card is sdc1)
```
sudo mount /dev/sdc1
sudo umount /dev/sdc1
sudo dosfsck -a -v /dev/sdc1
```
Please check dosfsck manual
```
man dosfsck
```
Maybe a more strong fix command needed:
```
sudo dosfsck -t -a -w -v /dev/sdc1
```

---

### Post by dkolars on 2013-05-24
Thanks for the assist... I tried all of your suggestions, but nothing worked.    I put the card into my Canon video camera, formatted it and shot some video & still pics... the computer can see and play/copy/etc. them just fine.  So, the card or USB card reader or the computer is not the problem!   

So, messed around...    If I format the card (32 Gb) with the video camera, it takes maybe 20 secs.  If I format it with the camera, it takes maybe 2 secs?!!  And, does not remove all the file system from the video camera, and the file manager says that over 30 Gb are in use.  IF the camera puts a pic onto the card, the card cannot be unmounted from the computer because "the file system is busy..."  So, cannot unmount it to format with the computer.  IF I format it with the video camera, it will unmount just fine from the file system.

The problem is my camera!  I did drop it earlier this month, and this is the first time I've used it since then... must have messed something up inside, as it will not format the card properly, and anything that the camera does makes the cards' contents (other than dir structure) unreadable.  Who'd have thought that?

So, guess I need a new camera!  Again, thank you

---

