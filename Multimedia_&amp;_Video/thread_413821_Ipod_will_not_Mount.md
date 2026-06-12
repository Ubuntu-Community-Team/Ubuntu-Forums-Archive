---
title: "Ipod will not Mount"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by rdavis7408 on 2007-04-19
My 3rd generation ipod will no longer auto mount. I have searched and attempted to mount manually but do not know how to tell what device the ipod is called. For example I have tried the following with no success:

sudo mount /dev/sda2 /mnt/ipod vfat
sudo mount /dev/sda /mnt/ipod vfat
sudo mount /dev/sdc /mnt/ipod vfat
sudo mount /dev/sda2 /media/ipod vfat
sudo mount /dev/sda /media/ipod vfat

When I go to the following:

sudo gedit /etc/fstab

And add the following at the bottom of the file:

/dev/sdc2 /media/iPod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000 ,user,defaults,noatime,iocharset=utf8 0 0

I can then see it in the file system in Computer but am unable to mount it.

I get a error: mount: special device /dev/sdc does not exist

I am connecting using a fire wire. 

The following is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/hda1
UUID=47ecd00e-7b06-4e59-9d91-e9056f3be3b0 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5
UUID=a27e3198-9895-486b-a57c-0c338d939354 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/ /media/floppy0 auto rw,user,noauto 0 0

The following is my mtab file:

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.17-11-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
_/dev/hda1 /mnt/ipod ext3 rw 0 0_

I do not know that the final line in the mtab file has always been there, I may have added it when trying to fix the problem. Because the device hda1 appears in the first line also.

I am confused also by how to determine the device name inorder to mount it.

Additionally, I have tried with the following line in the fstab in and deleted:

/dev/sdc /media/ipod vfat nosuid,,nodev,rw,umask=077,gid=1000,uid=1000 ,user,defaults,noatime,iocharset=utf8 0 0

I have tried to load the drivers for the saa7134 from one tutorial. 

I have followed the instructions for the tutorial at the following:

[http://www.ubuntugeek.com/howto-mount-2nd-generation-ipod-in-ubuntu.html](http://www.ubuntugeek.com/howto-mount-2nd-generation-ipod-in-ubuntu.html)

I have followed the instructions at the following url:

[http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu](http://www.ubuntux.org/how-to-use-an-ipod-with-ubuntu)

I am quite confused by now and would welcome any help. If I could just know the device name that would be a start.

I really could use any ideas on this issue. Thanks ahead of time.

---

### Post by tictacman on 2007-04-19
Ubuntu should recognize your ipod out of the box without having to add any lines to /etc/fstab.  I plugged my nano in today for the first time and was able to read/write files from the ipod using amarok.  Perhaps the settings have somehow been altered so the ipod doesn't mount automatically.  Do you get an icon on your desktop when its plugged in? Which version of ubuntu are you using ie. 6.06, 6.10 (edgy) or 7.04 (feisty)?  What windows manager ie kde,gnome,xfce4?

---

### Post by rdavis7408 on 2007-04-19
I do not get the icon on the desktop indicating that the ipod is connected. I am useing the Edgy version of Ubunut. I am using the Gnome desktop.

---

### Post by madcow72 on 2007-04-19
When you say 3rd Generation Ipod, we're talking about one of the older hard drive based ipods?  As tictacman said, any of those should mount out-of-the-box, especially if you're using Edgy or above.  (I don't have enough experience with Dapper to say, but I would assume it works fine there as well.)

Funny thing, I actually wrote the first "howto" that you mentioned, but I wrote it in Ubuntu forums [here.]("http://ubuntuforums.org/showthread.php?t=321397")  I just realized that I was stupid when I wrote that and didn't specify that I was talking about a 2nd Gen Nano, (NOT 2nd Gen regular Ipods.)  That howto is helpful for ipods recognized as RAID devices.

After plugging it in, if you run either:
```
lspci
```
or
```
dmesg | tail -32
```

What do you get?  Is it being recognized?

---

### Post by rdavis7408 on 2007-04-19
After running "lspci" I get the following result:

00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 1394) Controller (rev a3)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
01:06.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d0)
01:08.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 50)
02:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)


After running the "dmesg | tail -32" command I get the following:

rdavis@rdavis-desktop:~$ dmesg | tail -32
[17179593.692000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179593.976000] saa7134 ALSA driver for DMA sound loaded
[17179593.976000] saa7133[0]/alsa: saa7133[0] at 0xe7000000 irq 177 registered as card -2
[17179594.180000] lp0: using parport0 (interrupt-driven).
[17179594.284000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.284000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.320000] Adding 3791300k swap on /dev/disk/by-uuid/a27e3198-9895-486b-a57c-0c338d939354.  Priority:-1 extents:1 across:3791300k
[17179594.380000] EXT3 FS on hda1, internal journal
[17179595.076000] NET: Registered protocol family 10
[17179595.080000] lo: Disabled Privacy Extensions
[17179595.080000] IPv6 over IPv4 tunneling driver
[17179600.188000] ACPI: Power Button (FF) [PWRF]
[17179600.188000] ACPI: Power Button (CM) [PWRB]
[17179600.188000] ACPI: Sleep Button (CM) [SLPB]
[17179600.296000] ibm_acpi: ec object not found
[17179600.324000] pcc_acpi: loading...
[17179600.692000] acpi_cpufreq: Unknown symbol cpu_online_map
[17179603.272000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179603.272000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179603.272000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179604.108000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179604.108000] apm: overridden by ACPI.
[17179605.536000] eth0: no IPv6 routers present
[17179610.472000] Bluetooth: Core ver 2.8
[17179610.472000] NET: Registered protocol family 31
[17179610.472000] Bluetooth: HCI device and connection manager initialized
[17179610.472000] Bluetooth: HCI socket layer initialized
[17179610.588000] Bluetooth: L2CAP ver 2.8
[17179610.588000] Bluetooth: L2CAP socket layer initialized
[17179610.600000] Bluetooth: RFCOMM socket layer initialized
[17179610.600000] Bluetooth: RFCOMM TTY layer initialized
[17179610.600000] Bluetooth: RFCOMM ver 1.7

As I look through these results I do not see anything that makes sense.

Any thoughts?

Thanks

---

### Post by madcow72 on 2007-04-19
Yeah, I don't see it in there either.  Stupid question, I know, but your ipod was connected when you ran those commands right?  

Does your ipod's screen say "Do Not Disconnect" on there?  Also, just wanted to verify that you're talking about a 3rd Generation hard drive-based classic-looking ipod with a backlit monochrome screen?

I wonder if the ROM may just be screwy?  Worst case scenario, if you can't figure it out, you could always try backing up your songs, connecting it to ITunes in OSX or Windows, resetting the ipod to factory condition, and then connecting it to your computer again...

---

### Post by rdavis7408 on 2007-04-19
The ipod was connected when I ran the commands. It is a 3rd Generation Ipod with the hard drive. It has a wheel and four little buttons at the top. 

Let me see if I can restore the Ipod on a Windows machine and see how that goes. Thanks for the thought.

If you think of any thing else, please let me know. I will post how the progress is going once I try resetting to factory settings.

---

### Post by rdavis7408 on 2007-04-19
Okay. It is fixed. I did connected the Ipod to a Windows XP Machine. Opened ITunes then disconnected the Ipod from the Windows XP machine. I then plugged it back into the Ubuntu machine and "puff" it mounted and I can see all my files. 

Thank you ---- THANK YOU ---- Everyone's Help is appreciated so much.

---

### Post by rdavis7408 on 2007-04-19
Just for those searching with similar issues. The device was 
/dev/sda2 just like it said in all the articles/forums and tutorials.

Thanks again.

---

### Post by madcow72 on 2007-04-19
Cool!  So you didn't have to reset to factory conditions?  Just plugged it in, disconnected, and then into Ubuntu?  

Kinda weird, but glad it's working!

---

### Post by tictacman on 2007-04-21
Sounds to me like a bad connection/faulty lead.

Congrats on getting it working though.:)

---

### Post by rdavis7408 on 2007-04-21
Yep. I would rather be lucky than good. Thanks for all your help.

---

### Post by kalahari875 on 2007-05-01
My 8GB iPod nano (6th generation?) won't mount on its own in Feisty, and I can't communicate with it via Amarok. This is really important to me. :) It has never been plugged into a Windows machine.  The last time I used it I was running Kubuntu Edgy and it always mounted fine with no fstab entries. I rebuilt my machine, this time with Ubuntu Feisty (Gnome), and the iPod nano does not mount.

Here are the syslog entries from plugging in the iPod (which does cause the device to show the "do not disconnect" message):

```
May  1 21:39:28 pipistrelle kernel: [772786.799839] usb 4-2: new high speed USB device using ehci_hcd and address 14
May  1 21:39:28 pipistrelle kernel: [772786.933163] usb 4-2: configuration #1 chosen from 2 choices
May  1 21:39:28 pipistrelle kernel: [772786.933535] scsi12 : SCSI emulation for USB Mass Storage devices
May  1 21:39:28 pipistrelle kernel: [772786.933685] usb-storage: device found at 14
May  1 21:39:28 pipistrelle kernel: [772786.933688] usb-storage: waiting for device to settle before scanning
May  1 21:39:33 pipistrelle kernel: [772791.932487] usb-storage: device scan complete
May  1 21:39:33 pipistrelle kernel: [772791.935277] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
May  1 21:39:33 pipistrelle kernel: [772791.938455] SCSI device sdc: 3964928 2048-byte hdwr sectors (8120 MB)
May  1 21:39:33 pipistrelle kernel: [772791.939328] sdc: Write Protect is off
May  1 21:39:33 pipistrelle kernel: [772791.939333] sdc: Mode Sense: 68 00 00 08
May  1 21:39:33 pipistrelle kernel: [772791.939336] sdc: assuming drive cache: write through
May  1 21:39:33 pipistrelle kernel: [772791.941325] SCSI device sdc: 3964928 2048-byte hdwr sectors (8120 MB)
May  1 21:39:33 pipistrelle kernel: [772791.942200] sdc: Write Protect is off
May  1 21:39:33 pipistrelle kernel: [772791.942205] sdc: Mode Sense: 68 00 00 08
May  1 21:39:33 pipistrelle kernel: [772791.942207] sdc: assuming drive cache: write through
May  1 21:39:33 pipistrelle kernel: [772791.942212]  sdc: sdc1 sdc2
May  1 21:39:33 pipistrelle kernel: [772791.944876] sd 12:0:0:0: Attached scsi removable disk sdc
May  1 21:39:33 pipistrelle kernel: [772791.944926] sd 12:0:0:0: Attached scsi generic sg3 type 0

```

Here is the lsusb output:

```
Bus 004 Device 014: ID 05ac:1260 Apple Computer, Inc. 
Bus 004 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 1606:0060 Umax [hex] Astra 3400U
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

Here is the lspci output:
```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE Host-to-AGP Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R200 BB [Radeon All in Wonder 8500DV]
01:00.1 PCI bridge: ATI Technologies Inc R200 BC [Radeon All in Wonder 8500]
02:00.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 04)
03:03.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
03:04.0 RAID bus controller: Promise Technology, Inc. PDC20376 (FastTrak 376) (rev 02)
03:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet (rev 02)
03:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)
03:0e.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
03:0e.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)

```

If I make this fstab entry:
```
/dev/sdc2 /media/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0
```
Then I can mount the iPod and navigate its files with Nautilus. However, in no case can Amarok see it or communicate with it, and this is the key problem. What am I missing that is preventing the iPod from mounting on its own?

I shouldn't have to connect it to a Windows computer if I have never done so the whole time I've used it, right?


*** RESOLVED ***

I hate to admit this... but I rarely have to reboot my Linux box, so it didn't occur to me that a reboot would fix the mounting problem. After rebooting however, the problem went away. Back to Tech Support 101 for me I guess.

---

