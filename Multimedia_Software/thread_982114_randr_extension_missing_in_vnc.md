---
title: "randr extension missing in vnc"
date: 2008-11-14
forum: Multimedia Software
---

### Post by gnu2tux on 2008-11-14
Hi.

 I am making a project that connects a thin-client winCE based device to any RDP connection. I apt-get'ed xrdp on my intrepid box and it installs fine, after a little teakage to the startwm.sh script I made it start up a pekwm session and I could use xterm and basic X utils on the from terminal services.

I tried to start Firefox, and any normal gnome app and I get:

Xlib: extension "RANDR" missing on display ":10.0".

on closer inspection, if I forget all my xrdp nonsense and just run vanilla vncserver and connect to it from any host, all vnc sessions do not support the xrandr extension. I tried adding the vnc module into /etc/X11/xorg.conf but the module is borked at the moment (see launchpad for that), but I don't know if that's the answer anyway.

I know that vnc has supported xrandr since 2004 and I think that it's mainstream now, so how come it doesn't work in Intrepid? I can't launch any everyday apps without it, it appears.

Any help would be greatly appreciated. TIA!

Ali

---

### Post by gnu2tux on 2008-11-21
anyone?

---

### Post by keturn on 2008-12-08
This is now one of the top hits for searching for the terms randr vnc, which, oddly enough, I was also doing after trying to connect to xrdp from a winCE device.

I think the RANDR message from Firefox is actually a red herring.  If I start Xvnc with the XFIXES extension (as vnc4server does), firefox still emits that message but it starts okay.  To do that, add the parameters to /etc/xrdp/sesman.ini, e.g.

```
[Xvnc]
param1=-bs
param2=-ac
param3=-extension
param4=XFIXES

```

---

### Post by gnu2tux on 2008-12-08
Thanks for that. I don't think I could have guessed that one!

Cheers!

---

### Post by lulu135 on 2009-02-05
randr support in Xvnc has been a much requested feature by users, and a much ignored feature by developers.
There are several unofficial patches for various versions of realvnc and tightvnc floating around, but they have never been incorporated into the main codebases.  I guess the main developers need more nagging or something.

I currently run a patched version of realvnc 4.1.2 myself and the randr support works well.  You have to give it a list at startup of all the different resolutions you want available.  I found it here:

[http://yoush.homelinux.org:8079/nikita/vnc-xrandr/](http://yoush.homelinux.org:8079/nikita/vnc-xrandr/)

---

### Post by Ryuho on 2010-09-09
I'm using tightvncserver to access my Ubuntu 10.04 desktop edition from winodws 7 using tightvncViewer.

When I try to open up cheese (program that uses webcam) I get this error...
```

ryuho@ryuho-server:~$ cheese
Xlib:  extension "RANDR" missing on display ":1.0".
Segmentation fault
ryuho@ryuho-server:~$

```
Did anyone find a solution for this problem? Do I have to add anything to the ~/.vnc/xstartup?

---

### Post by icestation on 2010-12-29
I am running tighvnc set up as described here:

[http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot](http://www.abdevelopment.ca/blog/start-vnc-server-ubuntu-boot)

and I get the same error in UBUNTU 10.10 when I try to run disk utils!

iceman@ubuntu-server:/$ palimpsest
Xlib:  extension "RANDR" missing on display ":1.0".
Segmentation fault
iceman@ubuntu-server:/$ 

OK, so this sucks a bit, but no where near as bad as windoze.  Long live UBUNTU!

(However, if any one has a fix, please feel free to post it  :)

---

