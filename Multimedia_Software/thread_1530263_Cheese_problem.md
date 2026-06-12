---
title: "Cheese problem"
date: 2010-07-13
forum: Multimedia Software
---

### Post by onlypanatha on 2010-07-13
Hello,

I'm using ubuntu 10.04 and I am having a problem with cheese. It doesn't open. I tried to open it in terminal and I got this:




RGBA=on
libv4l2: error converting / decoding frame data: v4l-convert: error parsing JPEG header: Not a JPG file ?


The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 80 error_code 8 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



I don't know much about linux and I could really use your help to identify and fix my problem.
You must know it used to work perfectly. Had no problem with it.

Thank you.

---

### Post by arashiko28 on 2010-07-13
See if you accidentally shut down your web cam. It happened to me, in my computer it was Fn+Esc

---

### Post by onlypanatha on 2010-07-13
> **arashiko28 said:**
> See if you accidentally shut down your web cam. It happened to me, in my computer it was Fn+Esc

No that's not the problem, my camera is ON. It works in a greek site. I can take pictures from there normally.

---

### Post by no2498 on 2010-07-13
see if you can use wxcam

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it comes in a deb file if you need it 

hope this helps

---

### Post by abdusamed on 2010-09-14
I'm facing exactly the same problem

---

### Post by azwar on 2010-09-14
yes... try wxcam. it is better than cheese.

---

### Post by abdusamed on 2010-09-14
Guvideo from the repo works fine too but my question is why is it not working now? It was working a while ago but now it isn't

The log below shows the whole event from start to crash
```

bahie@bahie-laptop:~$ cheese

progname=cheese; RGBA=on
The program 'cheese' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 80 error_code 8 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
bahie@bahie-laptop:~$ 

```

---

### Post by abdusamed on 2010-09-16
It's only 32bit... the installaiton wouldn't work

---

### Post by abdusamed on 2010-10-16
mine was fixed by disabling rgba

---

