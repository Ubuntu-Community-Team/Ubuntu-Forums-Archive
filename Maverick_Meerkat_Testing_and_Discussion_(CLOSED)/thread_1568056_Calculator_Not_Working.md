---
title: "Calculator Not Working"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by VinDSL on 2010-09-04
Only have a minute.  This will be a quick one.

My calculator quit working today, or yesterday.  Actually...

I don't know exactly when it quit working, so let's say recently.

I tried to open it from CLI, so I could see the error:

```
vindsl@Zuul:~$ gcalctool

GLib-GIO-ERROR **: Settings schema 'org.gnome.gcalctool' is not installed

aborting...
Trace/breakpoint trap (core dumped)

vindsl@Zuul:~$ 

```

Anyone else having this problem?!?!?

I'll dog it when I get home later...

---

### Post by NightwishFan on 2010-09-04
I do not have this issue. I would purge and reinstall the package.

---

### Post by ktp on 2010-09-04
> **VinDSL said:**
> Only have a minute.  This will be a quick one.

My calculator quit working today, or yesterday.  Actually...

I don't know exactly when it quit working, so let's say recently.

I tried to open it from CLI, so I could see the error:

```
vindsl@Zuul:~$ gcalctool

GLib-GIO-ERROR **: Settings schema 'org.gnome.gcalctool' is not installed

aborting...
Trace/breakpoint trap (core dumped)

vindsl@Zuul:~$ 

```

Anyone else having this problem?!?!?

I'll dog it when I get home later...

could it be that you are running into this bug, which should be fixed:

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/602175](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/602175)

---

### Post by 23dornot23d on 2010-09-04
I get an error in the terminal .... but it runs and seems to work ok

[IMG]http://i52.tinypic.com/ogc1me.jpg[/IMG]

---

### Post by KdotJ on 2010-09-04
No problem here :???:

---

### Post by jeight on 2010-09-04
sudo apt-get remove --purge gcalctool[FONT=monospace]
sudo apt-get install gcalctool
[/FONT]

---

### Post by VinDSL on 2010-09-05
I'm home now.

Reinstalling via Synaptic did nothing.  So, I purged it...

```
vindsl@Zuul:~$ sudo apt-get remove --purge gcalctool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gcalctool*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1,442kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 151125 files and directories currently installed.)
Removing gcalctool ...
Purging configuration files for gcalctool ...
Processing triggers for menu ...
Processing triggers for libglib2.0-0 ...
No such schema `org.gnome.Empathy.conversation' specified in override file `/usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override'
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
vindsl@Zuul:~$ 

```

Then, a fresh install...

```
vindsl@Zuul:~$ sudo apt-get install gcalctool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  gcalctool
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/197kB of archives.
After this operation, 1,442kB of additional disk space will be used.
Selecting previously deselected package gcalctool.
(Reading database ... 150495 files and directories currently installed.)
Unpacking gcalctool (from .../gcalctool_5.31.91-0ubuntu1_i386.deb) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
No such schema `org.gnome.Empathy.conversation' specified in override file `/usr/share/glib-2.0/schemas/ubuntu-artwork.gschema.override'
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up gcalctool (5.31.91-0ubuntu1) ...
Processing triggers for menu ...
vindsl@Zuul:~$ 

```

No soap!

LoL!  ^%@! Empathy!  Gawd, I had that proggie!

Oh, well.  Plan C...

---

### Post by VinDSL on 2010-09-05
> **ktp said:**
> could it be that you are running into this bug, which should be fixed:

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/602175](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/602175)**[COLOR="Red"]Bingo!!![/COLOR]**  You're the winner, *ktp*!

Here's the rub...

I h-a-t-e Empathy!!!  I try it for a few minutes (thinking it will be better) every time I install a new Ubu distro, then I purge it (when I find out it still sucks balls) and install Pidgin. 

In its present state (according to the comments in the bug report) if you want to update/upgrade/install gcalctool in Maverick, Empathy MUST be installed.

The fix for me was:

[INDENT]Install Empathy :tongue:

Install gcalctool

Purge Empathy  =D>[/INDENT]

Looks like the calc will work until the next gcalctool update...

Thanks!  ;)

---

### Post by ktp on 2010-09-05
> **VinDSL said:**
> **[COLOR="Red"]Bingo!!![/COLOR]**  You're the winner, *ktp*!

Here's the rub...

I h-a-t-e Empathy!!!  I try it for a few minutes (thinking it will be better) every time I install a new Ubu distro, then I purge it (when I find out it still sucks balls) and install Pidgin. 

In its present state (according to the comments in the bug report) if you want to update/upgrade/install gcalctool in Maverick, Empathy MUST be installed.

The fix for me was:

[INDENT]Install Empathy :tongue:

Install gcalctool

Purge Empathy  =D>[/INDENT]

Looks like the calc will work until the next gcalctool update...

Thanks!  ;)

Nice...I guess we are even since I stole your wallpaper. =)

---

### Post by VinDSL on 2010-09-05
I added a comment to the bug report: [Comment 10 for bug 602175]("https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/602175/comments/10")

Basically, I just restated what I said here.

I doubt that the devs read every thread in these forums...  ;)

---

