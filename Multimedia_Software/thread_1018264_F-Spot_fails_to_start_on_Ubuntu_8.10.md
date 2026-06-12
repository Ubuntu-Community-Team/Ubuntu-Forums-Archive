---
title: "F-Spot fails to start on Ubuntu 8.10"
date: 2008-12-21
forum: Multimedia Software
---

### Post by MeanStreak on 2008-12-21
Hi,

I've resubmitted this thread as I received no responses to my initial post. Since upgrading to 8.10, F-Spot fails to start leaving me without a photo management tool. Has anyone else encountered this problem? Could someone please advise how I can resolve this issue! 

Re-started this thread [http://ubuntuforums.org/showthread.php?t=1004105](http://ubuntuforums.org/showthread.php?t=1004105)

---

### Post by sirlancelot on 2008-12-21
We might have the same problem (see thread: [http://ubuntuforums.org/showthread.php?t=1018060](http://ubuntuforums.org/showthread.php?t=1018060)).

Run f-spot in the terminal and post it's output. Open a terminal and type: f-spot

---

### Post by fblauer on 2009-01-07
I have same problem - In terminal  get
fred@HP_MEDIAPC:~$ f-spot
[Info  17:30:01.994] Initializing DBus
[Info  17:30:02.367] Initializing Mono.Addins
[Info  17:30:02.820] Starting new FSpot server
The program 'f-spot' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 336 error_code 1 request_code 157 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

