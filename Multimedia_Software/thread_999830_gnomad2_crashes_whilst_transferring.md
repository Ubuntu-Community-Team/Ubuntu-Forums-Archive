---
title: "gnomad2 crashes whilst transferring"
date: 2008-12-02
forum: Multimedia Software
---

### Post by nickstar on 2008-12-02
Hi guys,

I'm trying to backup my Creative NOMAD Zen Xtra so I can update the firmware on it. The trouble is sometimes gnomad2 will simply shut down whilst I'm making a transfer. It doesn't matter if im trying to transfer 2 or 20 mp3 files... sometimes Im able to copy an album without a drama, but at other times even just one file will trigger it. Here a copy o the terminal readout, is anyone able to help me make sense of it? Many thanks in advance!
> 
nicholas@nicholas-laptop:~$ gnomad2&
[1] 22379
nicholas@nicholas-laptop:~$ This is a PDE device
*** glibc detected *** gnomad2: malloc(): memory corruption: 0xb5980338 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb782f356]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb7830cad]
/usr/lib/libid3tag.so.0(id3_util_compress+0x42)[0xb7948462]
======= Memory map: ========
08048000-0806e000 r-xp 00000000 08:01 1450852    /usr/local/bin/gnomad2
0806e000-0806f000 rw-p 00025000 08:01 1450852    /usr/local/bin/gnomad2
0806f000-0877b000 rw-p 0806f000 00:00 0          [heap]
b5700000-b5761000 rw-p b5700000 00:00 0 
b5761000-b5800000 ---p b5761000 00:00 0 
b5900000-b59c2000 rw-p b5900000 00:00 0 
b59c2000-b5a00000 ---p b59c2000 00:00 0 
b5a9f000-b5afe000 r-xp 00000000 08:01 1346249    /usr/lib/libgio-2.0.so.0.0.0
b5afe000-b5b00000 rw-p 0005f000 08:01 1346249    /usr/lib/libgio-2.0.so.0.0.0
b5b00000-b5bff000 rw-p b5b00000 00:00 0 
b5bff000-b5c00000 ---p b5bff000 00:00 0 
b5c0c000-b5c23000 r-xp 00000000 08:01 2867325    /lib/libselinux.so.1
b5c23000-b5c25000 rw-p 00016000 08:01 2867325    /lib/libselinux.so.1
b5c25000-b5c34000 r-xp 00000000 08:01 2867238    /lib/libbz2.so.1.0.4
b5c34000-b5c35000 rw-p 0000f000 08:01 2867238    /lib/libbz2.so.1.0.4
b5c35000-b5d4f000 r-xp 00000000 08:01 1344027    /usr/lib/libxml2.so.2.6.31
b5d4f000-b5d54000 rw-p 00119000 08:01 1344027    /usr/lib/libxml2.so.2.6.31
b5d54000-b5d55000 rw-p b5d54000 00:00 0 
b5d55000-b5d87000 r-xp 00000000 08:01 1345245    /usr/lib/libcroco-0.6.so.3.0.1
b5d87000-b5d8a000 rw-p 00031000 08:01 1345245    /usr/lib/libcroco-0.6.so.3.0.1
b5d8a000-b5dba000 r-xp 00000000 08:01 1345499    /usr/lib/libgsf-1.so.114.0.7
b5dba000-b5dbd000 rw-p 0002f000 08:01 1345499    /usr/lib/libgsf-1.so.114.0.7
b5dbd000-b5dbe000 rw-p b5dbd000 00:00 0 
b5dbe000-b5dee000 r-xp 00000000 08:01 1345822    /usr/lib/librsvg-2.so.2.22.2
b5dee000-b5def000 rw-p 00030000 08:01 1345822    /usr/lib/librsvg-2.so.2.22.2
b5dfe000-b5dff000 r-xp 00000000 08:01 1369647    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5dff000-b5e00000 rw-p 00000000 08:01 1369647    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5e00000-b5ee3000 rw-p b5e00000 00:00 0 
b5ee3000-b5f00000 ---p b5ee3000 00:00 0 
b5f0c000-b5f93000 r--p 00000000 08:01 1500773    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b5f93000-b5f94000 ---p b5f93000 00:00 0 
b5f94000-b6794000 rw-p b5f94000 00:00 0 
b6794000-b6795000 r-xp 00000000 08:01 7561399    /usr/lib/gconv/ISO8859-1.so
b6795000-b6797000 rw-p 00000000 08:01 7561399    /usr/lib/gconv/ISO8859-1.so
b6798000-b6799000 ---p b6798000 00:00 0 
b6799000-b6f99000 rw-p b6799000 00:00 0 
b6f99000-b6ff9000 rw-s 00000000 00:09 5898256    /SYSV00000000 (deleted)
b6ff9000-b70fd000 rw-p b6ff9000 00:00 0 
b70fd000-b718e000 r--p 00000000 08:01 1500774    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b718e000-b7190000 r-xp 00000000 08:01 1427410    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7190000-b7191000 rw-p 00001000 08:01 1427410    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b7191000-b7197000 r--s 00000000 08:01 8202215    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b7197000-b719a000 r--s 00000000 08:01 8202213    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b719a000-b719b000 r--s 00000000 08:01 8202212    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b719b000-b719f000 r--s 00000000 08:01 8202193    /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b719f000-b71a0000 r--s 00000000 08:01 8202192    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b71a0000-b71a3000 r--s 00000000 08:01 8202161    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b71a3000-b71a6000 r--s 00000000 08:01 8202159    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b71a6000-b71a9000 r--s 00000000 08:01 8202105    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b71a9000-b71b1000 r--s 00000000 08:01 8202103    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
nicholas@nicholas-laptop:~$ 
[1]+  Aborted                 gnomad2


---

### Post by Whinger on 2012-04-23
> **nickstar said:**
> Hi guys,

I'm trying to backup my Creative NOMAD Zen Xtra so I can update the firmware on it. The trouble is sometimes gnomad2 will simply shut down whilst I'm making a transfer. It doesn't matter if im trying to transfer 2 or 20 mp3 files... sometimes Im able to copy an album without a drama, but at other times even just one file will trigger it. Here a copy o the terminal readout, is anyone able to help me make sense of it? Many thanks in advance!

I know this is a (very) old message but it appears in the first few results for the problem in a google search so I thought I'd add my experience.

Since the crash trace points to libid3tag I turned off all the two ID3-related options (remove all metadata tags, write tags to files) in "Preferences" tab and the problem went away.

Hope this helps someone.

---

