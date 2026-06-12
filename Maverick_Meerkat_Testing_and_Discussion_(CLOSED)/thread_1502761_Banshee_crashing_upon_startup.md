---
title: "Banshee crashing upon startup"
date: 2010-06-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-06-06
Just set up a fresh install of Maverick and installed Banshee from Ubuntu Software Centre, it quits immediately after starting up. Is anyone else having the same problem?

---

### Post by autocrosser on 2010-06-06
Have you tried starting it in a term to see why?  I've not installed it, so I don't know.......

---

### Post by go7Ul1ai on 2010-06-06
> **autocrosser said:**
> Have you tried starting it in a term to see why?  I've not installed it, so I don't know.......

```
[Info  06:40:32.888] Running Banshee 1.7.1: [Ubuntu maverick (development branch) (linux-gnu, x86_64) @ 2010-06-03 16:38:21 UTC]
[Info  06:40:34.427] All services are started 1.277574
[Info  06:40:35.220] nereid Client Started

Gdk-ERROR **: The program 'Banshee' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 2763 error_code 8 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
aborting...
Trace/breakpoint trap

```

---

### Post by fluteflute on 2010-06-06
[https://bugs.edge.launchpad.net/ubuntu/+source/banshee/+bug/585160](https://bugs.edge.launchpad.net/ubuntu/+source/banshee/+bug/585160)

---

### Post by jppr on 2010-06-06
> **lee.jarratt said:**
> Just set up a fresh install of Maverick and installed Banshee from Ubuntu Software Centre, it quits immediately after starting up. Is anyone else having the same problem?

I have same problem, I installed it Kubuntu 10.10

---

### Post by Gourgi on 2010-06-06
the upstream bug for banshee is this
[https://bugzilla.gnome.org/show_bug.cgi?id=620461](https://bugzilla.gnome.org/show_bug.cgi?id=620461)
i haven't tried the proposed solution yet though.

---

