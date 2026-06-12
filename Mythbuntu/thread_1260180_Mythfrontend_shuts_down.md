---
title: "Mythfrontend shuts down"
date: 2009-09-07
forum: Mythbuntu
---

### Post by korgman on 2009-09-07
When I hit ESC while watching live tv, instead of going back to the menu, myth frontend shuts down and exits to the desktop.  The log shows this when it exits.

```

2009-09-07 10:17:57.330 TVRec(1): Changing from WatchingLiveTV to None
2009-09-07 10:17:57.719 Finished recording Today: channel 2041
2009-09-07 10:17:57.726 MythSocket(21a40c0:-1): writeStringList: Error, socket went unconnected.

```
I was having problems with synaptic upgrades today (I tried updating codecs) and now this is happening.  It must be related somehow.
```

matt@mythbuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ia32-libs
The following NEW packages will be installed:
  ia32-libs
0 upgraded, 1 newly installed, 0 to remove and 71 not upgraded.
48 not fully installed or removed.
Need to get 0B/28.0MB of archives.
After this operation, 128MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 180298 files and directories currently installed.)
Unpacking ia32-libs (from .../ia32-libs_2.7ubuntu6.1_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/ia32-libs_2.7ubuntu6.1_amd64.deb (--unpack):
 trying to overwrite `/usr/lib32/libGL.so.1', which is also in package nvidia-glx-180
Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_2.7ubuntu6.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

