---
title: "PulseAudio problem"
date: 2009-06-10
forum: Multimedia Software
---

### Post by generalpp10 on 2009-06-10
Hi Actually my sound is ok, but then I want to make sure that I get the latest version of pulseaudio, so I followed part A in this guide [http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900) to get it, it seems ok till I get to step 5, which I got the connection error message: Connection failed: Connection refused, then I tried the Code:
$ pulseaudio & pavucontrol as suggested in the guide, but then I still got the same error message when opening the volume control, the whole log of my terminal sessions are as follow: 

```
admin2@admin2-laptop:~$ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/home/admin2/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory
admin2@admin2-laptop:~$ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
[sudo] password for admin2: 
rm: cannot remove `/home/admin2/.asound*': No such file or directory
rm: cannot remove `/etc/asound.conf': No such file or directory
admin2@admin2-laptop:~$ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libasound2-plugins is already the newest version.
The following packages were automatically installed and are no longer required:
  kdelibs4c2a ttf-kannada-fonts kdelibs-data liblualib50 libavahi-qt3-1
  ttf-telugu-fonts tzdata-java ttf-oriya-fonts liblua50 ttf-bengali-fonts
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0 paman paprefs
  pavucontrol pavumeter pulseaudio-module-zeroconf
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libgconfmm-2.6-1c2 libglademm-2.4-1c2a libpulse-mainloop-glib0
  libsdl1.2debian-pulseaudio padevchooser paman paprefs pavucontrol pavumeter
  pulseaudio-module-zeroconf
0 upgraded, 10 newly installed, 1 to remove and 14 not upgraded.
Need to get 555kB of archives.
After this operation, 2040kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://hk.archive.ubuntu.com jaunty/main libgconfmm-2.6-1c2 2.24.0-0ubuntu1 [31.1kB]
Get:2 http://hk.archive.ubuntu.com jaunty/main libglademm-2.4-1c2a 2.6.7-1 [21.4kB]
Get:3 http://hk.archive.ubuntu.com jaunty/main libpulse-mainloop-glib0 1:0.9.14-0ubuntu20 [30.9kB]
Get:4 http://hk.archive.ubuntu.com jaunty/universe pavumeter 0.9.3-1ubuntu1 [29.2kB]
Get:5 http://hk.archive.ubuntu.com jaunty/universe pavucontrol 0.9.7-1ubuntu3 [66.0kB]
Get:6 http://hk.archive.ubuntu.com jaunty/universe paman 0.9.4-1ubuntu2 [92.2kB]
Get:7 http://hk.archive.ubuntu.com jaunty/main pulseaudio-module-zeroconf 1:0.9.14-0ubuntu20 [18.4kB]
Get:8 http://hk.archive.ubuntu.com jaunty/universe paprefs 0.9.7-0ubuntu1 [35.2kB]
Get:9 http://hk.archive.ubuntu.com jaunty/universe padevchooser 0.9.3-2ubuntu4 [20.2kB]
Get:10 http://hk.archive.ubuntu.com jaunty/universe libsdl1.2debian-pulseaudio 1.2.13-4ubuntu3 [210kB]
Fetched 555kB in 1min 27s (6307B/s)                                            
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-4ubuntu3) | libsdl1.2debian-all (= 1.2.13-4ubuntu3) | libsdl1.2debian-esd (= 1.2.13-4ubuntu3) | libsdl1.2debian-oss (= 1.2.13-4ubuntu3) | libsdl1.2debian-nas (= 1.2.13-4ubuntu3) | libsdl1.2debian-pulseaudio (= 1.2.13-4ubuntu3); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 113511 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libgconfmm-2.6-1c2.
(Reading database ... 113503 files and directories currently installed.)
Unpacking libgconfmm-2.6-1c2 (from .../libgconfmm-2.6-1c2_2.24.0-0ubuntu1_i386.deb) ...
Selecting previously deselected package libglademm-2.4-1c2a.
Unpacking libglademm-2.4-1c2a (from .../libglademm-2.4-1c2a_2.6.7-1_i386.deb) ...
Selecting previously deselected package libpulse-mainloop-glib0.
Unpacking libpulse-mainloop-glib0 (from .../libpulse-mainloop-glib0_1%3a0.9.14-0ubuntu20_i386.deb) ...
Selecting previously deselected package pavumeter.
Unpacking pavumeter (from .../pavumeter_0.9.3-1ubuntu1_i386.deb) ...
Selecting previously deselected package pavucontrol.
Unpacking pavucontrol (from .../pavucontrol_0.9.7-1ubuntu3_i386.deb) ...
Selecting previously deselected package paman.
Unpacking paman (from .../paman_0.9.4-1ubuntu2_i386.deb) ...
Selecting previously deselected package pulseaudio-module-zeroconf.
Unpacking pulseaudio-module-zeroconf (from .../pulseaudio-module-zeroconf_1%3a0.9.14-0ubuntu20_i386.deb) ...
Selecting previously deselected package paprefs.
Unpacking paprefs (from .../paprefs_0.9.7-0ubuntu1_i386.deb) ...
Selecting previously deselected package padevchooser.
Unpacking padevchooser (from .../padevchooser_0.9.3-2ubuntu4_i386.deb) ...
Selecting previously deselected package libsdl1.2debian-pulseaudio.
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-4ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up libgconfmm-2.6-1c2 (2.24.0-0ubuntu1) ...

Setting up libglademm-2.4-1c2a (2.6.7-1) ...

Setting up libpulse-mainloop-glib0 (1:0.9.14-0ubuntu20) ...

Setting up pavumeter (0.9.3-1ubuntu1) ...

Setting up pavucontrol (0.9.7-1ubuntu3) ...

Setting up paman (0.9.4-1ubuntu2) ...

Setting up pulseaudio-module-zeroconf (1:0.9.14-0ubuntu20) ...
Setting up paprefs (0.9.7-0ubuntu1) ...

Setting up padevchooser (0.9.3-2ubuntu4) ...

Setting up libsdl1.2debian-pulseaudio (1.2.13-4ubuntu3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
admin2@admin2-laptop:~$ sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libflashsupport is not installed, so not removed
Package flashplugin-nonfree-extrasound is not installed, so not removed
The following packages were automatically installed and are no longer required:
  kdelibs4c2a ttf-kannada-fonts kdelibs-data liblualib50 libavahi-qt3-1
  ttf-telugu-fonts tzdata-java ttf-oriya-fonts liblua50 ttf-bengali-fonts
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
admin2@admin2-laptop:~$ pulseaudio & pavucontrol
[1] 6093
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:6094): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(pavucontrol:6094): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio
admin2@admin2-laptop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
admin2@admin2-laptop:~$ pulseaudio & pavucontrol
[1] 6343
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
E: socket-server.c: bind(): Address already in use
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

(pavucontrol:6344): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(pavucontrol:6344): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed
[1]+  Exit 1                  pulseaudio


```

Can anyone help? Thanks a lot.

---

### Post by markbuntu on 2009-06-11
In System/Adminstration/Users and Groups make sure that your users and root are members of the following groups

pulse
pulse-access
pulse-rt

---

### Post by generalpp10 on 2009-06-11
Solved, thank you. :)

---

### Post by bootdoc on 2009-09-07
I have no sound and i edited groups to include my user account.  now what?  I gave up pulse for esound a couple weeks ago and reinstalled pulse to help someone else on the forum.  Now I can't get pulse working again.  It worked for one session after changing group permissions.

---

### Post by Steve H on 2010-01-23
> **markbuntu said:**
> In System/Adminstration/Users and Groups make sure that your users and root are members of the following groups

pulse
pulse-access
pulse-rt

You're a life saver!!

ADDITION: Seemed to work for a bit and now it's back at square one, no sound output. I didn't see the pulse-rt group....could that be a problem? root and my account are still members of the relevant groups but now no sound anymore!!

---

### Post by papahonk on 2010-01-23
had same problem. Thank you very much  for the help.

---

