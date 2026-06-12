---
title: "PodEncoder as a User Job in MythTV"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by SuperDodge on 2008-02-11
I am trying to use [podencoder]("http://diveintomark.org/archives/2007/06/07/howto-batch-encode-video-for-ipod-under-linux-2007-edition") as a user job in MythTV to convert my videos to my iPhone.  The user job does not work; however, if I run the program on the command line it works just fin.  Any ideas?


From my log:
> Auto-cropping...crop=1280:720:0:0

(zenity:24669): Gtk-WARNING **: cannot open display:  
/usr/local/bin/podencoder: line 207: echo: write error: Broken pipe
/usr/local/bin/podencoder: line 207: echo: write error: Broken pipe
/usr/local/bin/podencoder: line 206: 100*
0
0/1633: syntax error in expression (error token is "0/1633")

(zenity:24760): Gtk-WARNING **: cannot open display:  
/usr/local/bin/podencoder: line 207: echo: write error: Broken pipe
/usr/local/bin/podencoder: line 210: echo: write error: Broken pipe
Creating 1786_20080208200000.mpg.mp4
*** glibc detected *** MP4Box: double free or corruption (top): 0x0000000000625010 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b12f042bb0a]
/lib/libc.so.6(cfree+0x8c)[0x2b12f042f6fc]
/usr/lib/libgpac.so(AVI_open_input_file+0xb5)[0x2b12efeaac85]
/usr/lib/libgpac.so(gf_media_export_avi_track+0x37)[0x2b12efeb6f27]
MP4Box[0x408a35]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b12f03d7b44]
MP4Box[0x406349]
======= Memory map: ========
00400000-00421000 r-xp 00000000 08:11 1687630                            /usr/bin/MP4Box
00621000-00625000 rw-p 00021000 08:11 1687630                            /usr/bin/MP4Box
00625000-00646000 rw-p 00625000 00:00 0                                  [heap]
2b12efb16000-2b12efb33000 r-xp 00000000 08:11 11117                      /lib/ld-2.6.1.so
2b12efb33000-2b12efb36000 rw-p 2b12efb33000 00:00 0 
2b12efd32000-2b12efd34000 rw-p 0001c000 08:11 11117                      /lib/ld-2.6.1.so
2b12efd34000-2b12eff94000 r-xp 00000000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b12eff94000-2b12f0194000 ---p 00260000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b12f0194000-2b12f019f000 rw-p 00260000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b12f019f000-2b12f01a3000 rw-p 2b12f019f000 00:00 0 
2b12f01a3000-2b12f01b9000 r-xp 00000000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b12f01b9000-2b12f03b9000 ---p 00016000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b12f03b9000-2b12f03ba000 rw-p 00016000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b12f03ba000-2b12f050c000 r-xp 00000000 08:11 11497                      /lib/libc-2.6.1.so
2b12f050c000-2b12f070b000 ---p 00152000 08:11 11497                      /lib/libc-2.6.1.so
2b12f070b000-2b12f070e000 r--p 00151000 08:11 11497                      /lib/libc-2.6.1.so
2b12f070e000-2b12f0710000 rw-p 00154000 08:11 11497                      /lib/libc-2.6.1.so
2b12f0710000-2b12f0715000 rw-p 2b12f0710000 00:00 0 
2b12f0715000-2b12f0795000 r-xp 00000000 08:11 12137                      /lib/libm-2.6.1.so
2b12f0795000-2b12f0994000 ---p 00080000 08:11 12137                      /lib/libm-2.6.1.so
2b12f0994000-2b12f0996000 rw-p 0007f000 08:11 12137                      /lib/libm-2.6.1.so
2b12f0996000-2b12f0997000 rw-p 2b12f0996000 00:00 0 
2b12f0997000-2b12f0a55000 r-xp 00000000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b12f0a55000-2b12f0c55000 ---p 000be000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b12f0c55000-2b12f0c5e000 rw-p 000be000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b12f0c5e000-2b12f0c74000 r-xp 00000000 08:11 12147                      /lib/libpthread-2.6.1.so
2b12f0c74000-2b12f0e73000 ---p 00016000 08:11 12147                      /lib/libpthread-2.6.1.so
2b12f0e73000-2b12f0e75000 rw-p 00015000 08:11 12147                      /lib/libpthread-2.6.1.so
2b12f0e75000-2b12f0e79000 rw-p 2b12f0e75000 00:00 0 
2b12f0e79000-2b12f0e7b000 r-xp 00000000 08:11 12136                      /lib/libdl-2.6.1.so
2b12f0e7b000-2b12f107b000 ---p 00002000 08:11 12136                      /lib/libdl-2.6.1.so
2b12f107b000-2b12f107d000 rw-p 00002000 08:11 12136                      /lib/libdl-2.6.1.so
2b12f107d000-2b12f107e000 rw-p 2b12f107d000 00:00 0 
2b12f107e000-2b12f10b4000 r-xp 00000000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b12f10b4000-2b12f12b3000 ---p 00036000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b12f12b3000-2b12f12b6000 rw-p 00035000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b12f12b6000-2b12f12ba000 rw-p 2b12f12b6000 00:00 0 
2b12f12ba000-2b12f12c7000 r-xp 00000000 08:11 11171                      /lib/libgcc_s.so.1
2b12f12c7000-2b12f14c7000 ---p 0000d000 08:11 11171                      /lib/libgcc_s.so.1
2b12f14c7000-2b12f14c8000 rw-p 0000d000 08:11 11171                      /lib/libgcc_s.so.1
2b12f4000000-2b12f4021000 rw-p 2b12f4000000 00:00 0 
2b12f4021000-2b12f8000000 ---p 2b12f4021000 00:00 0 
7fffbaf67000-7fffbaf94000 rw-p 7fffbaf67000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
/usr/local/bin/podencoder: line 477: 24790 Aborted                 (core dumped) MP4Box -aviraw video "$avioutput".avi > /dev/null
*** glibc detected *** MP4Box: double free or corruption (top): 0x0000000000625010 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b8317bbbb0a]
/lib/libc.so.6(cfree+0x8c)[0x2b8317bbf6fc]
/usr/lib/libgpac.so(AVI_open_input_file+0xb5)[0x2b831763ac85]
/usr/lib/libgpac.so(gf_media_export_avi_track+0x37)[0x2b8317646f27]
MP4Box[0x408a35]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b8317b67b44]
MP4Box[0x406349]
======= Memory map: ========
00400000-00421000 r-xp 00000000 08:11 1687630                            /usr/bin/MP4Box
00621000-00625000 rw-p 00021000 08:11 1687630                            /usr/bin/MP4Box
00625000-00646000 rw-p 00625000 00:00 0                                  [heap]
2b83172a6000-2b83172c3000 r-xp 00000000 08:11 11117                      /lib/ld-2.6.1.so
2b83172c3000-2b83172c6000 rw-p 2b83172c3000 00:00 0 
2b83174c2000-2b83174c4000 rw-p 0001c000 08:11 11117                      /lib/ld-2.6.1.so
2b83174c4000-2b8317724000 r-xp 00000000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b8317724000-2b8317924000 ---p 00260000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b8317924000-2b831792f000 rw-p 00260000 08:11 1737008                    /usr/lib/libgpac-0.4.2.so
2b831792f000-2b8317933000 rw-p 2b831792f000 00:00 0 
2b8317933000-2b8317949000 r-xp 00000000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b8317949000-2b8317b49000 ---p 00016000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b8317b49000-2b8317b4a000 rw-p 00016000 08:11 16508                      /usr/lib/libz.so.1.2.3.3
2b8317b4a000-2b8317c9c000 r-xp 00000000 08:11 11497                      /lib/libc-2.6.1.so
2b8317c9c000-2b8317e9b000 ---p 00152000 08:11 11497                      /lib/libc-2.6.1.so
2b8317e9b000-2b8317e9e000 r--p 00151000 08:11 11497                      /lib/libc-2.6.1.so
2b8317e9e000-2b8317ea0000 rw-p 00154000 08:11 11497                      /lib/libc-2.6.1.so
2b8317ea0000-2b8317ea5000 rw-p 2b8317ea0000 00:00 0 
2b8317ea5000-2b8317f25000 r-xp 00000000 08:11 12137                      /lib/libm-2.6.1.so
2b8317f25000-2b8318124000 ---p 00080000 08:11 12137                      /lib/libm-2.6.1.so
2b8318124000-2b8318126000 rw-p 0007f000 08:11 12137                      /lib/libm-2.6.1.so
2b8318126000-2b8318127000 rw-p 2b8318126000 00:00 0 
2b8318127000-2b83181e5000 r-xp 00000000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b83181e5000-2b83183e5000 ---p 000be000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b83183e5000-2b83183ee000 rw-p 000be000 08:11 1736837                    /usr/lib/libmozjs.so.0d
2b83183ee000-2b8318404000 r-xp 00000000 08:11 12147                      /lib/libpthread-2.6.1.so
2b8318404000-2b8318603000 ---p 00016000 08:11 12147                      /lib/libpthread-2.6.1.so
2b8318603000-2b8318605000 rw-p 00015000 08:11 12147                      /lib/libpthread-2.6.1.so
2b8318605000-2b8318609000 rw-p 2b8318605000 00:00 0 
2b8318609000-2b831860b000 r-xp 00000000 08:11 12136                      /lib/libdl-2.6.1.so
2b831860b000-2b831880b000 ---p 00002000 08:11 12136                      /lib/libdl-2.6.1.so
2b831880b000-2b831880d000 rw-p 00002000 08:11 12136                      /lib/libdl-2.6.1.so
2b831880d000-2b831880e000 rw-p 2b831880d000 00:00 0 
2b831880e000-2b8318844000 r-xp 00000000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b8318844000-2b8318a43000 ---p 00036000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b8318a43000-2b8318a46000 rw-p 00035000 08:11 16302                      /usr/lib/libnspr4.so.0d
2b8318a46000-2b8318a4a000 rw-p 2b8318a46000 00:00 0 
2b8318a4a000-2b8318a57000 r-xp 00000000 08:11 11171                      /lib/libgcc_s.so.1
2b8318a57000-2b8318c57000 ---p 0000d000 08:11 11171                      /lib/libgcc_s.so.1
2b8318c57000-2b8318c58000 rw-p 0000d000 08:11 11171                      /lib/libgcc_s.so.1
2b831c000000-2b831c021000 rw-p 2b831c000000 00:00 0 
2b831c021000-2b8320000000 ---p 2b831c021000 00:00 0 
7fff937d8000-7fff93804000 rw-p 7fff937d8000 00:00 0                      [stack]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vdso]
/usr/local/bin/podencoder: line 478: 24803 Aborted                 (core dumped) MP4Box -aviraw audio "$avioutput".avi > /dev/null
mv: cannot stat `/MythMedia/Temp/1786_20080208200000.mpg.temp_video.h264': No such file or directory
mv: cannot stat `/MythMedia/Temp/1786_20080208200000.mpg.temp_audio.raw': No such file or directory
 (Requested URL is not valid or cannot be found) (Requested URL is not valid or cannot be found)
(zenity:24818): Gtk-WARNING **: cannot open display:  
2008-02-11 08:19:22.950 JobQueue: Finished "Convert to iPhone" for "Bones" recorded from channel 1786 at Fri Feb 8 20:00:00 2008.

---

### Post by SuperDodge on 2008-02-12
Bump.  Can anyone help a Newbie out?

---

### Post by SuperDodge on 2008-02-12
Another bump...no one can offer any help?

---

### Post by madsteer on 2008-04-13
I think one of the programs in podencoder expects to have an X server available, even though it may not use it.  I can't run podencoder at all unless interactively inside of an X window service.  I think MP4Box might be the problem, but I'm not 100% sure.

I  would like to be able to run podencoder inside an AT job and am having these same errors.

Thanks,

---

