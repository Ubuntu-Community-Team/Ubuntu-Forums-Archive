---
title: "Slow frame rate"
date: 2012-03-12
forum: Multimedia Software
---

### Post by jekylhyde on 2012-03-12
Hi
why i have a slow frame rate and/or some frames get skipped when watching videos?
in the same pc with windows its smooth :confused:
thanks

---

### Post by papibe on 2012-03-12
Hard to say without more information.

What media player are you using?
What is your graphic cards?

Regards.

---

### Post by jekylhyde on 2012-03-12
> **papibe said:**
> Hard to say without more information.

What media player are you using?
What is your graphic cards?

Regards.

what does it matter? :) 
i said that with the same pc with windows its smooth...

i have dell inspiron 1520
128Mb nVidia
1Gb RAM
core2Duo

---

### Post by papibe on 2012-03-12
I'm going to assume you are trying to see an HD video (since your machine is fast enough for reproducing SD).

In order to play it smoothly you need to install the Nvidia proprietary driver and the vdpau library.

Then for the player, depending on your Ubuntu version, you would need to use VLC or SMplayer.

I would gladly give you more directions if you are kind enough to post the result of these commands:
```
lsb_release -a

lspci | grep -i vga

apt-cache policy nvidia-settings

apt-cache policy libvdpau
```
Regards.

---

### Post by jekylhyde on 2012-03-12
> **papibe said:**
> I'm going to assume you are trying to see an HD video (since your machine is fast enough for reproducing SD).

In order to play it smoothly you need to install the Nvidia proprietary driver and the vdpau library.

Then for the player, depending on your Ubuntu version, you would need to use VLC or SMplayer.

I would gladly give you more directions if you are kind enough to post the result of these commands:
```
lsb_release -a

lspci | grep -i vga

apt-cache policy nvidia-settings

apt-cache policy libvdpau
```
Regards.


```
ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

```


```
ubuntu@ubuntu:~$ lspci | grep -i vga
01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M GS] (rev a1)

```

```
ubuntu@ubuntu:~$ apt-cache policy nvidia-settings
nvidia-settings:
  Installed: (none)
  Candidate: 280.13-0ubuntu2
  Version table:
     280.13-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/main i386 Packages

```



```
ubuntu@ubuntu:~$ apt-cache policy libvdpau
N: Unable to locate package libvdpau

```



thanks
could you explain these commands & outputs too?

---

### Post by papibe on 2012-03-12
Sure.
[LIST]
[*]To get your Ubuntu version: lsb_release -a
[*]To get your exact card: lspci | grep -i vga
[*]To see if you have installed the Nvidia driver:apt-cache policy nvidia-settings
[*]To see if you've installed the acceleration drivers: apt-cache policy libvdpau1
[/LIST]
First, you need to install the Nvidia proprietary driver: go to additional drivers and install the recommended driver. You may need to restart after that.

Then, tou have you install the video acceleration libraries:
```
sudo apt-get install libvdpau1
```
Then install SMPlayer:
```
sudo apt-get install smplayer
```
Then configure SMplayer to use vdpau by going:
```
SMplayer -> Options -> Preferences -> General -> Video
```
There, set the 'Output driver' to:
```
vdpau
```
finally restart SMplayer, and test some movies.

Hope it helps, and tell us how it goes.
Regards.

---

### Post by jekylhyde on 2012-03-13
> **papibe said:**
> Sure.
[LIST]
[*]To get your Ubuntu version: lsb_release -a
[*]To get your exact card: lspci | grep -i vga
[*]To see if you have installed the Nvidia driver:apt-cache policy nvidia-settings
[*]To see if you've installed the acceleration drivers: apt-cache policy libvdpau1
[/LIST]
First, you need to install the Nvidia proprietary driver: go to additional drivers and install the recommended driver. You may need to restart after that.

Then, tou have you install the video acceleration libraries:
```
sudo apt-get install libvdpau1
```
Then install SMPlayer:
```
sudo apt-get install smplayer
```
Then configure SMplayer to use vdpau by going:
```
SMplayer -> Options -> Preferences -> General -> Video
```
There, set the 'Output driver' to:
```
vdpau
```
finally restart SMplayer, and test some movies.

Hope it helps, and tell us how it goes.
Regards.

i installed xubuntu now
i'm in "additional drivers" (its under the main menu > settings)
i dont see any nvidia there

---

### Post by papibe on 2012-03-13
You can also install the driver from the terminal like this
```
sudo apt-get install nvidia-current
```
Regards.

---

### Post by jekylhyde on 2012-03-13
> **papibe said:**
> You can also install the driver from the terminal like this
```
sudo apt-get install nvidia-current
```
Regards.

```
ubuntu@ubuntu:~$ sudo apt-get install nvidia-current
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot nvidia-settings patch python-central screen-resolution-extra
Suggested packages:
  diffutils-doc
The following NEW packages will be installed:
  dkms fakeroot nvidia-current nvidia-settings patch python-central
  screen-resolution-extra
0 upgraded, 7 newly installed, 0 to remove and 0 not upgraded.
Need to get 32.5 MB/32.8 MB of archives.
After this operation, 96.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com/ubuntu/ oneiric/restricted nvidia-current i386 280.13-0ubuntu6 [31.6 MB]
Get:2 http://archive.ubuntu.com/ubuntu/ oneiric/main python-central all 0.6.17 [41.5 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ oneiric/main screen-resolution-extra all 0.14build2 [13.4 kB]
Get:4 http://archive.ubuntu.com/ubuntu/ oneiric/main nvidia-settings i386 280.13-0ubuntu2 [923 kB]
Fetched 32.5 MB in 29s (1,087 kB/s)                                            
Selecting previously deselected package patch.
(Reading database ... 140707 files and directories currently installed.)
Unpacking patch (from .../p/patch/patch_2.6.1-2_i386.deb) ...
Selecting previously deselected package dkms.
Unpacking dkms (from .../dkms_2.2.0.2-1ubuntu4_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.17-1_i386.deb) ...
Selecting previously deselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_280.13-0ubuntu6_i386.deb) ...
Selecting previously deselected package python-central.
Unpacking python-central (from .../python-central_0.6.17_all.deb) ...
Selecting previously deselected package screen-resolution-extra.
Unpacking screen-resolution-extra (from .../screen-resolution-extra_0.14build2_all.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_280.13-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up patch (2.6.1-2) ...
Setting up dkms (2.2.0.2-1ubuntu4) ...
Setting up fakeroot (1.17-1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.
Setting up nvidia-current (280.13-0ubuntu6) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libOpenCL.so because associated file /usr/lib32/nvidia-current/libOpenCL.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/vdpau/libvdpau_nvidia.so.1 because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so.1 (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libvdpau_nvidia.so because associated file /usr/lib32/nvidia-current/vdpau/libvdpau_nvidia.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/nvidia-current/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-280.13 DKMS files...
First Installation: checking all kernels...
Building only for 3.0.0-12-generic
Building for architecture i686
Building initial module for 3.0.0-12-generic
Done.

nvidia_current:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.0.0-12-generic/updates/dkms/

depmod.......

DKMS: install Completed.
Setting up python-central (0.6.17) ...
Setting up screen-resolution-extra (0.14build2) ...
Processing triggers for python-central ...
Setting up nvidia-settings (280.13-0ubuntu2) ...
update-alternatives: using /usr/lib/nvidia-settings/ld.so.conf to provide /etc/ld.so.conf.d/nvidia_settings.conf (nvidia_settings_conf) in auto mode.
Processing triggers for gnome-menus ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.0.0-12-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
ubuntu@ubuntu:~$ 

```


its ok?

---

### Post by papibe on 2012-03-13
I've never seen those warnings, but it seems that the main installation went OK. 

Now create your X configuration file:
```
sudo nvidia-xconfig
```
And restart your computer so the driver takes effect.

Regards.

---

### Post by jekylhyde on 2012-03-13
> **papibe said:**
> I've never seen those warnings, but it seems that the main installation went OK. 

Now create your X configuration file:
```
sudo nvidia-xconfig
```
And restart your computer so the driver takes effect.

Regards.

why it didn't updated the config while installation?
anyway i ran it:
```
ubuntu@ubuntu:~$ sudo nvidia-xconfig

WARNING: Unable to locate/open X configuration file.

New X configuration file written to '/etc/X11/xorg.conf'


```

---

### Post by papibe on 2012-03-13
I wonder the same thing sometimes...

Now, you should restart your machine and continue with the steps of post #6.

Tell us how it goes.
Regards.

---

### Post by jekylhyde on 2012-03-13
> **papibe said:**
> I wonder the same thing sometimes...

Now, you should restart your machine and continue with the steps of post #6.

Tell us how it goes.
Regards.

the play button , the seeker & all the lower control panel of the player is stuck :confused:

---

### Post by Silviugdr on 2012-03-16
my problem is similar, only the slow frame started after installing ati 12.2 proprietary driver, i`m using ati hd 4870,witch should be sufficient for hd play, the driver is installed corectly, but when i`m playin 1080 and 720p hd movie with vlc,smplayer,mplayer it runs with small lag, i really don`t understand..i`ve disable sync to vblank because with it runs even worst, of course i had to check the reduce tearing image in catalyst witch automaticaly enables the vertical refresh to `always on`.Really weird situation, i was better off with no graphic driver :(.In windows theres no problem with hd movies with any player
ps:i have the restricted ubuntu package and de va api driver installed..i`m on ubuntu x64

---

### Post by jekylhyde on 2012-03-18
someone ?!?

---

