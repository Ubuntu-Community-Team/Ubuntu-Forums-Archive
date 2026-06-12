---
title: "ALSA Help"
date: 2011-06-24
forum: Multimedia Software
---

### Post by techmad on 2011-06-24
I'm trying to get sound over HDMI working on a new soundcard (Nvidia 550 Ti). It works fine on Ubuntu 11, its picked up automatically. On any earlier version of Ubuntu however it is not, even when I upgrade ALSA to the latest version (1.0.24).

So I know that audio over HDMI can work, but I just dont know what needs to be done after upgrading ALSA. Do I need to load a certain module for the card to be picked up? If so, how do I go about doing this and how do I find out what module needs to be loaded?

If anyone could help with this I'd be extremely greatful, the reason I dont want to stick with Ubuntu 11 is that qtsixa (Used for connecting PS3 controllers) no longer works properly with it. I'm trying to get audio working on an install of Ubuntu 10.04 (XBMC Live).

If any further information is needed let me know - thanks :)

---

### Post by jvlomax on 2011-06-24
Are you wanting to use just alsa, or are you using pulseaudio? If you are just using alsa, you will probably have to mess around with the .asoundrc file, which i can help you with if that's the route you want to go :) On the other hand if you are using pulse, you should be able to select hdmi output in the pulse volume control

---

### Post by techmad on 2011-06-24
I think all I need is alsa, the thing is that the card isnt being detected at all at the moment. When I run aplay -l this is what I get:

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```lspci -v lists the following for the  card:

```
01:00.1 Audio device: nVidia Corporation Device 0bee (rev a1)
    Subsystem: ZOTAC International (MCO) Ltd. Device 5194
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at fea7c000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```At the moment alsamixer shows the following for the card:

  [IMG]http://ubuntuforums.org/attachment.php?attachmentid=195893&stc=1&d=1308950069[/IMG]


Whereas in 11.04 I see the following:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=194683&stc=1&d=1307656274[/IMG]

Do I need to configure alsa so that it loads the correct driver/module for my card somehow? I used the script [here]("http://ubuntuforums.org/showthread.php?t=1681577") to update alsa, to me it looks as if the new kernel module (driver?) isnt loading.

---

### Post by BicyclerBoy on 2011-06-24
Have you upgraded the kernel alsa modules or just the user-space alsa drivers ?

With a very new video card , it is likely you need the latest video driver to expose the audio devices.
What nVidia driver version ?

XBMC Live comes with nVidia driver that is so old it does not support GT520 or later...

You can add the Xorg-edgers ppa & get nVidia version 260 & then the HDMI audio devices should appear..
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Sorry that will **not** work..

You need **270.41.06** or later...
Try this one...
[http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid](http://www.ubuntuupdates.org/ppa/ubuntu-x-swat?dist=lucid)


(nVidia 275 is the latest)

---

### Post by techmad on 2011-06-24
Sorry I forgot to add this in, I downloaded and installed the drivers from NVidia's website:

cat /proc/driver/nvidia/version:
```
NVRM version: NVIDIA UNIX x86 Kernel Module  270.41.19  Mon May 16 23:31:36 PDT 2011
```

This is the same version I installed on Ubuntu 11, where I was able to get the card working properly via HDMI. I installed it before I installed ALSA, Im not sure if that makes a difference?

> Have you upgraded the kernel alsa modules or just the user-space alsa drivers ?

I'm not really sure to be honest, I just ran the upgrade script available [here]("http://ubuntuforums.org/showthread.php?t=1681577"). How do I upgrade the kernel alsa modules?

---

### Post by techmad on 2011-06-24
I compiled from source as listed [here]("https://help.ubuntu.com/community/HdaIntelSoundHowto") using the following statement when configuring the driver:
```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
```I rebooted but still no change :(

---

### Post by BicyclerBoy on 2011-06-24
The sure-fire way to get the later alsa kernel modules is to update the kernel..
There is an natty-backport kernel for lucid 10.04 that will solve the alsa..
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)
or 
for just the alsa drivers this works for me & others..(older GPU) 
[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu)

The problem with the nvidia install method is that it will not stick.
With kernel updates it will break.
I advise using a pre-compiled package ppa for nVidia.

I don't know what the alsa upgrade script does exactly or if it interferes with nvidia kernel driver module.

---

### Post by BicyclerBoy on 2011-06-24
Are you using a snd-hda-intel options probe_mask value ?
(/etc/modprobe.d/*.conf)

I recommend you do not until everything is debugged.

Any changes to files in /etc/modprode.d/ requires
[sudo] update-initramfs -u

---

### Post by techmad on 2011-06-24
> **BicyclerBoy said:**
> The sure-fire way to get the later alsa kernel modules is to update the kernel..
There is an natty-backport kernel for lucid 10.04 that will solve the alsa..
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)
or 
for just the alsa drivers this works for me & others..(older GPU) 
[http://ppa.launchpad.net/team-iquik/alsa/ubuntu](http://ppa.launchpad.net/team-iquik/alsa/ubuntu)

The problem with the nvidia install method is that it will not stick.
With kernel updates it will break.
I advise using a pre-compiled package ppa for nVidia.

I don't know what the alsa upgrade script does exactly or if it interferes with nvidia kernel driver module.

Forgive  my ignorance, but what exactly do I need to do to do this? This is what I done:

```
sudo add-apt-repository ppa:team-iquik/alsa
sudo apt-get update
sudo apt-get install alsa alsa-utils
sudo shutdown -r now
```

But it didnt make any difference, I'm still learning Linux so sorry if this is something simple!

---

### Post by techmad on 2011-06-24
> **BicyclerBoy said:**
> Are you using a snd-hda-intel options probe_mask value ?
(/etc/modprobe.d/*.conf)

I recommend you do not until everything is debugged.

Any changes to files in /etc/modprode.d/ requires
[sudo] update-initramfs -u

No I haven't done anything like this yet.

---

### Post by BicyclerBoy on 2011-06-24
from iquik..

linux-sound-base
alsa-base
libasound2  + dev 
lib32asound2
libasound2-plugins

But i'm using this to build the AC3 encoder plugin for alsa..

This ppa (lucid packages) may not be cutting edge enough anyway..

I think the natty backport kernel is much cleaner solution..
2.6.38 is available for lucid 10.04.

---

### Post by techmad on 2011-06-24
Ok I'll try that instead, so I've added the PPA, now should the packages I need to install be **linux-lts-backport-natty-source-2.6.38** and **linux-lts-backport-natty-headers **?

Thanks for your help on this.

---

### Post by BicyclerBoy on 2011-06-24
Yes that looks good.
The headers package will be needed by the nvidia driver re-build.
You will have to re-run the nvidia installer script.

It look like XBMC live is 32 bit which is another possible cause of the problem.
There are no issues running 64bit Ubuntu.
As far as I know you can not change to 64 bit kernel.

The nVidia driver install contains both, the 32 bit support is optional & requires lib32 support build tools (I forget).

---

### Post by techmad on 2011-06-24
This is what I'm getting when I try to install:

```
sudo apt-get install linux-lts-backport-natty-source-2.6.38Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-lts-backport-natty-source-2.6.38 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package linux-lts-backport-natty-source-2.6.38 has no installation candidate
```

Its getting late here so I think I'm gona call it a night, I might just stick with natty as its turning into a lot of hassle just to get a wireless controller working, I think I'll survive without it! 

Thanks for your help with it anyway I appreciate it :)

---

### Post by BicyclerBoy on 2011-06-24
Maybe I'm wrong but..
You don't need the kernel source only the binary image package.
Because you added the ppa using apt-get it has added the source component.
I do not have the kernel ppa source only the binary component.

You may have a dependency for kernel source from your other packages..(doubtful)

I recommend you use synaptic or synaptic package manager GUI.
apt-get does not always get things right.
Synaptic package manager lets you check & fix the repository list (remove the kernel source component entry).

After some digging, I found I'm using this to update the alsa kernel modules
linux-backports-modules-alsa-lucid-generic
(lucid-proposed updates see synaptic package manager)
Note: this will not work in conjunction with the natty backport kernel because there is no matching alsa kernel module package.. because it does not need one!
And it is to old to help you.

I guess these problems is why you stay inside a release or start building everything or just upgrade.

Soo..just use 11.04....

---

