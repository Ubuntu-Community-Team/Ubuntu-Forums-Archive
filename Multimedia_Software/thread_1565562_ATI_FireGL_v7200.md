---
title: "ATI FireGL v7200"
date: 2010-09-01
forum: Multimedia Software
---

### Post by vaina on 2010-09-01
Hi everybody.
I had an **NVIDIA Quadro FX 550** on my little workstation (DELL Precision 490) and I had some (graphic?) problems with my software at work. I also installed NVIDIA proprietary drivers ([COLOR=Blue]nvidia-current[/COLOR]) but troubles still remained. Then I changed the graphic card and installed an **ATI FireGL 7200** and Jockey (on Ubuntu 10.04) seems to not be able to find proprietary drivers. So I just downloaded [COLOR=blue]xserver-xorg-video-radeonhd[COLOR=Black] package, but I still have problems. If I check with *glxinfo* I obtain:

[/COLOR][/COLOR]```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
3 GLXFBConfigs:
   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Segmentation fault
```I also don't find a clear procedure (I'm a newbie) for a manual installation of ATI drivers, can anyone help me?

---

### Post by dino99 on 2010-09-01
as actual kernel deal directly with X, there is often trouble when installing the driver from nvidia/ati, so better to install the package from synaptic.

first remove xorg.conf:

sudo rm -f /etc/X11/xorg.conf

then add this ppa to your synaptic repo tab:

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

and remove/purge (right click) all the nvidia/ati packages installed

update and upgrade, the system will install the necessary packages

reboot and check driver activation: system admin hardware driver

---

### Post by vaina on 2010-09-01
Thanks for your suggestions. I followed your instructions: removed *xorg.conf*, added the PPA, definitively removed all ATI/NVIDIA packages by the package manager, updated and upgraded the system. But Jockey still doesn't find any proprietary driver for ATI in the system or internet. Did I make a wrong step?

---

### Post by Mark Phelps on 2010-09-02
Your ATI card is one of the now-termed "legacy" cards -- for which there is no current proprietary ATI driver.  The last driver for it worked with Ubuntu 8.10; it won't work with Ubuntu versions newer than that.

The open-source drivers, which you already have installed, are the only drivers now available.

---

### Post by vaina on 2010-09-03
Thanks for your detailed reply, Mark. So I have two questions.

1. Is an updated proprietary driver (Ubuntu 10.04) for **ATI FireGL 7200** expected in the future? I guess the answer is 'no', I think it's not a question of time.

2. Is a current proprietary driver for **NVIDIA Quadro FX 550** available? If so, where can I find the installation procedure?

Thanks for your attention.

---

### Post by Yellow Pasque on 2010-09-03
1. No
2. You install them like you did above (using nvidia-current).

---

### Post by vaina on 2010-09-13
Sorry, if i get back to the thread. I'm really a beginner.
I gave up with the ATI graphic card and its drivers, so I turned back to the **Nvidia Quadro FX 550**. I installed the graphic card, I turn on the pc, *Jokey* didn't find any proprietary driver, so I added the ***ppa:ubuntu-x-swat/x-updates*** and installed [COLOR=Red]nvidia-current dev[/COLOR] package. Then I reboot the system but the monitor resolution is lower than optimal. If I choose *System/Preference/Monitor* I'm suggested to use the productor's tool. If I run *Nvidia X Server Settings* I have the message:

[COLOR=Blue]*You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.*[/COLOR]

What's the problem? If I run *Jockey* now I see *nvidia-current* active (with the annoying bug '*This driver is active but not in use*').

---

### Post by vaina on 2010-09-13
I fixed the problem by uninstalling [COLOR=Red]nvidia-current dev[/COLOR] and just installing the package [COLOR=Red]nvidia-current[/COLOR].
I'd like to look inside a question about Nvidia drivers. I read the page [BinaryDriverHowto Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") and I don't understand all.

1. Have I to remove *Nouveau* with ```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```2. I'd like to resolve the bug about [COLOR=Blue]'The driver is active but not in use'[COLOR=Black], maybe it can affect the right working of the Nvidia driver[/COLOR][/COLOR]. If I'm correct, I have to write```
sudo apt-get install nvidia-current
``` and then something like ```
sudo update-alternatives --config gl_conf
```I don't understand the sentence [COLOR=Blue]'select the alternative that matches the driver that you have installed (e.g. /usr/lib/nvidia-current/ld.so.conf for nvidia-current)'[/COLOR], so I'm not sure if I have to substitute *gl_conf* with another file.

Thanks for your help and patience.

---

