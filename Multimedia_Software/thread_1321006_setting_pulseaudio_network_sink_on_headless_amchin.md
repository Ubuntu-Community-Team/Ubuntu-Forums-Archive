---
title: "setting pulseaudio network sink on headless amchine"
date: 2009-11-09
forum: Multimedia Software
---

### Post by ssam on 2009-11-09
I am trying to set up a headless machine to act as a pulseaudio network sink, to that i can push audio to it over the network. as the machine will have no logged in user pulseaudio will need to run in system mode.

there are a few howtos such as [http://ubuntuforums.org/showpost.php?p=6869726&postcount=5](http://ubuntuforums.org/showpost.php?p=6869726&postcount=5) but they seem not to work in karmic.

the first issue seems to be that the /etc/pulse/system.pa file is a bit out of date and want to load module-hal-detect instead of the new module-udev-detect. if module-hal-detect is not found it just use the static loader instead
```

### Automatically load driver modules depending on the hardware available
.ifexists module-hal-detect.so
load-module module-hal-detect
.else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
.endif

```

so i get 
```

W: main.c: Running in system mode, but --disallow-exit not set!
W: main.c: Running in system mode, but --disallow-module-loading not set!
N: main.c: Running in system mode, forcibly disabling SHM mode!
N: main.c: Running in system mode, forcibly disabling exit idle time!
W: main.c: OK, so you are running PA in system mode. Please note that you most likely shouldn't be doing that.
W: main.c: If you do it nonetheless then it's your own fault if things don't work as expected.
W: main.c: Please read http://pulseaudio.org/wiki/WhatIsWrongWithSystemMode for an explanation why system mode is usually a bad idea.
W: module.c: module-detect is deprecated: Please use module-udev-detect instead of module-detect!
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0"): initialization failed.
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0"): initialization failed.
W: module.c: module-oss is deprecated: Please use module-alsa-card instead of module-oss!
Killed

```

if i change the 'hal's to 'udev' then i get
```

libudev: udev_monitor_enable_receiving: bind failed: Operation not permitted
E: module-udev-detect.c: Failed to enable monitor: Operation not permitted
E: module.c: Failed to load  module "module-udev-detect" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```

looks like pulse does not have get giving the permission to talk to udev. from searching around it sound like when pa is started for a normal user session, the udev permission are acquired from the user through policy kit but not so for system mode.

any ideas how to proceed?

---

### Post by ssam on 2009-11-11
i seem to be getting this sorted.

i had a lower level issue that alsa was not finding my sound card. i am running on a beagleboard, and switching from 2.6.29-58cf2f1-oer44.1 to 2.6.31.5-x5.3 from RobertCNelson fixed that.

now it seems to be loading pa alsa modules happily.

the next issue was getting rid of
```
W: main.c: Failed to acquire org.pulseaudio.Server: org.freedesktop.DBus.Error.AccessDenied: Connection ":1.17" is not allowed to own the service "org.pulseaudio.Server" due to security policies in the configuration file
```
i used the /etc/dbus-1/system.d/pulseaudio.conf from [http://bbs.archlinux.org/viewtopic.php?id=71010](http://bbs.archlinux.org/viewtopic.php?id=71010)

```

<!DOCTYPE busconfig PUBLIC
 "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
 "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
<busconfig>
        <policy user="pulse">
            <allow own="org.pulseaudio.Server"/>
            <allow send_destination="org.pulseaudio.Server"/>
            <allow receive_sender="org.pulseaudio.Server"/>
        </policy>
</busconfig>

```

---

