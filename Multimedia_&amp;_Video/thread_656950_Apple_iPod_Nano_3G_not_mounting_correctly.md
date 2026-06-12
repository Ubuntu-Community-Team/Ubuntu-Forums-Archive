---
title: "Apple iPod Nano 3G not mounting correctly"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by lmedland on 2008-01-03
Hi,

I hope you can help, I have searched the forums and net and tried various solutions but can't get my iPod to mount correctly.

I have an iPod Nano 3rd Generation and when I plug it in to my laptop via USB, it mounts it read only and specifies the Owner as unknown within the permissions.

The output from the command **dmsg** is the following:-

```
 1677.692000] usb-storage: device found at 7
[ 1677.692000] usb-storage: waiting for device to settle before scanning
[ 1682.692000] usb-storage: device scan complete
[ 1682.704000] scsi 4:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 1682.712000] sd 4:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 1682.712000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1682.712000] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1682.712000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1682.712000] sd 4:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 1682.712000] sd 4:0:0:0: [sdb] Write Protect is off
[ 1682.712000] sd 4:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 1682.712000] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1682.712000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 1682.748000] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1682.748000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[ 1698.016000] tg3: eth0: Link is up at 100 Mbps, full duplex.
[ 1698.016000] tg3: eth0: Flow control is off for TX and off for RX.
[ 1702.360000] NET: Registered protocol family 17
[ 2220.464000] Inbound IN=eth0 OUT= MAC=00:1c:23:20:06:f8:00:11:85:69:ea:1a:08:00 SRC=10.216.116.36 DST=10.216.117.16 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=55811 PROTO=UDP SPT=137 DPT=32772 LEN=70
[ 2221.212000] Inbound IN=eth0 OUT= MAC=00:1c:23:20:06:f8:00:11:85:69:ea:1a:08:00 SRC=10.216.116.36 DST=10.216.117.16 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=55824 PROTO=UDP SPT=137 DPT=32772 LEN=70
[ 2221.984000] Inbound IN=eth0 OUT= MAC=00:1c:23:20:06:f8:00:11:85:69:ea:1a:08:00 SRC=10.216.116.36 DST=10.216.117.16 LEN=90 TOS=0x00 PREC=0x00 TTL=128 ID=55827 PROTO=UDP SPT=137 DPT=32772 LEN=70
[ 3077.808000] usb 2-7: USB disconnect, address 7
[ 3122.972000] usb 2-7: new high speed USB device using ehci_hcd and address 8
[ 3123.104000] usb 2-7: configuration #1 chosen from 2 choices
[ 3123.132000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 3123.132000] usb-storage: device found at 8
[ 3123.132000] usb-storage: waiting for device to settle before scanning
[ 3128.132000] usb-storage: device scan complete
[ 3128.144000] scsi 5:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3128.148000] sd 5:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3128.148000] sd 5:0:0:0: [sdb] Write Protect is off
[ 3128.148000] sd 5:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3128.148000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3128.148000] sd 5:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3128.152000] sd 5:0:0:0: [sdb] Write Protect is off
[ 3128.152000] sd 5:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3128.152000] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[ 3128.152000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3128.184000] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 3128.184000] sd 5:0:0:0: Attached scsi generic sg1 type 0
[ 3263.608000] usb 2-7: USB disconnect, address 8
[ 3263.660000] scsi 5:0:0:0: rejecting I/O to dead device
[ 3263.660000] Buffer I/O error on device sdb3, logical block 0
[ 3263.660000] lost page write due to I/O error on sdb3
[ 3263.664000] scsi 5:0:0:0: rejecting I/O to dead device
[ 3284.220000] usb 2-7: new high speed USB device using ehci_hcd and address 9
[ 3284.352000] usb 2-7: configuration #1 chosen from 2 choices
[ 3284.380000] scsi6 : SCSI emulation for USB Mass Storage devices
[ 3284.380000] usb-storage: device found at 9
[ 3284.380000] usb-storage: waiting for device to settle before scanning
[ 3289.380000] usb-storage: device scan complete
[ 3289.392000] scsi 6:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3289.396000] sd 6:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3289.396000] sd 6:0:0:0: [sdb] Write Protect is off
[ 3289.396000] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3289.396000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3289.396000] sd 6:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3289.400000] sd 6:0:0:0: [sdb] Write Protect is off
[ 3289.400000] sd 6:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3289.400000] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 3289.400000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3289.432000] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 3289.432000] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 3289.920000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 3379.916000] usb 2-7: USB disconnect, address 9
[ 3386.128000] usb 2-7: new high speed USB device using ehci_hcd and address 10
[ 3386.260000] usb 2-7: configuration #1 chosen from 2 choices
[ 3386.288000] scsi7 : SCSI emulation for USB Mass Storage devices
[ 3386.288000] usb-storage: device found at 10
[ 3386.288000] usb-storage: waiting for device to settle before scanning
[ 3391.288000] usb-storage: device scan complete
[ 3391.300000] scsi 7:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3391.304000] sd 7:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3391.304000] sd 7:0:0:0: [sdb] Write Protect is off
[ 3391.304000] sd 7:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3391.304000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3391.308000] sd 7:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3391.308000] sd 7:0:0:0: [sdb] Write Protect is off
[ 3391.308000] sd 7:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3391.308000] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3391.308000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3391.340000] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 3391.340000] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 3416.900000] usb 2-7: USB disconnect, address 10
[ 3426.028000] usb 2-7: new high speed USB device using ehci_hcd and address 11
[ 3426.160000] usb 2-7: configuration #1 chosen from 2 choices
[ 3426.188000] scsi8 : SCSI emulation for USB Mass Storage devices
[ 3426.188000] usb-storage: device found at 11
[ 3426.188000] usb-storage: waiting for device to settle before scanning
[ 3431.188000] usb-storage: device scan complete
[ 3431.204000] scsi 8:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3431.212000] sd 8:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3431.216000] sd 8:0:0:0: [sdb] Write Protect is off
[ 3431.216000] sd 8:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3431.216000] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3431.220000] sd 8:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3431.220000] sd 8:0:0:0: [sdb] Write Protect is off
[ 3431.220000] sd 8:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3431.220000] sd 8:0:0:0: [sdb] Assuming drive cache: write through
[ 3431.220000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3431.260000] sd 8:0:0:0: [sdb] Attached SCSI removable disk
[ 3431.260000] sd 8:0:0:0: Attached scsi generic sg1 type 0
[ 3451.496000] usb 2-7: USB disconnect, address 11
[ 3466.072000] usb 2-7: new high speed USB device using ehci_hcd and address 12
[ 3466.204000] usb 2-7: configuration #1 chosen from 2 choices
[ 3466.232000] scsi9 : SCSI emulation for USB Mass Storage devices
[ 3466.232000] usb-storage: device found at 12
[ 3466.232000] usb-storage: waiting for device to settle before scanning
[ 3471.232000] usb-storage: device scan complete
[ 3471.244000] scsi 9:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3471.248000] sd 9:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3471.248000] sd 9:0:0:0: [sdb] Write Protect is off
[ 3471.248000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3471.248000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3471.248000] sd 9:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3471.252000] sd 9:0:0:0: [sdb] Write Protect is off
[ 3471.252000] sd 9:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3471.252000] sd 9:0:0:0: [sdb] Assuming drive cache: write through
[ 3471.252000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3471.284000] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 3471.284000] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 3491.936000] usb 2-7: USB disconnect, address 12
[ 3499.264000] usb 2-7: new high speed USB device using ehci_hcd and address 13
[ 3499.396000] usb 2-7: configuration #1 chosen from 2 choices
[ 3499.424000] scsi10 : SCSI emulation for USB Mass Storage devices
[ 3499.424000] usb-storage: device found at 13
[ 3499.424000] usb-storage: waiting for device to settle before scanning
[ 3504.424000] usb-storage: device scan complete
[ 3504.436000] scsi 10:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 3504.440000] sd 10:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3504.440000] sd 10:0:0:0: [sdb] Write Protect is off
[ 3504.440000] sd 10:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3504.440000] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3504.440000] sd 10:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 3504.444000] sd 10:0:0:0: [sdb] Write Protect is off
[ 3504.444000] sd 10:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 3504.444000] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[ 3504.444000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 3504.476000] sd 10:0:0:0: [sdb] Attached SCSI removable disk
[ 3504.476000] sd 10:0:0:0: Attached scsi generic sg1 type 0
[ 3505.040000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 3908.488000] attempt to access beyond end of device
[ 3908.488000] sda2: rw=0, want=3, limit=2
[ 3908.488000] hfs: unable to find HFS+ superblock
[ 3923.332000] attempt to access beyond end of device
[ 3923.332000] sda2: rw=0, want=17, limit=2
[ 3923.332000] HPFS: hpfs_map_sector: read error
[ 4060.288000] attempt to access beyond end of device
[ 4060.288000] sda2: rw=0, want=3, limit=2
[ 4060.288000] hfs: can't find a HFS filesystem on dev sda2.
[ 4064.128000] attempt to access beyond end of device
[ 4064.128000] sda2: rw=0, want=3, limit=2
[ 4064.128000] hfs: unable to find HFS+ superblock
[ 4290.972000] attempt to access beyond end of device
[ 4290.972000] sda2: rw=0, want=3, limit=2
[ 4290.972000] hfs: unable to find HFS+ superblock
[ 4366.052000] usb 2-7: USB disconnect, address 13
[ 4366.104000] scsi 10:0:0:0: rejecting I/O to dead device
[ 4380.600000] usb 2-7: new high speed USB device using ehci_hcd and address 14
[ 4380.732000] usb 2-7: configuration #1 chosen from 2 choices
[ 4380.760000] scsi11 : SCSI emulation for USB Mass Storage devices
[ 4380.760000] usb-storage: device found at 14
[ 4380.760000] usb-storage: waiting for device to settle before scanning
[ 4385.760000] usb-storage: device scan complete
[ 4385.772000] scsi 11:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4385.776000] sd 11:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 4385.776000] sd 11:0:0:0: [sdb] Write Protect is off
[ 4385.776000] sd 11:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4385.776000] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 4385.780000] sd 11:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 4385.780000] sd 11:0:0:0: [sdb] Write Protect is off
[ 4385.780000] sd 11:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4385.780000] sd 11:0:0:0: [sdb] Assuming drive cache: write through
[ 4385.780000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 4385.816000] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 4385.816000] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 4386.252000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 4442.712000] usb 2-7: USB disconnect, address 14
[ 4442.756000] scsi 11:0:0:0: rejecting I/O to dead device
[ 4453.952000] usb 2-7: new high speed USB device using ehci_hcd and address 15
[ 4454.084000] usb 2-7: configuration #1 chosen from 2 choices
[ 4454.112000] scsi12 : SCSI emulation for USB Mass Storage devices
[ 4454.112000] usb-storage: device found at 15
[ 4454.112000] usb-storage: waiting for device to settle before scanning
[ 4459.112000] usb-storage: device scan complete
[ 4459.128000] scsi 12:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 4459.132000] sd 12:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 4459.136000] sd 12:0:0:0: [sdb] Write Protect is off
[ 4459.136000] sd 12:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4459.136000] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 4459.136000] sd 12:0:0:0: [sdb] 950209 4096-byte hardware sectors (3892 MB)
[ 4459.136000] sd 12:0:0:0: [sdb] Write Protect is off
[ 4459.136000] sd 12:0:0:0: [sdb] Mode Sense: 68 00 00 08
[ 4459.136000] sd 12:0:0:0: [sdb] Assuming drive cache: write through
[ 4459.136000]  sdb: [mac] sdb1 sdb2 sdb3 sdb4
[ 4459.172000] sd 12:0:0:0: [sdb] Attached SCSI removable disk
[ 4459.172000] sd 12:0:0:0: Attached scsi generic sg1 type 0
[ 4459.632000] hfs: Filesystem was not cleanly unmounted, running fsck.hfsplus is recommended.  mounting read-only.
[ 4473.944000] hfs: unable to find HFS+ superblock

```

I have formatted my iPod on Mac OS X without using Journaling, yet the above seems to suggest that it still is.

Floola detects the iPod but quits as it can't write to it.

Any ideas would be great!

I'm using Ubuntu 7.10

Thanks.

---

### Post by Kobalt on 2008-01-03
If you used your iPod with OS X then it's formated in HFS+ filesystem, supported natively in read only in Ubuntu. I know some tools exists in the repos to read/write HFS+ but I've never used them...

---

### Post by Floola on 2008-01-03
Please delete my answer, gave a wrong suggestion.

---

### Post by lmedland on 2008-01-03
> **Kobalt said:**
> If you used your iPod with OS X then it's formated in HFS+ filesystem, supported natively in read only in Ubuntu. I know some tools exists in the repos to read/write HFS+ but I've never used them...

But I have seen posts suggesting to disable journaling on the drive and it is then writable by Ubuntu..... 

Surly people out there are using mac formatted iPod's in Ubuntu, after all Floola suggests you can use both iTunes and Floola to manage your iPod.

Ideas?

---

### Post by twright on 2008-01-03
hi,
itunes in OSX supports windows formatted drives but ubuntu cannot support HFS+ drives out of the box, 

you might be able to get it working with sudo apt-get install hfsplus hfsutils but it would be much simpler just to reset the ipod from a windows machine (if you don't have one you might have to borrow one)

the nano 3g has only recently been hacked so not all projects will support it yet

---

### Post by lmedland on 2008-01-03
> **twright said:**
> hi,
itunes in OSX supports windows formatted drives but ubuntu cannot support HFS+ drives out of the box, 

you might be able to get it working with sudo apt-get install hfsplus hfsutils but it would be much simpler just to reset the ipod from a windows machine (if you don't have one you might have to borrow one)

the nano 3g has only recently been hacked so not all projects will support it yet

Many thanks, I'll try it out and post back!

---

### Post by lmedland on 2008-01-04
Formatting on a Windows PC has worked. Thank you.

---

### Post by Heartsblood on 2008-01-04
Is it possible to get a 'windows format' on a 3g nano if I don't have access to windows?  I thought I was being smart for a second by installing iTunes through wine but it pretty much gave me the finger saying install required at least windows XP :/

---

### Post by twright on 2008-01-04
i have tried itunes with wine but no luck:(

you can use virtualbox if you do have a XP/Vista license and 10gb of diskspace but you will need to wait 1hour or so for it to install. Virtualbox puts windows in one file and doesn't partition your harddrive so you can install, format and then just delete Windows

---

