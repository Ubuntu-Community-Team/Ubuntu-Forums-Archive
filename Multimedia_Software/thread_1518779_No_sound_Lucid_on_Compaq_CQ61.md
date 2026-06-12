---
title: "No sound Lucid on Compaq CQ61"
date: 2010-06-27
forum: Multimedia Software
---

### Post by MichaelSM on 2010-06-27
Having had problems with sound in Lucid, I fiddled around a bit - uninstalling and reinstalling Pulseaudio - then went too far trying to upgrade Alsa to 1.0.23 (I think). There were some glitches along the way and now I have no sound at all. Pulseaudio doesn't detect any hardware, and it has one output 'Simultaneous Output Stereo' which means SFA.

This is on a ComPres CQ61 with Intel audio card. If I run sudo lspci -v I get the following output:

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3069
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at 94500000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
        Kernel modules: snd-hda-intel

but there are no kernel drivers (HDA-Intel) mentioned.

The kernel is Linux 2.6.32.22-generic-pae

Can this self-inflicted mess be fixed? Is it possible/worthwhile to rebuild all the sound, or better to wait for MM 10.10 upgrade?

Any help appreciated.

Apologies. Mike.

---

### Post by lidex on 2010-06-27
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

### Post by lidex on 2010-06-27
Sound should work out of the box for this model in lucid. Did you add any options to alsa-base.conf? I would remove them, reboot and re-install alsa. To re-install alsa:
```
sudo apt-get install --reinstall alsa-utils alsa-oss alsa-base libasound2 libasound2-plugins linux-sound-base gstreamer0.10-alsa
```
**Reboot.**

---

### Post by MichaelSM on 2010-06-27
Here you go:

~$ uname -a
Linux michael-laptop-10.04 2.6.32-22-generic-pae #36-Ubuntu SMP Thu Jun 3 23:14:23 UTC 2010 i686 GNU/Linux

~$ aplay -l
aplay: device_list:223: no soundcards found...

~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-oss                                       1.0.17-3                                        ALSA wrapper for OSS applications
ii  alsa-tools-gui                                 1.0.22-0ubuntu1                                 GUI based ALSA utilities for specific hardware
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                                   0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard driver
ii  alsaplayer-common                              0.99.80-5                                       PCM player designed for ALSA (common files)
ii  alsaplayer-esd                                 0.99.80-5                                       PCM player designed for ALSA (EsounD output module)
ii  alsaplayer-gtk                                 0.99.80-5                                       PCM player designed for ALSA (GTK+ version)
ii  bluez-alsa                                     4.60-0ubuntu8                                   Bluetooth audio support
ii  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
ii  libalsaplayer0                                 0.99.80-5                                       PCM player designed for ALSA (interface library)
ii  linux-backports-modules-alsa-2.6.32-22-generic 2.6.32-22.13                                    Ubuntu supplied Linux modules for version 2.6.32 ALSA snapshots.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.22.23                                    Backported drivers for alsa-driver snapshot.
ii  python-alsaaudio                               0.5+svn36-1ubuntu1                              Alsa bindings for Python

~$ head -n 1 /proc/asound/card*/codec#*
head: cannot open `/proc/asound/card*/codec#*' for reading: No such file or directory

Some of that output looks dodgy to me!!!

Thank you lidex for your interest. Rather than re-install alsa as per your second post, I think I'd better wait for your later opinion.

Don't know what you mean by 'Please post text output using code tags (the # in toolbar).'

The laptop is a Compaq Presario CQ61-210TU. Really basic but the best comp I've ever had!

Mike.

---

### Post by lidex on 2010-06-27
Dodgy, yes:
```
~$ aplay -l
aplay: device_list:223: no soundcards found...
```
Something screwy with your alsa install. Noticed you mentioned upgrading alsa. That would not have worked with backports installed. I recommend uninstalling that and following the directions in my other post.

---

### Post by MichaelSM on 2010-06-27
I did as you suggested - both backports dumped and alsa reinstalled, but still no sound card detected, and '/proc/asound/card*/codec#*' doesn't exist.
Maybe I should find some drivers for the sound card. I mean; I know it works because this laptop boots into Lucid, Linux Mint 8, or Win 7, and the sound is fine in the latter two.

Any advice greatly appreciated, lidex.

Mike.

All good now. Following a note I saw somewhere, instead of just uninstall then reinstall alsa, I ran  sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils then reinstalled alsa using your line in the previous post. I'm guessing the 'purge' got rid of a lot of garbage I'd dudded alsa-base.conf with. 
Thanks again!

Mike.

---

### Post by lidex on 2010-06-29
Thanks for updating us on that fix. Good job. I've been a little hesitant to recommend the purge command as it can cause deleterious side-effects if not done properly. So that didn't remove any other packages then?

---

### Post by MichaelSM on 2010-06-29
Good last question!

I'm very hesitant re. cause/effect but a couple of reboots later I could not boot into the -pae kernel and had to use the next one down on the grub list.

Some mention in the -pae kernel recovery screen about BUG: xxxxxxx and a 'soft lockup' CPU0 61s! or something like that.

I had a look around and couldn't find a repair simple enough for me, so I dodged the issue and just boot into this previous kernel..Linux michael-laptop-10.04 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux
.. my bad.

Any ideas?

Thank you.

Mike.

---

### Post by lidex on 2010-06-29
How about this:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-desktop
```
Then use synaptic to purge the pae kernel and header packages, reboot and re-install them.

---

