---
title: "[ubuntu server] X server, root and normal user"
date: 2009-04-14
forum: Multimedia Software
---

### Post by cipher999 on 2009-04-14
My problem is as follows : i have a ubuntu server with xbmc installed.

I start it up using this command :

```
sudo xinit /usr/bin/xbmc --standalone
```

Then it would start xbmc as a regular user (nico).

Now I want this to happen at startup (starting x as root, then xbmc as nico).

I tried to put this command in rc.local :

```
xinit sudo -u nico /usr/bin/xbmc --standalone
```

but it does not work, x starts and exits instantly.

Any ideas ?

---

### Post by antikristian on 2009-04-14
Xinit man page:

> The  xinit  program  is  used to start the X Window System server and a first client program on systems that cannot start X directly from /etc/init or in environments that use multiple window systems.  When this first client exits, xinit will kill the X server and then terminate.


So when sudo finishes, x stops.

So this should work:

```
xinit "sudo -u nico /usr/bin/xbmc --standalone"
```

---

### Post by cipher999 on 2009-04-14
It did not work I'm afraid. I have the same problem. Here is the output (the command is executed as root, as rc.local does) :

```
root@eeepo:~# xinit "sudo -u nico /usr/bin/xbmc --standalone"
X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux eeepo 2.6.27-11-server #1 SMP Wed Apr 1 21:53:55 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 14 21:03:29 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
xinit:  No such file or directory (errno 2):  no program named "xterm" in PATH

Specify a program on the command line or make sure that /usr/bin
is in your path.


waiting for X server to shut down 



```

There is a lot of buggy output in here. So I also provide the output of the command which WORKS (executed as normal user) :

```
nico@eeepo:/root$ sudo xinit /usr/bin/xbmc --standalone &
[2] 6883
nico@eeepo:/root$ 
X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux eeepo 2.6.27-11-server #1 SMP Wed Apr 1 21:53:55 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 14 21:07:44 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Error org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files
++ WARN: could not retrieve file info for `image.nrg': No such file or directory
++ WARN: can't open nrg image file image.nrg for reading


```

---

### Post by cipher999 on 2009-04-14
Continuing my investigations....

I now did a apt-get install xterm and here is the new error message :

```
root@eeepo:~# xinit "sudo -u nico /usr/bin/xbmc --standalone"

X: warning; process set to priority -1 instead of requested priority 0

X.Org X Server 1.5.2
Release Date: 10 October 2008
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-19-server i686 Ubuntu
Current Operating System: Linux eeepo 2.6.27-11-server #1 SMP Wed Apr 1 21:53:55 UTC 2009 i686
Build Date: 24 October 2008  08:00:16AM
xorg-server 2:1.5.2-2ubuntu3 (buildd@rothera.buildd) 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 14 22:08:56 2009
(==) Using config file: "/etc/X11/xorg.conf"
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
No absolute path found for shell: sudo -u nico /usr/bin/xbmc --standalone
^C
waiting for X server to shut down xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":0.0"


```

But now x is not stopping. The command is aparently passed to xterm which does not execute it somehow.

---

### Post by antikristian on 2009-04-14
maybe if you try with gksudo?

or try

```
/usr/bin/xinit "/usr/bin/sudo -u nico /usr/bin/xbmc --standalone"

```

Since it complains about the lack of a absolute path

---

