---
title: "Grip Crashing... where to start looking?"
date: 2009-05-06
forum: Multimedia Software
---

### Post by ajaygautam on 2009-05-06
Hello

I am using grip to convert my cds to mp3. Recently, this has stopped working!

Ripping seems to be progressing fine, but the encoding part seems to crap out at the very near end of the first track!

No errors, no warnings, nothing... just a crash. Nothing is in /var/log/messages or dmesg either! Running grip from the command line produced a lot of output at stdout/stderr - none of which makes sense to me (attached below).

Version information:
Ubuntu version 9.04, 2.6.28-11-generic #42-Ubuntu SMP
Grip version 3.3.1
cdparanoia III release 10.2 (September 11, 2008 )
LAME 32bits version 3.98

Any help / pointers / further steps / debugging would be greatly appreciated.

Thanks

Ajay

stdout/err:
```

agautam@Komputor ~ 23:55:53 $ grip
*** buffer overflow detected ***: grip terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb6ea6da8]
/lib/tls/i686/cmov/libc.so.6[0xb6ea4eb0]
/lib/tls/i686/cmov/libc.so.6[0xb6ea45a8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0xc8)[0xb6e16bb8]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0x6f3)[0xb6de8f23]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xa4)[0xb6ea4654]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xb6ea459d]
grip[0x8063afd]
grip[0x80605bb]
grip[0x80507a8]
grip[0x804ecc3]
/usr/lib/libglib-2.0.so.0[0xb721f2b6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb721eb88]
/usr/lib/libglib-2.0.so.0[0xb72220eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb72225ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb786e7d9]
grip[0x804ec98]
grip[0x804ea42]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb6dbf775]
grip[0x804e981]
======= Memory map: ========
08048000-08076000 r-xp 00000000 08:01 9782836    /usr/bin/grip
08076000-08077000 r--p 0002e000 08:01 9782836    /usr/bin/grip
08077000-0807b000 rw-p 0002f000 08:01 9782836    /usr/bin/grip
0807b000-080a8000 rw-p 0807b000 00:00 0 
08a02000-08e9b000 rw-p 08a02000 00:00 0          [heap]
b34c0000-b3784000 rw-p b437a000 00:00 0 
b4100000-b4121000 rw-p b4100000 00:00 0 
b4121000-b4200000 ---p b4121000 00:00 0 
b4221000-b53a5000 rw-p b4221000 00:00 0 
b53a5000-b53a6000 ---p b53a5000 00:00 0 
b53a6000-b5ba6000 rw-p b53a6000 00:00 0 
b5ba6000-b61ea000 r--p 00000000 08:01 5062735    /usr/share/icons/gnome/icon-theme.cache
b61ea000-b652f000 r--p 00000000 08:01 10108996   /usr/share/icons/hicolor/icon-theme.cache
b652f000-b6579000 r--p 00000000 08:01 606427     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono-Bold.ttf
b6579000-b65c8000 r--p 00000000 08:01 606426     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSansMono.ttf
b65c8000-b6660000 r--p 00000000 08:01 606424     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6660000-b6662000 r-xp 00000000 08:01 9912598    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6662000-b6663000 r--p 00001000 08:01 9912598    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6663000-b6664000 rw-p 00002000 08:01 9912598    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6664000-b666a000 r--s 00000000 08:01 35047503   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b666a000-b666f000 r--s 00000000 08:01 35047696   /var/cache/fontconfig/e25ca923d7a08ab6b0777bd7eb77ea77-x86.cache-2
b666f000-b6672000 r--s 00000000 08:01 35047701   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6672000-b6673000 r--s 00000000 08:01 35047686   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b6673000-b6675000 r--s 00000000 08:01 35047734   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b6675000-b6676000 r--s 00000000 08:01 35047710   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b6676000-b6677000 r--s 00000000 08:01 35047725   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b6677000-b667b000 r--s 00000000 08:01 35047719   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b667b000-b667d000 r--s 00000000 08:01 35047666   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b667d000-b6680000 r--s 00000000 08:01 35047509   /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b6680000-b6681000 r--s 00000000 08:01 35047699   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6681000-b6683000 r--s 00000000 08:01 35047735   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b6683000-b6686000 r--s 00000000 08:01 35047678   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6686000-b6688000 r--s 00000000 08:01 35047677   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b6688000-b668b000 r--s 00000000 08:01 35047667   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b668b000-b6692000 r--s 00000000 08:01 35047690   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6692000-b6695000 r--s 00000000 08:01 35047679   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6695000-b6697000 r--s 00000000 08:01 35047615   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6697000-b669f000 r--s 00000000 08:01 35047576   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b669f000-b66aa000 r--s 00000000 08:01 35047508   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b66aa000-b66ac000 r--s 00000000 08:01 3504700Aborted
agautam@Komputor ~ 00:00:52 $ 

```

---

### Post by ajaygautam on 2009-05-07
This is definitely a grip issue.

I started grip on the same cd and selected "Rip Only" - works fine.

Then, I selected rip and encode. (also did a ps and got the lame ps args).

Grip encoded track 1 to mp3, then crashed. It was successful in encoding track 1, because it deleted the track 1 wav file.

I re-ripped the disc (to get track 1 wav)
Then I took the ps args, and ran it from command line:

```
lame -h -b 128 track1.wav 1.mp3
```

It worked fine.

Did the same for track 2, that worked fine too!

So I guess whatever grip does between encoding of track 1 and track 2 crashes!

Anyone knows what that might be?

Ajay

---

### Post by malworthy on 2009-05-24
I had exactly the same problem.  I fixed it by downloading grip v 3.2 and compiling it from source.  The grip in the repositories is version 3.1.

I had to install a couple of packages before i could compile it, libgnomeui-dev and another one i don't remember, but I did get it to work.

---

### Post by ajaygautam on 2009-05-24
That is one way to do it. In case you don't want to re-compile manually, just disable id3v2 tags.

More details at:
[https://bugs.launchpad.net/ubuntu/+source/grip/+bug/283658](https://bugs.launchpad.net/ubuntu/+source/grip/+bug/283658)

---

