---
title: "Totem randomly stops working"
date: 2011-02-04
forum: Multimedia Software
---

### Post by Jesse David on 2011-02-04
I've been having problems with Totem occasionally deciding that it no longer wants to work.

When this happens whenever I try to open a video with Totem again it just quits right after I see the window popup.  After this the only way to get Totem to work is to restart the computer.

I was hoping that someone might have an idea of what I could do to fix this.  Preferably permanently however I'd be happy just being able to do something to make Totem work again without resetting.

---

### Post by Yellow Pasque on 2011-02-04
[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by Jesse David on 2011-02-04
I believe I already had that PPA installed, with MediBuntu or something of the like.  After adding the source and updating I still couldn't make Totem run again (VLC had problems too).

Hopefully, it fixed the problem but really only time will tell since it seems to happen on random.

---

### Post by Jesse David on 2011-02-10
That fix didn't work.  Just had it happen again.

No command that I can use to kill off processes that might be the problem?

I took a look at the current processes and nothing jumps out at me as being related to this issue.

---

### Post by Yellow Pasque on 2011-02-10
Install and use htop to monitor/kill processes. Other than that, I would advise you to start totem from a terminal and see if there are specific error messages.

---

### Post by Jesse David on 2011-02-26
This is the message I get when it decides not to work:

```
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 126 error_code 2 request_code 133 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

