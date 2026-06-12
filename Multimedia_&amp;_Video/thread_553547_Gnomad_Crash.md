---
title: "Gnomad Crash"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by ryangoff on 2007-09-17
I hope this is the right place to ask this, so here goes ...

I've been trying to use Gnomad2 to transfer files off my Creative Zen Vision:M, but every time it gets to about 650MB transferred, Gnomad crashes. I've tried it a couple of times, to no avail. Here's the terminal output:

```
ryan@home-desktop:~$ gnomad2
Autodetected device "Creative Zen Vision:M" (VID=041e,PID=413e) is known.
PTP: Opening session
Connected to MTP device.
Queried Creative Zen Vision:M
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  2
  Minor opcode:  0
  Resource id:  0x3201707
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3201707
*** glibc detected *** gnomad2: malloc(): memory corruption: 0x00002aaaac8607a0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2ad04935c1d1]
/lib/libc.so.6(__libc_malloc+0x7d)[0x2ad04935d98d]
/usr/lib/libid3tag.so.0(id3_util_compress+0x49)[0x2ad048b89259]
/usr/lib/libid3tag.so.0(id3_frame_render+0x316)[0x2ad048b88eb6]
/usr/lib/libid3tag.so.0(id3_tag_render+0x517)[0x2ad048b8a847]
gnomad2[0x40b10b]
gnomad2[0x411914]
/usr/lib/libglib-2.0.so.0[0x2ad048927b74]
/lib/libpthread.so.0[0x2ad0490d72a5]
/lib/libc.so.6(clone+0x6d)[0x2ad0493bb61d]
======= Memory map: ========
00400000-00429000 r-xp 00000000 08:01 6329297                            /usr/bin/gnomad2
00628000-0062a000 rw-p 00028000 08:01 6329297                            /usr/bin/gnomad2
0062a000-0169b000 rw-p 0062a000 00:00 0                                  [heap]
40000000-40001000 ---p 40000000 00:00 0 
40001000-40801000 rw-p 40001000 00:00 0 
40801000-40802000 ---p 40801000 00:00 0 
40802000-41002000 rw-p 40802000 00:00 0 
2aaaaaac6000-2aaaaaac7000 rw-p 2aaaaaac6000 00:00 0 
2aaaaaac7000-2aaaaab3d000 r--p 00000000 08:01 6586496                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
2aaaaab3d000-2aaaaab5e000 r--p 00000000 08:01 6586498                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-ExtraLight.ttf
2aaaaab5e000-2aaaaab5f000 rw-p 2aaaaab5e000 00:00 0 
2aaaaab70000-2aaaaab7d000 r-xp 00000000 08:01 3637310                    /lib/libgcc_s.so.1
2aaaaab7d000-2aaaaad7d000 ---p 0000d000 08:01 3637310                    /lib/libgcc_s.so.1
2aaaaad7d000-2aaaaad7e000 rw-p 0000d000 08:01 3637310                    /lib/libgcc_s.so.1
2aaaac000000-2aaaac879000 rw-p 2aaaac000000 00:00 0 
2aaaac879000-2aaab0000000 ---p 2aaaac879000 00:00 0 
2ad045100000-2ad04511c000 r-xp 00000000 08:01 3637267                    /lib/ld-2.5.so
2ad04511c000-2ad04511f000 rw-p 2ad04511c000 00:00 0 
2ad04511f000-2ad045120000 r--p 00000000 08:01 6390496                    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
2ad045120000-2ad045127000 r--s 00000000 08:01 6327916                    /usr/lib/gconv/gconv-modules.cache
2ad045127000-2ad045128000 r--p 00000000 08:01 6390497                    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
2ad045128000-2ad045129000 r--p 00000000 08:01 6390502                    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
2ad045129000-2ad04512a000 r--p 00000000 08:01 6390493                    /usr/lib/locale/en_US.utf8/LC_ADDRESS
2ad04512a000-2ad04512b000 r--p 00000000 08:01 6390499                    /usr/lib/locale/en_US.utf8/LC_NAME
2ad04512b000-2ad04512c000 r--p 00000000 08:01 6390501                    /usr/lib/locale/en_US.utf8/LC_PAPER
2ad04512c000-2ad04512d000 r--p 00000000 08:01 6390504                    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2ad04512d000-2ad04512e000 r--p 00000000 08:01 6390498                    /usr/lib/locale/en_US.utf8/LC_MONETARY
2ad04512e000-2ad045205000 r--p 00000000 08:01 6390494                    /usr/lib/locale/en_US.utf8/LC_COLLATE
2ad045205000-2ad045206000 r--p 00000000 08:01 6390503                    /usr/lib/locale/en_US.utf8/LC_TIME
2ad045206000-2ad045207000 r--p 00000000 08:01 6390500                    /usr/lib/locale/en_US.utf8/LC_NUMERIC
2ad045207000-2ad045242000 r--p 00000000 08:01 6390495                    /usr/lib/locale/en_US.utf8/LC_CTYPE
2ad04531b000-2ad04531d000 rw-p 0001b000 08:01 3637267                    /lib/ld-2.5.so
2ad04531d000-2ad045321000 r-xp 00000000 08:01 6326146                    /usr/lib/libgthread-2.0.so.0.1200.11
2ad045321000-2ad045520000 ---p 00004000 08:01 6326146                    /usr/lib/libgthread-2.0.so.0.1200.11
2ad045520000-2ad045521000 rw-p 00003000 08:01 6326146                    /usr/lib/libgthread-2.0.so.0.1200.11
2ad045521000-2ad045529000 r-xp 00000000 08:01 3637361                    /lib/librt-2.5.so
2ad045529000-2ad045728000 ---p 00008000 08:01 3637361                    /lib/librt-2.5.so
2ad045728000-2ad04572a000 rw-p 00007000 08:01 3637361                    /lib/librt-2.5.so
2ad04572a000-2ad045754000 r-xp 00000000 08:01 6330594                    /usr/lib/libnjb.so.5.1.0
2ad045754000-2ad045953000 ---p Aborted (core dumped)
ryan@home-desktop:~$ 
```

Those first two X Errors came from when I navigated around the file system. ie: went from /ryan to /ryan/music. It looks like all hell breaks loose when it gets to

```
*** glibc detected *** gnomad2: malloc(): memory corruption: 0x00002aaaac8607a0 ***
```

Any thoughts? Or other programs to use?

---

