---
title: "jackd not working, ubuntu 12.04"
date: 2012-11-28
forum: Multimedia Software
---

### Post by tontis on 2012-11-28
Hello,
im quite a new user to ubuntu and I have some problems that I'd appreciate any help for.

I'm trying to make audio work in rosegarden, and therefor installed jackd and qjackctll. That however does of course not just work on its own! However, after reading and searching a bit I'm still confused to exactly what these applications do or how they're supposed to be managed.

I tried method 1 solution from [*this*]("http://ubuntuforums.org/showthread.php?p=12377426#post12377426") post, without installing ubuntu studio, but it didn't do any difference.

This error text is produced in qjackctl when trying to start:
```
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
12:16:33.408 ALSA connection graph change.
12:16:40.718 D-BUS: JACK server could not be started. Sorry
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Wed Nov 28 12:16:40 2012: Starting jack server...
Wed Nov 28 12:16:40 2012: JACK server starting in realtime mode with priority 10
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot lock down 82241434 byte memory area (Cannot allocate memory)[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: can't load "/usr/lib/i386-linux-gnu/jack/jack_alsa.so": /usr/lib/i386-linux-gnu/jack/jack_alsa.so: undefined symbol: _ZN4Jack14JackPosixMutex4LockEv[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Cannot initialize driver[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: JackServer::Open() failed with -1[0m
Wed Nov 28 12:16:40 2012: [1m[31mERROR: Failed to open server[0m
Wed Nov 28 12:16:42 2012: Saving settings to "/home/bixop/.config/jack/conf.xml" ...
12:16:44.846 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```

Does it give anyone any idea?

---

### Post by AstroLlama on 2012-11-28
EDIT: are the correct interface, input device and output device selected in qjackctl? if you have one sound card (default) should work.

The first thing you should do is start qjackctl, press the triangle style "start" button to start the jack server.

Did jack start correctly? ok, after this open up rosegarden. Now go back to qjackctl and open the "connect" window and see if Rosegarden shows up at all. The next steps depend on how you want to use Rosegarden.

If you DON'T see rosegarden in the "connect" window then go into rosegardens settings and see if there is an option for where to route input/ output. It should be sending output to Jack (there may be 2 jack options), or ALSA.

---

### Post by tontis on 2012-11-29
Thx for your reply AstroLlama, but now it seems to be magically working for some reason!

I guess the install from the other repositories needed a reboot.

Over. out. and.

---

