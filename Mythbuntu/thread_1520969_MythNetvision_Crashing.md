---
title: "MythNetvision Crashing"
date: 2010-06-30
forum: Mythbuntu
---

### Post by g8keepR on 2010-06-30
Hello everyone,

On my revo box, mythnetvision refuses to play anything, crashes and returns to the desktop.  This machine is using the latest mythbuntu (lucid) and was successfully upgraded from karmic.  The only thing I've found in the logs is in /var/log/messages:

Jun 27 09:24:33 revo kernel: [299893.224879] mythfrontend.re[15661]: segfault at 28 ip 06537705 sp bf93eea0 error 6 in libgdk_pixbuf-2.0.so.0.2000.0[6531000+18000]

This is strange b/c on my main machine (a clean install of lucid), can play mythnetvision fine.  After coming across the above log entry, I decided to compare installed packages.  It seemed that my revo box had an older gtk2-engines-pixbuf package.  I then proceeded to compare /etc/apt/sources.list files between the machines, updated the sources then updated the gtk2-engines-pixbuf:

Package: gtk2-engines-pixbuf
State: installed
Automatically installed: no
Version: 2.20.1-0ubuntu2

... now it appears that all packages are equal between the working machine (my desktop) and non-working machine (revo).

I then proceeded to try mythnetvision again, it crashed and I received a similar error, but in a different address:

Jun 29 21:17:23 revo kernel: [515463.135556] mythfrontend.re[22869]: segfault at 28 ip 04131705 sp bfb51cd0 error 6 in libgdk_pixbuf-2.0.so.0.2000.0[412b000+18000]
Jun 29 21:47:00 revo kernel: [517240.389082] mythfrontend.re[24013]: segfault at 28 ip 0424c705 sp bf801490 error 6 in libgdk_pixbuf-2.0.so.0.2000.1[4246000+18000]

Has anyone seen this before?  Should I file a bug?  MythTV is set to use "internal" for the web player.

Here is the version I'm using:
Package: mythnetvision
State: installed
Automatically installed: no
Version: 0.23.0+fixes25178-0ubuntu0+mythbuntu2

... again , the same on both machines.

The only thing I can think of is on my desktop machine I'm using the nvidia packages for my video driver, and on my revo I could not get those to work (I had to manually install the .run package from nvidia's webpage - NVIDIA-Linux-x86-195.36.31-pkg1.run)

Thanks

---

### Post by cosmotherobot on 2010-07-04
My revo is doing the exact same thing with mythnetvision.   I'd love to figure it out.

---

### Post by golbez_88rule on 2010-09-10
I also run mythfronted on a Revo and I am having the exact same issue! All the mythnetvision [wiki]("http://www.mythtv.org/wiki/MythNetvision") says is to try a different MythTV window resolution?  I am not sure how to configure that setting.

---

### Post by iamlindoro on 2010-09-11
The crash is in libgtk, and appears to be your flash plugin (ie, the crash is not in Myth code).  There are some known funkinesses with Qt's NSPlugin interface with some versions of flash that causes exactly this crash, and unfortunately we're stuck waiting for Qt to fix it in some future version (and if possible apparently rolling back to Flash Plugin 10.0 rather than 10.1 helps some people).  Also, make sure you are running a real Java (from SUN) and not the open JRE, which can also cause crashes on pages with Java.

---

