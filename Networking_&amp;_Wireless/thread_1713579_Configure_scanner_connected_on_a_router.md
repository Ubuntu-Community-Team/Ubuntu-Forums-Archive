---
title: "Configure scanner connected on a router"
date: 2011-03-24
forum: Networking &amp; Wireless
---

### Post by Fenix-TX on 2011-03-24
Hello. I have a router Asus RT-n16 where i've connected my EPSON DX5000. I've configured the printer function, adding the printer as AppSocket, adding router IP and port 9100 (socket://Router_IP:9100), but now i can't get the scanner function. 

I've installed packages from here [http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL2.do) (iscan) and adding on /etc/sane.d/epkowa.conf the line
```

net 192.168.1.1 #my router ip

```

but it's not working. When i run scanimage -L i get this message:
```

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).

```

The scanner option worked fine when my printer is directly connected at my computer. Any suggestion? Thanks.

---

### Post by Fenix-TX on 2011-03-25
Up!

---

### Post by Fenix-TX on 2011-03-26
I've installed a win xp virtual machine, installed the asus driver to access to my allinone epson dx5000. Then, i've used wireshark to find the packets exchange when using the scanner, and i've finded source port 3394 from the router to do this connection, so i've added on epson2.conf the following:

```
net 192.168.1.1 3394
```

No, when i run scanimage -L i have this output:
```
*** buffer overflow detected ***: scanimage terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7ff3ad83f537]
/lib/libc.so.6(+0xfe3f0)[0x7ff3ad83e3f0]
/lib/libc.so.6(+0xfd2a7)[0x7ff3ad83d2a7]
/usr/lib/sane/libsane-epson2.so.1(+0x13010)[0x7ff3a59a6010]
/usr/lib/sane/libsane-epson2.so.1(+0x133e8)[0x7ff3a59a63e8]
/usr/lib/sane/libsane-epson2.so.1(sanei_configure_attach+0x37c)[0x7ff3a599a1fc]
/usr/lib/sane/libsane-epson2.so.1(sane_epson2_get_devices+0x2c)[0x7ff3a59a5e1c]
/usr/lib/libsane.so.1(sane_dll_get_devices+0xc6)[0x7ff3adccb0d6]
scanimage[0x403ce2]
/lib/libc.so.6(__libc_start_main+0xfe)[0x7ff3ad75ed8e]
scanimage[0x401ad9]
======= Memory map: ========
00400000-0040b000 r-xp 00000000 08:06 3309                               /usr/bin/scanimage
0060a000-0060b000 r--p 0000a000 08:06 3309                               /usr/bin/scanimage
0060b000-0060c000 rw-p 0000b000 08:06 3309                               /usr/bin/scanimage
019b9000-01a11000 rw-p 00000000 00:00 0                                  [heap]
7ff3a577d000-7ff3a5792000 r-xp 00000000 08:06 81                         /lib/libgcc_s.so.1
7ff3a5792000-7ff3a5991000 ---p 00015000 08:06 81                         /lib/libgcc_s.so.1
7ff3a5991000-7ff3a5992000 r--p 00014000 08:06 81                         /lib/libgcc_s.so.1
7ff3a5992000-7ff3a5993000 rw-p 00015000 08:06 81                         /lib/libgcc_s.so.1
7ff3a5993000-7ff3a59bd000 r-xp 00000000 08:06 272972                     /usr/lib/sane/libsane-epson2.so.1.0.21
7ff3a59bd000-7ff3a5bbd000 ---p 0002a000 08:06 272972                     /usr/lib/sane/libsane-epson2.so.1.0.21
7ff3a5bbd000-7ff3a5bbe000 r--p 0002a000 08:06 272972                     /usr/lib/sane/libsane-epson2.so.1.0.21
7ff3a5bbe000-7ff3a5bbf000 rw-p 0002b000 08:06 272972                     /usr/lib/sane/libsane-epson2.so.1.0.21
7ff3a5bbf000-7ff3a5bc1000 rw-p 00000000 00:00 0 
7ff3a5bc1000-7ff3a5bc9000 r-xp 00000000 08:06 3431                       /usr/lib/libltdl.so.7.2.1
7ff3a5bc9000-7ff3a5dc9000 ---p 00008000 08:06 3431                       /usr/lib/libltdl.so.7.2.1
7ff3a5dc9000-7ff3a5dca000 r--p 00008000 08:06 3431                       /usr/lib/libltdl.so.7.2.1
7ff3a5dca000-7ff3a5dcb000 rw-p 00009000 08:06 3431                       /usr/lib/libltdl.so.7.2.1
7ff3a5dcb000-7ff3a5f0f000 r-xp 00000000 08:06 396                        /usr/lib/libxml2.so.2.7.7
7ff3a5f0f000-7ff3a610e000 ---p 00144000 08:06 396                        /usr/lib/libxml2.so.2.7.7
7ff3a610e000-7ff3a6116000 r--p 00143000 08:06 396                        /usr/lib/libxml2.so.2.7.7
7ff3a6116000-7ff3a6118000 rw-p 0014b000 08:06 396                        /usr/lib/libxml2.so.2.7.7
7ff3a6118000-7ff3a6119000 rw-p 00000000 00:00 0 
7ff3a6119000-7ff3a614e000 r-xp 00000000 08:06 264133                     /usr/lib/sane/libsane-epkowa.so.1.0.15
7ff3a614e000-7ff3a634d000 ---p 00035000 08:06 264133                     /usr/lib/sane/libsane-epkowa.so.1.0.15
7ff3a634d000-7ff3a634f000 r--p 00034000 08:06 264133                     /usr/lib/sane/libsane-epkowa.so.1.0.15
7ff3a634f000-7ff3a6350000 rw-p 00036000 08:06 264133                     /usr/lib/sane/libsane-epkowa.so.1.0.15
7ff3a6350000-7ff3a6352000 rw-p 00000000 00:00 0 
7ff3a6352000-7ff3a637b000 r-xp 00000000 08:06 273012                     /usr/lib/sane/libsane-fujitsu.so.1.0.21
7ff3a637b000-7ff3a657b000 ---p 00029000 08:06 273012                     /usr/lib/sane/libsane-fujitsu.so.1.0.21
7ff3a657b000-7ff3a657c000 r--p 00029000 08:06 273012                     /usr/lib/sane/libsane-fujitsu.so.1.0.21
7ff3a657c000-7ff3a657d000 rw-p 0002a000 08:06 273012                     /usr/lib/sane/libsane-fujitsu.so.1.0.21
7ff3a657d000-7ff3a657f000 rw-p 00000000 00:00 0 
7ff3a657f000-7ff3a65b6000 r-xp 00000000 08:06 273403                     /usr/lib/sane/libsane-genesys.so.1.0.21
7ff3a65b6000-7ff3a67b5000 ---p 00037000 08:06 273403                     /usr/lib/sane/libsane-genesys.so.1.0.21
7ff3a67b5000-7ff3a67b6000 r--p 00036000 08:06 273403                     /usr/lib/sane/libsane-genesys.so.1.0.21
7ff3a67b6000-7ff3a67bb000 rw-p 00037000 08:06 273403                     /usr/lib/sane/libsane-genesys.so.1.0.21
7ff3a67bb000-7ff3a67bd000 rw-p 00000000 00:00 0 
7ff3a67bd000-7ff3a67e0000 r-xp 00000000 08:06 273408                     /usr/lib/sane/libsane-gt68xx.so.1.0.21
7ff3a67e0000-7ff3a69df000 ---p 00023000 08:06 273408                     /usr/lib/sane/libsane-gt68xx.so.1.0.21
7ff3a69df000-7ff3a69e0000 r--p 00022000 08:06 273408                     /usr/lib/sane/libsane-gt68xx.so.1.0.21
7ff3a69e0000-7ff3a69e4000 rw-p 00023000 08:06 273408                     /usr/lib/sane/libsane-gt68xx.so.1.0.21
7ff3a69e4000-7ff3a69e6000 rw-p 00000000 00:00 0 
7ff3a69e6000-7ff3a6a10000 r-xp 00000000 08:06 273791                     /usr/lib/sane/libsane-hp.so.1.0.21
7ff3a6a10000-7ff3a6c0f000 ---p 0002a000 08:06 273791                     /usr/lib/sane/libsane-hp.so.1.0.21
7ff3a6c0f000-7ff3a6c12000 r--p 00029000 08:06 273791                     /usr/lib/sane/libsane-hp.so.1.0.21
7ff3a6c12000-7ff3a6c13000 rw-p 0002c000 08:06 273791                     /usr/lib/sane/libsane-hp.so.1.0.21
7ff3a6c13000-7ff3a6c16000 rw-p 00000000 00:00 0 
7ff3a6c16000-7ff3a6c2c000 r-xp 00000000 08:06 1420                       /lib/libz.so.1.2.3.4
7ff3a6c2c000-7ff3a6e2c000 ---p 00016000 08:06 1420                       /lib/libz.so.1.2.3.4
7ff3a6e2c000-7ff3a6e2d000 r--p 00016000 08:06 1420                       /lib/libz.so.1.2.3.4
7ff3a6e2d000-7ff3a6e2e000 rw-p 00017000 08:06 1420                       /lib/libz.so.1.2.3.4
7ff3a6e2e000-7ff3a6e51000 r-xp 00000000 08:06 3804                       /usr/lib/libjpeg.so.62.0.0
7ff3a6e51000-7ff3a7050000 ---p 00023000 08:06 3804                       /usr/lib/libjpeg.so.62.0.0
7ff3a7050000-7ff3a7051000 r--p 00022000 08:06 3804                       /usr/lib/libjpeg.so.62.0.0
7ff3a7051000-7ff3a7052000 rw-p 00023000 08:06 3804                       /usr/lib/libjpeg.so.62.0.0
7ff3a7052000-7ff3a70b1000 r-xp 00000000 08:06 1162                       /usr/lib/libtiff.so.4.3.3
7ff3a70b1000-7ff3a72b1000 ---p 0005f000 08:06 1162                       /usr/lib/libtiff.so.4.3.3
7ff3a72b1000-7ff3a72b3000 r--p 0005f000 08:06 1162                       /usr/lib/libtiff.so.4.3.3Abortado

```

---

