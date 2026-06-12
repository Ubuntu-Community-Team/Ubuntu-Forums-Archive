---
title: "sshd fails - glibc problem"
date: 2012-06-30
forum: Networking &amp; Wireless
---

### Post by Conzar on 2012-06-30
I recently installed Ubuntu 11.10 (fresh).  I had 11.04 on my system and everything worked correctly!  

After the 11.10 install, sshd and samba did not work.  So I updated to 12.04.  Both sshd and samba still didn't work.  The clue is that glibc is segfaulting I think.

Output from /etc/init.d/sshd -d -D
```
sudo /usr/sbin/sshd -D -d
debug1: sshd version OpenSSH_5.9p1 Debian-5ubuntu1
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: read PEM private key done: type ECDSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.ECDSA-256
debug1: Checking blacklist file /etc/ssh/blacklist.ECDSA-256
debug1: private host key: #2 type 3 ECDSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-D'
debug1: rexec_argv[2]='-d'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Server listening on 0.0.0.0 port 22.
debug1: Bind to port 22 on ::.
Server listening on :: port 22.
*** glibc detected *** /usr/sbin/sshd: double free or corruption (out): 0x00007f7544592940 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7e626)[0x7f7541068626]
/lib/x86_64-linux-gnu/liblsp.so(freeaddrinfo+0x13a)[0x7f7542d27da2]
/usr/sbin/sshd(main+0x1777)[0x7f754315d967]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f754100b76d]
/usr/sbin/sshd(+0xfe89)[0x7f754315ee89]
======= Memory map: ========
7f753fb44000-7f753fb59000 r-xp 00000000 08:21 2359848                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f753fb59000-7f753fd58000 ---p 00015000 08:21 2359848                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f753fd58000-7f753fd59000 r--p 00014000 08:21 2359848                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f753fd59000-7f753fd5a000 rw-p 00015000 08:21 2359848                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f753fd5a000-7f753fd66000 r-xp 00000000 08:21 2359568                    /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f753fd66000-7f753ff65000 ---p 0000c000 08:21 2359568                    /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f753ff65000-7f753ff66000 r--p 0000b000 08:21 2359568                    /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f753ff66000-7f753ff67000 rw-p 0000c000 08:21 2359568                    /lib/x86_64-linux-gnu/libnss_files-2.15.so
7f753ff67000-7f753ff71000 r-xp 00000000 08:21 2359569                    /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f753ff71000-7f7540171000 ---p 0000a000 08:21 2359569                    /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f7540171000-7f7540172000 r--p 0000a000 08:21 2359569                    /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f7540172000-7f7540173000 rw-p 0000b000 08:21 2359569                    /lib/x86_64-linux-gnu/libnss_nis-2.15.so
7f7540173000-7f754017b000 r-xp 00000000 08:21 2359571                    /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f754017b000-7f754037a000 ---p 00008000 08:21 2359571                    /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f754037a000-7f754037b000 r--p 00007000 08:21 2359571                    /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f754037b000-7f754037c000 rw-p 00008000 08:21 2359571                    /lib/x86_64-linux-gnu/libnss_compat-2.15.so
7f754037c000-7f7540394000 r-xp 00000000 08:21 2359562                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f7540394000-7f7540594000 ---p 00018000 08:21 2359562                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f7540594000-7f7540595000 r--p 00018000 08:21 2359562                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f7540595000-7f7540596000 rw-p 00019000 08:21 2359562                    /lib/x86_64-linux-gnu/libresolv-2.15.so
7f7540596000-7f7540598000 rw-p 00000000 00:00 0 
7f7540598000-7f754059b000 r-xp 00000000 08:21 2359337                    /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f754059b000-7f754079a000 ---p 00003000 08:21 2359337                    /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f754079a000-7f754079b000 r--p 00002000 08:21 2359337                    /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f754079b000-7f754079c000 rw-p 00003000 08:21 2359337                    /lib/x86_64-linux-gnu/libkeyutils.so.1.4
7f754079c000-7f75407a3000 r-xp 00000000 08:21 2754749                    /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7f75407a3000-7f75409a2000 ---p 00007000 08:21 2754749                    /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7f75409a2000-7f75409a3000 r--p 00006000 08:21 2754749                    /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7f75409a3000-7f75409a4000 rw-p 00007000 08:21 2754749                    /usr/lib/x86_64-linux-gnu/libkrb5support.so.0.1
7f75409a4000-7f75409c9000 r-xp 00000000 08:21 2754735                    /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7f75409c9000-7f7540bc9000 ---p 00025000 08:21 2754735                    /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7f7540bc9000-7f7540bca000 r--p 00025000 08:21 2754735                    /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7f7540bca000-7f7540bcb000 rw-p 00026000 08:21 2754735                    /usr/lib/x86_64-linux-gnu/libk5crypto.so.3.1
7f7540bcb000-7f7540bcc000 rw-p 00000000 00:00 0 
7f7540bcc000-7f7540be3000 r-xp 00000000 08:21 2359563                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f7540be3000-7f7540de2000 ---p 00017000 08:21 2359563                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f7540de2000-7f7540de3000 r--p 00016000 08:21 2359563                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f7540de3000-7f7540de4000 rw-p 00017000 08:21 2359563                    /lib/x86_64-linux-gnu/libnsl-2.15.so
7f7540de4000-7f7540de6000 rw-p 00000000 00:00 0 
7f7540de6000-7f7540de8000 r-xp 00000000 08:21 2359575                    /lib/x86_64-linux-gnu/libdl-2.15.so
7f7540de8000-7f7540fe8000 ---p 00002000 08:21 2359575                    /lib/x86_64-linux-gnu/libdl-2.15.so
7f7540fe8000-7f7540fe9000 r--p 00002000 08:21 2359575                    /lib/x86_64-linux-gnu/libdl-2.15.so
7f7540fe9000-7f7540fea000 rw-p 00003000 08:21 2359575                    /lib/x86_64-linux-gnu/libdl-2.15.so
7f7540fea000-7f754119d000 r-xp 00000000 08:21 2359557                    /lib/x86_64-linux-gnu/libc-2.15.so
7f754119d000-7f754139c000 ---p 001b3000 08:21 2359557                    /lib/x86_64-linux-gnu/libc-2.15.so
7f754139c000-7f75413a0000 r--p 001b2000 08:21 2359557                    /lib/x86_64-linux-gnu/libc-2.15.so
7f75413a0000-7f75413a2000 rw-p 001b6000 08:21 2359557                    /lib/x86_64-linux-gnu/libc-2.15.so
7f75413a2000-7f75413a7000 rw-p 00000000 00:00 0 
7f75413a7000-7f75413aa000 r-xp 00000000 08:21 2359925                    /lib/x86_64-linux-gnu/libcom_err.so.2.1
7f75413aa000-7f75415a9000 ---p 00003000 08:21 2359925                    /lib/x86_64-linux-gnu/libcom_err.so.2.1
7f75415a9000-7f75415aa000 r--p 00002000 08:21 2359925                    /lib/x86_64-linux-gnu/libcom_err.so.2.1
7f75415aa000-7f75415ab000 rw-p 00003000 08:21 2359925                    /lib/x86_64-linux-gnu/libcom_err.so.2.1
7f75415ab000-7f754166f000 r-xp 00000000 08:21 2754091                    /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7f754166f000-7f754186e000 ---p 000c4000 08:21 2754091                    /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7f754186e000-7f7541878000 r--p 000c3000 08:21 2754091                    /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7f7541878000-7f7541879000 rw-p 000cd000 08:21 2754091                    /usr/lib/x86_64-linux-gnu/libkrb5.so.3.3
7f7541879000-7f75418b4000 r-xp 00000000 08:21 2754377                    /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7f75418b4000-7f7541ab4000 ---p 0003b000 08:21 2754377                    /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7f7541ab4000-7f7541ab5000 r--p 0003b000 08:21 2754377                    /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7f7541ab5000-7f7541ab7000 rw-p 0003c000 08:21 2754377                    /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2.2
7f7541ab7000-7f7541ac0000 r-xp 00000000 08:21 2359570                    /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f7541ac0000-7f7541cc0000 ---p 00009000 08:21 2359570                    /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f7541cc0000-7f7541cc1000 r--p 00009000 08:21 2359570                    /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f7541cc1000-7f7541cc2000 rw-p 0000a000 08:21 2359570                    /lib/x86_64-linux-gnu/libcrypt-2.15.so
7f7541cc2000-7f7541cf0000 rw-p 00000000 00:00 0 
7f7541cf0000-7f7541d06000 r-xp 00000000 08:21 2359831                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7541d06000-7f7541f05000 ---p 00016000 08:21 2359831                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7541f05000-7f7541f06000 r--p 00015000 08:21 2359831                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7541f06000-7f7541f07000 rw-p 00016000 08:21 2359831                    /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f7541f07000-7f7541f09000 r-xp 00000000 08:21 2359572                    /lib/x86_64-linux-gnu/libutil-2.15.so
7f7541f09000-7f7542108000 ---p 00002000 08:21 2359572                    /lib/x86_64-linux-gnu/libutil-2.15.so
7f7542108000-7f7542109000 r--p 00001000 08:21 2359572                    /lib/x86_64-linux-gnu/libutil-2.15.so
7f7542109000-7f754210a000 rw-p 00002000 08:21 2359572                    /lib/x86_64-linux-gnu/libutil-2.15.so
7f754210a000-7f75422a9000 r-xp 00000000 08:21 2359929                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f75422a9000-7f75424a8000 ---p 0019f000 08:21 2359929                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f75424a8000-7f75424c3000 r--p 0019e000 08:21 2359929                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f75424c3000-7f75424ce000 rw-p 001b9000 08:21 2359929                    /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
7f75424ce000-7f75424d2000 rw-p 00000000 00:00 0 
7f75424d2000-7f75424ea000 r-xp 00000000 08:21 2359579                    /lib/x86_64-linux-gnu/libpthread-2.15.so
7f75424ea000-7f75426e9000 ---p 00018000 08:21 2359579                    /lib/x86_64-linux-gnu/libpthread-2.15.so
7f75426e9000-7f75426ea000 r--p 00017000 08:21 2359579                    /lib/x86_64-linux-gnu/libpthread-2.15.so
7f75426ea000-7f75426eb000 rw-p 00018000 08:21 2359579                    /lib/x86_64-linux-gnu/libpthread-2.15.so
7f75426eb000-7f75426ef000 rw-p 00000000 00:00 0 
7f75426ef000-7f754270c000 r-xp 00000000 08:21 2359792                    /lib/x86_64-linux-gnu/libselinux.so.1
7f754270c000-7f754290b000 ---p 0001d000 08:21 2359792                    /lib/x86_64-linux-gnu/libselinux.so.1
7f754290b000-7f754290c000 r--p 0001c000 08:21 2359792                    /lib/x86_64-linux-gnu/libselinux.so.1
7f754290c000-7f754290d000 rw-p 0001d000 08:21 2359792                    /lib/x86_64-linux-gnu/libselinux.so.1
7f754290d000-7f754290e000 rw-p 00000000 00:00 0 
7f754290e000-7f754291a000 r-xp 00000000 08:21 2359357                    /lib/x86_64-linux-gnu/libpam.so.0.83.0
7f754291a000-7f7542b1a000 ---p 0000c000 08:21 2359357                    /lib/x86_64-linux-gnu/libpam.so.0.83.0
7f7542b1a000-7f7542b1b000 r--p 0000c000 08:21 2359357                    /lib/x86_64-linux-gnu/libpam.so.0.83.0
7f7542b1b000-7f7542b1c000 rw-p 0000d000 08:21 2359357                    /lib/x86_64-linux-gnu/libpam.so.0.83.0
7f7542b1c000-7f7542b24000 r-xp 00000000 08:21 2363327                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f7542b24000-7f7542d23000 ---p 00008000 08:21 2363327                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f7542d23000-7f7542d24000 r--p 00007000 08:21 2363327                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f7542d24000-7f7542d25000 rw-p 00008000 08:21 2363327                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f7542d25000-7f7542d29000 r-xp 00000000 08:21 2366798                    /lib/x86_64-linux-gnu/liblsp.so
7f7542d29000-7f7542f28000 ---p 00004000 08:21 2366798                    /lib/x86_64-linux-gnu/liblsp.so
7f7542f28000-7f7542f29000 r--p 00003000 08:21 2366798                    /lib/x86_64-linux-gnu/liblsp.so
7f7542f29000-7f7542f2a000 rw-p 00004000 08:21 2366798                    /lib/x86_64-linux-gnu/liblsp.so
7f7542f2a000-7f7542f4c000 r-xp 00000000 08:21 2359561                    /lib/x86_64-linux-gnu/ld-2.15.so
7f7543128000-7f7543132000 rw-p 00000000 00:00 0 
7f7543145000-7f7543146000 rw-p 00000000 00:00 0 
7f7543146000-7f754314a000 rw-s 00000000 00:04 0                          /SYSVa5723213 (deleted)
7f754314a000-7f754314c000 rw-p 00000000 00:00 0 
7f754314c000-7f754314d000 r--p 00022000 08:21 2359561                    /lib/x86_64-linux-gnu/ld-2.15.so
7f754314d000-7f754314f000 rw-p 00023000 08:21 2359561                    /lib/x86_64-linux-gnu/ld-2.15.so
7f754314f000-7f75431c9000 r-xp 00000000 08:21 2753556                    /usr/sbin/sshd
7f75433c9000-7f75433cc000 r--p 0007a000 08:21 2753556                    /usr/sbin/sshd
7f75433cc000-7f75433cd000 rw-p 0007d000 08:21 2753556                    /usr/sbin/sshd
7f75433cd000-7f75433d6000 rw-p 00000000 00:00 0 
7f754458d000-7f75445ae000 rw-p 00000000 00:00 0                          [heap]
7fff4c4dc000-7fff4c4fd000 rw-p 00000000 00:00 0                          [stack]
7fff4c53c000-7fff4c53d000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

```

Any ideas of what might be going wrong?

Ubuntu 12.04 3.2.0-26-generic
openssh-server 1:5.9p1-5ubuntu1
glibc 2.15

---

### Post by Conzar on 2012-07-01
I re-installed 11.04 and this resolved my problem.

---

