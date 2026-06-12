---
title: "x11vnc hangs"
date: 2010-01-30
forum: Networking &amp; Wireless
---

### Post by jnbptst on 2010-01-30
Hi,

I have been using ssh to connect over to my home computer from a laptop. Recently, I started using x11vnc tunelled through my ssh connection in order to have a graphic display.

Everything was working great, but yesterday x11vnc started hanging and refuses to start properly. Here is the output:

```
x11vnc -once -usepw
30/01/2010 12:59:51 -usepw: found /home/user/.vnc/passwd
30/01/2010 12:59:51 x11vnc version: 0.9.3 lastmod: 2007-09-30
30/01/2010 12:59:51 
30/01/2010 12:59:51 *** XOpenDisplay failed. No -display or DISPLAY.
30/01/2010 12:59:51 *** Trying ":0" in 4 seconds.  Press Ctrl-C to abort.
30/01/2010 12:59:51 *** 1 2 3 4 

```

After the line "30/01/2010 12:59:51 *** 1 2 3 4 " displays, the process stays like that with no further update. i have to exit it with CTRL + C.

Whenever I add the -display :0 to the command, here is what I get:

```
$ sudo x11vnc -once -usepw -display :0 
30/01/2010 13:01:24 -usepw: found /home/user/.vnc/passwd
30/01/2010 13:01:24 x11vnc version: 0.9.3 lastmod: 2007-09-30


```

Again, it just hangs there until I exit it with CTRL+C.

Any hint about what might solve that?

thanks a lot!

---

### Post by krunge on 2010-01-30
When you run these commands is your userid already logged into an X session? Or is no one logged in yet and only a 'login greeter' showing on the display? x11vnc needs to connect to an existing X server.

Does it hang indefinitely?  When I point x11vnc to a non-existent X server it times out after about 20 seconds.

---

### Post by jnbptst on 2010-01-30
Thanks for the quick response

The computer that I use as server has an open X server, and I login with SSH using the same userid that is running X.

It hangs undefinitely, I don't get a timeout message...

Any idea?

---

### Post by krunge on 2010-01-30
Ah, ok.  For simplicity I will refer to your username on the machine as 'jnb'.  So jnb is logged into an X session (e.g. gnome, kde, or xfce...) You ssh in as jnb and run 'x11vnc -display :0' and it hangs forever. Correct?

BTW, in one of your examples you mentioned you used 'sudo x11vnc ...' I recommend **not** using sudo, it will usually only add to the confusion. sudo occasionally makes things work but only fortuitously.  You see, just because x11vnc is running as root doesn't mean it will access the correct X authority (secret keys) file; in this case it might be /home/jnb/.Xauthority (i.e. not /root/.Xauthority.)  Since you say jnb is logged into the X session, don't use sudo in this troubleshooting, run everything as user jnb.

Anyway, I am not sure what is causing this hanging.  What is your distro version?  I know of some changes in ubuntu 9.10 that affect x11vnc, but I don't see how they would cause what you are seeing.

If this were my machine, I would troubleshoot as follows.  Install the strace package if it is not already installed.  Then run these commands:
```

strace -t -o /tmp/trace1.out x11vnc -nopw -display :0
strace -t -o /tmp/trace2.out xdpyinfo -display :0

```
(the -nopw just prevents x11vnc from printing out a warning message.)

One or both of those commands should hang (i.e. the problem you are seeing) and so after 20 secs or so one will need to Ctrl-C them. The log files contain all of the system calls the programs were making and so aid in troubleshooting problems.

If you want to run those commands and attach the two output files to this thread or send them to me as a PM, go ahead and I will have a look at them.

---

### Post by jnbptst on 2010-01-30
My bad, I had only used the sudo to debug, I don't usually use it to launch x11vnc.

Anyway, I followed you advice, and here are the outputs of the commands:


trace1.out:
```
23:21:17 execve("/usr/bin/x11vnc", ["x11vnc", "-nopw", "-display", ":0"], [/* 20 vars */]) = 0
23:21:17 brk(0)                         = 0x9705000
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78b8000
23:21:17 access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/etc/ld.so.cache", O_RDONLY) = 3
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=72901, ...}) = 0
23:21:17 mmap2(NULL, 72901, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb78a6000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libvncserver.so.0", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 a\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=219336, ...}) = 0
23:21:17 mmap2(NULL, 332480, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xc71000
23:21:17 mmap2(0xca5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x34) = 0xca5000
23:21:17 mmap2(0xca7000, 111296, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xca7000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libvncclient.so.0", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260!\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=95692, ...}) = 0
23:21:17 mmap2(NULL, 98800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x190000
23:21:17 mmap2(0x1a7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0x1a7000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/i686/cmov/libssl.so.0.9.8", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\305\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=298548, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a5000
23:21:17 mmap2(NULL, 301336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x72e000
23:21:17 mmap2(0x774000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x45) = 0x774000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/i686/cmov/libcrypto.so.0.9.8", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\303\3\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=1454876, ...}) = 0
23:21:17 mmap2(NULL, 1471224, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x804000
23:21:17 mmap2(0x953000, 86016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14e) = 0x953000
23:21:17 mmap2(0x968000, 13048, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x968000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/libcrypt.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\7\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=38360, ...}) = 0
23:21:17 mmap2(NULL, 201052, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x157000
23:21:17 mmap2(0x160000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0x160000
23:21:17 mmap2(0x162000, 155996, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x162000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXtst.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\17\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=22076, ...}) = 0
23:21:17 mmap2(NULL, 20848, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xaaf000
23:21:17 mmap2(0xab3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4) = 0xab3000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXext.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200+\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=60024, ...}) = 0
23:21:17 mmap2(NULL, 63136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xf86000
23:21:17 mmap2(0xf94000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xf94000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXinerama.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\7\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=6528, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a4000
23:21:17 mmap2(NULL, 9376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xd90000
23:21:17 mmap2(0xd92000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xd92000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXrandr.so.2", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\23\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=30064, ...}) = 0
23:21:17 mmap2(NULL, 32960, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x4bb000
23:21:17 mmap2(0x4c2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0x4c2000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXfixes.so.3", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\17\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=17696, ...}) = 0
23:21:17 mmap2(NULL, 20592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xfc7000
23:21:17 mmap2(0xfcb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xfcb000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXdamage.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\10\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=6260, ...}) = 0
23:21:17 mmap2(NULL, 9164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x5a1000
23:21:17 mmap2(0x5a3000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x5a3000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libX11.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3005\1\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=1233824, ...}) = 0
23:21:17 mmap2(NULL, 1237780, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x1a9000
23:21:17 mprotect(0x2d3000, 4096, PROT_NONE) = 0
23:21:17 mmap2(0x2d4000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12a) = 0x2d4000
23:21:17 mmap2(0x2d7000, 788, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x2d7000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libavahi-common.so.3", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`)\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=42548, ...}) = 0
23:21:17 mmap2(NULL, 45304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
23:21:17 mmap2(0x11a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0x11a000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libavahi-client.so.3", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 .\0\0004\0\0\0"..., 512) = 512
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a3000
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=63244, ...}) = 0
23:21:17 mmap2(NULL, 66016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xdd2000
23:21:17 mprotect(0xde0000, 4096, PROT_NONE) = 0
23:21:17 mmap2(0xde1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe) = 0xde1000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2201\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=79676, ...}) = 0
23:21:17 mmap2(NULL, 92136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x11c000
23:21:17 mmap2(0x12f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0x12f000
23:21:17 mmap2(0x131000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x131000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PI\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0755, st_size=116920, ...}) = 0
23:21:17 mmap2(NULL, 98792, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x133000
23:21:17 mmap2(0x148000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0x148000
23:21:17 mmap2(0x14a000, 4584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x14a000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/libz.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\31\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=83608, ...}) = 0
23:21:17 mmap2(NULL, 86284, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xce2000
23:21:17 mmap2(0xcf6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xcf6000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libjpeg.so.62", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20'\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=140900, ...}) = 0
23:21:17 mmap2(NULL, 143684, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x42a000
23:21:17 mmap2(0x44c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x21) = 0x44c000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a2000
23:21:17 mmap2(NULL, 1325416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x5a4000
23:21:17 mmap2(0x6e2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x6e2000
23:21:17 mmap2(0x6e5000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x6e5000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
23:21:17 mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x14c000
23:21:17 mmap2(0x14e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x14e000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXau.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\n\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=9564, ...}) = 0
23:21:17 mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x150000
23:21:17 mmap2(0x152000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x152000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXrender.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\24\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=34412, ...}) = 0
23:21:17 mmap2(NULL, 37260, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xe6c000
23:21:17 mmap2(0xe74000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0xe74000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libxcb.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P{\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=120380, ...}) = 0
23:21:17 mmap2(NULL, 119076, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb41000
23:21:17 mmap2(0xb5d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c) = 0xb5d000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/libdbus-1.so.3", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340Q\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=227000, ...}) = 0
23:21:17 mmap2(NULL, 230212, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x788000
23:21:17 mmap2(0x7bf000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x36) = 0x7bf000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/lib/tls/i686/cmov/librt.so.1", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\30\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=30684, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a1000
23:21:17 mmap2(NULL, 33364, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x2d8000
23:21:17 mmap2(0x2df000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0x2df000
23:21:17 close(3)                       = 0
23:21:17 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:21:17 open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
23:21:17 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\16\0\0004\0\0\0"..., 512) = 512
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=16628, ...}) = 0
23:21:17 mmap2(NULL, 19520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x189000
23:21:17 mmap2(0x18d000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0x18d000
23:21:17 close(3)                       = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78a0000
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb789f000
23:21:17 set_thread_area({entry_number:-1 -> 6, base_addr:0xb789f6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
23:21:17 mprotect(0x2df000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x7bf000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xb5d000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xe74000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x152000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x14e000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x6e2000, 8192, PROT_READ) = 0
23:21:17 mprotect(0x44c000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xcf6000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x148000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x12f000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xde1000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x11a000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x2d4000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xfcb000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x4c2000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xf94000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xab3000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x160000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x953000, 32768, PROT_READ) = 0
23:21:17 mprotect(0x774000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x1a7000, 4096, PROT_READ) = 0
23:21:17 mprotect(0xca5000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x813b000, 4096, PROT_READ) = 0
23:21:17 mprotect(0x2fe000, 4096, PROT_READ) = 0
23:21:17 munmap(0xb78a6000, 72901)      = 0
23:21:17 set_tid_address(0xb789f728)    = 19844
23:21:17 set_robust_list(0xb789f730, 0xc) = 0
23:21:17 futex(0xbfc419d0, FUTEX_WAKE_PRIVATE, 1) = 0
23:21:17 futex(0xbfc419d0, 0x189 /* FUTEX_??? */, 1, NULL, bfc419e0) = -1 EAGAIN (Resource temporarily unavailable)
23:21:17 rt_sigaction(SIGRTMIN, {0x137340, [], SA_SIGINFO}, NULL, 8) = 0
23:21:17 rt_sigaction(SIGRT_1, {0x137820, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
23:21:17 rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
23:21:17 getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
23:21:17 uname({sys="Linux", node="jean-baptiste-laptopserver", ...}) = 0
23:21:17 gettimeofday({1264890077, 717791}, NULL) = 0
23:21:17 getuid32()                     = 1000
23:21:17 geteuid32()                    = 1000
23:21:17 brk(0)                         = 0x9705000
23:21:17 brk(0x9726000)                 = 0x9726000
23:21:17 open("/home/jean-baptiste/.x11vncrc", O_RDONLY) = -1 ENOENT (No such file or directory)
23:21:17 uname({sys="Linux", node="jean-baptiste-laptopserver", ...}) = 0
23:21:17 time(NULL)                     = 1264890077
23:21:17 open("/etc/localtime", O_RDONLY) = 3
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=2945, ...}) = 0
23:21:17 fstat64(3, {st_mode=S_IFREG|0644, st_size=2945, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78b7000
23:21:17 read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\f\0\0\0\f\0\0\0\0"..., 4096) = 2945
23:21:17 _llseek(3, -28, [2917], SEEK_CUR) = 0
23:21:17 read(3, "\nCET-1CEST,M3.5.0,M10.5.0/3\n", 4096) = 28
23:21:17 close(3)                       = 0
23:21:17 munmap(0xb78b7000, 4096)       = 0
23:21:17 write(2, "30/01/2010 23:21:17 ", 20) = 20
23:21:17 write(2, "x11vnc version: 0.9.3 lastmod: 2"..., 42) = 42
23:21:17 socket(PF_FILE, SOCK_STREAM, 0) = 3
23:21:17 connect(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, 20) = 0
23:21:17 getpeername(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, [20]) = 0
23:21:17 uname({sys="Linux", node="jean-baptiste-laptopserver", ...}) = 0
23:21:17 access("/home/jean-baptiste/.Xauthority", R_OK) = 0
23:21:17 open("/home/jean-baptiste/.Xauthority", O_RDONLY) = 4
23:21:17 fstat64(4, {st_mode=S_IFREG|0600, st_size=192, ...}) = 0
23:21:17 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb78b7000
23:21:17 read(4, "\1\0\0\32jean-baptiste-laptopserver\0\2"..., 4096) = 192
23:21:17 read(4, "", 4096)              = 0
23:21:17 close(4)                       = 0
23:21:17 munmap(0xb78b7000, 4096)       = 0
23:21:17 fcntl64(3, F_GETFL)            = 0x2 (flags O_RDWR)
23:21:17 fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK) = 0
23:21:17 fcntl64(3, F_SETFD, FD_CLOEXEC) = 0
23:21:17 poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
23:21:17 writev(3, [{"l\0\v\0\0\0\0\0\0\0\0\0", 12}, {"", 0}], 2) = 12
23:21:17 read(3, 0x9706ec0, 8)          = -1 EAGAIN (Resource temporarily unavailable)
23:21:17 poll([{fd=3, events=POLLIN}], 1, -1) = ? ERESTART_RESTARTBLOCK (To be restarted)
23:22:47 --- SIGINT (Interrupt) @ 0 (0) ---
23:22:47 +++ killed by SIGINT +++
```

trace2.out:
```
23:23:03 execve("/usr/bin/xdpyinfo", ["xdpyinfo", "-display", ":0"], [/* 20 vars */]) = 0
23:23:03 brk(0)                         = 0x81c1000
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f2000
23:23:03 access("/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/etc/ld.so.cache", O_RDONLY) = 3
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=72901, ...}) = 0
23:23:03 mmap2(NULL, 72901, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb77e0000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXext.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200+\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=60024, ...}) = 0
23:23:03 mmap2(NULL, 63136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xc48000
23:23:03 mmap2(0xc56000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xc56000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libX11.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\3005\1\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=1233824, ...}) = 0
23:23:03 mmap2(NULL, 1237780, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x3ea000
23:23:03 mprotect(0x514000, 4096, PROT_NONE) = 0
23:23:03 mmap2(0x515000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12a) = 0x515000
23:23:03 mmap2(0x518000, 788, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x518000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXtst.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\17\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=22076, ...}) = 0
23:23:03 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77df000
23:23:03 mmap2(NULL, 20848, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x110000
23:23:03 mmap2(0x114000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4) = 0x114000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXxf86vm.so.1", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\v\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=17880, ...}) = 0
23:23:03 mmap2(NULL, 20672, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x52b000
23:23:03 mmap2(0x52f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0x52f000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXxf86dga.so.1", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\23\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=22020, ...}) = 0
23:23:03 mmap2(NULL, 24892, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xcff000
23:23:03 mmap2(0xd04000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4) = 0xd04000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXi.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\24\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=38384, ...}) = 0
23:23:03 mmap2(NULL, 41344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xcec000
23:23:03 mmap2(0xcf5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xcf5000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXrender.so.1", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\24\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=34412, ...}) = 0
23:23:03 mmap2(NULL, 37260, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x332000
23:23:03 mmap2(0x33a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7) = 0x33a000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXinerama.so.1", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\7\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=6528, ...}) = 0
23:23:03 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77de000
23:23:03 mmap2(NULL, 9376, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x5f2000
23:23:03 mmap2(0x5f4000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x5f4000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260l\1\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0755, st_size=1319364, ...}) = 0
23:23:03 mmap2(NULL, 1325416, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x116000
23:23:03 mmap2(0x254000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13e) = 0x254000
23:23:03 mmap2(0x257000, 10600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x257000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXau.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\n\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=9564, ...}) = 0
23:23:03 mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x645000
23:23:03 mmap2(0x647000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x647000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libxcb.so.1", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P{\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=120380, ...}) = 0
23:23:03 mmap2(NULL, 119076, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x741000
23:23:03 mmap2(0x75d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c) = 0x75d000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
23:23:03 mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x63d000
23:23:03 mmap2(0x63f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0x63f000
23:23:03 close(3)                       = 0
23:23:03 access("/etc/ld.so.nohwcap", F_OK) = -1 ENOENT (No such file or directory)
23:23:03 open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
23:23:03 read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\16\0\0004\0\0\0"..., 512) = 512
23:23:03 fstat64(3, {st_mode=S_IFREG|0644, st_size=16628, ...}) = 0
23:23:03 mmap2(NULL, 19520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xd57000
23:23:03 mmap2(0xd5b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xd5b000
23:23:03 close(3)                       = 0
23:23:03 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77dd000
23:23:03 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77dc000
23:23:03 set_thread_area({entry_number:-1 -> 6, base_addr:0xb77dc6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
23:23:03 mprotect(0x63f000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x75d000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x647000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x254000, 8192, PROT_READ) = 0
23:23:03 mprotect(0x33a000, 4096, PROT_READ) = 0
23:23:03 mprotect(0xcf5000, 4096, PROT_READ) = 0
23:23:03 mprotect(0xd04000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x52f000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x114000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x515000, 4096, PROT_READ) = 0
23:23:03 mprotect(0xc56000, 4096, PROT_READ) = 0
23:23:03 mprotect(0x804e000, 4096, PROT_READ) = 0
23:23:03 mprotect(0xeb5000, 4096, PROT_READ) = 0
23:23:03 munmap(0xb77e0000, 72901)      = 0
23:23:03 brk(0)                         = 0x81c1000
23:23:03 brk(0x81e2000)                 = 0x81e2000
23:23:03 socket(PF_FILE, SOCK_STREAM, 0) = 3
23:23:03 connect(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, 20) = 0
23:23:03 getpeername(3, {sa_family=AF_FILE, path=@"/tmp/.X11-unix/X0"}, [20]) = 0
23:23:03 uname({sys="Linux", node="jean-baptiste-laptopserver", ...}) = 0
23:23:03 access("/home/jean-baptiste/.Xauthority", R_OK) = 0
23:23:03 open("/home/jean-baptiste/.Xauthority", O_RDONLY) = 4
23:23:03 fstat64(4, {st_mode=S_IFREG|0600, st_size=192, ...}) = 0
23:23:03 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77f1000
23:23:03 read(4, "\1\0\0\32jean-baptiste-laptopserver\0\2"..., 4096) = 192
23:23:03 read(4, "", 4096)              = 0
23:23:03 close(4)                       = 0
23:23:03 munmap(0xb77f1000, 4096)       = 0
23:23:03 fcntl64(3, F_GETFL)            = 0x2 (flags O_RDWR)
23:23:03 fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK) = 0
23:23:03 fcntl64(3, F_SETFD, FD_CLOEXEC) = 0
23:23:03 poll([{fd=3, events=POLLIN|POLLOUT}], 1, -1) = 1 ([{fd=3, revents=POLLOUT}])
23:23:03 writev(3, [{"l\0\v\0\0\0\0\0\0\0\0\0", 12}, {"", 0}], 2) = 12
23:23:03 read(3, 0x81c6778, 8)          = -1 EAGAIN (Resource temporarily unavailable)
23:23:03 poll([{fd=3, events=POLLIN}], 1, -1) = ? ERESTART_RESTARTBLOCK (To be restarted)
23:23:39 --- SIGINT (Interrupt) @ 0 (0) ---
23:23:39 +++ killed by SIGINT +++
```

thanks again for the help!

---

### Post by krunge on 2010-01-30
That is useful info.  Note how neither x11vnc nor xdpyinfo can connect to the X server display: both hang and you have to Ctrl-C them. So this problem isn't directly with x11vnc, but rather with *all* X client apps launched this way.

The strace output shows that the X client connects to the X server socket OK and then sends the authority data (empty in this case, but that is OK.) The X server simply never replies.

What distro and version are you running?

Is there some sort of screensaver running that is locking or grabbing the screen?  Please give details on your desktop, window manager, screensaver and anything else you can think of that might be relevant.

I assume you can run x11vnc (or xdpyinfo) successfully from within the X desktop session (i.e. from inside a terminal inside the session.)  Correct?

---

### Post by jnbptst on 2010-01-31
I am running Ubuntu 9.10.

The thing is, I don't have physical access to the computer, which I left running before moving to another country. My only access for now is SSH, so it is hard for me to check if x11vnc runs properly locally, or if the screensaver is running. Is there any way to check that from the command line?

---

### Post by krunge on 2010-01-31
> The thing is, I don't have physical access to the computer, which I left running before moving to another country. My only access for now is SSH, so it is hard for me to check if x11vnc runs properly locally, or if the screensaver is running. Is there any way to check that from the command line?
Oh, ok, that will make things trickier.

To see if a (non-blank) screensaver is running I sometimes use the 'top' command (of course it has to be a screensaver that uses significant cpu; I usually set up a blank screensaver).

You can also run ps to see which processes are running.  Why don't you run 'ps wwaux' and post the output here (or PM) so I could have a look to see if I can spot anything strange.

---

### Post by jnbptst on 2010-01-31
a friend was able to access the computer and apparently it had crashed onto a black screen... that's probably why requests to X were hanging. after a restart everything is working fine again.

thanks a lot for your help, and really sorry for wasting your time...!

---

### Post by krunge on 2010-01-31
> **jnbptst said:**
> a friend was able to access the computer and apparently it had crashed onto a black screen... that's probably why requests to X were hanging. after a restart everything is working fine again.

Wow; I thought this was a new problem with the Xorg X server, but it appears to be the age-old problem of crashing/wedging..

FYI there is a way to have x11vnc connected to the GDM (etc.) login greeter panel:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
That way after reboots you will be able to access the greeter via VNC and log into your session.  E.g. in your current case you could have either rebooted or restarted the X server thru your ssh login without the need for someone onsite to do this for you.

---

