---
title: "Gnome-shell in Natty official repos"
date: 2010-11-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2010-11-26
An interesting change in the behaviour of the package gjs was carried out today in Natty official repos. New gjs package depends on libgjs0b (instead of libgjs0a) and xulrunner-2.0 is needed (instead of xulrunner-1.9.2).
Gnome-shell is still based on old GTK+2 and Gnome-desktop (2) in Natty repos.
These cannot be tested, however, because the build of package gnome-shell failed.

The Gnome-shell in Ricotz PPA is new and it is based on GTK+3 and Gnome-desktop3.
There, however, gjs still depends on libgjs0a and xulrunner-1.9.2 is needed.
BTW. I could not get the newest gjs (20101119) to work today. I will look into that more indepth tomorrow.

---

### Post by Harry33 on 2010-11-27
The newest gjs (0.7.8~git20101119.fd1b6558-0ubuntu1~11.04~ricotz0) in Rico's Staging PPA is really not working. The problem seems to be an incompatible mutter now.

I get the following error message:

(mutter:1638 ): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",
(mutter:1638 ): mutter-WARNING **: Could not load library [/usr/lib/mutter/plugins/libgnome-shell.so (/usr/lib/libgjs.so.0: undefined symbol: JS_RemoveObjectRoot)]

---

### Post by chrisccoulson on 2010-11-27
That's nothing to do with Mutter. It looks more like you are using a version of gjs that was built with Spidermonkey 2.0, but gnome-shell is loading Spidermonkey 1.9.2 instead

Do you have libgjs0a or libgjs0b installed?

---

### Post by Harry33 on 2010-11-27
> **chrisccoulson said:**
> That's nothing to do with Mutter. It looks more like you are using a version of gjs that was built with Spidermonkey 2.0, but gnome-shell is loading Spidermonkey 1.9.2 instead
Do you have libgjs0a or libgjs0b installed?

I am using Rico's PPAs, testing and staging.
The gjs package (gjs + libgjs0a) I was talking about is from staging PPA.
It is a git version 20101119 (0.7.8~git20101119.fd1b6558-0ubuntu1~11.04~ricotz0).

It is very possible that the build itself is faulty, at least Rico has uploaded a new version, which I haven't tested yet.

One thing is sure, there is no such package as libgjs0b in Rico's PPAs.
According to Ubuntu policy this means it has been built with Spidermonkey-1.9.2?

And yes package gnome-shell_2.91.2 depends on xulrunner-1.9.2

---

### Post by Harry33 on 2010-11-28
And now I have tried the Rico's staging PPA with the latest gjs (+ all other latest packages from staging and testing PPA).

I get the following bunch of JS errors:


(mutter:1658): Gtk-WARNING **: Unable to locate theme engine in module_path: "clearlooks",
Window manager warning: Log level 16: Attempting to read the recently used resources file at `/home/harry/.local/share/recently-used.xbel', but the parser failed: Error reading file '/home/harry/.local/share/recently-used.xbel': Is a directory.
    JS ERROR: !!!   Exception was: Error: Unsupported type interface for (out caller-allocates)
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = 'gjs_throw'
    JS ERROR: !!!     stack = 'Error("Unsupported type interface for (out caller-allocates)")@:0
("Unsupported type interface for (out caller-allocates)")@gjs_throw:0
@:0
()@/usr/share/gnome-shell/js/ui/magnifier.js:68
Magnifier()@/usr/share/gnome-shell/js/ui/magnifier.js:51
start()@/usr/share/gnome-shell/js/ui/main.js:129
@<main>:1
'
    JS ERROR: !!!     message = 'Unsupported type interface for (out caller-allocates)'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Unsupported type interface for (out caller-allocates)
harry@AMD64:~$ Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 13 character 78: Could not parse "blend/#000000/gtk:bg[NORMAL]/0.6" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 14 character 80: Could not parse "blend/#000000/gtk:bg[NORMAL]/0.8" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 16 character 82: Could not parse "blend/#ffffff/gtk:bg[NORMAL]/0.4" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 17 character 84: Could not parse "blend/gtk:fg[NORMAL]/gtk:bg[NORMAL]/0.1" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 19 character 88: Could not parse "blend/gtk:text[NORMAL]/gtk:bg[NORMAL]/0.9" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 23 character 88: Could not parse "blend/gtk:text[NORMAL]/gtk:bg[NORMAL]/0.9" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 25 character 87: Could not parse "blend/#000000/gtk:bg[NORMAL]/0.7" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 218 character 76: Could not parse "blend/#000000/gtk:bg[NORMAL]/0.6" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 606 character 77: Could not parse "blend/#000000/gtk:bg[NORMAL]/0.8" as an integer
Window manager warning: Log level 16: GError set over the top of a previous GError or uninitialized memory.
This indicates a bug in someone's code. You must ensure an error is NULL before it's set.
The overwriting error message was: Line 607 character 78: Could not parse "blend/#ffffff/gtk:bg[NORMAL]/0.6" as an integer

---

### Post by Harry33 on 2010-11-29
OK then,
Now the latest gjs in Rico's Staging PPA depends on libgjs0b and thus
xulrunner-2.0-mozjs is also needed.
But, there is no gnome-shell package around to cope with that one.

---

