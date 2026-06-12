---
title: "Attempting to PXE boot BARTPE from Linux"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by mdshann on 2008-12-12
I am attempting to set up a PXE boot server for use at work. Every once in a while we get a computer with no CD Drive in, or with a non-working CD Drive, and it would be useful to be able to load diagnostics and such from the network. I was beginning by attempt to get a Sony Vaio laptop to load BARTPE so that I could format the drive and run the windows installer off of a USB stick. This computer does not have a CD drive or floppy drive and will not boot off of a USB stick either as there is no option in BIOS for USB boot. I have not tried a USB CDROM yet as it was not readily available.

I spent a few hours trying to get PXE boot working off of an ubuntu 8.10 install. I set up dhcp3-server with the following config:

```
allow booting;
allow bootp;

subnet 192.168.129.0 netmask 255.255.255.0
{
range dynamic-bootp 192.168.129.100 192.168.129.110;
option broadcast-address 192.168.129.255;
option routers 192.168.129.1;
default-lease-time 600;
max-lease-time 7200;
filename "/startrom.0";
server-name "bm-desktop";
next-server bm-desktop;
}

```

I have the tftpd-hpa server for my tftp boot server and it is running as a daemon (at least I think it is running as there is nothing in syslog after I boot or attempt to start it) My inetd.conf contains the following line to start the server:

```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /tftpboot
```

 I have the tftp server pointing to /tftpboot which I chmoded to 777 to be sure that all files were readable. The 'netstat' program does not show the server nor does 'ps aux' run as root. Is it really running and if so how do I tell, if not by the previously stated methods?

/tftpbot contains the following files:
```

12/12/2008  07:00 PM                 0 winnt.sif~
12/09/2008  05:33 PM       163,493,888 BARTPE.ISO
03/24/2005  08:42 PM            47,772 ntdetect.com
03/24/2005  04:29 PM           278,016 NTLDR
03/24/2005  04:29 PM            22,528 ramdisk.sys
03/24/2005  03:06 PM            24,466 startrom.0
12/12/2008  07:02 PM               149 winnt.sif
12/12/2008  09:56 PM    <DIR>          pxelinux.cfg
```

pxelinux.cfg contains a file named default with the following contents:

```
PROMPT 1
IMPLICIT 0
TIMEOUT 600

LABEL bartpe
    kernel startrom.0
```

startrom.0 is renamed from startrom.n12 from XP CD,
ntdetect.com is from same CD.
ramdisk.sys is from server2003 sp1 as it doesn't reset USB like the XP one does.
NTLDR is from server2003, renamed from setupldr.exe

winnt.sif contains:

```
[SetupData]
BootDevice = "ramdisk(0)"
BootPath = "\i386\System32\"
OsLoadOptions = "/noguiboot /fastdetect /minint /rdexportascd /rdpath=bartpe.iso"
```

But I don't think any of that is the problem. I am currently getting an error from the client which states:
```

PXE-E32: TFTP Open Timeout
```

Does anyone have any ideas? Right now I would be happy to get it to boot anything just to prove that it's not the server configuration but the files that is wrong. All the bartpe stuff came from a couple of walkthroughs that I read, the rest came from walkthroughs on how to boot Linux. Thank you for any ideas!

---

### Post by Serpreme on 2009-02-26
> **mdshann said:**
> I am attempting to set up a PXE boot server for use at work. Every once in a while we get a computer with no CD Drive in, or with a non-working CD Drive, and it would be useful to be able to load diagnostics and such from the network. I was beginning by attempt to get a Sony Vaio laptop to load BARTPE so that I could format the drive and run the windows installer off of a USB stick. This computer does not have a CD drive or floppy drive and will not boot off of a USB stick either as there is no option in BIOS for USB boot. I have not tried a USB CDROM yet as it was not readily available.

I spent a few hours trying to get PXE boot working off of an ubuntu 8.10 install. I set up dhcp3-server with the following config:

```
allow booting;
allow bootp;

subnet 192.168.129.0 netmask 255.255.255.0
{
range dynamic-bootp 192.168.129.100 192.168.129.110;
option broadcast-address 192.168.129.255;
option routers 192.168.129.1;
default-lease-time 600;
max-lease-time 7200;
filename "/startrom.0";
server-name "bm-desktop";
next-server bm-desktop;
}

```

I have the tftpd-hpa server for my tftp boot server and it is running as a daemon (at least I think it is running as there is nothing in syslog after I boot or attempt to start it) My inetd.conf contains the following line to start the server:

```
tftp           dgram   udp     wait    root  /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /tftpboot
```

 I have the tftp server pointing to /tftpboot which I chmoded to 777 to be sure that all files were readable. The 'netstat' program does not show the server nor does 'ps aux' run as root. Is it really running and if so how do I tell, if not by the previously stated methods?

/tftpbot contains the following files:
```

12/12/2008  07:00 PM                 0 winnt.sif~
12/09/2008  05:33 PM       163,493,888 BARTPE.ISO
03/24/2005  08:42 PM            47,772 ntdetect.com
03/24/2005  04:29 PM           278,016 NTLDR
03/24/2005  04:29 PM            22,528 ramdisk.sys
03/24/2005  03:06 PM            24,466 startrom.0
12/12/2008  07:02 PM               149 winnt.sif
12/12/2008  09:56 PM    <DIR>          pxelinux.cfg
```

pxelinux.cfg contains a file named default with the following contents:

```
PROMPT 1
IMPLICIT 0
TIMEOUT 600

LABEL bartpe
    kernel startrom.0
```

startrom.0 is renamed from startrom.n12 from XP CD,
ntdetect.com is from same CD.
ramdisk.sys is from server2003 sp1 as it doesn't reset USB like the XP one does.
NTLDR is from server2003, renamed from setupldr.exe

winnt.sif contains:

```
[SetupData]
BootDevice = "ramdisk(0)"
BootPath = "\i386\System32\"
OsLoadOptions = "/noguiboot /fastdetect /minint /rdexportascd /rdpath=bartpe.iso"
```

But I don't think any of that is the problem. I am currently getting an error from the client which states:
```

PXE-E32: TFTP Open Timeout
```

Does anyone have any ideas? Right now I would be happy to get it to boot anything just to prove that it's not the server configuration but the files that is wrong. All the bartpe stuff came from a couple of walkthroughs that I read, the rest came from walkthroughs on how to boot Linux. Thank you for any ideas!

A few ideas.
Try logging into the tftp server from another computer first and getting a file. I believe the syntax is 
```
tftp xxx.xxx.xxx.xxx get startrom.0
```
If you can get the file, then you know it works.
Have you checked your logs yet to see what is being output during the whole process?

tail -f /var/logs/syslog and /var/log/messages should have something for you. and it'll automatically scroll with the new output.


Thats all i can think of at the moment.

---

### Post by it84 on 2009-08-02
/tftpbot contains the following files:
```

12/12/2008  07:00 PM                 0 winnt.sif~
12/09/2008  05:33 PM       163,493,888 BARTPE.ISO
03/24/2005  08:42 PM            47,772 ntdetect.com
03/24/2005  04:29 PM           278,016 NTLDR
03/24/2005  04:29 PM            22,528 ramdisk.sys
03/24/2005  03:06 PM            24,466 startrom.0
12/12/2008  07:02 PM               149 winnt.sif
12/12/2008  09:56 PM    <DIR>          pxelinux.cfg
```sanity check. 

winnit.sif is NOT EQUAL to winnt.sif~

the ~ is a backup file, and it is size 0. if this file is needed for deploy, then most likely the
process is looking for winnt.sif of size > 0.

---

### Post by jeff.sadowski on 2011-03-05
How I do it.
I use a Menu option that the user can select bartpe or moa.
I had to install drivers in bartpe and moa to allow them to work with memdisk but using gpxelinux to download via http works so much better it is worth the effort.

My default file looks like so
```

default vesamenu.c32
prompt 0
timeout 300

menu background splash.png

menu title welcome to plop linux

menu color border 	37;40 	#00000000 #00000000 none
menu color title  	1;37;40	#00000000 #00000000 none
menu color tabmsg  	40;37	#88888888 #00000000 none
menu color sel  	1;37;42	#ffffffff #ff808080 none
menu color unsel  	1;40;32	#ff00ff00 #00000000 none


label local
menu label localboot
localboot 0

label linux
menu label plop linux
kernel http://plop-virtual-directory/kernel/bzImage
initrd http://plop-virtual-directory/kernel/initramfs.gz
append vga=1 smbmount=//10.255.0.4/ploplinux:plop:ploplinux

LABEL bartpe
MENU LABEL bartpe
KERNEL memdisk
INITRD http://bartpe-virtual-directory/bartpe.iso
APPEND iso raw

LABEL moa
MENU LABEL moa
KERNEL memdisk
INITRD http://moa-virtual-directory/moa24-std.iso
APPEND iso raw

label memtest
menu label ^memtest
kernel memtest

```

Notice I used alot from plop linux because I found it pretty complete as a pxe boot solution to fix windows boxes. Works great for changing unknown passwords with "chntpw" and great for resizing windows partitions like vm's that you increase the disk size on.

There are instructions here [http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/) to build bartpe to work with memdisk.

The only other thing I did was modifying the source code for gpxelinux.0 to look in gpxelinux.cfg for config files rather than pxelinux.cfg
thus I can load gpxelinux from pxelinux I did this because pxelinux's localboot works better than gpxelinux's

---

### Post by syafu on 2011-03-15
Hi all,
Actually my problem almost similar with this thread.

I try to install Windows XP SP2 through pxe and linux ris server.

When I pxe boot my client machine, I get this error:

```
Windows Setup:

The operating system image you selected does not contain the necessary drivers for your network adapter. Try selecting a different operating system image. If the problem persists, contact your system administrator.

Setup cannot continue. Press any key to exit.
```

I run the binlsrv and get this error:

```
Succesfully loaded 1002 devices
Binlserver started... pid 8172
Recv BINL NCQ len = 48
NCQ Driver request
[R] Mac address 00:0c:76:e2:a7:92
[R] Vid: 0x10ec
[R] Pid: 0x8169
[R] rev_u1 = 0x2
[R] rev_u2 = 0x0
[R] rev_u3 = 0x0
[R] rev    = 0x10
[R] rev2   = 0x58
[R] subsys = 0x702c1462
[R] Source path: \\192.168.1.1\REMINST\winpe
Checking PCI\VEN_10EC&DEV_8169&SUBSYS_702C1462
Checking PCI\VEN_10EC&DEV_8169
Driver not found
```

Inside syslog no error appear only DHCP REQUEST and DHCP OFFER
I build the Windows XP SP2 iso with PE builer and put inside /var/lib/tftpboot/winpe.

Samba, Dhcp, TFTP is working. Do let me know if need futher details..

Any hints?

Thanks in advance.

---

### Post by jeff.sadowski on 2011-03-15
I don't know what you did in bartpe but I just did a regular bartpe setup.
I ran bartpe with a windows xp disk as its source.
I followed instuctions I found to install winvblock drivers to support memdisk
I built a regular iso using bartpe. That iso could be burnt to disk and would work that way or can be loaded as I did via gpxelinux and memdisk or syslinux via memdisk from a usb stick. Using this method, network drivers are not needed till you run an app on bartpe to access the network. I remodify my bartpe setup adding drivers from time to time to support more network cards. If I run bartpe from a machine that has an unsupported network card it still comes up but with no network capability.

Howto get winvblock
goto [http://reboot.pro](http://reboot.pro)
on the upper right it says register
register for an account on reboot.pro
after finishing registering make sure you can login
then goto [http://reboot.pro/8168/](http://reboot.pro/8168/)
it then says to go to his recent post
it it will have a link to download winvblock
if your not logged into reboot.pro it will ask you to to download the driver.

to add winvblock to bartpe
put the following three files in your bartpe drivers in the following location
C:\pebuilder3110a\drivers\SCSIAdapter\wvblk\win_xp_2k3_32\WinVBlk.INF
C:\pebuilder3110a\drivers\SCSIAdapter\wvblk\win_xp_2k3_32\wvblk32.sys
C:\pebuilder3110a\drivers\SCSIAdapter\wvblk\win_xp_2k3_32\txtsetup.oem

---

### Post by vader95 on 2011-05-21
@syafu, you would want this link [http://support.microsoft.com/kb/315279](http://support.microsoft.com/kb/315279)

@mdshann, i'm trying this now, i'll let you know

---

