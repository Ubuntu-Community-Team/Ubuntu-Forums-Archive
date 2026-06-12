---
title: "dvdauthor failing"
date: 2006-10-15
forum: Multimedia &amp; Video
---

### Post by GeryonD on 2006-10-15
I am trying to run DVDAuthor, via DVDStyler.  When I go to "burn" an ISO image of the DVD I am creating I get a "File Not Found" error from DVDAuthor.  This is under 6.06

I ran the command that DVDStyler is running by hand and the error still exists.  It looks like this:

```

STAT: VOBU 3472 at 193MB, 2 PGCS
INFO: Video pts = 0.178 .. 1279.456
INFO: Audio[0] pts = 0.178 .. 1279.442

STAT: Processing ...
ERR:  Error opening : No such file or directory

```

If I run an strace on the the command I see that it is trying to open 'libc.mo':

```

write(2, "\nSTAT: Processing ...\n", 22
STAT: Processing ...
) = 22
open("", O_RDONLY|O_LARGEFILE)          = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=1474, ...}) = 0
mmap2(NULL, 1474, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7f65000
close(4)                                = 0
write(2, "ERR:  Error opening : No such fi"..., 48ERR:  Error opening : No such file or directory
) = 48
exit_group(1) 

```

Now, 'libc.mo' is, accourding to 'file', a "libc.mo: GNU message catalog (little endian), revision 0, 11 message".  I indeed do not have this file for the 'en' language, which my system is configured for.  Looking in to it every language appears to have the 'libc.mo' catalog file, except 'en'.  So I tried copying the 'libc.mo' file from 'en_GB', next closest thing.  Re-ran it through strace and get this:

```

write(2, "\nSTAT: Processing ...\n", 22
STAT: Processing ...
) = 22
open("", O_RDONLY|O_LARGEFILE)          = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=1474, ...}) = 0
mmap2(NULL, 1474, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7faa000
close(4)                                = 0
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=1474, ...}) = 0
mmap2(NULL, 1474, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb7fa9000
close(4)                                = 0
write(2, "ERR:  Error opening : No such fi"..., 48ERR:  Error opening : No such file or directory
) = 48
exit_group(1) 

```

So it looks like copying the 'libc.mo' from another langauge does not work because it's expecting something different.  

Anyway, this is where I am and I can not get DVDAuthor to work under Ubuntu :(  Does anyone have any suggestions at all?

---

### Post by kafkaian on 2006-11-04
Yes I'm having problems too and it seems my Mpeg files are invalid and require ffmpeg to translate them before dvdauthor can convert them

Actually, suggestions on Ubuntu forums are thin on the ground but more ppl will get enticed eventually i reckon

---

### Post by grepster on 2006-11-09
Using strace is not very relevent.  
What is the output of the full dvdauthor command, along with the command line used ?

grepster

---

