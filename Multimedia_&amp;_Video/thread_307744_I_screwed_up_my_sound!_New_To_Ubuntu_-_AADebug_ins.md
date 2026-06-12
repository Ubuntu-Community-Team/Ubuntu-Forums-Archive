---
title: "I screwed up my sound! New To Ubuntu - AADebug inside"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by YoYoCeramic on 2006-11-27
Hello everyone.  I am brand new to Ubuntu Linux (6.10), and I am generally extremely skilled in software problem solving. However, after a few days and some IRC face time, I am baffled.

Initially, when trying to fix a microphone problem by following the directions here: ([http://ubuntuforums.org/showpost.php?p=1717589&postcount=10](http://ubuntuforums.org/showpost.php?p=1717589&postcount=10))

it killed all my sound and now there is a little x by my speaker icon in the upper-right corner.

Here is the aadebug report:

======================
mrussell@mrussell-laptop:~/Desktop$ '/home/mrussell/Desktop/aadebug' 
ALSA Audio Debug v0.1.0 - Mon Nov 27 00:44:34 CST 2006
[http://alsa.opensrc.org/index.php?page=aadebug](http://alsa.opensrc.org/index.php?page=aadebug)
[http://www.gnu.org/licenses/gpl.txt](http://www.gnu.org/licenses/gpl.txt)

Kernel ----------------------------------------------------
Linux mrussell-laptop 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

CPU -------------------------------------------------------
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
cpu MHz         : 1000.000
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
cpu MHz         : 1000.000

RAM -------------------------------------------------------
MemTotal:      1034092 kB
SwapTotal:     2096472 kB

Hardware --------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
==============================

And I have no idea how to make heads or tails of this readout!  I have tried the step-by step guides on this forum, but I don't know if I have to mess with kernels or modules or what!  I don't even know what a kernel is (gulp).  I will work with you, and I look forward to any advice or recommendations you might give.  Thanks


If anyone can help me, please point me in the right direction.  This is a deal-breaker for me if I cannot get my Sound (and Mic) to work.

Mark

---

### Post by drphilngood on 2006-11-27
See [here]("http://www.sabi.co.uk/Notes/linuxSoundALSA.html") and [here]("http://www.ubuntuforums.org/showthread.php?t=205449").
I hope these help.

Good luck!

addendum:
I almost forgot; you might find some useful info at the [ALSA bugtracking system]("https://bugtrack.alsa-project.org/alsa-bug/my_view_page.php") site.

---

### Post by jsteve54302 on 2006-11-28
> ======================
Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Warning: /proc/asound does not exist
This indicates that ALSA is not installed correctly
Check various logs in /var/log for a clue as to why

Dev Snd ---------------------------------------------------
Warning: /dev/snd does not exist

And I have no idea how to make heads or tails of this readout!  I have tried the step-by step guides on this forum, but I don't know if I have to mess with kernels or modules or what!  I don't even know what a kernel is (gulp).  I will work with you, and I look forward to any advice or recommendations you might give.  Thanks


If anyone can help me, please point me in the right direction.  This is a deal-breaker for me if I cannot get my Sound (and Mic) to work.

Mark1.  The kernel is the core of linux - it handles things like low-level disk, video, and other i/o access, as well as most of the boot process.  It uses modules (removable/replaceable bits of code) to handle things like sound cards and such so that it doesn't have to be recompiled every time a dvice changes.  This requires a configuration file to tell it where the modules are and which ones to load.  It looks like this file got hosed.  Since the kernel isn't able to load the modules properly, the asound deamon (think "driver"), probably along with others that do who knows what :) doesn't load, so the virtual files /proc/asound and /dev/snd never get created, thus the latter errors.  To the heart of the matter, try these first (I've learned the hard way - getting too deep too fast can hose a whole system and force a reinstall):

Open a terminal and run:
```
sudo apt-get install --reinstall linux-sound-base alsa-base alsa-utils libasound2
```and reboot.  This reinstalls the sound system, and may fix the broken modules config, but if not, try

```
sudo apt-get install --reinstall linux-image-`uname -r`
```which will reinstall the kernel itself, and should at least restore a working modules config.

To get the mic working, all I can suggest is:

```
sudo rm /var/alsa/asound.state
<reboot computer>
sudo alsactl store
```and play around with the newly created /var/alsa/asound.state.  Make a backup first though:

```
sudo cp /var/alsa/asound.state /var/alsa/asound.state-backup
```Hope this helps :)

---

### Post by YoYoCeramic on 2006-11-29
Thank you to everyone for your help - I have got my speakers up and running now thanks to you. jsteve54302 - Thanks for your advice - I got my sound back online, however, when I follow your mic directions (sudo rm /var/alsa/asound.state) it tells me the file does not exist.

What does this mean?  Do I need to download it somewhere?

Mark

---

### Post by YoYoCeramic on 2006-11-29
problem with the Mic solved!  Thanks everyone.

---

