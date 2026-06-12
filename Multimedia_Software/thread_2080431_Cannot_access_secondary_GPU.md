---
title: "Cannot access secondary GPU"
date: 2012-11-04
forum: Multimedia Software
---

### Post by PJOS13 on 2012-11-04
Hello, I just bought a new Dell XPS 14 Ultrabook which comes with a NVIDIA GeForce GT 630M. So, following some indications that I found in the documentation available online I add the bumblebee ppa and installed bumblebee and nvidia-bumblebee.

But when I tried to use the nvidia card to run something i got this error:
```

optirun firefox
[   76.145099] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) No devices detected.

[   76.145199] [ERROR]Aborting because fallback start is disabled.

```

Here are some of the configuration files:
[LIST]
[*]/etc/bumblebee/bumblebee.conf
```

# Configuration file for Bumblebee. Values should **not** be put between quotes

## Server options. Any change made in this section will need a server restart
# to take effect.
[bumblebeed]
# The secondary Xorg server DISPLAY number
VirtualDisplay=:8
# Should the unused Xorg server be kept running? Set this to true if waiting
# for X to be ready is too long and don't need power management at all.
KeepUnusedXServer=false
# The name of the Bumbleblee server group name (GID name)
ServerGroup=bumblebee
# Card power state at exit. Set to false if the card shoud be ON when Bumblebee
# server exits.
TurnCardOffAtExit=false
# The default behavior of '-f' option on optirun. If set to "true", '-f' will
# be ignored.
NoEcoModeOverride=false
# The Driver used by Bumblebee server. If this value is not set (or empty),
# auto-detection is performed. The available drivers are nvidia and nouveau
# (See also the driver-specific sections below)
Driver=

## Client options. Will take effect on the next optirun executed.
[optirun]
# The method used for VirtualGL to transport frames between X servers.
# Possible values are proxy, jpeg, rgb, xv and yuv.
VGLTransport=proxy
# Should the program run under optirun even if Bumblebee server or nvidia card
# is not available?
AllowFallbackToIGC=false


# Driver-specific settings are grouped under [driver-NAME]. The sections are
# parsed if the Driver setting in [bumblebeed] is set to NAME (or if auto-
# detection resolves to NAME).
# PMMethod: method to use for saving power by disabling the nvidia card, valid
# values are: auto - automatically detect which PM method to use
#         bbswitch - new in BB 3, recommended if available
#       switcheroo - vga_switcheroo method, use at your own risk
#             none - disable PM completely
# https://github.com/Bumblebee-Project/Bumblebee/wiki/Comparison-of-PM-methods

## Section with nvidia driver specific options, only parsed if Driver=nvidia
[driver-nvidia]
# Module name to load, defaults to Driver if empty or unset
KernelDriver=nvidia
Module=nvidia
PMMethod=auto
# colon-separated path to the nvidia libraries
LibraryPath=/usr/lib/nvidia-current:/usr/lib32/nvidia-current
# comma-separated path of the directory containing nvidia_drv.so and the
# default Xorg modules path
XorgModulePath=/usr/lib/nvidia-current/xorg,/usr/lib/xorg/modules
XorgConfFile=/etc/bumblebee/xorg.conf.nvidia

## Section with nouveau driver specific options, only parsed if Driver=nouveau
[driver-nouveau]
KernelDriver=nouveau
PMMethod=auto
XorgConfFile=/etc/bumblebee/xorg.conf.nouveau

```

[*]/etc/bumblebee/xorg.conf.nvidia 

```

Section "ServerLayout"
    Identifier "Layout0"
    Option "AutoAddDevices" "false"
EndSection

Section "Device"
    Identifier "Device1"
    Driver "nvidia"
    VendorName "NVIDIA Corporation"
    Option "NoLogo" "true"
    Option "UseEDID" "false"
    Option "ConnectedMonitor" "DFP"
EndSection

```

[*]And some additional information
```

ii  bumblebee-nvidia                          3.0.1-3~quantalppa1                       amd64        nVidia Optimus support using the proprietary NVIDIA driver
ii  nvidia-current                            304.51.really.304.43-0ubuntu1             amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
rc  nvidia-current-updates                    304.51-0ubuntu1                           amd64        NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                           304.51-0ubuntu2                           amd64        Tool for configuring the NVIDIA graphics driver

```
I removed the nvidia-current-updates because unity was not able to start with it installed.
[/LIST]

By the way, I'm using the latest version of 64 bit ubuntu (12.10).

Can you help me fixing this error? Is there other information you might need in order to help me?

Thanks in advance.

---

### Post by PJOS13 on 2012-11-04
Is this even supported in ubuntu 12.10 or is it a better idea to install 12.04?

---

### Post by Yellow Pasque on 2012-11-04
I've seen similar complaints of that error with GT6x0 chips on the nvidia linux site: [http://www.nvnews.net/vbulletin/showthread.php?t=184542](http://www.nvnews.net/vbulletin/showthread.php?t=184542)

---

### Post by PJOS13 on 2012-11-04
I set Driver=nvidia in the bumblebee.conf and now I'm getting 
```

[ 2961.831474] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 2961.832689] [INFO]Configured driver: nvidia
[ 2961.832848] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 2961.832909] [DEBUG]Socket closed.
[ 2961.832992] [ERROR]Could not connect to bumblebee daemon - is it running?

```

Any ideas?

---

### Post by PJOS13 on 2012-11-04
Solution founded here:

[http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10]("http://askubuntu.com/questions/202644/how-to-install-nvidia-optimus-driver-on-ubuntu-12-10")

---

### Post by Yellow Pasque on 2012-11-04
So I guess the problem was that linux-headers for your kernel weren't installed?

---

### Post by PJOS13 on 2012-11-04
I think you're right...

---

