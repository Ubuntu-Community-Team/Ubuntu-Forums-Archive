---
title: "dvgrab crashes when capturing VHS tapes via my Canon camcorder"
date: 2008-06-12
forum: Multimedia Software
---

### Post by cowmix on 2008-06-12
It will not capture for more than a few minutes when I get a crash like this:

mmarch@Cowmix-desktop:~/cap/cap2$ sudo dvgrab
Found AV/C device with GUID 0x0000850000849fea
Capture Started

"dvgrab-001.avi": buffer underrun near: timecode 134520770:-1993832910:00.00 date 2008.06.12 09:35:11
This error means that the frames could not be written fast enough.
"dvgrab-001.avi": 999.91 MB 8436 frames timecode 163303668:-1319378680:-1252003832.159928976 date 2008.06.12 09:39:52
*** stack smashing detected ***: dvgrab terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)<0xb7c6b138>
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x0)<0xb7c6b0f0>
dvgrab<0x8053232>
dvgrab<0x805525e>
dvgrab<0x80558b4>
dvgrab<0x8055b11>
/lib/tls/i686/cmov/libpthread.so.0<0xb7e374fb>
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)<0xb7c54e5e>
======= Memory map: ========
08048000-08083000 r-xp 00000000 08:06 5237452 /usr/bin/dvgrab
08083000-08084000 rw-p 0003a000 08:06 5237452 /usr/bin/dvgrab
08084000-09c4c000 rw-p 08084000 00:00 0
b049a000-b04cd000 rw-p b049a000 00:00 0
b051c000-b051d000 ---p b051c000 00:00 0
b051d000-b0d1d000 rw-p b051d000 00:00 0
b0d1d000-b0d9a000 rw-s 00000000 00:0e 110252 /dev/raw1394
b0d9a000-b0dbe000 rw-p b0d9a000 00:00 0
b0dbe000-b0dbf000 ---p b0dbe000 00:00 0
b0dbf000-b7b7e000 rw-p b0dbf000 00:00 0
b7b7e000-b7cc7000 r-xp 00000000 08:06 5637474 /lib/tls/i686/cmov/libc-2.7.so
b7cc7000-b7cc8000 r--p 00149000 08:06 5637474 /lib/tls/i686/cmov/libc-2.7.so
b7cc8000-b7cca000 rw-p 0014a000 08:06 5637474 /lib/tls/i686/cmov/libc-2.7.so
b7cca000-b7ccd000 rw-p b7cca000 00:00 0
b7ccd000-b7cd7000 r-xp 00000000 08:06 5619776 /lib/libgcc_s.so.1
b7cd7000-b7cd8000 rw-p 0000a000 08:06 5619776 /lib/libgcc_s.so.1
b7cd8000-b7dc0000 r-xp 00000000 08:06 5236794 /usr/lib/libstdc++.so.6.0.9
b7dc0000-b7dc3000 r--p 000e8000 08:06 5236794 /usr/lib/libstdc++.so.6.0.9
b7dc3000-b7dc5000 rw-p 000eb000 08:06 5236794 /usr/lib/libstdc++.so.6.0.9
b7dc5000-b7dcb000 rw-p b7dc5000 00:00 0
b7dcb000-b7dea000 r-xp 00000000 08:06 5236546 /usr/lib/libjpeg.so.62.0.0
b7dea000-b7deb000 rw-p 0001e000 08:06 5236546 /usr/lib/libjpeg.so.62.0.0
b7deb000-b7dee000 r-xp 00000000 08:06 5236736 /usr/lib/librom1394.so.0.3.0
b7dee000-b7def000 rw-p 00002000 08:06 5236736 /usr/lib/librom1394.so.0.3.0
b7def000-b7df2000 r-xp 00000000 08:06 5236110 /usr/lib/libavc1394.so.0.3.0
b7df2000-b7df3000 rw-p 00002000 08:06 5236110 /usr/lib/libavc1394.so.0.3.0
b7df3000-b7df4000 rw-p b7df3000 00:00 0
b7df4000-b7df6000 r-xp 00000000 08:06 5637480 /lib/tls/i686/cmov/libdl-2.7.so
b7df6000-b7df8000 rw-p 00001000 08:06 5637480 /lib/tls/i686/cmov/libdl-2.7.so
b7df8000-b7e0c000 r-xp 00000000 08:06 5236869 /usr/lib/libz.so.1.2.3.3
b7e0c000-b7e0d000 rw-p 00013000 08:06 5236869 /usr/lib/libz.so.1.2.3.3
b7e0d000-b7e30000 r-xp 00000000 08:06 5637482 /lib/tls/i686/cmov/libm-2.7.so
b7e30000-b7e32000 rw-p 00023000 08:06 5637482 /lib/tls/i686/cmov/libm-2.7.so
b7e32000-b7e46000 r-xp 00000000 08:06 5637500 /lib/tls/i686/cmov/libpthread-2.7.so
b7e46000-b7e48000 rw-p 00013000 08:06 5637500 /lib/tls/i686/cmov/libpthread-2.7.so
b7e48000-b7e4a000 rw-p b7e48000 00:00 0
b7e4a000-b7f13000 r-xp 00000000 08:06 5237364 /usr/lib/libquicktime.so.1.0.0
b7f13000-b7f16000 rw-p 000c9000 08:06 5237364 /usr/lib/libquicktime.so.1.0.0
b7f16000-b7f17000 rw-p b7f16000 00:00 0
b7f17000-b7f30000 r-xp 00000000 08:06 5236215 /usr/lib/libdv.so.4.0.3
b7f30000-b7f32000 rw-p 00019000 08:06 5236215 /usr/lib/libdv.so.4.0.3
b7f32000-b7f3f000 rw-p b7f32000 00:00 0
b7f3f000-b7f4b000 r-xp 00000000 08:06 5236534 /usr/lib/libiec61883.so.0.1.0
b7f4b000-b7f4c000 rw-p 0000b000 08:06 5236534 /usr/lib/libiec61883.so.0.1.0
b7f4c000-b7f51000 r-xp 00000000 08:06 5236729 /usr/lib/libraw1394.so.8.2.0
b7f51000-b7f52000 rw-p 00004000 08:06 5236729 /usr/lib/libraw1394.so.8.2.0
b7f60000-b7f62000 rw-p b7f60000 00:00 0
b7f62000-b7f63000 r-xp b7f62000 00:00 0
b7f63000-b7f7d000 r-xp 00000000 08:06 5619731 /lib/ld-2.7.so
b7f7d000-b7f7f000 rw-p 00019000 08:06 5619731 /lib/ld-2.7.so
bfdc9000-bfdde000 rw-p bffeb000 00:00 0
Aborted

---

### Post by xc3RnbFO8P on 2008-06-12
Maybe a bug?
[https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/197176]("https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/197176")

---

### Post by cowmix on 2008-06-12
> **Ringi said:**
> Maybe a bug?
[https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/197176]("https://bugs.launchpad.net/ubuntu/+source/dvgrab/+bug/197176")

Yeah.. that's it.

---

### Post by roberto.eiberle on 2008-06-12
dvgrab won't work with VHS tapes it is for dv tapes only e.g. minidv.

---

### Post by cowmix on 2008-06-28
Most DV camcorders do on-the-fly A->D convertion... so dvgrab should work when encoding VHS tapes.

> **roberto.eiberle said:**
> dvgrab won't work with VHS tapes it is for dv tapes only e.g. minidv.

---

