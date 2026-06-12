---
title: "Sony Mp4 Nwz-s616f"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by RaZoR-x11 on 2008-01-02
Hey all!,  
I brought a Sony Mp4 Walkman NWZ-S616F a few day's ago and ive seem to 
ran into some problem's, It won't unmount, and i did dmesg like any normal Ubuntu user would =), and came up with this lovely sexy code.... or evil... (lol)

```
[ 2362.400000] scsi 3:0:0:0: Direct-Access     SONY     WALKMAN          1.00 PQ: 0 ANSI: 0 CCS
[ 2363.416000] ready
[ 2363.416000] SCSI device sdb: 1875968 2048-byte hdwr sectors (3842 MB)
[ 2363.524000] sdb: Write Protect is off
[ 2363.524000] sdb: Mode Sense: 00 2a 00 00
[ 2363.524000] sdb: assuming drive cache: write through
[ 2363.528000] SCSI device sdb: 1875968 2048-byte hdwr sectors (3842 MB)
[ 2363.528000] sdb: Write Protect is off
[ 2363.528000] sdb: Mode Sense: 00 2a 00 00
[ 2363.528000] sdb: assuming drive cache: write through
[ 2363.528000]  sdb: sdb1
[ 2363.532000]  sdb: p1 exceeds device capacity
[ 2363.540000] sd 3:0:0:0: Attached scsi removable disk sdb
[ 2363.540000] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967044, limit=7503872
[ 2363.696000] printk: 22 messages suppressed.
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741760
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967048, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741761
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967044, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741760
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967048, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741761
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.696000] Buffer I/O error on device sdb1, logical block 1073741822
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967228, limit=7503872
[ 2363.696000] attempt to access beyond end of device
[ 2363.696000] sdb: rw=0, want=4294967232, limit=7503872
[ 2363.700000] attempt to access beyond end of device
[ 2363.700000] sdb: rw=0, want=4294967284, limit=7503872
[ 2363.700000] attempt to access beyond end of device
[ 2363.700000] sdb: rw=0, want=4294967288, limit=7503872
[ 2363.700000] attempt to access beyond end of device
[ 2363.700000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.700000] attempt to access beyond end of device
[ 2363.700000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.772000] attempt to access beyond end of device
[ 2363.772000] sdb: rw=0, want=4294967044, limit=7503872
[ 2363.784000] attempt to access beyond end of device
[ 2363.784000] sdb: rw=0, want=4294967048, limit=7503872
[ 2363.784000] attempt to access beyond end of device
[ 2363.784000] sdb: rw=0, want=4294967044, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967048, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967228, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967232, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967284, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967288, limit=7503872
[ 2363.788000] attempt to access beyond end of device
[ 2363.788000] sdb: rw=0, want=4294967292, limit=7503872
[ 2363.792000] attempt to access beyond end of device
[ 2363.792000] sdb: rw=0, want=4294967292, limit=7503872

```

Just wanting to no if this is why i had to take the one i got yesterday back and get a replacement?, 

Cheer's raz =)

---

