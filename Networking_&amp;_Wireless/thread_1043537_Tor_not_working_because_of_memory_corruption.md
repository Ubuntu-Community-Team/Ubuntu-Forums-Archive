---
title: "Tor not working because of memory corruption?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by winrowc on 2009-01-18
Hi I just reinstalled the tor and vidalia packages but am getting an error when I try to start tor or vidalia. Both installs seem to have been successful but when I run either tor or vidalia, I get 
```
*** glibc detected *** /usr/local/bin/tor: malloc(): memory corruption: 0x08333f98 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d6e116]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x95)[0xb7d6f865]
/usr/local/bin/tor[0x80e77c1]
/usr/local/bin/tor[0x80ef6cf]
/usr/local/bin/tor[0x8071ec9]
/usr/local/bin/tor[0x8072c3c]
/usr/local/bin/tor[0x806941c]
/usr/local/bin/tor[0x8069abf]
/usr/local/bin/tor[0x806b390]
/usr/local/bin/tor[0x80a778a]
/usr/local/bin/tor[0x80ab6a8]
/usr/local/bin/tor[0x80e3542]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d12685]
/usr/local/bin/tor[0x804d521]
======= Memory map: ========
08048000-0812f000 r-xp 00000000 08:01 2008216    /usr/local/bin/tor
0812f000-08130000 r--p 000e6000 08:01 2008216    /usr/local/bin/tor
08130000-08134000 rw-p 000e7000 08:01 2008216    /usr/local/bin/tor
08134000-08135000 rw-p 08134000 00:00 0 
08330000-08351000 rw-p 08330000 00:00 0          [heap]
b7b00000-b7b21000 rw-p b7b00000 00:00 0 
b7b21000-b7c00000 ---p b7b21000 00:00 0 
b7cc3000-b7cc5000 rw-p b7cc3000 00:00 0 
b7cc5000-b7cd5000 r-xp 00000000 08:01 1975857    /lib/tls/i686/cmov/libresolv-2.8.90.so
b7cd5000-b7cd6000 r--p 0000f000 08:01 1975857    /lib/tls/i686/cmov/libresolv-2.8.90.so
b7cd6000-b7cd7000 rw-p 00010000 08:01 1975857    /lib/tls/i686/cmov/libresolv-2.8.90.so
b7cd7000-b7cd9000 rw-p b7cd7000 00:00 0 
b7cd9000-b7ce0000 r-xp 00000000 08:01 1975858    /lib/tls/i686/cmov/librt-2.8.90.so
b7ce0000-b7ce1000 r--p 00007000 08:01 1975858    /lib/tls/i686/cmov/librt-2.8.90.so
b7ce1000-b7ce2000 rw-p 00008000 08:01 1975858    /lib/tls/i686/cmov/librt-2.8.90.so
b7ce2000-b7cf7000 r-xp 00000000 08:01 1975848    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7cf7000-b7cf8000 r--p 00014000 08:01 1975848    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7cf8000-b7cf9000 rw-p 00015000 08:01 1975848    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7cf9000-b7cfc000 rw-p b7cf9000 00:00 0 
b7cfc000-b7e54000 r-xp 00000000 08:01 1975842    /lib/tls/i686/cmov/libc-2.8.90.so
b7e54000-b7e56000 r--p 00158000 08:01 1975842    /lib/tls/i686/cmov/libc-2.8.90.so
b7e56000-b7e57000 rw-p 0015a000 08:01 1975842    /lib/tls/i686/cmov/libc-2.8.90.so
b7e57000-b7e5a000 rw-p b7e57000 00:00 0 
b7e5a000-b7e5c000 r-xp 00000000 08:01 1975845    /lib/tls/i686/cmov/libdl-2.8.90.so
b7e5c000-b7e5d000 r--p 00001000 08:01 1975845    /lib/tls/i686/cmov/libdl-2.8.90.so
b7e5d000-b7e5e000 rw-p 00002000 08:01 1975845    /lib/tls/i686/cmov/libdl-2.8.90.so
b7e5e000-b7e73000 r-xp 00000000 08:01 1975856    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e73000-b7e74000 r--p 00014000 08:01 1975856    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e74000-b7e75000 rw-p 00015000 08:01 1975856    /lib/tls/i686/cmov/libpthread-2.8.90.so
b7e75000-b7e77000 rw-p b7e75000 00:00 0 
b7e77000-b7fa9000 r-xp 00000000 08:01 205529     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7fa9000-b7faa000 ---p 00132000 08:01 205529     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7faa000-b7fb2000 r--p 00132000 08:01 205529     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7fb2000-b7fbf000 rw-p 0013a000 08:01 205529     /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7fbf000-b7fc3000 rw-p b7fbf000 00:00 0 
b7fc3000-b8005000 r-xp 00000000 08:01 205530     /usr/lib/i686/cmov/libssl.so.0.9.8
b8005000-b8006000 r--p 00041000 08:01 205530     /usr/lib/i686/cmov/libssl.so.0.9.8
b8006000-b8009000 rw-p 00042000 08:01 205530     /usr/lib/i686/cmov/libssl.so.0.9.8
b8009000-b800a000 rw-p b8009000 00:00 0 
b800a000-b801d000 r-xp 00000000 08:01 4014571    /usr/lib/libevent-1.3e.so.1.0.3
b801d000-b801f000 rw-p 00013000 08:01 4014571    /usr/lib/libevent-1.3e.so.1.0.3
b801f000-b8020000 rw-p b801f000 00:00 0 
b8020000-b8034000 r-xp 00000000 08:01 174579     /usr/lib/libz.so.1.2.3.3
b8034000-b8036000 rw-p 00013000 08:01 174579     /usr/lib/libz.so.1.2.3.3
b803a000-b8047000 r-xp 00000000 08:01 1957950    /lib/libgcc_s.so.1
b8047000-b8048000 r--p 0000c000 08:01 1957950    /lib/libgcc_s.so.1
b8048000-b8049000 rw-p 0000d000 08:01 1957950    /lib/libgcc_s.so.1
b8049000-b804c000 rw-p b8049000 00:00 0 
b804c000-b8066000 r-xp 00000000 08:01 1957991    /lib/ld-2.8.90.so
b8066000-b8067000 r-xp b8066000 00:00 0          [vdso]
b8067000-b8068000 r--p 0001a000 08:01 1957991    /lib/ld-2.8.90.so
b8068000-b8069000 rw-p 0001b000 08:01 1957991    /lib/ld-2.8.90.so
bff54000-bff69000 rw-p bffeb000 00:00 0          [stack]

```

Any help would be greatly appreciated. Thanks!

---

### Post by winrowc on 2009-01-19
Its the same error as 
[here]("http://forums.remote-exploit.org/showthread.php?t=11979") but the only suggestion they give is to redownload a newer package or get rid of a firewall which ubuntu doesnt have. I have compiled tor from source before and it still doesn't work...

---

### Post by winrowc on 2009-01-20
tor now works, I think.

When I do "sudo /etc/init.d/tor restart" it that restarting the tor process?

I get no errors doing that and tor seems to be successful, however when I just type "tor" in the terminal, I get the memory corruption error.

---

