---
title: "No sound on my Vaio VPCF11M1E"
date: 2010-02-20
forum: Multimedia Software
---

### Post by dvancoevorden on 2010-02-20
Hi 

I have checked everything but have no sound on my vaio laptop.
Does anyone know what's going on? Thanks! Dave
Here's my output from lspci:

00:00.0 Host bridge: Intel Corporation Arrandale DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Arrandale PCI Express x16 Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a29 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
02:00.0 Network controller: Intel Corporation Device 422c (rev 35)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4380 (rev 10)
3f:00.0 Host bridge: Intel Corporation QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Device 2d12 (rev 02)
3f:02.3 Host bridge: Intel Corporation Device 2d13 (rev 02)

---

### Post by dvancoevorden on 2010-02-20
Forgot to mention it's Ubuntu 9.10. I have upgraded to kernel 

2.6.32-020632-generic #020632

because it solved my wireless issue.
Thanks
D

---

### Post by Pistolpete2 on 2010-03-08
On the Vaio VPCEB1S1E I've got the same issue

---

### Post by paradoxy on 2010-03-08
- download the latest alsa driver here [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.1.tar.bz2)

```

tar jxvf alsa-driver-1.0.22.1.tar.bz2
cd alsa-driver-1.0.22.1
./configure --with-sequencer=yes && make
sudo make install
sudo ./snddevices

```

reboot

Enjoy

---

### Post by Pistolpete2 on 2010-03-09
I've just tried it but it didn't solve my problem.

My computer still won't produce any sound.

Thanks for your suggestion though, it was worth trying.

---

### Post by dcnlwfh on 2010-03-09
it might not be a supported system yet.  my parent's new and beefed up dell desktop with HD sound won't work, but my old hand-me-down dell desktop will work no problem.  i also can't get desktop effects on their HD video card either unless i install the driver.

---

### Post by leorolla on 2010-03-09
Indeed,
[http://wiki.debian.org/InstallingDebianOn/Sony/VPCEB1J1E](http://wiki.debian.org/InstallingDebianOn/Sony/VPCEB1J1E)
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934)

But support for this device is being developed right now... see implementations on the last couple of days:
[http://git.alsa-project.org/?p=alsa-kernel.git&a=search&h=HEAD&st=commit&s=alc269](http://git.alsa-project.org/?p=alsa-kernel.git&a=search&h=HEAD&st=commit&s=alc269)

You can follow some of the "Build ALSA" guides you will find with google, but replacing the downloaded file by today's version from
[http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/](http://ftp.kernel.org/pub/linux/kernel/people/tiwai/alsa/alsa-driver/)

If you are not that neubie, you can help with this bug:
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4934)

You can also test Kubuntu Lucid Alpha 3 to see what it gives
[http://forums.fedoraforum.org/showthread.php?p=1335892](http://forums.fedoraforum.org/showthread.php?p=1335892)

Edit:
To get the built-last-night ALSA, you can get a .deb file here:
[https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra](https://edge.launchpad.net/~ubuntu-audio-dev/+archive/ppa/+sourcepub/989385/+listing-archive-extra)

---

### Post by leorolla on 2010-03-10
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-
sudo reboot
cat /proc/asound/version
```

Works on Karmic with kernel 2.6.31-20-generic

Should work with other kernels

Should work on Lucid

This is the latest possible ALSA.
(Don't follow any other guide you find googling the web, unless you know what you're doing.)

---

### Post by Cuppa-Chino on 2010-03-11
> **leorolla said:**
> ```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-
sudo reboot
cat /proc/asound/version
```

Works on Karmic with kernel 2.6.31-20-generic

Should work with other kernels

Should work on Lucid

This is the latest possible ALSA.
(Don't follow any other guide you find googling the web, unless you know what you're doing.)

FYI when applying that my system becomes unbootable - Lucid A3

---

### Post by leorolla on 2010-03-11
> **Cuppa-Chino said:**
> FYI when applying that my system becomes unbootable - Lucid A3

That's strange. It should only affect the last kernel.

Do you still see grub menu during boot?

---

### Post by Cuppa-Chino on 2010-03-12
the problem was not the module but the startup mechanism -- I can still start with the restore setting, dropping to root prompt and manually starting gdm

still no sound with my vaio (which is not the same as the f mind you)

---

### Post by yadun1 on 2010-05-02
Hello,
I have a sony vaio VPCF11M1E running ubuntu 10.04.
Sound is available when headphones are plugged in.
In case no headphones are plugged in, nothing can be heared though.
The system speakers do work when windows is run.

The numpad does not work as well.

Does anybody have a solution for this?

Cheers,

Yadun1

---

### Post by yadun1 on 2010-05-02
Forgot to mention the kernel version:

Kernel Linux 2.6.32-21-generic-pae

---

### Post by lidex on 2010-05-02
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by Pistolpete2 on 2010-05-04
IF ```
aplay -l
``` command gives something like:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Then you have the same problem as me.  I've found a **_[COLOR="DarkGreen"]solution[/COLOR]_** in bug report 445889.  And I have put a guide online, that explains how you can get your sound to work: [http://ubuntu42.blogspot.com/2010/05/fixing-sound-issue-on-sony-vaio.html](http://ubuntu42.blogspot.com/2010/05/fixing-sound-issue-on-sony-vaio.html)

---

### Post by yadun1 on 2010-05-05
Hello lidex,
here you go:

```


:~$ uname -a
Linux bbx 2.6.32-21-generic-pae #32-Ubuntu SMP Fri Apr 16 09:39:35 UTC 2010 i686 GNU/Linux

:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 275

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID a

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID a


```

---

### Post by lidex on 2010-05-05
You're gonna need alsa 1.0.23:
[http://ubuntuforums.org/showpost.php?p=9136618&postcount=2]("http://ubuntuforums.org/showpost.php?p=9136618&postcount=2")

---

### Post by Negative Black on 2010-05-15
I've got the same laptop and found a script written by Bob Nelson which installs the ALSA driver.
I modified it to use the latest version of ALSA and the sound is working
now. However the input still doesn't work, maybe someone can have a
look at that... it's probably only the model setting that's wrong but i haven't
found the correct one yet.

anyways here is the script:

```

#!/bin/sh

# This script will recompile the ALSA drivers for Ubuntu
# This procedure was gotten from
# https://help.ubuntu.com/community/HdaIntelSoundHowto
#
# Authored by	Bob Nelson  	admin@stchman.com - 9/6/2007
# Modified by	Roy van Dam	roy@negative-black.org - 5/15/2010


script_name="alsa_setup.sh"

# Script must run as root 
if [ $USER != "root" ]; then
	echo "You need to run this script as root."
	echo "Use 'sudo ./$script_name' then enter your password when prompted."
	exit 1
fi

# Install the required tools
sudo apt-get -y install build-essential ncurses-dev gettext

# Install your kernel headers
sudo apt-get -y install linux-headers-`uname -r`

# Change to users home folder
cd ~

# Get the files from www.stchman.com
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2

# make a new folder 
sudo mkdir -p /usr/src/alsa

# Change to that folder
cd /usr/src/alsa

# Copy the downloaded files to the newly made folder
sudo cp ~/alsa* .

# Unpack the tar archive files
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*

#Compile and install alsa-driver
cd alsa-driver*
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

# Compile and install alsa-lib
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install

# Compile and install alsa-utils
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install

# Remove the archives as they are no longer needed
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*

# Add the following line to the file, replacing '3stack' with your model
sudo echo -e '\n' >> /etc/modprobe.d/alsa-base
sudo echo "options snd-hda-intel model=3stack" >> /etc/modprobe.d/alsa-base

# Reboot the computer
sudo reboot

```

---

### Post by M.Vilenius on 2010-05-26
Negative black, thanks for the script. It got my sound working on my Vaio nice and easy.

However, I don't seem to get MIDI working. I tried to find a solution from the net, with the result of adding --with-oss=yes --with-sequencer=yes to the ./configure.

EDIT: When I say "I can't get midi working" what I'm actually trying is to get my MIDI USB Keyboard to work with soft synth Bristol via Jack Audio Connection kit. But as the modules are not there, I think this might be the root of the problem.

But still snd_seq_midi and snd_rawmidi modules can't be found.

With ```
modprobe snd_seq_midi
``` I get ```
FATAL: Module snd_seq_midi not found.
``` and same thing basically for modprobe snd_rawmidi.

lsmod | grep snd gives me:

```
snd_hda_codec_atihdmi     3055  1 
snd_hda_codec_realtek   297355  1 
snd_hda_intel          23768  5 
snd_hda_codec          99419  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6938  1 snd_hda_codec
snd_pcm_oss            40601  0 
snd_mixer_oss          16474  1 snd_pcm_oss
snd_pcm                88109  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            31490  0 
snd_seq_midi_event      7267  1 snd_seq_oss
snd_seq                57460  7 snd_seq_oss,snd_seq_midi_event
snd_timer              23021  2 snd_pcm,snd_seq
snd_seq_device          7048  2 snd_seq_oss,snd_seq
```

and cat /dev/sndstat:

```
Sound Driver:3.8.1a-980706 (ALSA v1.0.23 emulation code)
Kernel: Linux Kamimusubi 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0xf5e00000 irq 36
HD-Audio Generic at 0xf0040000 irq 37

Audio devices:
0: ALC269 Analog (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Realtek ALC269
1: ATI R6xx HDMI
```

Any help would be highly appreciated!

-Mikko

---

### Post by feedbee on 2010-06-11
> **leorolla said:**
> ```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-
sudo reboot
cat /proc/asound/version
```


**This advice solved the sound problem for me.**
My OS:
Linux feedbee-ubuntu 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
My laptop:
Sony Vaio VPCEB1S1E

Thanks.

---

### Post by Borgond on 2010-06-28
> **leorolla said:**
> ```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa/ubuntu
sudo aptitude update
sudo aptitude install linux-alsa-driver-modules-$(uname -r) linux-backports-modules-alsa-$(uname -r)-
sudo reboot
cat /proc/asound/version
```

Works on Karmic with kernel 2.6.31-20-generic

Should work with other kernels

Should work on Lucid

This is the latest possible ALSA.
(Don't follow any other guide you find googling the web, unless you know what you're doing.)

Thanks for this hint! - this worked flawlessly on my machine ( VPCF11M1E / Lucid / 2.6.32-22-generic )

> ~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.23.
Compiled on Jun 28 2010 for kernel 2.6.32-22-generic (SMP).

---

### Post by terry.r on 2010-07-05
As of this post the current Lucid Kernel is 2.6.32-23-generic however there arent any linux-backports-modules-alsa or linux-alsa-driver-modules packages for this kernel. I reverted to the 2.6.32.22 kernel and then installed the matching alsa module packages and after that I have audio on my Vaio VPCF121FD

---

### Post by Borgond on 2010-07-10
Hi there,

as of today there are backported packages available again :

```
Die folgenden NEUEN Pakete werden zusätzlich installiert:
  linux-alsa-driver-modules-2.6.32-23-generic 
0 Pakete aktualisiert, 1 zusätzlich installiert, 0 werden entfernt und 0 nicht aktualisiert.
```

... after rebooting sound should be available again.

I guess I'll have to reinstall this every time there is a new kernel - couldn't this be working out of the box? - would be nice! :-)

Cheers!

---

