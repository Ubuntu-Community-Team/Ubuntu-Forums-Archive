---
title: "[SOLVED] FATAL: Module ivtv not found"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by SPW06 on 2006-07-04
Hello,

I'm trying to install IvTV on Kubuntu Dapper.

I'm fallowing the how-to at:

[http://www.ubuntuforums.org/showthread.php?t=186747](http://www.ubuntuforums.org/showthread.php?t=186747)

Everything runs smoothly until I go to run

```
modprobe ivtv
FATAL: Module ivtv not found.
```

If this helps, herse my output from ls -ltra /lib/firmware/

```
total 1084
drwxr-xr-x  3 root root   4096 2006-05-30 21:19 2.6.15-23-386
drwxr-xr-x  3 root root   4096 2006-06-30 12:47 2.6.15-25-386
lrwxrwxrwx  1 root root     28 2006-07-01 21:13 v4l-cx2341x-dec.fw -> lib/firmwa
re/ivtv-fw-dec.bin
drwxr-xr-x  4 root root   4096 2006-07-01 21:22 .
drwxr-xr-x 19 root root   4096 2006-07-02 21:02 ..
-r--r--r--  1 root root  14264 2006-07-04 12:21 v4l-cx25840.fw
-rw-r--r--  1 root root 262144 2006-07-04 12:25 ivtv-fw-enc.bin
-rw-r--r--  1 root root 262144 2006-07-04 12:25 ivtv-fw-dec.bin
-r--r--r--  1 root root 376836 2006-07-04 12:27 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 155648 2006-07-04 12:30 v4l-cx2341x-init.mpg

```

And my output from lspci

```
0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridg
e
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
0000:00:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23                                             416) MPEG-2 Encoder (rev 01)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                             oller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                             oller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr                                             oller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82                                             3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8                                             237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev                                              74)
0000:01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

```

Thanks

---

### Post by gdselzer on 2006-07-04
I had this problem.  The fix is in the HOWTO.  Specifically:

> In some rare cases (I don't believe that this will happen to you, but I am leaving this bit here just in case) the drivers end up installed in the wrong place; they land in /lib/modules/<kver>/ivtv rather than /lib/modules/`uname -r`/ivtv. So, check on this. If they are installed incorrectly, you can fix this just by copying

    cp -r /lib/modules/<kver>/ivtv /lib/modules/`uname -r`/

To see if this is your problem, see if the modules are in /lib/modules/`uname -r`/ivtv.

---

### Post by SPW06 on 2006-07-04
```
utils# cp -r /lib/modules/2.6.15/ivtv /lib/modules/`uname -r`/
cp: cannot stat `/lib/modules/2.6.15/ivtv': No such file or directory

```

Nope, thanks anyway

EDIT: It's not even in there

/lib/modules/2.6.15-25-386$ ls
build    madwifi-ng      modules.ieee1394map  modules.pcimap    volatile
initrd   modules.alias   modules.inputmap     modules.seriomap
kernel   modules.ccwmap  modules.isapnpmap    modules.symbols
madwifi  modules.dep     modules.ofmap        modules.usbmap

---

### Post by fragos on 2006-07-04
Perhaps not your problem but after I installed ivtv I had a similar result.  The cause turned out to that only the source for the ivtv driver was installed with all the binaries of the other components.

---

### Post by Hokky on 2006-07-16
I had the same problem. Found out that I entered EXTRAVERSION = -27-k7 instead of EXTRAVERSION = -26-k7 in the /usr/src/linux/Makefile file.

Just in case anyone does the same mistake as me.

- Hokky

---

