---
title: "No Sound - aplay gives nothing, lspci shows soundcard"
date: 2011-04-04
forum: Multimedia Software
---

### Post by limescout on 2011-04-04
Hello,
I have had on and off problems with my sound for quite some time now.  Each time it would stop working, I would find a fix which would work for a month or so, then I would go back to having no sound.  I have had consistent sound on my Windows partition, so I don't think something is wrong with the hardware.  The first fix I used was using "sudo alsa force-reload" to get ALSA working again.  The latest fix I used was to add the line "options snd-hda-intel model=toshiba" to alsa-base.conf, which worked up until now.  My built-in computer speakers won't make any sound, nor will my external monitors when they are plugged into the headphone jack.  I do get sound when I plug in a pair of USB headphones.

I have tried using the Comprehensive Sound Problem Solution Guide ([http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)), but I run into a predicament...

aplay -l (with or without being root) gives...
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
:~$ 

```
lspci -v DOES show my soundcard though
```
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Toshiba America Info Systems Device ff50
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at d0640000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```
alsamixer isn't much help either.  It shows the name of my card in the top left, but there are no sliders to adjust.

I've tried compiling the modules from source, reinstalling through Synaptic, and plenty of other things, to no avail.

Does anyone have any suggestions for what I should do?
Thank you so much for your time.

EDIT:  Almost forgot:  Ubuntu 10.04 on a Toshiba Satellite U305-S5107

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by limescout on 2011-04-05
[http://www.alsa-project.org/db/?f=f6e1ce41be6a491acc5c151b0fe19e4f7378c5c0]("http://www.alsa-project.org/db/?f=f6e1ce41be6a491acc5c151b0fe19e4f7378c5c0")

Thank you for your time!

[COLOR="Red"]EDIT: I tried updating ALSA to the latest version once I realized the versions were all mismatched.  Now lib and utils are both .24, while driver is still on .23 (I don't know why, I didn't get any errors when compiling or installing)

so here is the new URL:[/COLOR]
[http://www.alsa-project.org/db/?f=4149b0bf6e35ec24f74f524ab0523672d5c03936]("http://www.alsa-project.org/db/?f=4149b0bf6e35ec24f74f524ab0523672d5c03936")

---

### Post by lidex on 2011-04-05
> **limescout said:**
> [http://www.alsa-project.org/db/?f=f6e1ce41be6a491acc5c151b0fe19e4f7378c5c0]("http://www.alsa-project.org/db/?f=f6e1ce41be6a491acc5c151b0fe19e4f7378c5c0")

Thank you for your time!

[COLOR="Red"]EDIT: I tried updating ALSA to the latest version once I realized the versions were all mismatched.  Now lib and utils are both .24, while driver is still on .23 (I don't know why, I didn't get any errors when compiling or installing)

so here is the new URL:[/COLOR]
[http://www.alsa-project.org/db/?f=4149b0bf6e35ec24f74f524ab0523672d5c03936]("http://www.alsa-project.org/db/?f=4149b0bf6e35ec24f74f524ab0523672d5c03936")
Edit alsa-base.conf and replace the line you added with this:
```
options snd-hda-intel model=ref position_fix=1
```
Reboot. Now:
```
aplay -l
```
```
dpkg -l | grep "alsa"
```

---

### Post by limescout on 2011-04-06
aplay -l
```
:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
:~$ 

```

dpkg -l | grep "alsa"
```
:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-modules-2.6.32-29-generic                 1.0.22.1+dfsg-0ubuntu3+2.6.32-29.58             ALSA modules for kernel 2.6.32-29-generic
ii  alsa-source                                    1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
rc  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
rc  libclalsadrv1                                  1.2.2-2                                         ALSA driver C++ access library
rc  libsdl1.2debian-alsa                           1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
rc  linux-backports-modules-alsa-2.6.32-27-generic 2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-28-generic 2.6.32-28.27                                    Ubuntu supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-29-generic 2.6.32-29.28                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-2.6.32-30-generic 2.6.32-30.29                                    Ubuntu supplied Linux modules for version 2.
ii  linux-backports-modules-alsa-lucid-generic     2.6.32.30.36                                    Backported drivers for alsa-driver snapshot.

```

Still no sound.  Thank you very much for your support!

---

### Post by lidex on 2011-04-07
First let's undo what you did. Completely remove these packages:
```
sudo apt-get purge alsa-modules-2.6.32-29-generic alsa-source libclalsadrv1 libsdl1.2debian-alsa linux-backports-modules-alsa-2.6.32-27-generic linux-backports-modules-alsa-2.6.32-28-generic linux-backports-modules-alsa-2.6.32-29-generic linux-backports-modules-alsa-2.6.32-30-generic linux-backports-modules-alsa-lucid-generic     
```

Next disable backports:
```
gksu software-properties-gtk
```
On the 'Updates' tab
Close that. Now re-install alsa:
```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```
**Reboot.**

For a 'command not found' error simply install aptitude:
```
sudo apt-get install aptitude
```

---

### Post by limescout on 2011-04-07
Ok, did all of that, no major errors.  Still no sound though.  Here's the new script output
[http://www.alsa-project.org/db/?f=7a0492bc9d1899f2b0df4c03726c4cb33a79d38c](http://www.alsa-project.org/db/?f=7a0492bc9d1899f2b0df4c03726c4cb33a79d38c)

---

### Post by lidex on 2011-04-09
> **limescout said:**
> Ok, did all of that, no major errors.  Still no sound though.  Here's the new script output
[http://www.alsa-project.org/db/?f=7a0492bc9d1899f2b0df4c03726c4cb33a79d38c](http://www.alsa-project.org/db/?f=7a0492bc9d1899f2b0df4c03726c4cb33a79d38c)

We're getting closer. Can you post these outputs (again) please:
```
dpkg -l | grep "alsa"
```
Your alsa install is still not right. Update your kernel - do you have have updates repo enabled? Where you disabled backports, make sure the top three items are checked. Run synaptic, click the reload button. Next search 'kernel'. In the results mark the packages 'linux-generic' 'linux-headers-generic' and 'linux-image-generic' for install and apply. Close that out. Open a terminal:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**

---

### Post by limescout on 2011-04-10
upgraded those packages and everything.  Here is dpkg

```
:~$ dpkg -l | grep "alsa"
ii  alsa-base                                      1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                                     1.0.22-0ubuntu5                                 ALSA utilities
rc  gnome-alsamixer                                0.9.7~cvs.20060916.ds.1-2                       ALSA sound mixer for GNOME
ii  gstreamer0.10-alsa                             0.10.28-1                                       GStreamer plugin for ALSA
rc  libclalsadrv1                                  1.2.2-2                                         ALSA driver C++ access library
rc  libsdl1.2debian-alsa                           1.2.13-4ubuntu4                                 Simple DirectMedia Layer (with X11 and ALSA 
rc  linux-backports-modules-alsa-2.6.32-27-generic 2.6.32-27.26                                    Ubuntu supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-28-generic 2.6.32-28.27                                    Ubuntu supplied Linux modules for version 2.
rc  linux-backports-modules-alsa-2.6.32-29-generic 2.6.32-29.28                                    Ubuntu supplied Linux modules for version 2.
:~$

```

As always, thank you SO much

---

### Post by lidex on 2011-04-10
Did it update your kernel:
```
uname -a
```

---

### Post by limescout on 2011-04-10
> **lidex said:**
> Did it update your kernel:
```
uname -a
```

I think I may have ran that command before rebooting.  Here's "uname -a"


```
:~$ uname -a
Linux ********** 2.6.32-31-generic #60-Ubuntu SMP Thu Mar 17 22:14:33 UTC 2011 i686 GNU/Linux
=:~$ 

```

---

### Post by limescout on 2011-04-10
```
:~$ uname -a
Linux D**********p 2.6.32-31-generic #60-Ubuntu SMP Thu Mar 17 22:14:33 UTC 2011 i686 GNU/Linux
:~$ 

```

---

### Post by limescout on 2011-04-12
Hello?  Is anyone still there?

---

### Post by lidex on 2011-04-12
Let's see an updated alsa-info text please.

---

### Post by limescout on 2011-04-13
[http://www.alsa-project.org/db/?f=5149f4d6e0141748221b6111d8d955c69e664eed](http://www.alsa-project.org/db/?f=5149f4d6e0141748221b6111d8d955c69e664eed)


Thanks as always :)

---

### Post by highflyr on 2011-04-13
FYI- Just did update for 2.6.32-31-generic #60-Ubuntu and it broke my sound (dummy output/no sound cards)```
# cat /proc/asound/cards
``` --- no soundcards ---. 

Rebooted to 2.6.32-29/30 and its back in action.

---

### Post by lidex on 2011-04-13
> **highflyr said:**
> FYI- Just did update for 2.6.32-31-generic #60-Ubuntu and it broke my sound (dummy output/no sound cards)```
# cat /proc/asound/cards
``` --- no soundcards ---. 

Rebooted to 2.6.32-29/30 and its back in action.
All good now?
Looks like the alsa modules/backports are making it work so when you update the kernel with no modules available, you lose it. 
At some point you may want to try LiveCD of maverick or a later kernel from here:
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
to see if it's fixed upstream.

---

### Post by limescout on 2011-04-13
I'm still not getting anything :( it's so bizarre. Recently I booted up Windows on the same machine, which I rarely do anymore. I noticed windows was having trouble with its sound as well! Could this be some kind of hardware problem? How would I know?
 
EDIT:  I tried out a live USB of maverick UNE, and sound was fine.  I like the Unity interface a lot as well, so I think I'm just going to upgrade to maverick UNE and hopefully the sound will work.  I'll keep you posted.

---

### Post by limescout on 2011-04-15
Hmm.  Install of Maverick went fine, but I still have no sound.  Sound workes on the live usb or cd, but never on the os installed on the hard disk.  Any clues?

EDIT:  It was completely from scratch, no upgrade.

---

### Post by limescout on 2011-04-17
Now sound doesn't work on the live USB either.  Does anyone have any idea what's going on?

Thanks

---

### Post by lidex on 2011-04-17
> **limescout said:**
> Now sound doesn't work on the live USB either.  Does anyone have any idea what's going on?

Thanks

So, new install?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by limescout on 2011-04-20
[http://www.alsa-project.org/db/?f=185c09c637f4bacf4dd8ae704b040283ca3172e8](http://www.alsa-project.org/db/?f=185c09c637f4bacf4dd8ae704b040283ca3172e8)

Thanks :)

---

### Post by lidex on 2011-04-20
Alright. If you make configuration changes and they don't work, please reset to default before trying something else. Remove your edit from alsa-base.conf and then follow the link in my sig to upgrade alsa.

---

### Post by limescout on 2011-04-21
YES!  Removed the line, upgraded to .24, now I have sound again!!!!

Thank you for all of your time.  If I could mail you a cake I would :popcorn:

---

### Post by lidex on 2011-04-21
> **limescout said:**
> YES!  Removed the line, upgraded to .24, now I have sound again!!!!

Thank you for all of your time.  If I could mail you a cake I would :popcorn:

I would so enjoy seeing SOLVED attached to this thread :)
It's under 'Thread Tools' up top.

---

### Post by limescout on 2011-04-22
AGH!  I did a reboot, and it's right back where it was before.  The card is recognized, but no sound devices >.<

[http://www.alsa-project.org/db/?f=51319e532ae427a59b94743889e4de64c13b6414](http://www.alsa-project.org/db/?f=51319e532ae427a59b94743889e4de64c13b6414)

Another thing I don't think i mentioned was that sound will work if I plug in a pair of cheap usb headphones... Something to consider.
[COLOR="Red"]EDIT:  Ubuntu did an update this morning.  When I rebooted, all of a sudden I have sound again!  It switches on and off... so strange.  I'll reboot a couple times and see if something in the update fixed it.  Hopefully my problem is solved.[/COLOR]

---

### Post by limescout on 2011-04-25
Sweet!  I rebooted several times last night and this afternoon, and my sound seems stable.  I'm gonna mark this as solved, thank you so much Lidex for all of your help :)

---

### Post by Yellow Pasque on 2011-04-25
You'll have to run the ALSA upgrade script with -i after every kernel update. I was going to make a dkms script for it, but it requires a lot of tedious typing and/or copying/pasting. Since I'm lazy, I'll leave that burden to the user. ;P

---

### Post by limescout on 2011-04-28
> **Temüjin said:**
> You'll have to run the ALSA upgrade script with -i after every kernel update. I was going to make a dkms script for it, but it requires a lot of tedious typing and/or copying/pasting. Since I'm lazy, I'll leave that burden to the user. ;P

if I knew what a "dkms script" was, or anything about writing scripts for that matter, then I'd do it myself :)  that's good information to know though, for when there is a kernel upgrade.

---

