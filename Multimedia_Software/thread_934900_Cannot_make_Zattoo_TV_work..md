---
title: "Cannot make Zattoo TV work."
date: 2008-10-01
forum: Multimedia Software
---

### Post by 2blue on 2008-10-01
Have anyone managed to make Zattoo tv work in (X)ubuntu Hardy Heron?

So far I have downloaded the Zattoo software but it will not open. It has placed it self under "multimedia" and I cannot see why it should not work / respond at all? 

Is there any other way to have TV on Xubuntu?

---

### Post by aurelieng on 2008-10-01
Same problem here, tested on two different Kubuntu 8.04. Strangely, a third one is working correctly. Interestingly a new release is available since this morning: Zattoo 3.3.0. I can't test it now. Does it fix the problem ?

---

### Post by 2blue on 2008-10-01
Thanks for the info, I shall try it when I get home, in about 4 hours or so :)

---

### Post by ronnielsen1 on 2008-10-01
> You seem to be accessing the Zattoo website from a country we do not yet serve.

:(

---

### Post by lqyjzmms on 2008-12-17
Zattoo does not start on my machine, either. I'm running Kubuntu 8.10.

Output of Zattoo:
```

20:18:32 17.12.2008 [MSG]       Current locale is de_DE.UTF-8
20:18:32 17.12.2008 [MSG]       Wilkommen bei Zattoo (3.3.1.18350)
20:18:32 17.12.2008 [MSG]       Further log messages will be written to /home/myusername/.Zattoo/Data/logs/zattoo.debuglog

```

Content of zattoo.debuglog:
```

20:18:32 17.12.2008 [MSG]       Wilkommen bei Zattoo (3.3.1.18350)
20:18:32 17.12.2008 [MSG]       response parsing failed
20:18:32 17.12.2008 [MSG]       zattood_initlib.  Assumes zattood is in the same current working dir.
20:18:32 17.12.2008 [MSG]       Using conf directory: /home/myusername/.Zattoo/Data
20:18:32 17.12.2008 [MSG]       Using executable home: /usr/bin
12-17 19:18:32.622      D2 Absent nb backup address, do without.
12-17 19:18:32.623      D2 NATC: reinited, server 91.123.96.18:3478.
12-17 19:18:32.623      D1 tmeshd: realmaxcp set to 0

```

Last lines of strace zattoo_player:
```

open("/usr/lib/dri/r300_dri.so", O_RDONLY) = 23
read(23, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\323\1"..., 512) = 512
fstat64(23, {st_mode=S_IFREG|0644, st_size=2274052, ...}) = 0
mmap2(NULL, 2321768, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 23, 0) = 0xb3d71000
mmap2(0xb3f88000, 86016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 23, 0x216) = 0xb3f88000
mmap2(0xb3f9d000, 44392, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb3f9d000
close(23)                               = 0
open("/usr/lib/zattoo/libdrm.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 23
fstat64(23, {st_mode=S_IFREG|0644, st_size=94713, ...}) = 0
mmap2(NULL, 94713, PROT_READ, MAP_PRIVATE, 23, 0) = 0xb3d59000
close(23)                               = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdrm.so.2", O_RDONLY)  = 23
read(23, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\37\0"..., 512) = 512
fstat64(23, {st_mode=S_IFREG|0644, st_size=30040, ...}) = 0
mmap2(NULL, 34216, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 23, 0) = 0xb582b000
mmap2(0xb5832000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 23, 0x6) = 0xb5832000
close(23)                               = 0
mprotect(0xb5832000, 4096, PROT_READ)   = 0
munmap(0xb3d59000, 94713)               = 0
munmap(0xb3d71000, 2321768)             = 0
munmap(0xb582b000, 34216)               = 0
select(4, [3], [3], NULL, NULL)         = 1 (out [3])
writev(3, [{"\217\23\3\0\0\0\0\0\2\0\0\0", 12}], 1) = 12
select(4, [3], [], NULL, NULL)          = 1 (in [3])
read(3, "\0\1\216\0\4\0 \3\23\0\217\0\2600\265\2670\202\267\23\350"..., 4096) = 32
open("/usr/share/X11/XErrorDB", O_RDONLY) = 23
fstat64(23, {st_mode=S_IFREG|0644, st_size=38887, ...}) = 0
brk(0x85e6000)                          = 0x85e6000
read(23, "! $Xorg: XErrorDB,v 1.3 2000/08/"..., 38887) = 38887
close(23)                               = 0
write(2, "The program \'zattoo_player\' rece"..., 589) = 589
writev(20, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(20)                               = 0
writev(18, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
close(18)                               = 0
close(16)                               = 0
close(12)                               = 0
unlink("/tmp/orbit-myusername/linc-5d4e-0-1147578d78d7c") = 0
close(19)                               = 0
exit_group(1)                           = ?
Process 23886 detached

```

---

### Post by lqyjzmms on 2008-12-20
Another piece of information that might be relevant:

~/.Zattoo/Data/logs/zattoo.errlog contains this error message after trying to start zattoo_player:
```

The program 'zattoo_player' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 206 error_code 1 request_code 143 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

