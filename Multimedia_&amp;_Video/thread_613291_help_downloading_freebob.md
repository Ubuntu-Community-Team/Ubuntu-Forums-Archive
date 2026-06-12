---
title: "help downloading freebob"
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by rafafredd on 2007-11-14
OK, let me say I'm pretty new to all this. I come from a win world, and installed ubuntustudio some days ago.

I'm willing to make it work with my OZONIC soundcard / midi controler from maudio.

All went well with ubuntustudio. Now, following these instructions:

[http://freebob.sourceforge.net/index.php/Compiling_from_SVN_HOWTO](http://freebob.sourceforge.net/index.php/Compiling_from_SVN_HOWTO)

I'm trying to download and compile and install freebob, All went well with the first two libs. I got the the third lib with lots of hope, but I get error messages when trying to get the libs from sourceforge.net. That's what I'm getting:

I write

svn co [https://svn.sourceforge.net/svnroot/libavc1394/trunk/](https://svn.sourceforge.net/svnroot/libavc1394/trunk/) libavc1394

and get

svn: PROPFIND request failed on '/svnroot/libavc1394/trunk'
svn: PROPFIND of '/svnroot/libavc1394/trunk': Could not resolve hostname `svn.sourceforge.net': No address associated with hostname ([https://svn.sourceforge.net](https://svn.sourceforge.net))

Same thing for libfreebob... I just wrote this:

svn co [https://svn.sourceforge.net/svnroot/freebob/trunk/libfreebob](https://svn.sourceforge.net/svnroot/freebob/trunk/libfreebob) libfreebob

and got the exact same result.
It seems the files are not there?

Anyway, sorry for my long first post. Any help is very welcome. It would be a dream making it work.

Thanks!

---

### Post by rafafredd on 2007-11-16
UGH! no replies?? :(

---

### Post by wooster on 2007-11-16
I'll try to help out here. The SVN trunk for libavc1394 seems to be at [https://libavc1394.svn.sourceforge.net/svnroot/libavc1394](https://libavc1394.svn.sourceforge.net/svnroot/libavc1394). So I think the svn check out command for that would look like this. 

```
 svn co https://libavc1394.svn.sourceforge.net/svnroot/libavc1394/trunk libavc1394
```

As for the libfreebob svn repository I think this command should work for you.

```
 svn co https://freebob.svn.sourceforge.net/svnroot/freebob/trunk/libfreebob libfreebob
```

Hope that helps. Good luck.

---

### Post by rafafredd on 2007-11-16
Thanks a lot for your help. It seems that as far as I was able to go with this compilation thing was to trash my jack all the way. Now it asks for my ubuntstudio CD to recover it, wich is unfortunaly not handy, as I'm not home. As soon as I get home, I'&#314;l try to recover it and try to install again freebob, But ths time form this autoatic location I just found a thread about:

[http://ubuntuforums.org/showthread.php?t=544472&highlight=freebob+ozonic](http://ubuntuforums.org/showthread.php?t=544472&highlight=freebob+ozonic)

---

### Post by rafafredd on 2007-11-17
OK, after getting the automatic freebob instalation and reinstalling jack, the error remains the same:

jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Freebob using Firewire port 0, node -1
Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?
[31mFatal (devicemanager.cpp)[68] initialize: Could not initialize Ieee1349Service object
[0m[31mFatal (freebob.cpp)[69] freebob_new_handle: Could not initialize device manager
FreeBoB ERR: FREEBOB: Error creating virtual device
[0mcannot load driver module freebob
19:57:00.360 JACK was stopped successfully.
19:57:00.361 Post-shutdown script...
19:57:00.361 killall jackd
jackd: no process killed
19:57:00.568 Post-shutdown script terminated with exit status=256.
19:57:02.282 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

Any info on how to make it work. Argh! freebob should come ready in he next ubuntustudio, with realtime and all...

---

### Post by rafafredd on 2007-11-17
OK, I think Ie tried it all now. permissons sems to not be the problem, as I've already addedpermissions for raw1394 to audio group.

It says:

Ieee1394Service::initialize: Could not get 1394 handle: No such file or directory
Is ieee1394 and raw1394 driver loaded?

But how do I check for the drivers? How can I know if it's there or not? Well, at least on my device manager, I see:

Firewire (IEEE 1394)
     ozoni

It's strangely listed as ozoni instead of ozonic.

Well, I've been working for days on this, reading all I can find, and trying all.

Maybe I've just destroyed my operating system when trying to compile freebob, I don't know what else to think. The problem is that on freebob site there's nothing about the automatic installation. Then I've found it and tried it, and my jack lib was destroyed. Then ubuntu asked for the installation cd to recover it, it was recovered, and I just cannot get it to work anymore. I'm hopeless now. Sorry for the big cry.... Ijust wanted to make some:guitar: with ubuntu...:mad:

---

