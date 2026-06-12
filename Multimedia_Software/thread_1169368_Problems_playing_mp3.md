---
title: "Problems playing mp3"
date: 2009-05-25
forum: Multimedia Software
---

### Post by xodeus on 2009-05-25
I've some issues when I try to play mp3's..

When I do I get an error:
```
Mon May 25 10:44:59 2009: GStreamer encountered a general resource error.
```

And the sound is like someone is scratching an LP...
Never heard it before.
I've tried Totem, Rhythmbox, Audacious and Quod Libet. So I think it's an issue with GStreamer...

I've installed the ubuntu-restricted-extras package...

The file plays just fine on my mobile phone...

I've now reproduced this issue with Audacious open from the Terminal, and here's the output:
```

....
** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated
^CAudacious has received SIGINT and is shutting down.

** (audacious:11844): WARNING **: Connection died: Connection terminated

** (audacious:11844): WARNING **: Connection died: Connection terminated
amidi-plug(i_backend.c:i_backend_unload:164): unloading backend 'alsa'
amidi-plug(i_backend.c:i_backend_unload:167): backend 'alsa' unloaded
LASTFM: (cleanup) Cleanup finished
*** glibc detected *** audacious: double free or corruption (fasttop): 0x095d8ca8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75f2604]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb75f45b6]
/usr/lib/libglib-2.0.so.0(g_free+0x36)[0xb7eb2126]
audacious[0x8065cb9]
audacious[0x8066aaf]
audacious[0x805ca60]
audacious[0x805d15e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7599775]
audacious[0x8056f11]
======= Memory map: ========
08048000-08117000 r-xp 00000000 08:02 177657     /usr/bin/audacious
08117000-08118000 r--p 000cf000 08:02 177657     /usr/bin/audacious
08118000-0811e000 rw-p 000d0000 08:02 177657     /usr/bin/audacious
0811e000-08121000 rw-p 0811e000 00:00 0 
0950a000-09ae7000 rw-p 0950a000 00:00 0          [heap]
ade00000-adf00000 rw-p ade00000 00:00 0 
b2a00000-b2ba0000 rw-p b2a00000 00:00 0 
b2ba0000-b2c00000 ---p b2ba0000 00:00 0 
b2c00000-b2e00000 rw-p b2c00000 00:00 0 
b2e00000-b2f00000 rw-p b2e00000 00:00 0 
b2fc3000-b2fc4000 rw-p b2fc3000 00:00 0 
b2fc4000-b2fc5000 ---p b2fc4000 00:00 0 
b2fc5000-b37c5000 rw-p b2fc5000 00:00 0 
b37c5000-b37c6000 ---p b37c5000 00:00 0 
b37c6000-b3fc6000 rw-p b37c6000 00:00 0 
b3fc6000-b3fc8000 r-xp 00000000 08:02 2625       /lib/libnss_mdns4_minimal.so.2
b3fc8000-b3fc9000 rw-p 00001000 08:02 2625       /lib/libnss_mdns4_minimal.so.2
b3fd9000-b4071000 r--p 00000000 08:02 42093      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4138000-b413d000 r-xp 00000000 08:02 6188       /lib/tls/i686/cmov/libnss_dns-2.9.so
b413d000-b413e000 r--p 00004000 08:02 6188       /lib/tls/i686/cmov/libnss_dns-2.9.so
b413e000-b413f000 rw-p 00005000 08:02 6188       /lib/tls/i686/cmov/libnss_dns-2.9.so
b413f000-b41cb000 r--p 00000000 08:02 42092      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b41cb000-b41ce000 r--s 00000000 08:02 107218     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b41ce000-b41d1000 r--s 00000000 08:02 107214     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b41d1000-b41d4000 r--s 00000000 08:02 107224     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b41d4000-b41dc000 r--s 00000000 08:02 107227     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b41dc000-b41e7000 r--s 00000000 08:02 107207     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b41e7000-b4209000 r--s 00000000 08:02 134564     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4209000-b4210000 r--s 00000000 08:02 107221     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4210000-b4216000 r--s 00000000 08:02 107206     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4216000-b421d000 r--s 00000000 08:02 175941     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b421d000-b427d000 rw-s 00000000 00:09 6881300    /SYSV00000000 (deleted)
b427d000-b42dd000 rw-s 00000000 00:09 6848530    /SYSV00000000 (deleted)
b42dd000-b42e3000 r-xp 00000000 08:02 12696      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b42e3000-b42e4000 r--p 00005000 08:02 12696      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b42e4000-b42e5000 rw-p 00006000 08:02 12696      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b42e5000-b42e6000 ---p b42e5000 00:00 0 
b42e6000-b4ae6000 rw-p b42e6000 00:00 0 
b4ae6000-b4aea000 r-xp 00000000 08:02 12689      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4aea000-b4aeb000 r--p 00003000 08:02 12689      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4aeb000-b4aec000 rw-p 00004000 08:02 12689      /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b4aed000-b4b06000 rw-p b4aed000 00:00 0 
b4f06000-b4f07000 ---p b4f06000 00:00 0 
b4f07000-b5707000 rw-p b4f07000 00:00 0 
b578e000-b57ad000 r-xp 00000000 08:02 133697     /usr/lib/libneon-gnutls.so.27.1.2
b57ad000-b57ae000 r--p 0001e000 08:02 133697     /usr/lib/libneon-gnutls.so.27.1.2
b57ae000-b57af000 rw-p 0001f000 08:02 133697     /usr/lib/libneon-gnutls.so.27.1.2
b57af000-b57b5000 r--s 00000000 08:02 107217     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b57b5000-b57bf000 rw-p b57b5000 00:00 0 
b57cc000-b57d2000 r-xp 00000000 08:02 175839     /usr/lib/audacious/Transport/neon.so
b57d2000-b57d3000 r--p 00005000 08:02 175839     /usr/lib/audacious/Transport/neon.so
b57d3000-b57d4000 rw-p 00006000 08:02 175839     /usr/lib/audacious/Transport/neon.so
b5840000-b5842000 r-xp 00000000 08:02 18005      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5842000-b5843000 r--p 00001000 08:02 18005      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5843000-b5844000 rw-p 00002000 08:02 18005      /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b58e5000-b5a1a000 r-xp 00000000 08:02 10331      /usr/lib/libxml2.so.2.6.32
b5a1a000-b5a1b000 ---p 00135000 08:02 10331      /usr/lib/libxml2.so.2.6.32
b5a1b000-b5a1f000 r--p 00135000 08:02 10331      /usr/lib/libxml2.so.2.6.32
b5a1f000-b5a20000 rw-p 00139000 08:02 10331      /usr/lib/libxml2.so.2.6.32
b5a20000-b5a21000 rw-p b5a20000 00:00 0 
b5a21000-b5a24000 r--s 00000000 08:02 107226     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5a5c000-b5a5f000 r--s 00000000 08:02 134435     /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b5a7e000-b5a81000 r-xp 00000000 08:02 2599       /lib/libgpg-error.so.0.3.0
b5a81000-b5a82000 rw-p 00002000 08:02 2599       /lib/libgpg-error.so.0.3.0
b5a82000-b5a84000 r-xp 00000000 08:02 2604       /lib/libkeyutils-1.2.so
b5a84000-b5a85000 r--p 00001000 08:02 2604       /lib/libkeyutils-1.2.so
b5a85000-b5a86000 rw-p 00002000 08:02 2604       /lib/libkeyutils-1.2.so
b5a86000-b5a8d000 r-xp 00000000 08:02 9958       /usr/lib/libkrb5support.so.0.1
b5a8d000-b5a8e000 r--p 00006000 08:02 9958       /usr/lib/libkrb5support.so.0.1
b5a8e000-b5a8f000 rw-p 00007000 08:02 9958       /usr/lib/libkrb5support.so.0.1
b5a8f000-b5a91000 r-xp 00000000 08:02 2580       /lib/libcom_err.so.2.1
b5a91000-b5a92000 r--p 00001000 08:02 2580       /lib/libcom_err.so.2.1
b5a92000-b5a93000 rw-p 00002000 08:02 2580       /lib/libcom_err.so.2.1
b5a93000-b5ab5000 r-xp 00000000 08:02 9950       /usr/lib/libk5crypto.so.3.1
b5ab5000-b5ab6000 r--p 00022000 08:02 9950       /usr/lib/libk5crypto.so.3.1
b5ab6000-b5ab7000 rw-p 00023000 08:02 9950       /usr/lib/libk5crypto.so.3.1
b5ab7000-b5b46000 r-xp 00000000 08:02 9956       /usr/lib/libkrb5.so.3.3
b5b46000-b5b48000 r--p 0008e000 08:02 9956       /usr/lib/libkrb5.so.3.3
b5b48000-b5b49000 rw-p 00090000 08:02 9956       /usr/lib/libkrb5.so.3.3
b5b61000-b5b73000 r-xp 00000000 08:02 6201       /lib/tls/i686/cmov/libresolv-2.9.so
b5b73000-b5b74000 r--p 00011000 08:02 6201       /lib/tls/i686/cmov/libresolv-2.9.so
b5b74000-b5b75000 rw-p 00012000 08:02 6201       /lib/tls/i686/cmov/libresolv-2.9.so
b5b75000-b5b77000 rw-p b5b75000 00:00 0 
b5b77000-b5bdd000 r-xp 00000000 08:02 2597       /lib/libgcrypt.so.11.4.4
b5bdd000-b5bde000 r--p 00065000 08:02 2597       /lib/libgcrypt.so.11.4.4
b5bde000-b5be0000 rw-p 00066000 08:02 2597       /lib/libgcrypt.so.11.4.4
b5be0000-b5bf0000 r-xp 00000000 08:02 10249      /usr/lib/libtasn1.so.3.0.16
b5bf0000-b5bf1000 r--p 0000f000 08:02 10249      /usr/lib/libtasn1.so.3.0.16
b5bf1000-b5bf2000 rw-p 00010000 08:02 10249      /usr/lib/libtasn1.so.3.0.16
b5bf2000-b5c89000 r-xp 00000000 08:02 9765       /usr/lib/libgnutls.so.26.4.6
b5c89000-b5c8e000 r--p 00097000 08:02 9765       /usr/lib/libgnutls.so.26.4.6
b5c8e000-b5c8f000 rw-p 0009c000 08:02 9765       /usr/lib/libgnutls.so.26.4.6
b5c8f000-b5cb8000 r-xp 00000000 08:02 9805       /usr/lib/libgssapi_krb5.so.2.2
b5cb8000-b5cb9000 r--p 00028000 08:02 9805       /usr/lib/libgssapi_krb5.so.2.2
b5cb9000-b5cba000 rw-p 00029000 08:02 9805       /usr/lib/libgssapi_krb5.so.2.2
b6033000-b60f6000 r-xp 00000000 08:02 9431       /usr/lib/libasound.so.2.0.0
b60f6000-b60f8000 r--p 000c2000 08:02 9431       /usr/lib/libasound.so.2.0.0
b60f8000-b60fb000 rw-p 000c4000 08:02 9431       /usr/lib/libasound.so.2.0.0
b653e000-b6540000 r--s 00000000 08:02 107223     /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b65b3000-b65b4000 r--s 00000000 08:02 107212     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b65b4000-b65b5000 r--s 00000000 08:02 107210     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b65ec000-b65ee000 r--s 00000000 08:02 134563     /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b6731000-b673e000 r-xp 00000000 08:02 2595       /lib/libgcc_sAborted
mariusz@mariusz-laptop:~$ 

```

---

### Post by blazemore on 2009-05-26
Try going into Sound preferences, and changing from Autodetect to ALSA (or Analogue if that's an option)
If that doesn't work you could use OSS.

---

### Post by xodeus on 2009-05-26
Okay. All I can say that it doesn't work with ALSA directly or OSS directly.

---

### Post by bujums on 2009-05-26
I am not sure about the scratchy sound... but you might try going to this site and follow the directions on it. 

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

 This usually enables my computer to to play WMA's and mp3 as well as what I need to play video and DVD.  Also, install VLC this is great player for video or music.

---

### Post by blazemore on 2009-05-27
I had this on an Aspire One. I took the opportunity to do a clean upgrade to Jaunty. However, I am interested in what the problem was.

---

### Post by xodeus on 2009-05-29
I've a clean install of Jaunty. Medibuntu is enabled and the system is up to date... But I still have this issue...

---

### Post by xodeus on 2009-06-02
Can anyone please help me out here?

---

### Post by xodeus on 2009-06-02
So far I only found 1 solution. But it's putting me back to the stoneage...
I hope that anyone can help me one day...
Pulseaudio is gone...

[http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html](http://www.ubuntugeek.com/fix-for-all-pulseaudio-related-issues.html)

---

