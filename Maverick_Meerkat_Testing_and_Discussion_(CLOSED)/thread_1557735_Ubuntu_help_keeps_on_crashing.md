---
title: "Ubuntu help keeps on crashing"
date: 2010-08-21
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-08-21
I had issue with Gnome help windows - yelp - showing squares and numbers for quite a while and for that a ticket went upstream to Gnome. But now I can not even get help to start. Anyone the same issues? Where can I find error logs on the crashing? Dmesg shows nothing

---

### Post by Stoneface on 2010-08-21
Found one bug report that seems similar: [https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/580206](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/580206) Checking it now.

---

### Post by SevenMachines on 2010-08-21
You mean something like this?....

---

### Post by Stoneface on 2010-08-21
> **SevenMachines said:**
> You mean something like this?.... The title issue - showing cubes with numbers - has been put upstream now: [https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/605577](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/605577) . But now I cannot even OPEN Yelp / Help. It simply shuts down...

---

### Post by SevenMachines on 2010-08-21
what does it say when you run it from the command line?

---

### Post by Stoneface on 2010-08-21
Here you go:
```

me@ubuntu:~$ yelp
Could not initialize gecko!
```

is it related to Firefox? I do run 3.6 and I run 4.0 Beta as well..

---

### Post by SevenMachines on 2010-08-21
hmm, sounds like a xulrunner problem maybe. make sure your repositories are up-to-date and try
$ sudo apt-get install --reinstall xulrunner-1.9.2
$ sudo apt-get install --reinstall yelp

Is apport turned on so it catches the crash (if it does!?)
$ sudo service apport start force_start=1
$ yelp

---

### Post by SevenMachines on 2010-08-21
> **Stoneface said:**
> is it related to Firefox? I do run 3.6 and I run 4.0 Beta as well..
Sorry I should really pay more attention :) yes, xulrunner is part of firefox, depending on how you've got firefox 4 installed that could well be the problem

---

### Post by Stoneface on 2010-08-21
Here is the result:
```
me@ubuntu:~$ sudo apt-get install --reinstall xulrunner-1.9.2
[sudo] password for jasper: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/9,352kB of archives.
After this operation, 0B of additional disk space will be used.
(Reading database ... 410217 files and directories currently installed.)
Preparing to replace xulrunner-1.9.2 1.9.2.8+build1+nobinonly-0ubuntu1 (using .../xulrunner-1.9.2_1.9.2.8+build1+nobinonly-0ubuntu1_i386.deb) ...
update-alternatives: using /usr/bin/xulrunner-2.0 to provide /usr/bin/xulrunner (xulrunner) in auto mode.
Unpacking replacement xulrunner-1.9.2 ...
Setting up xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
N: Ignoring file 'silverwave-one-daily-a-month-1-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'n-muench-firefox-daily-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ddebs.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'silverwave-one-daily-a-month-1-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'n-muench-firefox-daily-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ddebs.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
me@ubuntu:~$ sudo apt-get install --reinstall yelp
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 375kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main yelp i386 2.30.1-0ubuntu1 [375kB]
Fetched 375kB in 6s (61.0kB/s)                                                                                                                                                  
(Reading database ... 410217 files and directories currently installed.)
Preparing to replace yelp 2.30.1-0ubuntu1 (using .../yelp_2.30.1-0ubuntu1_i386.deb) ...
Unpacking replacement yelp ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for python-support ...
Setting up yelp (2.30.1-0ubuntu1) ...
N: Ignoring file 'silverwave-one-daily-a-month-1-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'n-muench-firefox-daily-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ddebs.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'silverwave-one-daily-a-month-1-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'n-muench-firefox-daily-maverick.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ddebs.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
me@ubuntu:~$ sudo service apport start force_start=1
start: Job is already running: apport
me@ubuntu:~$ yelp
Could not initialize gecko!
```

Still a Gecko warning..

P.S. Last update I did an hour or so ago..

---

### Post by SevenMachines on 2010-08-21
I imagine its something to do with the newer xulrunner version with firefox 4, xulrunner versions dont seem to be very inerchangeable

---

### Post by Stoneface on 2010-08-21
@ SevenMachines Thanks for all your help so far. Really appreciated! Removed Firefox 4.0 and the ppas. Doing a 17 MB update now and will try Yelp again after the update.

---

### Post by Stoneface on 2010-08-21
Nope, crashed again :-(

```
me@ubuntu:~$ yelp
Could not initialize gecko!
```

Reading: [http://linuxgator.org/forums/viewtopic.php?f=23&t=1064](http://linuxgator.org/forums/viewtopic.php?f=23&t=1064) ..

---

### Post by Stoneface on 2010-08-21
Read [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.2/+bug/568876](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9.2/+bug/568876) as well . Problem seems to related to /etc/ gre.d:
```
me@ubuntu:/etc/gre.d$ ls
1.9.2.8.system.conf  2.0b4pre.system.conf
me@ubuntu:/etc/gre.d$ cat 2.0b4pre.system.conf
[2.0b4pre]
GRE_PATH=/usr/lib/xulrunner-2.0b4pre
xulrunner=true
abi=x86-gcc3
me@ubuntu:/etc/gre.d$
me@ubuntu:/etc/gre.d$ cat 1.9.2.8.system.conf
[1.9.2.8]
GRE_PATH=/usr/lib/xulrunner-1.9.2.8
xulrunner=true

```

---

### Post by Stoneface on 2010-08-21
I did ```
me@ubuntu:/etc/gre.d$ sudo mv 2.0b4pre.system.conf 2.0b4pre.system.conf.bak
me@ubuntu:/etc/gre.d$ ls
1.9.2.8.system.conf  2.0b4pre.system.conf.bak

```

and yelp started up even though there were errors:
```
me@ubuntu:/etc/gre.d$ yelp

(yelp:2144): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:2144): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:2144): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:2144): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

(yelp:2144): Gtk-CRITICAL **: IA__gtk_tool_button_new: assertion `icon_widget == NULL || GTK_IS_MISC (icon_widget)' failed

(yelp:2144): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(yelp:2144): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(yelp:2144): Gtk-CRITICAL **: IA__gtk_toolbar_insert: assertion `GTK_IS_TOOL_ITEM (item)' failed

```

---

