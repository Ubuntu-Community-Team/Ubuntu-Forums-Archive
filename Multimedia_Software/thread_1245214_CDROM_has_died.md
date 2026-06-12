---
title: "CDROM has died"
date: 2009-08-20
forum: Multimedia Software
---

### Post by MartinEve on 2009-08-20
Hi all,

I had a CD/DVD drive that was working fine, but now seems to refuse to mount.

Some diagnostics:

sudo mount /dev/scd0
```

mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

dmesg | tail
```

[  162.336755] Info fld=0x0
[  162.336758] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  162.336765] end_request: I/O error, dev sr0, sector 2496
[  162.336865] UDF-fs: No partition found (1)
[  162.395263] sr 1:0:0:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[  162.395270] sr 1:0:0:0: [sr0] Sense Key : Hardware Error [current]
[  162.395277] Info fld=0x0
[  162.395279] sr 1:0:0:0: [sr0] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[  162.395287] end_request: I/O error, dev sr0, sector 64
[  162.395382] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

```

cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c69630a9-eede-43e6-89d5-8c6940cede5d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=fa388ad1-17f5-4d66-a59c-64f0b36c584e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/vg01/datadrive     /data   ext3    user,relatime   0       0

```

sudo lshw -sanitize -C disk
```

*snip*
  *-cdrom                                                                                           
       description: DVD reader                                                                      
       product: CDRW/DVD SM-352F                                                                    
       vendor: SAMSUNG                                                                              
       physical id: 1                                                                               
       bus info: scsi@1:0.0.0                                                                       
       logical name: /dev/cdrom                                                                     
       logical name: /dev/cdrw                                                                      
       logical name: /dev/dvd                                                                       
       logical name: /dev/scd0                                                                      
       logical name: /dev/sr0                                                                       
       version: T902                                                                                
       capabilities: removable audio cd-r cd-rw dvd                                                 
       configuration: ansiversion=5 status=ready                                                    
     *-medium                                                                                       
          physical id: 0                                                                            
          logical name: /dev/cdrom  
*snip

```

In light of kernel updates, I also downgraded to 2.6.28-14-generic, but the problem still occurs.

Can anyone provide any insight into what has happened? Has the drive physically died? :(

Thanks in advance,

Martin

---

### Post by bowens44 on 2009-08-20
Put in a bootable CD and see if you can boot from it. If not, chances are the CD-ROM is bad.

---

### Post by MartinEve on 2009-08-20
Hiya,

I had thought of that, but it's an utter pain - the box doesn't have a monitor attached - I've been trying to mount via ssh.

If nobody else has any other ideas, I will plug in a monitor, but I'm increasingly suspicious of a dodgy cable/drive.

Martin

---

### Post by MartinEve on 2009-08-22
Ok, seems this was a hardware failure.

How do I mark as solved? There doesn't seem to be an option under "Thread Tools".

---

