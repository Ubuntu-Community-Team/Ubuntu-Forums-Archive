---
title: "Video failure on startup 9.1"
date: 2010-01-24
forum: Multimedia Software
---

### Post by dradams on 2010-01-24
Hi,
 
I know there are a number of threads relating to 9.10 video issues, but after four hours of reading this morning, no clear answers arose. I'd truely appreciate any help you can give.
 
Problem: About 1 hour after successfully installing 9.10, the window elements started flickering and were inaccessible. I was working on intalling dimdim, but I did not touch any system files around the time the failure occurred. Thereafter, any regular login attempt results in a flickering black box on top of the new dim-gray-light ubuntu login window. The machine needs to be rebooted to get out of this mode. System restore mode works perfectly. startx starts the x environment, but with the flickering and uselnessness. 
 
The machine is a dual bood Ubuntu/Vista box (yeah, I know, Vista came with it). It is an intel quad core 2.33 MHz processor. The video is a cheapo on-board type. I have included system stats at the end of this message. 
 
Please let me know what I can provide that might be useful. Thanks much! -David
 
System Information report written at: 01/24/10 14:51:33
System Name: MERCURY
[Components]
 
[Multimedia]
 
[Audio Codecs]
CODEC Manufacturer Description Status File Version Size Creation Date 
c:\windows\system32\msadp32.acm Microsoft Corporation OK C:\Windows\system32\MSADP32.ACM 6.0.6000.16386 22.00 KB (22,528 bytes) 11/2/2006 5:53 AM 
c:\windows\system32\msgsm32.acm Microsoft Corporation OK C:\Windows\system32\MSGSM32.ACM 6.0.6000.16386 28.00 KB (28,672 bytes) 11/2/2006 5:53 AM 
c:\windows\system32\l3codeca.acm Fraunhofer Institut Integrierte Schaltungen IIS Fraunhofer IIS MPEG Layer-3 Codec OK C:\Windows\system32\L3CODECA.ACM 1.9.0.401 70.50 KB (72,192 bytes) 1/20/2008 9:51 PM 
c:\windows\system32\msg711.acm Microsoft Corporation OK C:\Windows\system32\MSG711.ACM 6.0.6000.16386 14.00 KB (14,336 bytes) 11/2/2006 5:53 AM 
c:\windows\system32\imaadp32.acm Microsoft Corporation OK C:\Windows\system32\IMAADP32.ACM 6.0.6000.16386 21.00 KB (21,504 bytes) 11/2/2006 5:53 AM 
[Video Codecs]
CODEC Manufacturer Description Status File Version Size Creation Date 
c:\windows\system32\iyuv_32.dll Microsoft Corporation OK C:\Windows\system32\IYUV_32.DLL 6.0.6000.16386 52.50 KB (53,760 bytes) 11/2/2006 5:43 AM 
c:\windows\system32\msyuv.dll Microsoft Corporation OK C:\Windows\system32\MSYUV.DLL 6.0.6000.16386 24.50 KB (25,088 bytes) 11/2/2006 5:43 AM 
c:\windows\system32\msvidc32.dll Microsoft Corporation OK C:\Windows\system32\MSVIDC32.DLL 6.0.6001.18000 37.50 KB (38,400 bytes) 1/20/2008 9:48 PM 
c:\windows\system32\msrle32.dll Microsoft Corporation OK C:\Windows\system32\MSRLE32.DLL 6.0.6000.16386 15.50 KB (15,872 bytes) 11/2/2006 5:53 AM 
c:\windows\system32\tsbyuv.dll Microsoft Corporation OK C:\Windows\system32\TSBYUV.DLL 6.0.6000.16386 13.50 KB (13,824 bytes) 11/2/2006 5:43 AM 
[CD-ROM]
Item Value 
Drive E: 
Description CD-ROM Drive 
Media Loaded No 
Media Type UNKNOWN 
Name TSSTcorp CDDVDW TS-H653R 
Manufacturer (Standard CD-ROM drives) 
Status OK 
Transfer Rate -1.00 kbytes/sec 
SCSI Target ID 1 
PNP Device ID IDE\CDROMTSSTCORP_CDDVDW_TS-H653R________________0301____\4&1820EC13&0&0.1.0 
Driver c:\windows\system32\drivers\cdrom.sys (6.0.6001.18000, 78.00 KB (79,872 bytes), 1/20/2008 9:46 PM) 
[Sound Device]
Item Value 
Name Realtek High Definition Audio 
Manufacturer Realtek 
Status OK 
PNP Device ID HDAUDIO\FUNC_01&VEN_10EC&DEV_0888&SUBSYS_103C2A6F&REV_1001\4&9C41AD1&0&0001 
Driver c:\windows\system32\drivers\rtkvhd64.sys (6.0.1.5789, 1.63 MB (1,708,192 bytes), 9/22/2009 5:31 PM) 
[Display]
Item Value 
Name Intel(R) G33/G31 Express Chipset Family 
PNP Device ID PCI\VEN_8086&DEV_29C2&SUBSYS_2A6F103C&REV_02\3&11583659&0&10 
Adapter Type Intel(R) GMA 3100, Intel Corporation compatible 
Adapter Description Intel(R) G33/G31 Express Chipset Family 
Adapter RAM 320.00 MB (335,544,320 bytes) 
Installed Drivers igdumd64.dll 
Driver Version Not Available 
INF File oem80.inf (iBLB0 section) 
Color Planes Not Available 
Color Table Entries 4294967296 
Resolution 1680 x 1050 x 60 hertz 
Bits/Pixel 32 
Memory Address 0xFE800000-0xFE87FFFF 
I/O Port 0x0000C080-0x0000C087 
Memory Address 0xD0000000-0xDFFFFFFF 
Memory Address 0xFE700000-0xFE7FFFFF 
IRQ Channel IRQ 16 
I/O Port 0x000003B0-0x000003BB 
I/O Port 0x000003C0-0x000003DF 
Memory Address 0xA0000-0xBFFFF 
Driver c:\windows\system32\drivers\igdkmd64.sys (7.15.10.1666, 9.80 MB (10,276,352 bytes), 9/22/2009 4:51 PM) 
[Infrared]
Item Value 
[Input]
 
[Keyboard]
Item Value 
Description USB Human Interface Device 
Name Enhanced (101- or 102-key) 
Layout 00000409 
PNP Device ID USB\VID_045E&PID_00DB&MI_00\7&574F281&0&0000 
Number of Function Keys 12 
Driver c:\windows\system32\drivers\hidusb.sys (6.0.6001.18000, 15.50 KB (15,872 bytes), 1/20/2008 9:46 PM) 
[Pointing Device]
Item Value 
Hardware Type USB Human Interface Device 
Number of Buttons 0 
Status OK 
PNP Device ID USB\VID_046D&PID_C526&MI_00\7&1BA1B322&0&0000 
Power Management Supported No 
Double Click Threshold Not Available 
Handedness Not Available 
Driver c:\windows\system32\drivers\hidusb.sys (6.0.6001.18000, 15.50 KB (15,872 bytes), 1/20/2008 9:46 PM) 
[Modem]
Item Value 
Name Agere Systems PCI-SV92EX Soft Modem 
Description Agere Systems PCI-SV92EX Soft Modem 
Device ID PCI\VEN_11C1&DEV_0630&SUBSYS_063011C1&REV_01\4&37C315F9&0&00E1 
Device Type Internal Modem 
Attached To COM3 
Answer Mode Not Available 
PNP Device ID PCI\VEN_11C1&DEV_0630&SUBSYS_063011C1&REV_01\4&37C315F9&0&00E1 
Provider Name Agere 
Modem INF Path oem75.inf 
Modem INF Section AGERE_PCI_EX 
Blind Off X4 
Blind On X3 
Compression Off %C0 
Compression On %C1 
Error Control Forced \N4 
Error Control Off \N1 
Error Control On \N3 
Flow Control Hard &K3 
Flow Control Off &K0 
Flow Control Soft &K4 
DCB &#x001c; 
Default < 
Inactivity Timeout 0 
Modulation Bell B1B16B2 
Modulation CCITT B0B15B2 
Prefix AT 
Pulse P 
Reset AT&F<cr> 
Responses Key Name Agere Systems PCI-SV92EX Soft Modem::Agere::Agere 
Speaker Mode Dial M1 
Speaker Mode Off M0 
Speaker Mode On M2 
Speaker Mode Setup M3 
Speaker Volume High L3 
Speaker Volume Low L0 
Speaker Volume Med L2 
String Format Not Available 
Terminator <cr> 
Tone T 
Memory Address 0xFEAFF000-0xFEAFFFFF 
IRQ Channel IRQ 17 
Driver c:\windows\system32\drivers\modem.sys (6.0.6001.18000, 39.50 KB (40,448 bytes), 1/20/2008 9:50 PM) 
[Network]
 
[Adapter]
Item Value 
Name [00000000] WAN Miniport (L2TP) 
Adapter Type Not Available 
Product Type WAN Miniport (L2TP) 
Installed Yes 
PNP Device ID ROOT\MS_L2TPMINIPORT\0000 
Last Reset 1/24/2010 1:31 PM 
Index 0 
Service Name Rasl2tp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\rasl2tp.sys (6.0.6001.18000, 122.00 KB (124,928 bytes), 1/20/2008 9:49 PM) 
 
Name [00000001] WAN Miniport (PPTP) 
Adapter Type Wide Area Network (WAN) 
Product Type WAN Miniport (PPTP) 
Installed Yes 
PNP Device ID ROOT\MS_PPTPMINIPORT\0000 
Last Reset 1/24/2010 1:31 PM 
Index 1 
Service Name PptpMiniport 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 50:50:54:50:30:30 
Driver c:\windows\system32\drivers\raspptp.sys (6.0.6001.18000, 96.50 KB (98,816 bytes), 1/20/2008 9:49 PM) 
 
Name [00000002] WAN Miniport (PPPOE) 
Adapter Type Wide Area Network (WAN) 
Product Type WAN Miniport (PPPOE) 
Installed Yes 
PNP Device ID ROOT\MS_PPPOEMINIPORT\0000 
Last Reset 1/24/2010 1:31 PM 
Index 2 
Service Name RasPppoe 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 33:50:6F:45:30:30 
Driver c:\windows\system32\drivers\raspppoe.sys (6.0.6001.18000, 49.00 KB (50,176 bytes), 1/20/2008 9:49 PM) 
 
Name [00000003] WAN Miniport (IPv6) 
Adapter Type Not Available 
Product Type WAN Miniport (IPv6) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANIPV6\0000 
Last Reset 1/24/2010 1:31 PM 
Index 3 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6001.18000, 165.50 KB (169,472 bytes), 1/20/2008 9:48 PM) 
 
Name [00000004] Realtek RTL8168C(P)/8111C(P) Family PCI-E GBE NIC 
Adapter Type Ethernet 802.3 
Product Type Realtek RTL8168C(P)/8111C(P) Family PCI-E GBE NIC 
Installed Yes 
PNP Device ID PCI\VEN_10EC&DEV_8168&SUBSYS_2A6F103C&REV_02\4&5D52B92&0&00E2 
Last Reset 1/24/2010 1:31 PM 
Index 4 
Service Name RTL8169 
IP Address 192.168.8.54, fe80::e42d:54c1:31d5:5565 
IP Subnet 255.255.255.0, 64 
Default IP Gateway 192.168.8.1 
DHCP Enabled Yes 
DHCP Server 192.168.8.1 
DHCP Lease Expires 1/25/2010 1:32 PM 
DHCP Lease Obtained 1/24/2010 1:32 PM 
MAC Address 00:26:18:65:3C:95 
I/O Port 0x0000E800-0x0000E8FF 
Memory Address 0xFEBFF000-0xFEBFFFFF 
Memory Address 0xFDFF0000-0xFDFFFFFF 
IRQ Channel IRQ 18 
Driver c:\windows\system32\drivers\rtlh64.sys (6.216.120.2009, 191.00 KB (195,584 bytes), 9/22/2009 5:31 PM) 
 
Name [00000005] Microsoft Tun Miniport Adapter 
Adapter Type Ethernet 802.3 
Product Type Microsoft Tun Miniport Adapter 
Installed Yes 
PNP Device ID ROOT\*TUNMP\0000 
Last Reset 1/24/2010 1:31 PM 
Index 5 
Service Name tunmp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address 02:00:54:55:4E:01 
Driver c:\windows\system32\drivers\tunmp.sys (6.0.6001.18000, 18.00 KB (18,432 bytes), 1/20/2008 9:48 PM) 
 
Name [00000006] WAN Miniport (IP) 
Adapter Type Not Available 
Product Type WAN Miniport (IP) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANIP\0000 
Last Reset 1/24/2010 1:31 PM 
Index 6 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6001.18000, 165.50 KB (169,472 bytes), 1/20/2008 9:48 PM) 
 
Name [00000007] Microsoft ISATAP Adapter 
Adapter Type Tunnel 
Product Type Microsoft ISATAP Adapter 
Installed Yes 
PNP Device ID ROOT\*ISATAP\0001 
Last Reset 1/24/2010 1:31 PM 
Index 7 
Service Name tunnel 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\tunnel.sys (6.0.6001.18000, 27.50 KB (28,160 bytes), 1/20/2008 9:48 PM) 
 
Name [00000009] RAS Async Adapter 
Adapter Type Not Available 
Product Type RAS Async Adapter 
Installed Yes 
PNP Device ID Not Available 
Last Reset 1/24/2010 1:31 PM 
Index 9 
Service Name AsyncMac 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
 
Name [00000010] WAN Miniport (SSTP) 
Adapter Type Not Available 
Product Type WAN Miniport (SSTP) 
Installed Yes 
PNP Device ID ROOT\MS_SSTPMINIPORT\0000 
Last Reset 1/24/2010 1:31 PM 
Index 10 
Service Name RasSstp 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\rassstp.sys (6.0.6001.18000, 76.50 KB (78,336 bytes), 1/20/2008 9:51 PM) 
 
Name [00000011] WAN Miniport (Network Monitor) 
Adapter Type Not Available 
Product Type WAN Miniport (Network Monitor) 
Installed Yes 
PNP Device ID ROOT\MS_NDISWANBH\0000 
Last Reset 1/24/2010 1:31 PM 
Index 11 
Service Name NdisWan 
IP Address Not Available 
IP Subnet Not Available 
Default IP Gateway Not Available 
DHCP Enabled No 
DHCP Server Not Available 
DHCP Lease Expires Not Available 
DHCP Lease Obtained Not Available 
MAC Address Not Available 
Driver c:\windows\system32\drivers\ndiswan.sys (6.0.6001.18000, 165.50 KB (169,472 bytes), 1/20/2008 9:48 PM) 
[Protocol]
Item Value 
Name MSAFD Tcpip [TCP/IP] 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 16 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD Tcpip [UDP/IP] 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 16 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name MSAFD Tcpip [TCP/IPv6] 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 28 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name MSAFD Tcpip [UDP/IPv6] 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 28 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption No 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name RSVP TCPv6 Service Provider 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 28 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name RSVP TCP Service Provider 
Connectionless Service No 
Guarantees Delivery Yes 
Guarantees Sequencing Yes 
Maximum Address Size 16 bytes 
Maximum Message Size 0 bytes 
Message Oriented No 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting No 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data Yes 
Supports Graceful Closing Yes 
Supports Guaranteed Bandwidth No 
Supports Multicasting No 
 
Name RSVP UDPv6 Service Provider 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 28 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 28 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
 
Name RSVP UDP Service Provider 
Connectionless Service Yes 
Guarantees Delivery No 
Guarantees Sequencing No 
Maximum Address Size 16 bytes 
Maximum Message Size 63.99 KB (65,527 bytes) 
Message Oriented Yes 
Minimum Address Size 16 bytes 
Pseudo Stream Oriented No 
Supports Broadcasting Yes 
Supports Connect Data No 
Supports Disconnect Data No 
Supports Encryption Yes 
Supports Expedited Data No 
Supports Graceful Closing No 
Supports Guaranteed Bandwidth No 
Supports Multicasting Yes 
[WinSock]
Item Value 
File c:\windows\syswow64\wsock32.dll 
Size 15.00 KB (15,360 bytes) 
Version 6.0.6001.18000 
 
File c:\windows\system32\wsock32.dll 
Size 18.00 KB (18,432 bytes) 
Version 6.0.6001.18000 
[Ports]
 
[Serial]
Item Value 
[Parallel]
Item Value 
[Storage]
 
[Drives]
Item Value 
Drive C: 
Description Local Fixed Disk 
Compressed No 
File System NTFS 
Size 201.00 GB (215,823,085,568 bytes) 
Free Space 164.35 GB (176,472,961,024 bytes) 
Volume Name HP 
Volume Serial Number 5EDA67F4 
 
Drive D: 
Description Local Fixed Disk 
Compressed No 
File System NTFS 
Size 13.81 GB (14,830,178,304 bytes) 
Free Space 1.95 GB (2,094,477,312 bytes) 
Volume Name FACTORY_IMAGE 
Volume Serial Number 9CA46A86 
 
Drive E: 
Description CD-ROM Disc 
 
Drive F: 
Description Removable Disk 
 
Drive G: 
Description Removable Disk 
 
Drive H: 
Description Removable Disk 
 
Drive I: 
Description Removable Disk 
[Disks]
Item Value 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model ST3750528AS 
Bytes/Sector 512 
Media Loaded Yes 
Media Type Fixed hard disk 
Partitions 4 
SCSI Bus 0 
SCSI Logical Unit 0 
SCSI Port 0 
SCSI Target ID 0 
Sectors/Track 63 
Size 698.64 GB (750,153,761,280 bytes) 
Total Cylinders 91,201 
Total Sectors 1,465,144,065 
Total Tracks 23,256,255 
Tracks/Cylinder 255 
Partition Disk #0, Partition #0 
Partition Size 201.00 GB (215,823,089,664 bytes) 
Partition Starting Offset 32,256 bytes 
Partition Disk #0, Partition #1 
Partition Size 13.81 GB (14,830,179,840 bytes) 
Partition Starting Offset 735,323,581,440 bytes 
Partition Disk #0, Partition #2 
Partition Size 483.82 GB (519,500,459,520 bytes) 
Partition Starting Offset 215,823,121,920 bytes 
 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model Generic- Compact Flash USB Device 
Bytes/Sector Not Available 
Media Loaded Yes 
Media Type Not Available 
Partitions 0 
SCSI Bus Not Available 
SCSI Logical Unit Not Available 
SCSI Port Not Available 
SCSI Target ID Not Available 
Sectors/Track Not Available 
Size Not Available 
Total Cylinders Not Available 
Total Sectors Not Available 
Total Tracks Not Available 
Tracks/Cylinder Not Available 
 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model Generic- MS/MS-Pro USB Device 
Bytes/Sector Not Available 
Media Loaded Yes 
Media Type Not Available 
Partitions 0 
SCSI Bus Not Available 
SCSI Logical Unit Not Available 
SCSI Port Not Available 
SCSI Target ID Not Available 
Sectors/Track Not Available 
Size Not Available 
Total Cylinders Not Available 
Total Sectors Not Available 
Total Tracks Not Available 
Tracks/Cylinder Not Available 
 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model Generic- SD/MMC USB Device 
Bytes/Sector Not Available 
Media Loaded Yes 
Media Type Not Available 
Partitions 0 
SCSI Bus Not Available 
SCSI Logical Unit Not Available 
SCSI Port Not Available 
SCSI Target ID Not Available 
Sectors/Track Not Available 
Size Not Available 
Total Cylinders Not Available 
Total Sectors Not Available 
Total Tracks Not Available 
Tracks/Cylinder Not Available 
 
Description Disk drive 
Manufacturer (Standard disk drives) 
Model Generic- SM/xD-Picture USB Device 
Bytes/Sector Not Available 
Media Loaded Yes 
Media Type Not Available 
Partitions 0 
SCSI Bus Not Available 
SCSI Logical Unit Not Available 
SCSI Port Not Available 
SCSI Target ID Not Available 
Sectors/Track Not Available 
Size Not Available 
Total Cylinders Not Available 
Total Sectors Not Available 
Total Tracks Not Available 
Tracks/Cylinder Not Available 
[SCSI]
Item Value 
Name Intel(R) ICH8R/ICH9R/ICH10R/DO SATA RAID Controller 
Manufacturer Intel 
Status OK 
PNP Device ID PCI\VEN_8086&DEV_2822&SUBSYS_2A6F103C&REV_02\3&11583659&0&FA 
I/O Port 0x0000D880-0x0000D887 
I/O Port 0x0000D800-0x0000D803 
I/O Port 0x0000D480-0x0000D487 
I/O Port 0x0000D400-0x0000D403 
I/O Port 0x0000D080-0x0000D09F 
Memory Address 0xFE8FF000-0xFE8FF7FF 
IRQ Channel IRQ 19 
Driver c:\windows\system32\drivers\iastor.sys (8.7.0.1007, 397.52 KB (407,064 bytes), 9/22/2009 5:30 PM) 
 
Name Microsoft iSCSI Initiator 
Manufacturer Microsoft 
Status OK 
PNP Device ID ROOT\ISCSIPRT\0000 
Driver c:\windows\system32\drivers\msiscsi.sys (6.0.6001.18000, 210.05 KB (215,096 bytes), 1/20/2008 9:46 PM) 
[IDE]
Item Value 
[Printing]
Name Driver Port Name Server Name 
Microsoft XPS Document Writer Microsoft XPS Document Writer XPSPort: 
[Problem Devices]
Device PNP Device ID Error Code 
[USB]
Device PNP Device ID 
Intel(R) ICH9 Family USB Universal Host Controller - 2937 PCI\VEN_8086&DEV_2937&SUBSYS_2A6F103C&REV_02\3&11583659&0&D0 
Intel(R) ICH9 Family USB Universal Host Controller - 2938 PCI\VEN_8086&DEV_2938&SUBSYS_2A6F103C&REV_02\3&11583659&0&D1 
Intel(R) ICH9 Family USB2 Enhanced Host Controller - 293C PCI\VEN_8086&DEV_293C&SUBSYS_2A6F103C&REV_02\3&11583659&0&D7 
Intel(R) ICH9 Family USB Universal Host Controller - 2934 PCI\VEN_8086&DEV_2934&SUBSYS_2A6F103C&REV_02\3&11583659&0&E8 
Intel(R) ICH9 Family USB Universal Host Controller - 2935 PCI\VEN_8086&DEV_2935&SUBSYS_2A6F103C&REV_02\3&11583659&0&E9 
Intel(R) ICH9 Family USB Universal Host Controller - 2936 PCI\VEN_8086&DEV_2936&SUBSYS_2A6F103C&REV_02\3&11583659&0&EA 
Intel(R) ICH9 Family USB Universal Host Controller - 2939 PCI\VEN_8086&DEV_2939&SUBSYS_2A6F103C&REV_02\3&11583659&0&EB 
Intel(R) ICH9 Family USB2 Enhanced Host Controller - 293A PCI\VEN_8086&DEV_293A&SUBSYS_2A6F103C&REV_02\3&11583659&0&EF

---

### Post by dradams on 2010-01-25
Nothing? Dimdim was a pain in the a** to get installed, I'd hate to have to revert to 9.04 because 9.10 turns out to be too buggy...

---

### Post by dradams on 2010-01-26
Hi,

Is there any less-useless way to get support for ubuntu problems? The only response I got was a guy who wrote off-line to say, basically, 9.10 video support is terrible--roll back to 9.04. 

-David

---

