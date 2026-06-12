---
title: "gconf2 issue"
date: 2010-05-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by dino99 on 2010-05-16
have 2 packages requesting a gconf2 upstream: update-notifier & simple-scan.

picking the "sid" package is ok but with some warnings

---

### Post by jppr on 2010-05-16
+ 1

---

### Post by ratcheer on 2010-05-16
I had the same problem a few days ago. I was instructed to not allow it to do a "partial upgrade". Now, I have three packages in "held back" status, but no problems with gconf2.

Tim

---

### Post by philinux on 2010-05-16
Same here. I did a dist upgrade. Waiting for the new gconf2.

a```
pt-get install update-notifier
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  update-notifier: Depends: gconf2 (>= 2.28.1-2) but 2.28.1-0ubuntu1 is to be installed
E: Broken packages

```

---

### Post by dino99 on 2010-05-16
no bad issue with "sid" gconf2

---

### Post by ranch hand on 2010-05-16
Oh come on guys, this is not earth shaking and will probably be on its way within 24hrs.

Are there any problems scanning with the current setup (I do not have a scanner).

---

### Post by philinux on 2010-05-16
> **ranch hand said:**
> Oh come on guys, this is not earth shaking and will probably be on its way within 24hrs.



Yep sit back and wait for the bugger lo.

---

### Post by Starks on 2010-05-16
> **ranch hand said:**
> Oh come on guys, this is not earth shaking and will probably be on its way within 24hrs.

Well, it's been a week for tomboy.

---

### Post by autocrosser on 2010-05-16
> **Starks said:**
> Well, it's been a week for tomboy.

Well, with gconf touching almost everything Gnome, I'll bet there will be a lot of updates when it finally hits......

---

### Post by ranch hand on 2010-05-16
> **Starks said:**
> Well, it's been a week for tomboy.
This is true.

It is also true that we are testing 10.10.  We are not testing 10.10 with different versions of stuff than it is supposed to run.

Now don't jump my butt.  I know I have done these things too.  I also have at least one install that is not messed with.

I do not have tomboy sitting there on this install, for instance, as it is not installed.  I have never used it and do not want it on here as I have enough clutter as it is.  The other four installs are waiting patiently for it to clear.

---

### Post by ronacc on 2010-05-16
we aren't even to the first daily yet , its hardly the time to panic about a couple of held back packages .

---

### Post by ranch hand on 2010-05-16
> **ronacc said:**
> we aren't even to the first daily yet , its hardly the time to panic about a couple of held back packages .
Oh I don't know.

We could pair off in bunches and scatter out in groups.

---

### Post by mxboy15u on 2010-05-16
Nothing drives me more nuts than just watching those updates sit there...arg!

---

### Post by ronacc on 2010-05-16
> **ranch hand said:**
> Oh I don't know.

We could pair off in bunches and scatter out in groups.

when in worry when in doubt , run in circles scream and shout .

---

### Post by autocrosser on 2010-05-16
> **ronacc said:**
> when in worry when in doubt , run in circles scream and shout .

LOL!!!!:guitar:

I almost fell out of my seat!!! Stop That......:P:P

---

### Post by ubername on 2010-05-17
Gconf2 has landed, fixed up tomboy, simple-scan, update-notifier, ubuntu-desktop (my held back packages)

---

### Post by rexes13 on 2010-05-20
Gconf 2 gives me this error when upgrading ```
Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop]
```

---

### Post by philinux on 2010-05-20
[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/583279](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/583279)

---

### Post by dino99 on 2010-05-20
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/276272](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/276272)

[https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/581188](https://bugs.launchpad.net/ubuntu/+source/gconf/+bug/581188)

---

### Post by philinux on 2010-05-20
> Sebastien Bacher
don't use maverick so early, it's just opened and people were busy at UDS and travelling, starting opening bugs now about what is not installable yet on maverick is creating work rather than being useful.

Interesting. When is the bug season open then?

---

### Post by null_pointer_us on 2010-06-04
Was a fix found, or did everyone just decide to wait a while?

```
$ sudo aptitude purge f-spot

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  f-spot{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 9,806kB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 174296 files and directories currently installed.)
Removing f-spot ...
Purging configuration files for f-spot ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

$ sudo aptitude install f-spot

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  f-spot 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,467kB of archives. After unpacking 9,806kB will be used.
Writing extended state information... Done
Selecting previously deselected package f-spot.
(Reading database ... 173904 files and directories currently installed.)
Unpacking f-spot (from .../f-spot_0.6.2-1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_y)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_y)
Processing triggers for python-support ...
Setting up f-spot (0.6.2-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

$ apt-cache policy f-spot gconf2

f-spot:
  Installed: 0.6.2-1
  Candidate: 0.6.2-1
  Version table:
 *** 0.6.2-1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main Packages
        100 /var/lib/dpkg/status
gconf2:
  Installed: 2.31.3-0ubuntu1
  Candidate: 2.31.3-0ubuntu1
  Version table:
 *** 2.31.3-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ maverick/main Packages
        100 /var/lib/dpkg/status

$ cat /schemas/apps/control-center/cc_actions_list

cat: /schemas/apps/control-center/cc_actions_list: No such file or directory

$ sudo apt-get install --reinstall gnome-control-center

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/413kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 162601 files and directories currently installed.)
Preparing to replace gnome-control-center 1:2.30.1-0ubuntu1 (using .../gnome-control-center_1%3a2.30.1-0ubuntu1_amd64.deb) ...
Unpacking replacement gnome-control-center ...
Processing triggers for man-db ...
Setting up gnome-control-center (1:2.30.1-0ubuntu1) ...

$ cat /schemas/apps/control-center/cc_actions_list

cat: /schemas/apps/control-center/cc_actions_list: No such file or directory

$ sudo aptitude purge f-spot

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  f-spot{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 9,806kB will be freed.
Do you want to continue? [Y/n/?] 
Writing extended state information... Done
(Reading database ... 162600 files and directories currently installed.)
Removing f-spot ...
Purging configuration files for f-spot ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

$ sudo aptitude install f-spot

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following NEW packages will be installed:
  f-spot 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1,467kB of archives. After unpacking 9,806kB will be used.
Writing extended state information... Done
Selecting previously deselected package f-spot.
(Reading database ... 162208 files and directories currently installed.)
Unpacking f-spot (from .../f-spot_0.6.2-1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_y)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_y)
Processing triggers for python-support ...
Setting up f-spot (0.6.2-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

I suppose the easiest thing will be to do a clean install of a fresh image (after the gstreamer0.10-plugins-bad mess is resolved).

---

### Post by dino99 on 2010-06-04
i've not seen side effets anyway

---

