---
title: "Bbswitch, Ubuntu 13.04 nvidia geforce 770m w/ optimus"
date: 2013-08-07
forum: Multimedia Software
---

### Post by thejuice152003 on 2013-08-07
Hello all,

I have been having a terrible time with this problem and I can't figure out anything else on my own I have concluded. I have searched the web far and wide for the past few days, probably putting in close to 20 hours of work, but still no luck!! I have a sager np8290 laptop with NVidia geforce GTX 770m (optimus). I'm currently trying to get bumblebee to work with ubuntu 13.04. Through all the mess, and fresh system installs, I have been able to get bumblebee to work I believe, because I can run the optirun glxspheres and it works fine. I can't run bbswitch though. I know the main Nvidia card is running constantly because the computer is getting very hot and the fan keeps revving. 
Running:

```
sudo modprobe bbswitch
```

gives

```
ERROR: could not insert 'bbswitch': No such device
```


```
bumblebeed -vv
```

gives

```
[ 2433.048330] [DEBUG]Found card: 01:00.0 (discrete)
[ 2433.048343] [DEBUG]Found card: 00:02.0 (integrated)
[ 2433.048346] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2433.048534] [INFO]Configured driver: nvidia
[ 2433.048541] [DEBUG]Skipping auto-detection, using configured driver 'nvidia'
[ 2433.048604] [DEBUG]Process /sbin/modprobe started, PID 23369.
[ 2433.048641] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 2433.049564] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 2433.049710] [INFO]Loading driver bbswitch (module bbswitch)
[ 2433.049765] [DEBUG]Process modprobe started, PID 23370.
ERROR: could not insert 'bbswitch': Operation not permitted
[ 2433.050644] [DEBUG]Process with PID 23370 returned code 1
[ 2433.050735] [ERROR]Module bbswitch could not be loaded (timeout?)
[ 2433.050739] [DEBUG]bbswitch is not available, perhaps you need to insmod it?
[ 2433.050742] [INFO]Skipping switcheroo PM method because it is not explicitly selected in the configuration.
[ 2433.050746] [WARN]No switching method available. The dedicated card will always be on.
[ 2433.050749] [DEBUG]Active configuration:
[ 2433.050751] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 2433.050754] [DEBUG] X display: :8
[ 2433.050757] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-325:/usr/lib32/nvidia-325
[ 2433.050760] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 2433.050763] [DEBUG] pidfile: /var/run/bumblebeed.pid
[ 2433.050766] [DEBUG] xorg.conf file: /etc/bumblebee/xorg.conf.nvidia
[ 2433.050768] [DEBUG] xorg.conf.d dir: /etc/bumblebee/xorg.conf.d
[ 2433.050771] [DEBUG] ModulePath: /usr/lib/nvidia-325/xorg,/usr/lib/xorg/modules
[ 2433.050774] [DEBUG] GID name: bumblebee
[ 2433.050777] [DEBUG] Power method: auto
[ 2433.050780] [DEBUG] Stop X on exit: 1
[ 2433.050783] [DEBUG] Driver: nvidia
[ 2433.050785] [DEBUG] Driver module: nvidia-325
[ 2433.050788] [DEBUG] Card shutdown state: 1
[ 2433.050844] [DEBUG]Process /sbin/modprobe started, PID 23371.
[ 2433.050886] [DEBUG]Hiding stderr for execution of /sbin/modprobe
[ 2433.051741] [DEBUG]SIGCHILD received, but wait failed with No child processes
[ 2433.051748] [DEBUG]Configuration test passed.
[ 2433.051766] [ERROR]Cannot open or write pidfile /var/run/bumblebeed.pid.
```

Alse,
```
dmesg | grep bbswitch
```

gives

```
[    2.604556] bbswitch: module verification failed: signature and/or required key missing - tainting kernel
[    2.606299] bbswitch: version 0.7
[    2.606303] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.606307] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.606309] bbswitch: No discrete VGA device found
[    2.620803] bbswitch: version 0.7
[    2.620809] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.620812] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.620814] bbswitch: No discrete VGA device found
[    2.632556] bbswitch: version 0.7
[    2.632562] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.632566] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.632569] bbswitch: No discrete VGA device found
[    2.643909] bbswitch: version 0.7
[    2.643914] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.643918] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.643920] bbswitch: No discrete VGA device found
[    2.652674] bbswitch: version 0.7
[    2.652678] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.652682] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.652683] bbswitch: No discrete VGA device found
[    2.680709] bbswitch: version 0.7
[    2.680714] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.680717] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.680719] bbswitch: No discrete VGA device found
[    2.691707] bbswitch: version 0.7
[    2.691711] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.691713] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.691715] bbswitch: No discrete VGA device found
[    2.700902] bbswitch: version 0.7
[    2.700907] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.700910] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.700912] bbswitch: No discrete VGA device found
[    2.711751] bbswitch: version 0.7
[    2.711755] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.711758] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.711760] bbswitch: No discrete VGA device found
[    2.724398] bbswitch: version 0.7
[    2.724403] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.724429] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.724433] bbswitch: No discrete VGA device found
[    2.752170] bbswitch: version 0.7
[    2.752176] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    2.752179] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[    2.752181] bbswitch: No discrete VGA device found
[ 1369.306337] bbswitch: version 0.7
[ 1369.306343] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[ 1369.306349] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[ 1369.306352] bbswitch: No discrete VGA device found
[ 2356.234401] bbswitch: version 0.7
[ 2356.234406] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[ 2356.234409] bbswitch: cannot find ACPI handle for VGA device 0000:01:00.0
[ 2356.234412] bbswitch: No discrete VGA device found
```


I am running the updated kernel now 

```
uname -r
```

```
3.9.4-030904-generic
```

I have no other idea why I can't get bbswitch to run...I would like to turn off the Nvidia card to prevent it from getting so hot!


Any ideas, or links to other solutions would be appreciated. I have tried everything I can think of.

If you need anything else please let me know.

---

### Post by JYzeeeJ on 2013-09-26
Did you manage to fix your problem? Did you try updating to 13.10? I was looking at getting a laptop with a 770.

---

### Post by thejuice152003 on 2013-09-26
I never did get it to work, so I just use 12.04 in 2D mode now. Works fine for me. Maybe eventually I will try upgrading to 13.10 and see if it works out. Sorry I can't be of more help.

---

