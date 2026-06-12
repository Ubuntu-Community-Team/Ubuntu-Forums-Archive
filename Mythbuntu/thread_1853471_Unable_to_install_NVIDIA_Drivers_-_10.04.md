---
title: "Unable to install NVIDIA Drivers - 10.04"
date: 2011-10-02
forum: Mythbuntu
---

### Post by crbnrod on 2011-10-02
Installing a new secondary backend (hence using 10.04 so as to avoid updating the rest of the mythboxes) & using nvidia GT430 card stuck into M4A88T-M motherboard.
The restricted drivers manager doesn't give me the option to install the NVIDIA drivers, and if I install them manually through package manager, I just get stuck into low graphics mode upon reboot.
The only think I can think of is the onboard graphics on the mobo are somehow interfering w/the graphics card? 

lspci does show an nvidia VGA controller, but it doesn't show the chipset or anything like that as far as I can tell.

So I guess two questions:

1. How can I make sure the system is detecting the device?
2. How the heck do I get the NVIDIA drivers installed?

Thanks for any suggestions.

---

### Post by nickrout on 2011-10-02
Is there an option in the bios to switch from the onboard to the pci-e graphics adaptor?

Is the nvidia card plugged in properly?

---

### Post by crbnrod on 2011-10-02
Pretty sure the operating system is using the card. the motherboard's onboard graphics is radeon 4250, and the output of 

```
lspci -nn | grep VGA
```

gives me

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0de1] (rev a1)
```

I did try changing some settings in the BIOS (and then changed them back) to see if that affected anything, but no dice. What strikes me as really weird is I'm actually getting video output through the HDMI out on the card, I just can't adjust the res/overscan/etc.

---

### Post by nickrout on 2011-10-02
> **crbnrod said:**
> Pretty sure the operating system is using the card. the motherboard's onboard graphics is radeon 4250, and the output of 

```
lspci -nn | grep VGA
```

gives me

```
01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:0de1] (rev a1)
```

I did try changing some settings in the BIOS (and then changed them back) to see if that affected anything, but no dice. What strikes me as really weird is I'm actually getting video output through the HDMI out on the card, I just can't adjust the res/overscan/etc.

Sorry I misread your first post I thought you said lspci DOESN'T show the card, my bad.

The logs for X are in /var/log/Xorg.0.log. They will tell you which driver is being used.

It may be that your TV/monitor is not giving good edid info on what resolutions it supports.

It may also be that the version of the nvidia drivers in 10.04 does not support the 430, which is a relatively recent card. What version do you have? ```
dpkg -l nvidia*
``` should tell you.

---

### Post by crbnrod on 2011-10-02
I also do not appear to have an xorg.conf file in my /etc/X11 directory.

---

### Post by crbnrod on 2011-10-02
> **nickrout said:**
> It may also be that the version of the nvidia drivers in 10.04 does not support the 430, which is a relatively recent card. What version do you have? ```
dpkg -l nvidia*
``` should tell you.

```

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name               Version            Description
+++-==================-==================-====================================================
ii  nvidia-173-modalia 173.14.22-0ubuntu1 Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modalias 96.43.17-0ubuntu1  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common      0.2.23             Find obsolete NVIDIA drivers
rc  nvidia-current     195.36.24-0ubuntu1 NVIDIA binary Xorg driver, kernel module and VDPAU l
ii  nvidia-current-mod 195.36.24-0ubuntu1 Modaliases for the NVIDIA binary X.Org driver
un  nvidia-glx-ia32    <none>             (no description available)
ii  nvidia-kernel-comm 20080825+1ubuntu2  NVIDIA binary kernel module common files
un  nvidia-libvdpau    <none>             (no description available)
un  nvidia-libvdpau-ia <none>             (no description available)
un  nvidia-libvdpau1   <none>             (no description available)
un  nvidia-settings    <none>             (no description available)
un  nvidia-vdpau-drive <none>             (no description available)
un  nvidia-vdpau-drive <none>             (no description available)

```


I'm poking around in the Xorg logs right now...there is an error that says "[drm] failed to open device." I'm also not positive here but it appears it ends up loading the VESA driver? I can post the file if that'd be helpful. Thanks a bunch for your assistance.

---

### Post by nickrout on 2011-10-02
Your card is not supported in nvidia 195.36.24:

[http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/supportedchips.html](http://us.download.nvidia.com/XFree86/Linux-x86/195.36.24/README/supportedchips.html)

There are a number of ppa's that give access to later versions of the nvidia drivers.

---

### Post by crbnrod on 2011-10-03
And we're solved. Thanks for your help. 



For future reference:

Added the following to my software sources list:

```

deb [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu](http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu) lucid main

```Ran update mgr, then opened restricted drivers menu & nvidia driver was in there, awaiting activation.

---

