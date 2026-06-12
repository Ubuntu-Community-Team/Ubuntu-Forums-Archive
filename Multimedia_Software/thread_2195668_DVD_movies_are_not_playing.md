---
title: "DVD movies are not playing"
date: 2013-12-25
forum: Multimedia Software
---

### Post by San-Tiago on 2013-12-25
Hi All!

Since upgrading from Ubuntu 10.10 to 12 and then to 13, I've got a problem with playing movies form DVD's. When I was using 10.10 version everything was fine, and I didn't have any problems with this issue. I am still using the same notebook with the same drive. DVDs with data are working fine. 

I followed all the instructions posted here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) . Nothing has worked for me. 

When /dvd/sr0 is set VLC gives this:
```
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdread: Could not open /dev/sr0 with libdvdcss.
libdvdread: Can't open /dev/sr0 for reading
[0xb52042e8] dvdread demux error: DVDRead cannot open source: /dev/sr0
[0xb5200618] main input error: open of `dvd:///dev/sr0' failed
```

When  /dev/dvd/:
```
libdvdnav: Using dvdnav version 4.2.0
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdread: Can't stat /dev/dvd
Nie ma takiego pliku ani katalogu
libdvdread: Could not open /dev/dvd
libdvdnav: vm: failed to open/read the DVD
libdvdread: Using libdvdcss version 1.2.13 for DVD access
libdvdread: Can't stat /dev/dvd
Nie ma takiego pliku ani katalogu
libdvdread: Could not open /dev/dvd
[0xb5203b68] dvdread demux error: DVDRead cannot open source: /dev/dvd
[0xb5204b18] main input error: open of `dvd:///dev/dvd' failed
```

sudo apt-get install dvd+rw-tools command gives this(DVD is in the drive)::```
INQUIRY:                [HL-DT-ST][DVDRAM GSA-T50N ][RT04]
GET [CURRENT] CONFIGURATION:
:-( no media mounted, exiting...
```

[ls -al /dev/ command gives this:
```
razem 4
drwxr-xr-x  16 root root        4080 gru 23 16:18 .
drwxr-xr-x  22 root root        4096 gru  7 10:35 ..
crw-------   1 root root     10, 235 gru 23 16:18 autofs
drwxr-xr-x   2 root root         620 gru 23 16:17 block
drwxr-xr-x   2 root root          80 gru 23 16:17 bsg
crw-------   1 root root     10, 234 gru 23 16:18 btrfs-control
drwxr-xr-x   3 root root          60 gru 23 16:17 bus
lrwxrwxrwx   1 root root           3 gru 23 16:23 cdrom -> sr0
drwxr-xr-x   2 root root        3820 gru 23 16:18 char
crw-------   1 root root      5,   1 gru 23 16:18 console
lrwxrwxrwx   1 root root          11 gru 23 16:17 core -> /proc/kcore
drwxr-xr-x   2 root root          60 gru 23 16:18 cpu
crw-------   1 root root     10,  60 gru 23 16:18 cpu_dma_latency
drwxr-xr-x   4 root root          80 gru 23 16:17 disk
drwxr-xr-x   2 root root          80 gru 23 16:18 dri
crw-------   1 root root     10,  61 gru 23 16:18 ecryptfs
crw-rw----   1 root video    29,   0 gru 23 16:18 fb0
lrwxrwxrwx   1 root root          13 gru 23 16:17 fd -> /proc/self/fd
crw-rw-rw-   1 root root      1,   7 gru 23 16:18 full
crw-rw-rw-   1 root root     10, 229 gru 23 16:18 fuse
crw-------   1 root root    251,   0 gru 23 16:18 fw0
crw-------   1 root root    250,   0 gru 23 16:18 hidraw0
crw-------   1 root root     10, 228 gru 23 16:18 hpet
lrwxrwxrwx   1 root root          14 gru 23 16:17 .initramfs -> /run/initramfs
drwxr-xr-x   4 root root         380 gru 23 16:18 input
crw-r--r--   1 root root      1,  11 gru 23 16:18 kmsg
srw-rw-rw-   1 root root           0 gru 23 16:18 log
brw-rw----   1 root disk      7,   0 gru 23 16:18 loop0
brw-rw----   1 root disk      7,   1 gru 23 16:18 loop1
brw-rw----   1 root disk      7,   2 gru 23 16:18 loop2
brw-rw----   1 root disk      7,   3 gru 23 16:18 loop3
brw-rw----   1 root disk      7,   4 gru 23 16:18 loop4
brw-rw----   1 root disk      7,   5 gru 23 16:18 loop5
brw-rw----   1 root disk      7,   6 gru 23 16:18 loop6
brw-rw----   1 root disk      7,   7 gru 23 16:18 loop7
crw-------   1 root root     10, 237 gru 23 16:18 loop-control
drwxr-xr-x   2 root root          60 gru 23 16:17 mapper
crw-------   1 root root     10, 227 gru 23 16:18 mcelog
crw-r-----   1 root kmem      1,   1 gru 23 16:18 mem
drwxr-xr-x   2 root root          60 gru 23 16:17 net
crw-------   1 root root     10,  59 gru 23 16:18 network_latency
crw-------   1 root root     10,  58 gru 23 16:18 network_throughput
crw-rw-rw-   1 root root      1,   3 gru 23 16:18 null
crw-r-----   1 root kmem      1,   4 gru 23 16:18 port
crw-------   1 root root    108,   0 gru 23 16:18 ppp
crw-------   1 root root     10,   1 gru 23 16:18 psaux
crw-rw-rw-   1 root tty       5,   2 gru 23 16:26 ptmx
drwxr-xr-x   2 root root           0 gru 23 16:17 pts
brw-rw----   1 root disk      1,   0 gru 23 16:18 ram0
brw-rw----   1 root disk      1,   1 gru 23 16:18 ram1
brw-rw----   1 root disk      1,  10 gru 23 16:18 ram10
brw-rw----   1 root disk      1,  11 gru 23 16:18 ram11
brw-rw----   1 root disk      1,  12 gru 23 16:18 ram12
brw-rw----   1 root disk      1,  13 gru 23 16:18 ram13
brw-rw----   1 root disk      1,  14 gru 23 16:18 ram14
brw-rw----   1 root disk      1,  15 gru 23 16:18 ram15
brw-rw----   1 root disk      1,   2 gru 23 16:18 ram2
brw-rw----   1 root disk      1,   3 gru 23 16:18 ram3
brw-rw----   1 root disk      1,   4 gru 23 16:18 ram4
brw-rw----   1 root disk      1,   5 gru 23 16:18 ram5
brw-rw----   1 root disk      1,   6 gru 23 16:18 ram6
brw-rw----   1 root disk      1,   7 gru 23 16:18 ram7
brw-rw----   1 root disk      1,   8 gru 23 16:18 ram8
brw-rw----   1 root disk      1,   9 gru 23 16:18 ram9
crw-rw-rw-   1 root root      1,   8 gru 23 16:18 random
crw-rw-r--+  1 root root     10,  62 gru 23 16:18 rfkill
lrwxrwxrwx   1 root root           4 gru 23 16:18 rtc -> rtc0
crw-------   1 root root    254,   0 gru 23 16:18 rtc0
brw-rw----   1 root disk      8,   0 gru 23 16:18 sda
brw-rw----   1 root disk      8,   1 gru 23 16:18 sda1
brw-rw----   1 root disk      8,   2 gru 23 16:18 sda2
brw-rw----   1 root disk      8,   5 gru 23 16:18 sda5
crw-rw----   1 root disk     21,   0 gru 23 16:18 sg0
crw-rw----+  1 root cdrom    21,   1 gru 23 16:18 sg1
lrwxrwxrwx   1 root root           8 gru 23 16:18 shm -> /run/shm
crw-------   1 root root     10, 231 gru 23 16:18 snapshot
drwxr-xr-x   3 root root         280 gru 23 16:18 snd
brw-rw----+  1 root cdrom    11,   0 gru 23 16:23 sr0
lrwxrwxrwx   1 root root          15 gru 23 16:17 stderr -> /proc/self/fd/2
lrwxrwxrwx   1 root root          15 gru 23 16:17 stdin -> /proc/self/fd/0
lrwxrwxrwx   1 root root          15 gru 23 16:17 stdout -> /proc/self/fd/1
crw-rw-rw-   1 root tty       5,   0 gru 23 16:22 tty
crw--w----   1 root tty       4,   0 gru 23 16:18 tty0
crw-rw----   1 root tty       4,   1 gru 23 16:18 tty1
crw--w----   1 root tty       4,  10 gru 23 16:18 tty10
crw--w----   1 root tty       4,  11 gru 23 16:18 tty11
crw--w----   1 root tty       4,  12 gru 23 16:18 tty12
crw--w----   1 root tty       4,  13 gru 23 16:18 tty13
crw--w----   1 root tty       4,  14 gru 23 16:18 tty14
crw--w----   1 root tty       4,  15 gru 23 16:18 tty15
crw--w----   1 root tty       4,  16 gru 23 16:18 tty16
crw--w----   1 root tty       4,  17 gru 23 16:18 tty17
crw--w----   1 root tty       4,  18 gru 23 16:18 tty18
crw--w----   1 root tty       4,  19 gru 23 16:18 tty19
crw-rw----   1 root tty       4,   2 gru 23 16:18 tty2
crw--w----   1 root tty       4,  20 gru 23 16:18 tty20
crw--w----   1 root tty       4,  21 gru 23 16:18 tty21
crw--w----   1 root tty       4,  22 gru 23 16:18 tty22
crw--w----   1 root tty       4,  23 gru 23 16:18 tty23
crw--w----   1 root tty       4,  24 gru 23 16:18 tty24
crw--w----   1 root tty       4,  25 gru 23 16:18 tty25
crw--w----   1 root tty       4,  26 gru 23 16:18 tty26
crw--w----   1 root tty       4,  27 gru 23 16:18 tty27
crw--w----   1 root tty       4,  28 gru 23 16:18 tty28
crw--w----   1 root tty       4,  29 gru 23 16:18 tty29
crw-rw----   1 root tty       4,   3 gru 23 16:18 tty3
crw--w----   1 root tty       4,  30 gru 23 16:18 tty30
crw--w----   1 root tty       4,  31 gru 23 16:18 tty31
crw--w----   1 root tty       4,  32 gru 23 16:18 tty32
crw--w----   1 root tty       4,  33 gru 23 16:18 tty33
crw--w----   1 root tty       4,  34 gru 23 16:18 tty34
crw--w----   1 root tty       4,  35 gru 23 16:18 tty35
crw--w----   1 root tty       4,  36 gru 23 16:18 tty36
crw--w----   1 root tty       4,  37 gru 23 16:18 tty37
crw--w----   1 root tty       4,  38 gru 23 16:18 tty38
crw--w----   1 root tty       4,  39 gru 23 16:18 tty39
crw-rw----   1 root tty       4,   4 gru 23 16:18 tty4
crw--w----   1 root tty       4,  40 gru 23 16:18 tty40
crw--w----   1 root tty       4,  41 gru 23 16:18 tty41
crw--w----   1 root tty       4,  42 gru 23 16:18 tty42
crw--w----   1 root tty       4,  43 gru 23 16:18 tty43
crw--w----   1 root tty       4,  44 gru 23 16:18 tty44
crw--w----   1 root tty       4,  45 gru 23 16:18 tty45
crw--w----   1 root tty       4,  46 gru 23 16:18 tty46
crw--w----   1 root tty       4,  47 gru 23 16:18 tty47
crw--w----   1 root tty       4,  48 gru 23 16:18 tty48
crw--w----   1 root tty       4,  49 gru 23 16:18 tty49
crw-rw----   1 root tty       4,   5 gru 23 16:18 tty5
crw--w----   1 root tty       4,  50 gru 23 16:18 tty50
crw--w----   1 root tty       4,  51 gru 23 16:18 tty51
crw--w----   1 root tty       4,  52 gru 23 16:18 tty52
crw--w----   1 root tty       4,  53 gru 23 16:18 tty53
crw--w----   1 root tty       4,  54 gru 23 16:18 tty54
crw--w----   1 root tty       4,  55 gru 23 16:18 tty55
crw--w----   1 root tty       4,  56 gru 23 16:18 tty56
crw--w----   1 root tty       4,  57 gru 23 16:18 tty57
crw--w----   1 root tty       4,  58 gru 23 16:18 tty58
crw--w----   1 root tty       4,  59 gru 23 16:18 tty59
crw-rw----   1 root tty       4,   6 gru 23 16:18 tty6
crw--w----   1 root tty       4,  60 gru 23 16:18 tty60
crw--w----   1 root tty       4,  61 gru 23 16:18 tty61
crw--w----   1 root tty       4,  62 gru 23 16:18 tty62
crw--w----   1 root tty       4,  63 gru 23 16:18 tty63
crw--w----   1 root tty       4,   7 gru 23 16:18 tty7
crw--w----   1 root tty       4,   8 gru 23 16:18 tty8
crw--w----   1 root tty       4,   9 gru 23 16:18 tty9
crw-------   1 root root      5,   3 gru 23 16:18 ttyprintk
crw-rw----   1 root dialout   4,  64 gru 23 16:18 ttyS0
crw-rw----   1 root dialout   4,  65 gru 23 16:18 ttyS1
crw-rw----   1 root dialout   4,  74 gru 23 16:18 ttyS10
crw-rw----   1 root dialout   4,  75 gru 23 16:18 ttyS11
crw-rw----   1 root dialout   4,  76 gru 23 16:18 ttyS12
crw-rw----   1 root dialout   4,  77 gru 23 16:18 ttyS13
crw-rw----   1 root dialout   4,  78 gru 23 16:18 ttyS14
crw-rw----   1 root dialout   4,  79 gru 23 16:18 ttyS15
crw-rw----   1 root dialout   4,  80 gru 23 16:18 ttyS16
crw-rw----   1 root dialout   4,  81 gru 23 16:18 ttyS17
crw-rw----   1 root dialout   4,  82 gru 23 16:18 ttyS18
crw-rw----   1 root dialout   4,  83 gru 23 16:18 ttyS19
crw-rw----   1 root dialout   4,  66 gru 23 16:18 ttyS2
crw-rw----   1 root dialout   4,  84 gru 23 16:18 ttyS20
crw-rw----   1 root dialout   4,  85 gru 23 16:18 ttyS21
crw-rw----   1 root dialout   4,  86 gru 23 16:18 ttyS22
crw-rw----   1 root dialout   4,  87 gru 23 16:18 ttyS23
crw-rw----   1 root dialout   4,  88 gru 23 16:18 ttyS24
crw-rw----   1 root dialout   4,  89 gru 23 16:18 ttyS25
crw-rw----   1 root dialout   4,  90 gru 23 16:18 ttyS26
crw-rw----   1 root dialout   4,  91 gru 23 16:18 ttyS27
crw-rw----   1 root dialout   4,  92 gru 23 16:18 ttyS28
crw-rw----   1 root dialout   4,  93 gru 23 16:18 ttyS29
crw-rw----   1 root dialout   4,  67 gru 23 16:18 ttyS3
crw-rw----   1 root dialout   4,  94 gru 23 16:18 ttyS30
crw-rw----   1 root dialout   4,  95 gru 23 16:18 ttyS31
crw-rw----   1 root dialout   4,  68 gru 23 16:18 ttyS4
crw-rw----   1 root dialout   4,  69 gru 23 16:18 ttyS5
crw-rw----   1 root dialout   4,  70 gru 23 16:18 ttyS6
crw-rw----   1 root dialout   4,  71 gru 23 16:18 ttyS7
crw-rw----   1 root dialout   4,  72 gru 23 16:18 ttyS8
crw-rw----   1 root dialout   4,  73 gru 23 16:18 ttyS9
drwxr-xr-x   3 root root          60 gru 23 16:18 .udev
crw-------   1 root root     10, 239 gru 23 16:18 uhid
crw-------   1 root root     10, 223 gru 23 16:18 uinput
crw-rw-rw-   1 root root      1,   9 gru 23 16:18 urandom
drwxr-xr-x   4 root root          80 gru 23 16:18 v4l
crw-rw----   1 root tty       7,   0 gru 23 16:18 vcs
crw-rw----   1 root tty       7,   1 gru 23 16:18 vcs1
crw-rw----   1 root tty       7,   2 gru 23 16:18 vcs2
crw-rw----   1 root tty       7,   3 gru 23 16:18 vcs3
crw-rw----   1 root tty       7,   4 gru 23 16:18 vcs4
crw-rw----   1 root tty       7,   5 gru 23 16:18 vcs5
crw-rw----   1 root tty       7,   6 gru 23 16:18 vcs6
crw-rw----   1 root tty       7,   7 gru 23 16:18 vcs7
crw-rw----   1 root tty       7, 128 gru 23 16:18 vcsa
crw-rw----   1 root tty       7, 129 gru 23 16:18 vcsa1
crw-rw----   1 root tty       7, 130 gru 23 16:18 vcsa2
crw-rw----   1 root tty       7, 131 gru 23 16:18 vcsa3
crw-rw----   1 root tty       7, 132 gru 23 16:18 vcsa4
crw-rw----   1 root tty       7, 133 gru 23 16:18 vcsa5
crw-rw----   1 root tty       7, 134 gru 23 16:18 vcsa6
crw-rw----   1 root tty       7, 135 gru 23 16:18 vcsa7
crw-------   1 root root     10,  63 gru 23 16:18 vga_arbiter
crw-------   1 root root     10, 238 gru 23 16:18 vhost-net
crw-rw----+  1 root video    81,   0 gru 23 16:18 video0
crw-rw-rw-   1 root root      1,   5 gru 23 16:18 zero
```

wodim scanbus command:
```
wodim scanbus
wodim: No write mode specified.
wodim: Assuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.
Device was not specified. Trying to find an appropriate drive...
Detected CD-R drive: /dev/sr0
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'HL-DT-ST'
Identification : 'DVDRAM GSA-T50N '
Revision       : 'RT04'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: 
wodim: No such file or directory. Cannot open 'scanbus'.
```

Obviously, I am trying to play original DVDs from my region and the same region is set for the drive. I would really loved to watch some movies on my notebook. Could you help me?

---

