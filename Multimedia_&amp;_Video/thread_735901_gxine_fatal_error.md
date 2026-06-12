---
title: "gxine fatal error"
date: 2008-03-26
forum: Multimedia &amp; Video
---

### Post by nlz on 2008-03-26
i used VLC and GXine to play VCD's. Sometimes VLC plays VCD's jittery and then gxine works perfectly, and sometimes GXine won't jump over VCD menu and i'll use VLC.

Now i had to reinstall my gutsy. Now i have the new fgrlx driver working but when i want to start gxine i get this:

```
qnuf@mediaction:~$ gxine
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 327 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
qnuf@mediaction:~$ 

```

I removed and reinstalled it several times but it won't work.. And i really don't see why..

---

### Post by nlz on 2008-03-26
the only thing i can think of is that it has something to do with the new fglrx or with this manual: [http://ubuntuforums.org/showthread.php?t=661833&highlight=vcd](http://ubuntuforums.org/showthread.php?t=661833&highlight=vcd)

---

### Post by nlz on 2008-03-27
huh? now totem seems to do the same thing!!

It must be something with x windows. anyone got an idea?

```
qnuf@mediaction:~$ totem vcd://
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 42 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
qnuf@mediaction:~$ 

```

---

### Post by nlz on 2008-03-27
see: [http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4588900](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=4588900)

---

