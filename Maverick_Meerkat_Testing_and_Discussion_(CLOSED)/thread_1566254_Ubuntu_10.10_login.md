---
title: "Ubuntu 10.10 login"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by su-37 on 2010-09-02
Hey, ive installed 10.10 twice and the following has occurred each time. It installs perfectly but when i go to reboot, the dots show up and then it boots into cli.
Any ideas?

---

### Post by overdrank on 2010-09-02
Moved to Maverick Meerkat Testing and Discussion :)

---

### Post by bennachie on 2010-09-02
It would help us to provide a more useful response if you could let us know what version of 10.10 you are installing, and in what circumstances. For example, is this a clean installation of the A3 version in a dedicated Ubuntu environment, or are you dual-booting with Windows? Are you attempting to replace a working installation of 10.04?

Maverick is only just approaching the status of beta software. It might actually be better from your point of view to revert to the recently released stable version (10.04.1) unless, like many others in this forum, you take a perverse delight in chasing down, reporting, and helping to resolve unlikely bugs.

---

### Post by su-37 on 2010-09-02
I upgraded from Ubuntu 10.04 64 bit to ubuntu 10.10 64 bit desktop. Sorry about posting in the wrong area.
Yeah itd be the perverse delight.

---

### Post by VMC on 2010-09-02
> **su-37 said:**
> Hey, ive installed 10.10 twice and the following has occurred each time. It installs perfectly but when i go to reboot, the dots show up and then it boots into cli.
Any ideas?

I think your in a VT. Does typing "startx" from the cli give you a desktop?

Also typing "tty" from that cli will probably reveal "/dev/tty1"

---

### Post by su-37 on 2010-09-02
startx gives me more text and tty as far as i can tell does nothing. 

One of the highlights is
this server has a video drive rABI version 8.0that this driver does not support.

It then says fatal server error:
no screens found

---

### Post by jpeddicord on 2010-09-02
> **su-37 said:**
> startx gives me more text and tty as far as i can tell does nothing. 

One of the highlights is
this server has a video drive rABI version 8.0that this driver does not support.

It then says fatal server error:
no screens found

You must be using an NVIDIA card:

[http://ubuntuforums.org/showpost.php?p=9702585&postcount=25](http://ubuntuforums.org/showpost.php?p=9702585&postcount=25)

NVIDIA recently released a driver update to support the newer X, so this should go away shortly.

---

### Post by su-37 on 2010-09-02
> **jpeddicord said:**
> You must be using an NVIDIA card:

[http://ubuntuforums.org/showpost.php?p=9702585&postcount=25](http://ubuntuforums.org/showpost.php?p=9702585&postcount=25)

NVIDIA recently released a driver update to support the newer X, so this should go away shortly.

so is there anything i can do? or do i just wait? or just nuke it and reinstall?
Thanks for the responses.

---

### Post by VMC on 2010-09-02
> **su-37 said:**
> so is there anything i can do? or do i just wait? or just nuke it and reinstall?
Thanks for the responses.

I can tell you what I just did and a few others with success. Both Lucid and  Maverick had problems booting. Lucid failed to start GDM, Maverick just failed with using the new X server 1.9. 

Followed this thread to [_install nVidia drivers_]("http://ubuntuforums.org/showthread.php?t=1467074"). The install also applies to Maverick.

first go to [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") site and download the drivers.

Do you know what nvidia hardware you have?

---

### Post by jpeddicord on 2010-09-02
> **su-37 said:**
> so is there anything i can do? or do i just wait? or just nuke it and reinstall?
Thanks for the responses.

Do what the link tells you to do:

> Adding ignoreABI to xorg.conf solves this. 

```
Section "ServerFlags"
Option "ignoreABI" "True"
EndSection
```

Edit /etc/x11/xorg.conf as root, add that section, and reboot.

---

### Post by ktp on 2010-09-02
Installing the latest drivers also seems to fix the issue for most.

---

### Post by su-37 on 2010-09-03
> **VMC said:**
> I can tell you what I just did and a few others with success. Both Lucid and  Maverick had problems booting. Lucid failed to start GDM, Maverick just failed with using the new X server 1.9. 

Followed this thread to [_install nVidia drivers_]("http://ubuntuforums.org/showthread.php?t=1467074"). The install also applies to Maverick.

first go to [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") site and download the drivers.

Do you know what nvidia hardware you have?
I think is the Nvidia geforce 9200. Thanks for the info. How do i download it via cli? The rest i think i know how to do via terminal.

---

### Post by IanW on 2010-09-03
> **su-37 said:**
> I think is the Nvidia geforce 9200. Thanks for the info. How do i download it via cli? The rest i think i know how to do via terminal.

To download direct from Nvidia's site use:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86_64/256.53/NVIDIA-Linux-x86_64-256.53.run
```

---

### Post by su-37 on 2010-09-03
> **VMC said:**
> I can tell you what I just did and a few others with success. Both Lucid and  Maverick had problems booting. Lucid failed to start GDM, Maverick just failed with using the new X server 1.9. 

Followed this thread to [_install nVidia drivers_]("http://ubuntuforums.org/showthread.php?t=1467074"). The install also applies to Maverick.

first go to [nVidia]("http://www.nvidia.com/Download/index.aspx?lang=en-us") site and download the drivers.

Do you know what nvidia hardware you have?

I downloaded the driver and i typed in the sudo gedit
it comes up with Gtk-WARNING **: cannot open display:

---

### Post by IanW on 2010-09-03
> **su-37 said:**
> I downloaded the driver and i typed in the sudo gedit
it comes up with Gtk-WARNING **: cannot open display:

Gedit requires an already running desktop.
From the cli, use nano instead.

ie:-
```
sudo nano /etc/modprobe.d/blacklist.conf
```

The shortcuts at the bottom of the screen use ^ to mean "CTRL"
That is, to exit nano use CTRL-X

---

### Post by su-37 on 2010-09-03
I followed that thread to where it says cd to the directory. I entered th wget. how do i cd to it?
Much appreciated for all the help!!!

---

### Post by Sophont on 2010-09-03
```
cd whatever-the-dir-name-is
```

Replace "whatever-the-dir-name-is" with - well - whatever dir you want to **c**hange **d**irectory to.

---

### Post by VMC on 2010-09-03
> **su-37 said:**
> I followed that thread to where it says cd to the directory. I entered th wget. how do i cd to it?
Much appreciated for all the help!!!

From the directory your in, what is the output of ***ls*** command.

---

### Post by Kevin Kent on 2010-09-03
Changing the drivers as per VMC's post worked a treat after I only had a terminal after upgrading from 10.04 to 10.10 Beta.  Thanks

---

### Post by J8Stereo on 2010-09-03
I'm having a similar problem: After boot, I get a terminal login prompt. When I ask gnome to start manually (with a call to gnome-session or gnome3-session), I get: "WARNING **: Cannot open display". This machine doesn't have a video card, so I don't think updating video drivers is the solution for me. Anyone have any ideas on how to fix this problem, or at the very least, get a lesser version of gnome up and running? (P.S. Sorry for the lack of formatting, lynx is fun, but doesn't lend itself to posting.)

---

### Post by cariboo on 2010-09-03
If your system doesn't have a video card, how does it display graphics? :) Try typing startx at the prompt, If it doesn't start, have a look at /var/log/Xorg.0.log, it should tell you what the problem is.

---

### Post by su-37 on 2010-09-03
> **VMC said:**
> From the directory your in, what is the output of ***ls*** command.

i enter the ls command
Desktop libdvdcss2_1.2.9-2medibuntu4_amd64.deb
Documents Music public Templates Ubuntu one Videos
Downloads NVIDIA-Linux-x86_64-256.53.run

---

### Post by J8Stereo on 2010-09-03
My mistake describing my video card. It's onboard video, an nVidia GeForce 6 GPU, and yes, drivers are my problem it seems.The x log file says: Loading /usr/lib/xorg/extra-modules/nvidia_drv.so, dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData, Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so, UnloadModule: "nvidia", Failed to load module "nvidia" (loader failed, 7), No drivers available
So it seems I have to upgrade my drivers, nVidia's site does not play nice with with lynx though, and I'm having trouble getting the proper drivers downloaded, let alone installed. Are there any methods to update my video drivers without visiting nVidia's horrid site using lynx?

---

### Post by VMC on 2010-09-03
> **J8Stereo said:**
> My mistake describing my video card. It's onboard video, an nVidia GeForce 6 GPU, and yes, drivers are my problem it seems.The x log file says: Loading /usr/lib/xorg/extra-modules/nvidia_drv.so, dlopen: /usr/lib/xorg/extra-modules/nvidia_drv.so: undefined symbol: miEmptyData, Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so, UnloadModule: "nvidia", Failed to load module "nvidia" (loader failed, 7), No drivers available
So it seems I have to upgrade my drivers, nVidia's site does not play nice with with lynx though, and I'm having trouble getting the proper drivers downloaded, let alone installed. Are there any methods to update my video drivers without visiting nVidia's horrid site using lynx?
Follow the instructions on this [link]("http://ubuntuforums.org/showthread.php?t=1467074").

---

### Post by VMC on 2010-09-03
> **su-37 said:**
> i enter the ls command
Desktop libdvdcss2_1.2.9-2medibuntu4_amd64.deb
Documents Music public Templates Ubuntu one Videos
Downloads **NVIDIA-Linux-x86_64-256.53.run**
The one in bold above is the one you want to run. You must condition your files first, follow instructions [_here_]("http://ubuntuforums.org/showthread.php?t=1467074").

---

### Post by xebian on 2010-09-03
> **J8Stereo said:**
> <snip>
So it seems I have to upgrade my drivers, nVidia's site does not play nice with with lynx though, and I'm having trouble getting the proper drivers downloaded, let alone installed. Are there any methods to update my video drivers without visiting nVidia's horrid site using lynx?
Firefox, Opera, chrome, take your pick.

---

### Post by jpeddicord on 2010-09-03
> **xebian said:**
> Firefox, Opera, chrome, take your pick.

You can't really use those if you don't have X.

@J8Stereo: The nvidia driver update was pushed to the archives today; an upgrade should pull it in and bring you back to speed. If that doesn't work, you can try w3m as an alternative terminal browser; I find it slightly less unusable than lynx. :P

---

### Post by su-37 on 2010-09-03
i cd to the downloads directory and typ sudo sh then the drivers name. it says it cant open it. ive tried ending with .run .pkg2 .pkg2.run and all end the same. the pc also says the are updates available

---

### Post by ranch hand on 2010-09-03
Most folks have a Live CD or two laying around.  Use one of those.

---

### Post by su-37 on 2010-09-03
> **ranch hand said:**
> Most folks have a Live CD or two laying around.  Use one of those.

to run the driver?

---

### Post by ranch hand on 2010-09-03
To down load it and put it somewhere on your install so you can install it.

---

### Post by su-37 on 2010-09-03
> **VMC said:**
> The one in bold above is the one you want to run. You must condition your files first, follow instructions [_here_]("http://ubuntuforums.org/showthread.php?t=1467074").

I follow those and when i hit enter on the gdm start it says its already ruinning.

---

### Post by IanW on 2010-09-03
> **su-37 said:**
> i cd to the downloads directory and typ sudo sh then the drivers name. it says it cant open it. ive tried ending with .run .pkg2 .pkg2.run and all end the same. the pc also says the are updates available

The repository nvidia-current is now at 256.53, so first try:-
```
sudo apt-get update
sudo apt-get install nvidia-current
```

If that doesn't work for you, then lets go back to the file you downloaded. It sounds like the downloaded file is not executable.
Try this after cd-ing to the place the file is:-

```
sudo chmod +x NVIDIA-Linux-x86_64-256.53.run
```

Then do 

```
sudo sh NVIDIA-Linux-x86_64-256.53.run
```

---

### Post by VMC on 2010-09-03
> **IanW said:**
> The repository nvidia-current is now at 256.53, so first try:-
```
sudo apt-get update
sudo apt-get install nvidia-current
```...] This is great news! 
Makes it so much easier for new or inexperienced users.

---

### Post by su-37 on 2010-09-03
Halleuyah and praise the penguin it worked!!!!
Thanks IanW!!!

---

### Post by VMC on 2010-09-03
Yes they have updated nVida drivers, and it works! Either use jockey or update manager or apt-get update.

```
apt-cache show nvidia-current-modaliases
Package: nvidia-current-modaliases
Priority: optional
Section: admin
Installed-Size: 100
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: nvidia-graphics-drivers
Version: **256.53**-0ubuntu1
```

---

