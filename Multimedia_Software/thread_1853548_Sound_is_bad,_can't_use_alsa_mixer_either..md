---
title: "Sound is bad, can't use alsa mixer either."
date: 2011-10-02
forum: Multimedia Software
---

### Post by taco143 on 2011-10-02
Hi, I'm new to Ubuntu, and I'm really liking it for a small sound problem, I don't know whether it might be my speakers getting old, but it's only happened since I installed Ubuntu. 
Whenever I run a youtube video or anything else like a game I have to put it on the lowest possible volume, because if I put it up anything, even the smallest change up, it will start making the sound like feedback, but here's the thing, I leave it at the apps lowest volume, but if I move it up through the speakers themselves they sound louder and just fine. I looked on the Internet and I found something to do with the alsa mixer. I go on terminal, and type amixer or alsamixer and it says it doesn't exist, then I went to Ubuntu Software Center and downloaded the GNOME Alsa Mixer, only to find out when I run it, it simply shows a blank window. I'd appreciate the help :) Thanks in advance. I'm running on Ubuntu 11.04.

---

### Post by ajgreeny on 2011-10-02
I did not realise that alsamixer was not in the default 11.04, but just to check what alsa packages you have installed, run the command ```
dpkg -l | grep alsa
``` and report back here the output.

For alsamixer or amixer to be available you need **alsa-utils** to show in the output of that command, so if it doesn't seem to be installed, add it and try running alsamixer again.

---

### Post by taco143 on 2011-10-02
> **ajgreeny said:**
> I did not realise that alsamixer was not in the default 11.04, but just to check what alsa packages you have installed, run the command ```
dpkg -l | grep alsa
``` and report back here the output.

For alsamixer or amixer to be available you need **alsa-utils** to show in the output of that command, so if it doesn't seem to be installed, add it and try running alsamixer again.
 
```

ii  alsa-base                             1.0.24+dfsg-0ubuntu1                       ALSA driver configuration files
ii  alsa-source                           1.0.24+dfsg-0ubuntu1                       ALSA driver sources
ii  alsa-utils                            1.0.24.2-0ubuntu6                          Utilities for configuring and using ALSA
ii  bluez-alsa                            4.91-0ubuntu1                              Bluetooth ALSA support
ii  gnome-alsamixer                       0.9.7~cvs.20060916.ds.1-2                  ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                    0.10.32-1ubuntu5                           GStreamer plugin for ALSA

```Oh, that explains, thanks for the help, gonna try it right now.
Edit: got this while trying to run alsamixer. 
"cannot open mixer: No such file or directory"

---

### Post by ajgreeny on 2011-10-02
Very odd, and I don't know quite where to go from here.

Try ```
which alsamixer
``` in terminal and it should output```
/usr/bin/alsamixer
``` or similar, so try that full path in terminal, ie ```
/usr/bin/alsamixer
``` or whatever, and see if you still get the same error.

---

### Post by taco143 on 2011-10-02
> **ajgreeny said:**
> Very odd, and I don't know quite where to go from here.

Try ```
which alsamixer
``` in terminal and it should output```
/usr/bin/alsamixer
``` or similar, so try that full path in terminal, ie ```
/usr/bin/alsamixer
``` or whatever, and see if you still get the same error.
I got the same error, 
```

$which alsamixer
/usr/bin/alsamixer
$/usr/bin/alsamixer
cannot open mixer: No such file or directory

```

---

### Post by ajgreeny on 2011-10-02
OK now try ```
ls -la /usr/bin/alsamixer
```to check if alsamixer is executable.  This is baffling me at the moment.

---

### Post by taco143 on 2011-10-02
> **ajgreeny said:**
> OK now try ```
ls -la /usr/bin/alsamixer
```to check if alsamixer is executable.  This is baffling me at the moment.
As I said, I'm still new xD how do I check if it's executable? 
```

-rwxr-xr-x 1 root root 51376 2011-04-20 12:10 /usr/bin/alsamixer

```
That was the output, Sorry my computer is baffling you xD

---

### Post by ajgreeny on 2011-10-03
Well, that got us nowhere!

In the output ```
-rw[COLOR=Red]x[/COLOR]r-[COLOR=Red]x[/COLOR]r-[COLOR=Red]x[/COLOR] 1 root root 51376 2011-04-20 12:10 /usr/bin/alsamixer
``` the three x shown in red indicate that the file is executable, and by everybody, ie the owner, the group and all others.

There seems to be no good reason why the alsamixer in your system is not running, so as a last option try purging alsa-utils using terminal ```
sudo apt-get remove --purge alsa-utils
```or in synaptic, then reinstall, just in case the original package or the files it installed were corrupt.

---

### Post by matt_symes on 2011-10-03
Hi

It's not an issue with one of the config files is it ?

```
ls -l /var/lib/alsa/asound.state
cat /var/lib/alsa/asound.state
```

Kind regards

---

### Post by taco143 on 2011-10-03
> **matt_symes said:**
> Hi

It's not an issue with one of the config files is it ?

```
ls -l /var/lib/alsa/asound.state
cat /var/lib/alsa/asound.state
```Kind regards
```
$ ls -l /var/lib/alsa/asound.state
ls: cannot access /var/lib/alsa/asound.state: No such file or directory
$ cat /var/lib/alsa/asound.state
cat: /var/lib/alsa/asound.state: No such file or directory
timothy@timothy-GG038AA-ABA-a6109n:~$ 
```
Also, I already tried re-installing the utilities, and it still doesn't work, It was actually my first reaction :P

---

### Post by matt_symes on 2011-10-03
Hi

Well i am going to go out on a limb here as i really don't know the alsa system at all but let's try this.

Open a terminal and type

```
alsactl init
```and then type

```
sudo alsactl store
```Enter your password. It will not be echoed to the screen. This is normal.

Then type 

```
alsamixer
```Do you get the alsa mixer ?

Kind regards

---

### Post by taco143 on 2011-10-07
```

~$ alsactl init
alsactl: init:1743: No soundcards found...
~$ sudo alsactl store
alsactl: save_state:1519: No soundcards found...
~$ alsamixer
cannot open mixer: No such file or directory

```
Nope, still doesn't work, what the hell? What do you mean no sound card is there? I think I have a sound card, I mean, I can hear videos and stuff okay, so why should it say I don't?

---

### Post by matt_symes on 2011-10-08
Hi

What's the output of (open a terminal)

```
sudo lshw -c multimedia
```and 

> lsmod | grep sndPost the results back here.

If we can keep this thread going then hopefully someone who knows the sound subsystem well will chime in (hint, hint).

Kind regards

---

### Post by taco143 on 2011-10-08
> **matt_symes said:**
> Hi

What's the output of (open a terminal)

```
sudo lshw -c multimedia
```and 

Post the results back here.

If we can keep this thread going then hopefully someone who knows the sound subsystem well will chime in (hint, hint).

Kind regards
```

  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fcffc000-fcffffff


```

I think it might be the graphics card, I have an extra ATI one. I'm gonna try it.

---

### Post by matt_symes on 2011-10-09
Hi

```
*-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fcffc000-fcffffff
```This is interesting. 

You have an device that is using the oss_hdaudio driver and another that is UNCLAIMED. I.E It has no driver!

oss is a legacy sound system even though it can be emulated by alsa. This i think is the root cause of your problem.

Let's get even more info. 

Open a terminal and type (or copy and paste - case sensitive)

```
lspci -nnk | grep -iA3 audio
```Post the results back here.

Kind regards

---

### Post by taco143 on 2011-10-09
> **matt_symes said:**
> Hi

```
*-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: 5
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=oss_hdaudio latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
  *-multimedia UNCLAIMED
       description: Audio device
       product: High Definition Audio Controller
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fcffc000-fcffffff
```This is interesting. 

You have an device that is using the oss_hdaudio driver and another that is UNCLAIMED. I.E It has no driver!

oss is a legacy sound system even though it can be emulated by alsa. This i think is the root cause of your problem.

Let's get even more info. 

Open a terminal and type (or copy and paste - case sensitive)

```
lspci -nnk | grep -iA3 audio
```Post the results back here.

Kind regards
```
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a58]
    Kernel driver in use: oss_hdaudio
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a58]
    Kernel driver in use: pata_amd
--
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Subsystem: nVidia Corporation Device [10de:0000]
```
 There, I'll do my best to research and understand all this :P

---

### Post by matt_symes on 2011-10-11
Hi

To be honest, i am not sure of what the problem may be here. I don't know alsa and pulse well enough.

I will keep looking for a solution for you but in the meantime have a 

*bump*

so others can look at this.

Kind regards

---

### Post by taco143 on 2011-10-15
Heh, I guess my computer's weird, there's a new upgrade for ubuntu so I'm gonna have my fake hopes on and hope it gets fixed by it xP.

---

### Post by matt_symes on 2011-10-15
*bump*

---

### Post by taco143 on 2011-10-17
-bump- Please help xD

---

### Post by taco143 on 2011-10-21
*Bump* Getting frustrated, looking everywhere and noone seems to have this happenned before D:

---

### Post by BicyclerBoy on 2011-10-21
What happens if you
sudo rmmod oss_hdaudio
sudo rmmod snd-pcm-oss
sudo modprobe snd-hda-intel

may need to try:
sudo modprobe snd-hda-intel enable_msi=0

lspci -nnk | grep -iA3 audio

dmesg | grep HDA

did you build your own alsa kernel modules ?
Have you installed OSS packages in synaptic ? (get rid of them)

This h/w looks to be nVidia chipset..there are suggestions (inc. alsa source code) that does not work very well with msi


If that stuff works then a workaround is to have this line in /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel index=0 enable_msi=0

---

### Post by taco143 on 2011-10-27
> **BicyclerBoy said:**
> What happens if you
sudo rmmod oss_hdaudio
sudo rmmod snd-pcm-oss
sudo modprobe snd-hda-intel

may need to try:
sudo modprobe snd-hda-intel enable_msi=0

lspci -nnk | grep -iA3 audio

dmesg | grep HDA

did you build your own alsa kernel modules ?
Have you installed OSS packages in synaptic ? (get rid of them)

This h/w looks to be nVidia chipset..there are suggestions (inc. alsa source code) that does not work very well with msi


If that stuff works then a workaround is to have this line in /etc/modprobe.d/alsa-base.conf:

options snd-hda-intel index=0 enable_msi=0
Exactly as you said. Now I can't hear anything D:. Idk if I did everything right. And no, I didn't build my own alsa kernel module.
```

$ sudo rmmod oss_hdaudio
$ sudo rmmod snd-pcm-oss
ERROR: Module snd_pcm_oss does not exist in /proc/modules
$ sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
$ sudo modprobe snd-hda-intel enable_msi=0
FATAL: Module snd_hda_intel not found.
$ lspci -nnk | grep -iA3 audio
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a58]
00:06.0 IDE interface [0101]: nVidia Corporation MCP61 IDE [10de:03ec] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a58]
--
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Subsystem: nVidia Corporation Device [10de:0000]
$ dmesg | grep HDA
$ /etc/modprobe.d/alsa-base.conf:
bash: /etc/modprobe.d/alsa-base.conf:: No such file or directory
$ options snd-hda-intel index=0 enable_msi=0
options: command not found


```Finally, Someone to come to my aid :D :biggrin:

---

### Post by BicyclerBoy on 2011-10-28
Don't start any celebrations, I have no idea what's going on.

Your audio device is not being claimed by the right driver.

There has been bugs with the MCP6* nVidia audio controller.

All I can suggest is trolling thru' the kernel logs (or run dmesg) & look for any audio driver stuff..

You could try to update the alsa kernel drivers by adding the ubuntu audio dev ppa 
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=natty](https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=natty)

This cnd:
sudo modprobe snd-hda-intel
should not come back with errors; especially errors about not being found..

Have you used some alsa update scripts that could have purged packages ?

dpkg -s alsa-base

Find your kernel version
uname -r
Then check this path:
ls -al /lib/modules/2.6.38-12-generic/kernel/sound/pci/hda
(you must replace the "2.6.38-12-generic" bit with your kernel version..

---

### Post by taco143 on 2011-10-28
> **BicyclerBoy said:**
> Don't start any celebrations, I have no idea what's going on.

Your audio device is not being claimed by the right driver.

There has been bugs with the MCP6* nVidia audio controller.

All I can suggest is trolling thru' the kernel logs (or run dmesg) & look for any audio driver stuff..

You could try to update the alsa kernel drivers by adding the ubuntu audio dev ppa 
[https://launchpad.net/~ubuntu-audio-dev/+archive/ppa?field.series_filter=natty]("https://launchpad.net/%7Eubuntu-audio-dev/+archive/ppa?field.series_filter=natty")

This cnd:
sudo modprobe snd-hda-intel
should not come back with errors; especially errors about not being found..

Have you used some alsa update scripts that could have purged packages ?

dpkg -s alsa-base
Sorry for forgetting to mention this but I updated to oneiric Ocelot about a week ago. I think it might affect the kernel driver I need. and in addition to the problem, I can't hear anything from banshee player.
```

$ uname -r
3.0.0-12-generic
$ ls -al /lib/modules/3.0.0-12-generic/kernel/sound/pci/hda
ls: cannot access /lib/modules/3.0.0-12-generic/kernel/sound/pci/hda: No such file or directory


```Fuuuuuuuu what the hell D:

---

### Post by BicyclerBoy on 2011-10-28
Can you see my last post..

lsmod | grep snd

aplay -l

---

### Post by taco143 on 2011-10-28
Sorry, 
```

$ sudo modprobe snd-hda-intel
FATAL: Module snd_hda_intel not found.
$ dpkg -s alsa-base
Package: alsa-base
Status: install ok installed
Priority: optional
Section: sound
Installed-Size: 516
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: all
Source: alsa-driver
Version: 1.0.24+dfsg-0ubuntu2
Provides: alsa
Depends: module-init-tools (>= 3.2.1), linux-sound-base, udev
Recommends: alsa-utils
Suggests: apmd (>= 3.0.2-1), alsa-oss, oss-compat
Conffiles:
 /etc/modprobe.d/blacklist-modem.conf 83850631d180e0c064ee313d57cd7c86
 /etc/modprobe.d/alsa-base.conf 817bff6351a7321f5bbf000f39f587c0
 /etc/apm/scripts.d/alsa f83b2095c1d2a46d7eac161c5ff0373d
Description: ALSA driver configuration files
 This package contains various configuration files for
 the ALSA drivers.
 .
 For ALSA to work on a system with a given sound card,
 there must be an ALSA driver for that card in the kernel.
 Linux 2.6 as shipped in linux-image packages contains
 ALSA drivers for all supported sound cards in the form
 of loadable modules. A custom alsa-modules package can
 be built from the sources in the alsa-source package
 using the m-a utility (included in the module-assistant
 package). Please read the README.Debian file for more
 information about loading and building modules.
 .
 ALSA is the Advanced Linux Sound Architecture.
Homepage: http://www.alsa-project.org/
Original-Maintainer: Debian ALSA Maintainers <pkg-alsa-devel@lists.alioth.debian.org>



```

---

### Post by BicyclerBoy on 2011-10-28
I've just rebooted into 11.10 & that path exists & has 12 .ko files including snd-hda-intel.ko...

---

### Post by taco143 on 2011-10-28
> **BicyclerBoy said:**
> I've just rebooted into 11.10 & that path exists & has 12 .ko files including snd-hda-intel.ko...
Well, I don't know what's wrong with my computer D:
```

$ lsmod | grep snd
$ aplay -l
aplay: device_list:240: no soundcards found...

```

---

