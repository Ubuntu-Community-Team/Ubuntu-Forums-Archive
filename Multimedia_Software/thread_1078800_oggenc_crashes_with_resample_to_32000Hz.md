---
title: "oggenc crashes with resample to 32000Hz"
date: 2009-02-23
forum: Multimedia Software
---

### Post by ezekiel000 on 2009-02-23
I have a directory of wav files to convert but if I try to batch re-sample them to 32000Hz (from 22050Hz and 44100Hz) I get this:
oggenc -b 64 --resample 32000 --downmix  *.wav
Opening with wav module: WAV file reader
Resampling input from 22050 Hz to 32000 Hz
WARNING: Can't downmix except from stereo to mono
Encoding "0005.wav" to 
         "0005.ogg" 
at approximate bitrate 64 kbps (VBR encoding enabled)
	[ 73.9%] [ 0m00s remaining] - 

Done encoding file "0005.ogg"

	File length:  0m 02.0s
	Elapsed time: 0m 00.1s
	Rate:         24.6719
	Average bitrate: 47.9 kb/s

*** glibc detected *** oggenc: munmap_chunk(): invalid pointer: 0x0000000000405540 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fa4c94d7a58]
oggenc[0x404fad]
oggenc[0x404357]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fa4c947c466]
oggenc[0x402699]
======= Memory map: ========
00400000-0040f000 r-xp 00000000 08:01 52719                              /usr/bin/oggenc
0060e000-0060f000 r--p 0000e000 08:01 52719                              /usr/bin/oggenc
0060f000-00610000 rw-p 0000f000 08:01 52719                              /usr/bin/oggenc
0213e000-02189000 rw-p 0213e000 00:00 0                                  [heap]
7fa4c9246000-7fa4c925c000 r-xp 00000000 08:01 73471                      /lib/libgcc_s.so.1
7fa4c925c000-7fa4c945c000 ---p 00016000 08:01 73471                      /lib/libgcc_s.so.1
7fa4c945c000-7fa4c945d000 r--p 00016000 08:01 73471                      /lib/libgcc_s.so.1
7fa4c945d000-7fa4c945e000 rw-p 00017000 08:01 73471                      /lib/libgcc_s.so.1
7fa4c945e000-7fa4c95c7000 r-xp 00000000 08:01 7770                       /lib/libc-2.8.90.so
7fa4c95c7000-7fa4c97c6000 ---p 00169000 08:01 7770                       /lib/libc-2.8.90.so
7fa4c97c6000-7fa4c97ca000 r--p 00168000 08:01 7770                       /lib/libc-2.8.90.so
7fa4c97ca000-7fa4c97cb000 rw-p 0016c000 08:01 7770                       /lib/libc-2.8.90.so
7fa4c97cb000-7fa4c97d0000 rw-p 7fa4c97cb000 00:00 0 
7fa4c97d0000-7fa4c97d5000 r-xp 00000000 08:01 9604                       /usr/lib/libogg.so.0.5.3
7fa4c97d5000-7fa4c99d4000 ---p 00005000 08:01 9604                       /usr/lib/libogg.so.0.5.3
7fa4c99d4000-7fa4c99d5000 r--p 00004000 08:01 9604                       /usr/lib/libogg.so.0.5.3
7fa4c99d5000-7fa4c99d6000 rw-p 00005000 08:01 9604                       /usr/lib/libogg.so.0.5.3
7fa4c99d6000-7fa4c9a5a000 r-xp 00000000 08:01 7774                       /lib/libm-2.8.90.so
7fa4c9a5a000-7fa4c9c59000 ---p 00084000 08:01 7774                       /lib/libm-2.8.90.so
7fa4c9c59000-7fa4c9c5a000 r--p 00083000 08:01 7774                       /lib/libm-2.8.90.so
7fa4c9c5a000-7fa4c9c5b000 rw-p 00084000 08:01 7774                       /lib/libm-2.8.90.so
7fa4c9c5b000-7fa4c9ca3000 r-xp 00000000 08:01 8862                       /usr/lib/libFLAC.so.8.2.0
7fa4c9ca3000-7fa4c9ea3000 ---p 00048000 08:01 8862                       /usr/lib/libFLAC.so.8.2.0
7fa4c9ea3000-7fa4c9ea4000 r--p 00048000 08:01 8862                       /usr/lib/libFLAC.so.8.2.0
7fa4c9ea4000-7fa4c9ea5000 rw-p 00049000 08:01 8862                       /usr/lib/libFLAC.so.8.2.0
7fa4c9ea5000-7fa4c9ec4000 r-xp 00000000 08:01 9822                       /usr/lib/libvorbis.so.0.4.0
7fa4c9ec4000-7fa4ca0c3000 ---p 0001f000 08:01 9822                       /usr/lib/libvorbis.so.0.4.0
7fa4ca0c3000-7fa4ca0c4000 r--p 0001e000 08:01 9822                       /usr/lib/libvorbis.so.0.4.0
7fa4ca0c4000-7fa4ca0d2000 rw-p 0001f000 08:01 9822                       /usr/lib/libvorbis.so.0.4.0
7fa4ca0d2000-7fa4ca0ec000 r-xp 00000000 08:01 9824                       /usr/lib/libvorbisenc.so.2.0.3
7fa4ca0ec000-7fa4ca2eb000 ---p 0001a000 08:01 9824                       /usr/lib/libvorbisenc.so.2.0.3
7fa4ca2eb000-7fa4ca2ec000 r--p 00019000 08:01 9824                       /usr/lib/libvorbisenc.so.2.0.3
7fa4ca2ec000-7fa4ca4ab000 rw-p 0001a000 08:01 9824                       /usr/lib/libvorbisenc.so.2.0.3
7fa4ca4ab000-7fa4ca4ca000 r-xp 00000000 08:01 7767                       /lib/ld-2.8.90.so
7fa4ca58b000-7fa4ca58c000 rw-p 7fa4ca58b000 00:00 0 
7fa4ca58c000-7fa4ca58d000 r--p 00000000 08:01 61933                      /usr/share/locale-langpack/en_GB/LC_MESSAGES/vorbis-tools.mo
7fa4ca58d000-7fa4ca58e000 rw-p 7fa4ca58d000 00:00 0 
7fa4ca58e000-7fa4ca5cd000 r--p 00000000 08:01 12898                      /usr/lib/locale/en_GB.utf8/LC_CTYPE
7fa4ca5cd000-7fa4ca6ae000 r--p 00000000 08:01 12897                      /usr/lib/locale/en_GB.utf8/LC_COLLATE
7fa4ca6ae000-7fa4ca6b1000 rw-p 7fa4ca6ae000 00:00 0 
7fa4ca6b5000-7fa4ca6b6000 r--p 00000000 08:01 12942                      /usr/lib/locale/en_GB.utf8/LC_NUMERIC
7fa4ca6b6000-7fa4ca6b7000 r--p 00000000 08:01 12793                      /usr/lib/locale/en_GB.utf8/LC_TIME
7fa4ca6b7000-7fa4ca6b8000 r--p 00000000 08:01 12794                      /usr/lib/locale/en_GB.utf8/LC_MONETARY
7fa4ca6b8000-7fa4ca6b9000 r--p 00000000 08:01 12920                      /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7fa4ca6b9000-7fa4ca6ba000 r--p 00000000 08:01 12904                      /usr/lib/locale/en_GB.utf8/LC_PAPER
7fa4ca6ba000-7fa4ca6bb000 r--p 00000000 08:01 12915                      /usr/lib/locale/en_GB.utf8/LC_NAME
7fa4ca6bb000-7fa4ca6bc000 r--p 00000000 08:01 12795                      /usr/lib/locale/en_GB.utf8/LC_ADDRESS
7fa4ca6bc000-7fa4ca6bd000 r--p 00000000 08:01 12796                      /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
7fa4ca6bd000-7fa4ca6be000 r--p 00000000 08:01 12900                      /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
7fa4ca6be000-7fa4ca6c5000 r--s 00000000 08:01 7563                       /usr/lib/gconv/gconv-modules.cache
7fa4ca6c5000-7fa4ca6c6000 r--p 00000000 08:01 12797                      /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
7fa4ca6c6000-7fa4ca6c9000 rw-p 7fa4ca6c6000 00:00 0 
7fa4ca6c9000-7fa4ca6ca000 r--p 0001e000 08:01 7767                       /lib/ld-2.8.90.so
7fa4ca6ca000-7fa4ca6cb000 rw-p 0001f000 08:01 7767                       /lib/ld-2.8.90.so
7fffd26aa000-7fffd26ca000 rw-p 7ffffffdf000 00:00 0                      [stack]
7fffd27f4000-7fffd27f5000 r-xp 7fffd27f4000 00:00 0                      [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

Can anyone help?

---

### Post by kumoshk on 2009-10-31
I get the same error using Karmic 64-bit on my laptop with the following command:
oggenc -q -1.0 --resample 14000 --downmix someFile.wav

It worked fine in Jaunty 32-bit, so I tried installing the jaunty version of vorbis-tools on my 64-bit laptop, but I get the same error with it, even.

Does the same error occur in Karmic 32-bit?

EDIT:
It even gives the same error if I build vorbis-tools from the source (on 64-bit Karmic). I'm guessing it's not the fault of oggenc, but rather there must be some conflicting file(s) in Karmic.

---

### Post by kumoshk on 2009-10-31
All right, I've found a temporary solution, until they fix the 64-bit version (excuse me if you don't need these detailed instructions&#8212;I figure someone else might):

Download vorbis-tools:
[http://downloads.xiph.org/releases/vorbis/vorbis-tools-1.2.0.tar.gz](http://downloads.xiph.org/releases/vorbis/vorbis-tools-1.2.0.tar.gz)

Compile it on a 32-bit computer with Ubuntu. If you don't want to figure out the dependencies, do this first:
sudo apt-get build-dep vorbis-tools

Then do this
./configure
make

Then copy the folder over to your 64-bit computer.

Then make sure you have 32-bit support:
sudo apt-get install ia32-libs

All right. Don't do make install on the 64-bit computer&#8212;it shouldn't work.

So, uncompress and find a nice place to store your built vorbis-tools.

Make a link to oggenc (it's in the oggenc folder) and put your link in your home directory's bin folder (make one if there isn't one).

To make the link right-click and select make link. Rename it whatever you want. If your bin directory didn't already exist, you may have to restart your computer before it will show up in your path.

Then you can use oggenc as you normally would.

Let me know if you need the compiled binaries. I'll have to send you a link from my server since it's too big to upload unless I cut out files that may or may not be important (and I'm not sure where the license stuff is in all this).

---

