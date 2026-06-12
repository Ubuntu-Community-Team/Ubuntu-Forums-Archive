---
title: "Unable To Watch Recordings After Upgrade To 0.21"
date: 2008-03-11
forum: Mythbuntu
---

### Post by tom purl on 2008-03-11
Tonight, my mythtv backend/frontend installation was upgraded via the Ubuntu backports repository to 0.21.  When I try to watch one of my recordings using mythfrontend, it crashes and I get the following error message:

```
/usr/bin/mythfrontend.real: symbol lookup error: /usr/lib/libmythtv-0.21.so.0: undefined symbol: glXGetProcAddress
```

This looked like a video driver issue to me, so I checked to make sure that I still had them installed.  I use a Riva TNT2 video card, so I have the following nvidia drivers installed (according to aptitude):

[LIST]
[*]nvidia-glx-legacy
[*]nvidia-kernel-common
[/LIST]

I checked my restricted drivers manager, and it said that I had the binary nvidia driver enabled.  Also, my xorg.conf file says that I'm using the proprietary 'nvidia' driver, not the open source 'nv' driver.  

I also tried restarting mythbackend a bunch of times, and rebooted the media server.  

Does anyone have any idea why I'm having this issue?  Is it a packaging problem, or do you think it's a bug in Mythtv?

Thanks in advance for any help!

Tom Purl

---

### Post by mike-g on 2008-03-12
Sadly I can report the same issue !

I am using .021 after upgrade from .020 I cannot watch recordings made with myth - the front end crashes out as above.

I suspect something to do with nvidia-glx-legacy as I run this too - without problems on previous build.

Please can anyone shed light on this?

From back end log when trying to play:
2008-03-12 18:35:06.002 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)
2008-03-12 18:35:06.005 Using protocol version 40
2008-03-12 18:35:07.671 TV: Attempting to change from None to WatchingPreRecorded
2008-03-12 18:35:07.773 DPMS Deactivated 
2008-03-12 18:35:16.877 AFD Error: Could not find codec parameters. file was "/var/lib/mythtv/recordings/1097_20080311231000.mpg".
2008-03-12 18:35:16.878 Couldn't open decoder for: /var/lib/mythtv/recordings/1097_20080311231000.mpg
2008-03-12 18:35:16.878 TV Error: StartPlayer(): NVP is not playing after 20000 mse

...
-03-12 18:36:10.648 AFD: Opened codec 0x8322ba0, id(MP2) type(Audio)
2008-03-12 18:36:10.648 AFD: codec MP2 has 2 channels
2008-03-12 18:36:10.648 AFD: Opened codec 0x836f8a0, id(MP2) type(Audio)
2008-03-12 18:36:12.119 NVP: Prebuffer wait timed out 10 times.
2008-03-12 18:36:13.451 NVP: Prebuffer wait timed out 10 times.
2008-03-12 18:36:14.782 NVP: Prebuffer wait timed out 10 times.
2008-03-12 18:36:16.114 NVP: Prebuffer wait timed out 10 times.
2008-03-12 18:36:17.445 NVP: Prebuffer wait timed out 10 times.
2008-03-12 18:36:18.776 NVP: Prebuffer wait timed out 10 times.
...
/usr/bin/mythfrontend.real: symbol lookup error: /usr/lib/libmythtv-0.21.so.0: undefined symbol: glXGetProcAddress
[crashes after that]
Codec problem? Any ideas appreciated!


EDIT: This seems to be the root of problem:
"This is not a NVIDIA bug, glXGetProcAddress() is part of GLX 1.4, which the NVIDIA Linux/UNIX graphics driver doesn't claim to support (nor do I think was GLX 1.4 ever finalized); you should always use glXGetProcAddressARB()." [http://www.nvnews.net/vbulletin/showthread.php?t=15297](http://www.nvnews.net/vbulletin/showthread.php?t=15297)

Anyone care to fix? I dont know enough about myth to do this!

---

### Post by thatkidandy on 2008-03-12
when you apt upgraded did all of the packages update?

check.

I just did sort of without thinking, and my mythtv-backend and several other packages did not upgrade with the rest. I got some frontend/backend communication errors, that may or may not be related to your issue. Just throwing it out there as something to look into...

---

### Post by majoridiot on 2008-03-12
> **thatkidandy said:**
> when you apt upgraded did all of the packages update?

check.

I just did sort of without thinking, and my mythtv-backend and several other packages did not upgrade with the rest. I got some frontend/backend communication errors, that may or may not be related to your issue. Just throwing it out there as something to look into...

this is a very good suggestion... the updater has been notifying me of packages to update for a couple of days, but as 
of a few hours ago it was still warning of the ability to only partially-upgrade.  you might very well have an 
uncompleted update, which is causing this issue.

---

### Post by mike-g on 2008-03-12
I'm not sure the partial update is problem: the reference to "undefined symbol: glXGetProcAddress" is caused when myth calls a function not available to to the legacy video cards (as I understand it) - there is a safer function to call (see link) but that is not called.

---

### Post by trriss on 2008-03-12
The problem seems to be that the packagers build the package in a way that makes myth use the glXGetProcAddress instead of the glXGetProcAddressARB function.... When you compile the package yourself, the configure should detect which one your driver supports and then use that one, but in the binary package that choice is made already..... i think i'm going to try to compile the source packages myself to see if that helps.....

I reported this in launchpad: [https://bugs.launchpad.net/mythbuntu/+bug/201567](https://bugs.launchpad.net/mythbuntu/+bug/201567)

---

### Post by mike-g on 2008-03-12
It would  be great if you could let us know how that goes - and any special steps to get that to work.

Cheers.

---

### Post by trriss on 2008-03-13
recompiling the source package doesn't seem to work, since the compile stops with an error that the glXGetProcAddress function isn't available.... I tried installing the nvidia-glx-legacy-dev package, but that didn't help...

going to try to find a newer driver which still supports my geforce 4 mx 4000, hoping that it also supports the glXGetProcAddress....

---

### Post by aradke on 2008-03-14
Playback is incompatible with nvidia-glx-legacy.

I switched to nvidia-glx-new on my frontend and upgraded the graphics card to one that it supports and now all is working.

I believe this means that the mythtv-frontend package should have a conflict listed with nvidia-glx-legacy.

---

### Post by laga on 2008-03-15
Does this also happen in Hardy?

---

### Post by yanii on 2008-03-15
As a temporary measure you can manually recompile libmythtv-0.21 after applying the following patch to undefine GLX_VERSION_1_4, it's really only a temporary fix though.

diff -u mythtv-0.21.0/libs/libmythtv/util-opengl.cpp.old mythtv-0.21.0/libs/libmythtv/util-opengl.cpp
--- mythtv-0.21.0/libs/libmythtv/util-opengl.cpp.old    2008-03-15 09:46:54.000000000 -0400
+++ mythtv-0.21.0/libs/libmythtv/util-opengl.cpp        2008-03-15 07:28:15.000000000 -0400
@@ -306,8 +306,8 @@
 {
     __GLXextFuncPtr ret = NULL;
 
-#if GLX_VERSION_1_4
-    X11S(ret = glXGetProcAddress((const GLubyte*)procName.latin1()));
+/*#if GLX_VERSION_1_4
+    X11S(ret = glXGetProcAddress((const GLubyte*)procName.latin1()));*/
 #if GLX_ARB_get_proc_address
     X11S(ret = glXGetProcAddressARB((const GLubyte*)procName.latin1()));
 #elif GLX_EXT_get_proc_address


I've attached the packages I could, unfortunately the libmythtv package is 7mb and well beyond the limits of the forum, but you can download it here:

[http://launchpadlibrarian.net/12685276/libmyth-0.21-0_0.21.0-0ubuntu2%7Egutsy1_i386.deb](http://launchpadlibrarian.net/12685276/libmyth-0.21-0_0.21.0-0ubuntu2%7Egutsy1_i386.deb)

---

