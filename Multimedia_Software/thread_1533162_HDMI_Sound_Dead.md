---
title: "HDMI Sound Dead"
date: 2010-07-17
forum: Multimedia Software
---

### Post by jda8818 on 2010-07-17
10..04 - Ran suggested updates yesterday.  Everything seemed OK.

System locked up today and would not reboot.  Finally after several reboot attempts I was able to recover, but the HDMI sound is dead
.  
In the past I have re-compiled and re-installed the AlsaUprgrade Script with success. no such luck today.  

```
jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ ^C
```This aplay -l result is much less extensive that it should be.  When the system is working properly aplay -l returns at least four separate cards.  I didn't save the previous output.

As always, thanks in advance for any help/comments

JA

---

### Post by jda8818 on 2010-07-17
here is the recovered aplay -l file from earlier when the HDMI sound was working::

```
jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ 
```Once again, many thanks for help or comments!

JA

---

### Post by lidex on 2010-07-18
Use gnome-alsamixer to make sure digital outs are enabled. I believe they are muted by default. Also try toggling off/on. 
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

### Post by jda8818 on 2010-07-18
Thank you again, Lidex,

I had previously installed Gnome-Alsamixer, so i was able to invoke it at your suggestion.  Previously, none of the controls had any perceptible effect except one of IE958 (?) checkboxes which would simply mute or unmute all sound.

Everything seemed to be enabled today,  checking/unchecking had no perceptible effect. still no sound at all.   Sound Card Properties shows all options enabled.

It is interesting to note that the HDMI devices from the  previously (successful) aplay -l result have just disappeared.  I have no idea why, but i guess it is somehow related to the crash i described in my first post in this thread.

no idea how to proceed ...

Thank you Lidex,

as always, all comments/suggestions/etc are greatly appreciated!

JA

---

### Post by lidex on 2010-07-18
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by jda8818 on 2010-07-19
Thank you Lidex,

Zotac H55-ITX WIFI, i3-530, 4GB DDR3, using onboard Intel Video

```
jadcock@HTPC:~$ uname -a
Linux HTPC 2.6.32-23-generic-pae #37-Ubuntu SMP Fri Jun 11 09:26:55 UTC 2010 i686 GNU/Linux
jadcock@HTPC:~$ 
``````
jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ 
``````
jadcock@HTPC:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                     1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                               1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                            1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                           0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
jadcock@HTPC:~$ 
``````
jadcock@HTPC:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888
jadcock@HTPC:~$ 
```As always, thanks for any comments/suggestions,

JA

---

### Post by lidex on 2010-07-19
Let's try an alsa upgrade. Use the alsa-upgrade link in my sig.

---

### Post by jda8818 on 2010-07-19
Hello again, Lidex!

If you're referring to the AlsaUpgrade Script version 1.0.23-2.sh, I have already re-run this script twice recently (this thread) without any change to the situation.

Two weeks (or so) ago (previous thread) I ran into trouble after an upgrade, at which time aplay -l returned no sound card at all. I re-ran (-c, then -i) the script and recovered completely.  But that was two weeks ago.

 No luck with the script this time.

Comments or suggestions will certainly be appreciated!

Thank you for you interest Lidex,

JA

---

### Post by lidex on 2010-07-19
> **jda8818 said:**
> Hello again, Lidex!

If you're referring to the AlsaUpgrade Script version 1.0.23-2.sh, I have already re-run this script twice recently (this thread) without any change to the situation.

Two weeks (or so) ago (previous thread) I ran into trouble after an upgrade, at which time aplay -l returned no sound card at all. I re-ran (-c, then -i) the script and recovered completely.  But that was two weeks ago.

 No luck with the script this time.

Comments or suggestions will certainly be appreciated!

Thank you for you interest Lidex,

JA
And that is the problem.
Do this for me please. Reboot into an older kernel and go to synaptic. Find and mark for complete removal your latest kernel and header packages. Apply. Now this:
```
sudo apt-get update
sudo apt-get upgrade

```
Reboot into latest kernel and re-install alsa:
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

---

### Post by jda8818 on 2010-07-20
> Do this for me please. Reboot into an older kernel and go to synaptic.  Find and mark for complete removal your latest kernel and header  packages. ApplyThank you Lidex.

First of all, my current boot loader fails to give me any options as to kernel variety.   I'm guessing that I'll need to interrupt the boot process with a keystroke or two, or perhaps hack a .conf file or something.  Any idea where one might find a description of rebooting into an older kernel?

And to prepare you for a further shock, I'll probably end up needing to ask how to identify all the files (kernel and header packages) that need to be completely removed.

Thank you again Lidex for your interest!

JA

---

### Post by lidex on 2010-07-20
Do you get a grub menu when you boot up?

---

### Post by jda8818 on 2010-07-20
Hi Lidex,

no.  in fact:

```
jadcock@HTPC:~$ grub --help
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
jadcock@HTPC:~$

```So I will proceed with 

```
sudo apt-get install grub 
```and post further

thanks, JA

---

### Post by lidex on 2010-07-20
I don't think you want to do that. If you don't have it you should have grub2 - grub-pc, I believe.
With grub2, hold down the shift key after the bios screen to get the menu. Select the third line, which should be your previous kernel
and boot into that.

A better indicator:
```
dpkg -l | grep "grub"
```

---

### Post by jda8818 on 2010-07-20
```
jadcock@HTPC:~$ grub --help
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub
jadcock@HTPC:~$ sudo apt-get install grub
[sudo] password for jadcock: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  grub-legacy-doc mdadm
The following packages will be REMOVED:
  grub-pc
The following NEW packages will be installed:
  grub
0 upgraded, 1 newly installed, 1 to remove and 6 not upgraded.
Need to get 406kB of archives.
After this operation, 1,335kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
jadcock@HTPC:~$ grub-pc --help
grub-pc: command not found
jadcock@HTPC:~$
```how do i proceed with grub-pc?

---

### Post by lidex on 2010-07-20
I guess grub-pc is the package, not a command. So obviously it is installed. If you only have one OS the default is to skip the menu and go directly into your default kernel (usually newest). See my last post.

---

### Post by jda8818 on 2010-07-20
OK, thanks, we're on the same page ...

I'll proceed and post later

JA

---

### Post by jda8818 on 2010-07-20
```
jadcock@HTPC:~$ uname -a
Linux HTPC 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
jadcock@HTPC:~$ 
```OK, I'm here and checking out synaptic ...

more to follow, thanks Lidex,

JA

---

### Post by jda8818 on 2010-07-20
looking in synaptic for kernel and header packages version 2.6.32.23... i find:

linux-generic-pae                        2.6.32.23.24
linux-headers-2.6.32-23                    2.6.32-23.37
linux-headers-2.6.32-23-generic-pae        2.6.32-23.37
linux-headers-generic-pae                2.6.32.23.24
linux-image-2.6.32-23-generic-pae        2.6.32-23.37
linux-image-generic-pae                    2.6.32.23.24
linux-libc-dev                            2.6.32-23.37

which of these should I mark for complete removal?

Thanks in advance, Lidex

JA

---

### Post by jda8818 on 2010-07-23
OK, it turns out that one marks "linux-image-6.32-23-generic-pae" for "complete removal" and that entire kernel and header packages are removed.

I then ran your suggested steps Lidex, and here are some results:

```
jadcock@HTPC:~$ uname -a
Linux HTPC 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux
jadcock@HTPC:~$ 
``` note that this is not the latest kernel

```
jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ 
``` still no HDMI devices 

```
jadcock@HTPC:~$ dpkg -l | grep "alsa"
ii  alsa-base                                 1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-firmware-loaders                     1.0.22-0ubuntu1                                 ALSA software loaders for specific hardware
ii  alsa-oss                                  1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-source                               1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-tools                                1.0.22-0ubuntu1                                 Console based ALSA utilities for specific ha
ii  alsa-tools-gui                            1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardwa
ii  alsa-utils                                1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                                4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                           0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                        0.10.28-1                                       GStreamer plugin for ALSA
jadcock@HTPC:~$ 
``````
jadcock@HTPC:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC888
jadcock@HTPC:~$ 
```next re-run the AlsaUpgrade script?

Thanks in advance for any comments or suggestions,

JA

---

### Post by jda8818 on 2010-07-23
Re-ran AlsaUpgrade Script, no joy, no changes.

I feel like I'm in a dark basement, feeling around, looking for the light switch.  

ALSA v PULSEAUDIO ...  anyone know of a description of how these two packages are supposed to  interact??

As always, comments or  suggestions are always appreciated ...

JA

---

### Post by lidex on 2010-07-24
OK. Let's try to get back to defaults. Do this for me please. 
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub

```
```

rm -r ~/.pulse ~/.asound* 
sudo rm /etc/asound.conf
```
Reboot into latest kernel and re-install alsa:
```
sudo apt-get purge linux-sound-base alsa-base alsa-utils

```
```
sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```
**gdm and ubuntu-desktop usually get taken out in the process, so we add them back**
**Reboot.**

With new config run the alsa-info script. Right-click the alsa-info script link in my sig and "save as" to your user folder. Then run this command in a terminal:
```
sudo bash utils_alsa-info.sh
```
Enter your user password when prompted. Provide a link for the output or post it here using code tags.

---

### Post by jda8818 on 2010-07-24
the good news first:  Analog sound is back!  Including flash in Firefox.

The strange news: Despite update, upgrade, my latest kernel is -22 (but it is working and not crashing)  I guess this is actually more good news.

the bad news:  Intel HDMI sound card devices are not recognized (aplay -l).

```
jadcock@HTPC:~$ sudo bash utils_alsa-info.sh
ALSA Information Script v 0.4.59
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See 'utils_alsa-info.sh --help' for command line options.

Automatically upload ALSA information to www.alsa-project.org? [y/N] : y
Uploading information to www.alsa-project.org ...  Done!

Your ALSA information is located at http://www.alsa-project.org/db/?f=fd53d412bbc4dade17dfc092537a25e161dbb60a

Please inform the person helping you.

jadcock@HTPC:~$ 


```Thanks, Lidex.

Hope to hear from you soon

JA

---

### Post by lidex on 2010-07-24
This line from alsa-info:
```
[   14.385395] hda_codec: ALC888: BIOS auto-probing.

```
tells us we need to add a model name to alsa-base.conf

These I would like to see at  1.0.23 for all:
```
!ALSA Version
!!------------
Driver version:     1.0.23
Library version:    1.0.23
Utilities version:  1.0.22

```
That would require you to rerun the alsa-upgrade script, which probably should be done anyway since we reset you to defaults.

In the modules section, I do not see the hdmi module loaded. It must have been loading previously as the hdmi devices were recognized earlier.

Try this:
```
sudo modprobe snd-hda-codec-intelhdmi

```
Now this:
```
aplay -l
```

---

### Post by jda8818 on 2010-07-25
Good Morning Lidex,

I'm unsure as to what model name to add to alsa-base.conf

Other than that, I re-ran the AlsaUpgrade script, and the 

```
sudo modprobe snd-hda-codec-intelhdmi

```command.  

aplay -l is unchanged, that is to say the hdmi devices are still not loaded/recognized.

Comments or suggestions are always appreciated!

JA

---

### Post by lidex on 2010-07-25
Did you recently change/update your video driver?

---

### Post by jda8818 on 2010-07-25
Bingo!

```
jadcock@HTPC:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI 0 [INTEL HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 7: INTEL HDMI 1 [INTEL HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jadcock@HTPC:~$ 
```The "BIOS auto-probing" message prompted me too reset my bios to it's default values, come to think of it i had to set the bios date and time after the crash that prompted this thread ... (i was prompted to do so).  so somehow the bios was disrupted.

anyway, all is well except audio in flash, which i  suppose is because we wiped out the asound.conf file earlier in this thread.   I will re-create and post.

Thanks so much for your patience and help, Lidex!

JA

---

### Post by lidex on 2010-07-25
What kind of crash could you have that would affect the bios? Tell me you were using windows.

---

### Post by jda8818 on 2010-07-25
Nope, notihing on this machine except Ubuntu 10.04 ...

but i may have a hardware problem of some sort.  if so, it is very intermittent.  the old story, "if it ain't broke, i can't fix it" applies in this case.  nothing to do but keep going.

JA

---

### Post by jda8818 on 2010-07-25
OK, i re-created the etc/asound.conf file and rebooted, EVERYTHING works.

Thanks Lidex, hopefully I'll be able to leave you to your other devices (at least for a while).

JA

Footnote:  this is a completely new system, Ubuntu 10.04 is the only OS ever installed on this hard drive.  Absolutely no quirky behavior prior to this thread.  And seemingly stable now.

---

### Post by lidex on 2010-07-25
You must have disabled hdmi in the bios. That would explain why it wasn't recognized. All is good now though. Just remember next time you have a problem to report everything that happened or was changed prior to the issue no matter how unrelated it may seem. Good Luck ;)

---

### Post by jda8818 on 2010-07-25
More correctly Lidex, ***something*** disabled hdmi in the bios.  After a kernel upgrade i might add.  As you are well aware, i have spent many many hours trying to enable and preserve hdmi sound on this machine; it seems unliklely that i would disable it. What's more, i can't find any documented way to accomplish this.

I should have mentioned a bios date and time update prompt when i was able to reboot after the crash (lockup) that prompted this thread (see my first post).  That probably would have required less effort on your part which i will thank you for again.

A brief visit to the "Installation and Update" area on this forum leads me to believe that there may have been problems with kernel 2.6.32-23.  You may recall that i'm running 2.6.32.22 after removing 2.6.32.23.

UpdateManager on my machine does not request any kernel updates for some reason.  Are any kernel updates being withheld?

Since everything (i hope) is working correctly at this point, i don't see any reason to run any more updates.  At least not kernel updates.

Thanks Lidex,

JA

---

### Post by lidex on 2010-07-25
Oh no, not to infer you knowingly disabled it . Seems strange though and I'm curious as to how that could happen. I guess it's possible to corrupt the bios via the OS but at what level does the OS have write access to it? Seems that would be a glaring security flaw.

Whatever happened seems to revolve around kernel 2.6.32.23 and no need to revisit that. I had a problematic kernel in Maverick Testing that I had to purge and it never resurfaced again in updates or synaptic. Not sure how that works?

I have seen 24 out there but it may be in proposed.

---

### Post by jda8818 on 2010-07-26
OK, thanks for that Lidex.

And yes, it is an odd set of circumstances.  I still have not ruled out some sort of a hardware situation, but everything is still solid and working ...

Thank you again Lidex,

JA

---

### Post by lidex on 2010-07-26
Glad you're up and running! If you would please mark the thread as solved - use 'Thread Tools' up top. Thanks.

---

