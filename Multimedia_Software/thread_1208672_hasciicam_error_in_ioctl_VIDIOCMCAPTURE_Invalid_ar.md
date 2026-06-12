---
title: "hasciicam: error in ioctl VIDIOCMCAPTURE: Invalid argument"
date: 2009-07-09
forum: Multimedia Software
---

### Post by creepandpeep on 2009-07-09
Hello all,

I'm trying to get hasciicam running on jaunty and it is giving me this error:

```
userx@server:~$ hasciicam
HasciiCam 0.9.1 - (h)ascii 4 the masses! - http://ascii.dyne.org
(c)2000-2003 Denis Rojo < jaromil @ dyne.org >
watch out for the (h)ASCII ROOTS http://hascii.org

Device detected is /dev/video0
Logitech QuickCam Zoom
1 channels detected
max size w[640] h[480] - min size w[160] h[120]
Video capabilities:
VID_TYPE_CAPTURE          can capture to memory
VIDEO_PALETTE_GREY        device is able to grab greyscale frames
memory map of 2 frames: 925696 bytes
Offset of frame 0: 0
Offset of frame 1: 462848
error in ioctl VIDIOCMCAPTURE: Invalid argument*** buffer overflow detected ***: hasciicam terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7ef2da8]
/lib/tls/i686/cmov/libc.so.6[0xb7ef0eb0]
/lib/tls/i686/cmov/libc.so.6[0xb7ef07b7]
/lib/tls/i686/cmov/libc.so.6(__snprintf_chk+0x34)[0xb7ef06a4]
hasciicam[0x8049979]
hasciicam[0x804abcf]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7e0b775]
hasciicam[0x8049591]
======= Memory map: ========
08048000-0804f000 r-xp 00000000 08:05 831799     /usr/bin/hasciicam
0804f000-08050000 r--p 00006000 08:05 831799     /usr/bin/hasciicam
08050000-08051000 rw-p 00007000 08:05 831799     /usr/bin/hasciicam
08051000-08052000 rw-p 08051000 00:00 0 
08186000-081a7000 rw-p 08186000 00:00 0          [heap]
b7aaa000-b7ab7000 r-xp 00000000 08:05 49216      /lib/libgcc_s.so.1
b7ab7000-b7ab8000 r--p 0000c000 08:05 49216      /lib/libgcc_s.so.1
b7ab8000-b7ab9000 rw-p 0000d000 08:05 49216      /lib/libgcc_s.so.1
b7ab9000-b7b9b000 rw-s 00000000 00:0f 5509       /dev/video0
b7b9b000-b7b9d000 rw-p b7b9b000 00:00 0 
b7b9d000-b7ba1000 r-xp 00000000 08:05 828876     /usr/lib/libXdmcp.so.6.0.0
b7ba1000-b7ba2000 rw-p 00003000 08:05 828876     /usr/lib/libXdmcp.so.6.0.0
b7ba2000-b7ba4000 r-xp 00000000 08:05 828865     /usr/lib/libXau.so.6.0.0
b7ba4000-b7ba5000 r--p 00001000 08:05 828865     /usr/lib/libXau.so.6.0.0
b7ba5000-b7ba6000 rw-p 00002000 08:05 828865     /usr/lib/libXau.so.6.0.0
b7ba6000-b7bbe000 r-xp 00000000 08:05 831804     /usr/lib/libxcb.so.1.1.0
b7bbe000-b7bbf000 r--p 00017000 08:05 831804     /usr/lib/libxcb.so.1.1.0
b7bbf000-b7bc0000 rw-p 00018000 08:05 831804     /usr/lib/libxcb.so.1.1.0
b7bc0000-b7bc2000 r-xp 00000000 08:05 66887      /lib/tls/i686/cmov/libdl-2.9.so
b7bc2000-b7bc3000 r--p 00001000 08:05 66887      /lib/tls/i686/cmov/libdl-2.9.so
b7bc3000-b7bc4000 rw-p 00002000 08:05 66887      /lib/tls/i686/cmov/libdl-2.9.so
b7bc4000-b7bc5000 rw-p b7bc4000 00:00 0 
b7bc5000-b7bca000 r-xp 00000000 08:05 829280     /usr/lib/libgpm.so.2.0.0
b7bca000-b7bcb000 r--p 00004000 08:05 829280     /usr/lib/libgpm.so.2.0.0
b7bcb000-b7bcc000 rw-p 00005000 08:05 829280     /usr/lib/libgpm.so.2.0.0
b7bcc000-b7cb6000 r-xp 00000000 08:05 828859     /usr/lib/libX11.so.6.2.0
b7cb6000-b7cb7000 ---p 000ea000 08:05 828859     /usr/lib/libX11.so.6.2.0
b7cb7000-b7cb8000 r--p 000ea000 08:05 828859     /usr/lib/libX11.so.6.2.0
b7cb8000-b7cba000 rw-p 000eb000 08:05 828859     /usr/lib/libX11.so.6.2.0
b7cba000-b7cbb000 rw-p b7cba000 00:00 0 
b7cbb000-b7cdf000 r-xp 00000000 08:05 66889      /lib/tls/i686/cmov/libm-2.9.so
b7cdf000-b7ce0000 r--p 00023000 08:05 66889      /lib/tls/i686/cmov/libm-2.9.so
b7ce0000-b7ce1000 rw-p 00024000 08:05 66889      /lib/tls/i686/cmov/libm-2.9.so
b7ce1000-b7d7c000 r-xp 00000000 08:05 49283      /lib/libslang.so.2.1.3
b7d7c000-b7d7f000 r--p 0009a000 08:05 49283      /lib/libslang.so.2.1.3
b7d7f000-b7d8c000 rw-p 0009d000 08:05 49283      /lib/libslang.so.2.1.3
b7d8c000-b7dc2000 rw-p b7d8c000 00:00 0 
b7dc2000-b7df1000 r-xp 00000000 08:05 49231      /lib/libncurses.so.5.7
b7df1000-b7df3000 r--p 0002e000 08:05 49231      /lib/libncurses.so.5.7
b7df3000-b7df4000 rw-p 00030000 08:05 49231      /lib/libncurses.so.5.7
b7df4000-b7df5000 rw-p b7df4000 00:00 0 
b7df5000-b7f51000 r-xp 00000000 08:05 66881      /lib/tls/i686/cmov/libc-2.9.so
b7f51000-b7f52000 ---p 0015c000 08:05 66881      /lib/tls/i686/cmov/libc-2.9.so
b7f52000-b7f54000 r--p 0015c000 08:05 66881      /lib/tls/i686/cmov/libc-2.9.so
b7f54000-b7f55000 rw-p 0015e000 08:05 66881      /lib/tls/i686/cmov/libc-2.9.so
b7f55000-b7f58000 rw-p b7f55000 00:00 0 
b7f58000-b7f70000 r-xp 00000000 08:05 828920     /usr/lib/libaa.so.1.0.4
b7f70000-b7f71000 r--p 00018000 08:05 828920     /usr/lib/libaa.so.1.0.4
b7f71000-b7f72000 rw-p 00019000 08:05 828920     /usr/lib/libaa.so.1.0.4
b7f7200Aborted

```

I think the important bit of that is: ```
error in ioctl VIDIOCMCAPTURE: Invalid argument*** buffer overflow detected ***: hasciicam terminated
```

Now, I would assume that it is a problem with my camera, or my distro setup. . .however, I have had this problem on three different machines with three different cameras now, spread across about 2 years! each time I put ubuntu on a new comp, I always give it a shot, jsut incase :p but still no luck. . .I have searched high and low, long and hard, but still no resolution. . .

Can anyone help with this :D ?

Thanks

Tom

---

