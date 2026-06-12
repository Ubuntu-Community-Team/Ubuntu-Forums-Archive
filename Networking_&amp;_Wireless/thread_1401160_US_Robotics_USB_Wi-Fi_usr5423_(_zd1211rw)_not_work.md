---
title: "US Robotics USB Wi-Fi usr5423 ( zd1211rw) not working on 9.10 amd64"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by roby.a on 2010-02-07
Hello everybody,

I've been using this USB Wi-Fi Adapter since 7.10 on my previous box and it always worked fine. I've used it also on a 9.04PPC edition.

Now I've got a new PC (AMD AthlonII x3 435, 4GB RAM) and I've installed Ubuntu 9.10 Amd64 Desktop, and this device won't work.
It doesn't even show on lsusb. Here's my output:

```

roby@roby-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 004 Device 002: ID 046d:092f Logitech, Inc. QuickCam Express Plus
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

All you can see is my mouse and my webcam. The end.

Other commands (iwconfig, ifconfig, sudo lshw -C network) doesn't show anything that has something to do with wireless networking.

I've also tried ndiswrapper, but I cannot manage to get x64 drivers (they comes only with an installer package for Vista64, wich I have not).

That's my kernel version and architecture:

```

roby@roby-desktop:~$ uname -mr
2.6.31-19-generic x86_64

```

Any ideas? I really need a hand...

---

### Post by roby.a on 2010-02-08
I've also tried the following:

1. Installing Open Source drivers from [http://sourceforge.net/projects/zd1211/develop](http://sourceforge.net/projects/zd1211/develop) while blacklisting the original zd1211rw module: it doesn't work
2. Using Vista x64 drivers through ndiswrapper: the driver is loaded correctly, but it says it cannot find any hardware.

Obviously, the key is plugged into a fully-functional USB port and the LED on its body lights up, like if it was functioning...

Have anybody got an idea? Thanks a lot!

---

