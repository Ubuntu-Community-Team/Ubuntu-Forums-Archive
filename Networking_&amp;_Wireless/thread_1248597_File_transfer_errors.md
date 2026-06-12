---
title: "File transfer errors"
date: 2009-08-24
forum: Networking &amp; Wireless
---

### Post by avhohlov on 2009-08-24
ubuntu-9.04-desktop-i386
SAMBA 2:3.3.2-1ubuntu 3.1
LAN RTL8111C (integrated)
or D-Link DFE-520TX PCI (other PC)

second PC Windows NT 4.0
PII/350
LAN D-Link DFE-520TX PCI

Switch 3COM 3C16791B

If Ubuntu is a client and WinNT is a file server, files are copied from server to client with STABLE errors (duplicate copy has same errors as first copy). Offsets between errors seems equals (except first):

```

Comparing files oracle-xe_10.2.0.1-1.0_i386.deb and oracle-xe_10.2.0.1-1.0_i386.err
0000F000: D3 83
00026001: 07 78
00035002: 04 74
00044003: 3A 75
00053004: 01 C8
00062005: 68 9B
00071006: 27 7D
00080007: 26 2F
0008F008: B1 E6
...

```No errors in all oter cases (Ubuntu - server or second machine are new/WindowsXP/server or client).

I also try Mandiva Spring 2007 and seen NO ERRORS, but its file transfer speed 1.5Mb/sec vs 2.2Mb/sec.

What can I do to solve this?
Thanks

---

### Post by avhohlov on 2009-09-04
I test following:

1.Adapter replacement
2.Cable replacement
3.Direct connection (without hub)

Same errors.

There are no errors if I download file via http (Apache on Windows NT).

 							[IMG]http://forum.ubuntu.ru/Themes/firefox_ro/images/icons/modify_inline.gif[/IMG]

---

### Post by avhohlov on 2009-11-30
I remove NT4 and install same Ubuntu 9.04 on PII/350. No errors. Program incompatibility with old versions on WinNT?

---

