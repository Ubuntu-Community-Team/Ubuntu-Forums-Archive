---
title: "Totem Help"
date: 2008-01-02
forum: Multimedia &amp; Video
---

### Post by tayyy on 2008-01-02
Totem only works in root. When I run it normally, it says that jackd is missing. After I install jackd from synaptic it still does not work. Please help thanks.

---

### Post by tayyy on 2008-01-02
After a while I found out that this may not have to do with jackd. Here is the log from terminal:


The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 50 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


In root I dont get this.

---

