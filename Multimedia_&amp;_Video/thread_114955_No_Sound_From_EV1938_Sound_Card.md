---
title: "No Sound From EV1938 Sound Card"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by wsmoser2004 on 2006-01-09
I originally tried posting this question in the Kubuntu Support forum, but didn't get any response...probably because it was in the wrong forum :) .

I am brand new to Kubuntu, and I installed 5.10 on a Gateway Solo 2150 laptop.  Everything so far seems to work except for the sound card, which is a Creative Labs EV1938 (searching Google, I've also come across the number CT4730).  I cannot get any sound to come from either the laptop speakers or the headphones, and when I log into KDE I get a message something like this: "/dev/dsp cannot be initialized.  Output will continue, but using the null output device."  In KDE System Settings, I have tried setting sound to "Autodetect", "OSS", and "ALSA", and none of the above seem to work.  I have also tried to change the volume (and mute/unmute) with alsamixer and KMix, and while both mixers seem to communicate (when I change the volume in one, it changes in the other) I still cannot hear any sound.  It looks like ALSA is loading the module "snd_ens1370", which I believe to be correct, but which is apparently not working.

I have searched endlessly on Google for a fix, and while I see many others with the problem, I have yet to find a solution.  Apparently this sound card is notoriously difficult to get working.  A month ago I had FreeBSD installed on this same laptop and I had the same problem under FreeBSD, but someone had issued a patch for a *.c file and that fixed the problem after I recompiled the kernel.  However I cannot find such a fix for Kubuntu.

There might be something simple I am missing here...I'm new to both Linux and ALSA, so it could be as simple as a setting to change or an updated driver to download, but so far I have found nothing.

Any suggestions?

---

### Post by FarEast on 2006-01-10
It seems that the ALSA module for 'Sound Blaster EV1938' is
'snd-ens1371' .

Do the following to know whether the modules is loaded and
the system recognizes your card;) .

```
$ lsmod | grep snd
$ cat /proc/asound/card[COLOR="Red"]s[/COLOR]
```

---

### Post by wsmoser2004 on 2006-01-10
Thanks FarEast.  I tried the commands you suggested, and to my surprise, nothing came up from **lsmod | grep snd**, and **cat /proc/asound/cards** returned with "/proc/asound/cards: No such file or directory".  I could have sworn ALSA was loading modules before (and now that I think about it, I believe ALSA was loading snd_ens1371).  

By playing around for a little while, I managed to load the module "es1371", which is an OSS module.  I now have sound and I can control it with KMix, but I know even less about OSS than I know about ALSA.  How do I make this module load at startup (so I don't have to type **modprobe es1371** every time I want to use sound)?  Can ALSA and OSS co-exist?  Will I have any problems with programs that want to use ALSA but can't because I'm using OSS instead and/or should I just keep trying to get ALSA working?  And finally, is there any kind of setup to use OSS (right now all I've done is **modprobe es1371** and it works)?

Thanks for your help.

UPDATE: 
I tried to load the ALSA module **snd_ens1371** with a **modprobe snd_ens1371** and I got the following errors:
```
FATAL: Module snd_ens1371 not found.
FATAL: Error running install command for snd_ens1371

```
...So, I can't load the modules for ALSA.  Also I've found a few programs already that are trying to use ALSA (amaroK and Kaffeine are the ones I've seen) but don't work.  I'll keep trying though...

---

### Post by FarEast on 2006-01-10
Hi,
It is odd that /proc/asound does not exist:confused: .
Are you running kernel-2.6.12-10? (type 'uname -r' to know that.)

---

### Post by wsmoser2004 on 2006-01-11
For some reason it seemed like the ALSA modules had completely disappeared from my computer...I think it might be because I used Adept to update my kernel, which might have gotten rid of them.  I did not know how to get them back, so I tried to recompile my kernel.  After a restart, I got a kernel panic saying that it could not load the root partition (or something similar).  Rather than spending endless amounts of time fixing this problem, I just did a complete reinstall with Breezy 5.10 (it was only about 2 weeks old anyway).  Now I have a fresh install but still no sound.  **uname -r** says that my kernel is 2.6.12-9-386.  ALSA is now loading modules again, so here is the output of the commands you wanted me try:

**lsmod | grep snd**
```
snd_ens1371            22240  1
gameport               14472  1 snd_ens1371
snd_rawmidi            22816  1 snd_ens1371
snd_seq_device          8204  1 snd_rawmidi
snd_ac97_codec         72188  1 snd_ens1371
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_ens1371,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  1 snd_pcm
snd                    48644  10 snd_ens1371,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  1 snd_pcm

```

**cat /proc/asound/cards:**
```

0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0x1800, irq 5

```

And if this is helpful at all, this is what **lspci** says about my sound card: ```

0000:00:09.0 Multimedia audio controller: Creative Labs Ectiva EV1938

```

Also, now that I've done a reinstall, I can't use **modprobe es1371** to load the OSS module.  It loads OK, but I don't get any sound.

---

### Post by FarEast on 2006-01-11
Hi, wsmoser2004

It seems that the module 'snd_ens1371' is properly loaded...
Have you checked the volume? (I think you have already done it.)

Well, there is a good tool(script) 'alsaconf' that current package
'alsa-utils' from Ubuntu team does not provide.
I recommend you to try it, for you can compile kernel-image:p .

Install '[COLOR="Red"]lib[/COLOR]asound2-dev', '[COLOR="Red"]pciutils[/COLOR]' and 'dialog' with APT.

```
$ dpkg --status alsa-utils
```
Execute above to know the version of alsa-utils which is already
installed on your system.

Download the source archive from:
[ftp://ftp.alsa-project.org/pub/utils/](ftp://ftp.alsa-project.org/pub/utils/)

Decompress it and enter the directory. Then
```
$ ./configure
$ make
$ cd alsaconf
$ chmod 755 alsaconf
$ sudo cp alsaconf /usr/local/bin
$ cd ~
$ sudo alsaconf
```
(Follow the dialogs.)

I hope this will help;) .

---

### Post by wsmoser2004 on 2006-01-11
Thanks for the idea, FarEast.  I've read a lot about alsaconf in forums, but I could never figure out how to make it work.  I did manage to compile alsa-utils and run alsaconf.  It detected my sound card and tried to configure it with snd-ens1371.  It ran the alsasound init script and amixer to set volume levels, and it ended with 

```

Now ALSA is ready to use.
For adjustment of volumes, use your favorite mixer.

Have a lot of fun!

```

I still have no sound however.  At first I was concerned that perhaps ALSA was not shutting down (alsaconf warns to shut down ALSA before running alsaconf) but I dropped down into single-user mode and ran alsaconf and I still had no sound when I went back into KDE.

Any more ideas?

---

### Post by FarEast on 2006-01-12
Hi :) 
I have searched with google and come across an article written by
a guy in my country.
He says that he chose 'Sound_Blaster_PCI_ 64' in the dialog shown
by alsaconf and it was a success.
Was the option listed when you ran alsaconf?

---

### Post by wsmoser2004 on 2006-01-12
Thanks FarEast...

I get two options when I run alsaconf.  One is **ens1371 - Creative Labs Ectiva EV1938** and the other is **legacy - Probe legacy ISA (non-PnP) chips**.  I have tried both; the first says that it was successful (but I still have no sound) and the second says "No legacy chips found" after it finishes.

---

### Post by FarEast on 2006-01-12
I have found another interesting thread.
Have you already read it?

[http://forum.xandros.com/viewtopic.php?p=97636&sid=5796fdf4c42e45d3a47c4e01d1eca503](http://forum.xandros.com/viewtopic.php?p=97636&sid=5796fdf4c42e45d3a47c4e01d1eca503)

FarEast:p

PS

Here is one more article (Can you read German?), solution using oss module.
[http://forum.kanotix.net/PNphpBB2-viewtopic-t-8144-highlight-ev1938.html](http://forum.kanotix.net/PNphpBB2-viewtopic-t-8144-highlight-ev1938.html)

---

### Post by wsmoser2004 on 2006-01-12
Thanks FarEast,

I had read the thread you mentioned, but I re-read it to see if I had missed anything.  I believe I've tried everything in that thread however.  

I can't read German, but I translated the article with Babelfish and tried to figure out what they were saying.  I think they were loading the es1371 module that is part of OSS.  I can also get sound working with that module, but I've found a few programs (amaroK and Kaffeine) that want to use ALSA.  They don't seem work with the OSS module loaded (because ALSA is not loaded I guess).  Maybe there is a way to make them work with OSS, but I don't know how to do it.  

I've heard of an ALSA/OSS emulator or wrapper or something...is there any way that I can use this wrapper to make ALSA use the OSS module?  If so, that might be best because I would get the best of both worlds (ALSA and OSS):p. 

Also (as an aside), how do I upgrade my kernel?  The last time I tried to update my kernel from 2.6.12-9 to 2.6.12-10 with APT, ALSA stopped working.  Do I have to do something differently?  Recompile the kernel?  :confused:

---

### Post by FarEast on 2006-01-12
I see, wsmoser2004:( 

According to some articles on the net, EV1938 can be driven by 'snd-es1371'
on some distro(certain version).  Let's continue with working around;) .

> Also (as an aside), how do I upgrade my kernel? The last time I tried to
> update my kernel from 2.6.12-9 to 2.6.12-10 with APT, ALSA stopped
> working. Do I have to do something differently? Recompile the kernel?

I also updated my kernel 2.6.12-10-386 to 2.6.12-10-686 with APT, and
ALSA works fine.

Below are current version of packages regarding ALSA:

alsa-base 1.0.9b-4
alsa-utils 1.0.9a-4ubuntu5
gstreamer0.8-alsa 0.8.11-0ubuntu5
libesd-alsa0 0.2.36-1ubuntu5 Enlightened Sound Daemon (ALSA)
libpt-plugins-alsa 1.8.7-1ubuntu1 Portable Windows Library Audio Plugin
libasound2 1.0.9-2

regards

PS
> I've heard of an ALSA/OSS emulator or wrapper or something...is there any
> way that I can use this wrapper to make ALSA use the OSS module?

I found something interesting.  Visit the web below to read the information
of 'ALSA compatibility library (libsalsa)'.

[http://www.opensound.com/](http://www.opensound.com/)

-----
BTW Did 'alsaconf' write anything in /etc/modprobe.d/sound ?
If not, let's make one more try!

Describe 'options [COLOR="Red"]snd-ens1371[/COLOR] index=0 enable=1' in it, execute 'sudo update-modules'
and restart the system.

Below is the output when I executed 'modinfo snd-ens1371' .

filename:       /lib/modules/2.6.12-10-686/kernel/sound/pci/snd-ens1371.ko
author:         Jaroslav Kysela <perex@suse.cz>, Thomas Sailer <sailer@ife.ee.ethz.ch>
license:        GPL
description:    Ensoniq/Creative AudioPCI ES1371+
vermagic:       2.6.12-10-686 686 gcc-3.4
depends:        snd-pcm,snd-rawmidi,snd,gameport,snd-ac97-codec
alias:          pci:v00001274d00001371sv*sd*bc*sc*i*
alias:          pci:v00001274d00005880sv*sd*bc*sc*i*
alias:          pci:v00001102d00008938sv*sd*bc*sc*i*
srcversion:     D3D8CC5AD67BB5BCEE48E2D
parm:           joystick_port:Joystick port address. (array of int)
parm:           enable:Enable Ensoniq AudioPCI soundcard. (array of bool)
parm:           id:ID string for Ensoniq AudioPCI soundcard. (array of charp)
parm:           index:Index value for Ensoniq AudioPCI soundcard. (array of int)

---

### Post by wsmoser2004 on 2006-01-13
Thanks for the info, FarEast...I updated all of ALSA's packages as per the versions you mentioned, and also the kernel.  You are correct, ALSA still works just fine.  I don't know what I did before to make it stop working.  

> 
BTW Did 'alsaconf' write anything in /etc/modprobe.d/sound ?
If not, let's make one more try!

Describe 'options ens-1371 index=0 enable=1' in it, execute 'sudo update-modules'
and restart the system.


**alsaconf** put the following in my **/etc/modprobe.d/sound**:
```

options snd  device_mode=0666
alias snd-card-0 snd-ens1371
alias sound-slot-0 snd-ens1371

```

Did you mean **ens-1371** or **snd-ens1371** in **options *ens-1371* index=0 enable=1**?  I have tried it both ways multiple times.  One time, I had tried it with **snd-ens1371**, found that it didn't work, changed it back to **ens-1371** and restarted the computer, forgetting about the **sudo update-modules**.  When the computer came back up, I tried to get sound but found that it didn't work.  I opened emacs to change **/etc/modprobe.d/sound** back to **snd-ens1371** and accidentally hit an arrow key in a direction my cursor couldn't move, and to my surprise I got a console beep!  (On this laptop the console beep comes out of the normal speakers.)  I even had mixer control over this beep with KMix.  However this was the only sound I could get out of the laptop...not very useful.  I have been playing around with the laptop since then, and I seem to have lost the beep and cannot get it back.  Are there possibly more options to be put in **/etc/modprobe.d/sound** that might make the card work more fully?

> 
Below is the output when I executed 'modinfo snd-ens1371' .


Mine is the same as yours, FarEast.

> 
I found something interesting. Visit the web below to read the information
of 'ALSA compatibility library (libsalsa)'.


That is very interesting, FarEast!  I briefly looked into it, but was unable to download the files.  I will work more on it later, but that would be exactly what I'm looking for!:p

---

### Post by FarEast on 2006-01-14
Hi wsmoser2004,

> Did you mean ens-1371 or snd-ens1371...

I wonder why I make mistakes so often in writing module/command names#-o 

> to my surprise I got a console beep!

Great :p 
It means that 'options snd-ens1371 enable=1' is necessary to enable
pcm output.  Maybe you can get sound in the following way, too.

```
$ cd /usr/share/sounds
(choose any sound file with extention .wav)
$ aplay xxx.wav
(or)
$ cat xxx.wav > /dev/dsp
```

If OK, then tweak preferences in 'Control Center' regarding sound.
I am convinced that you can come over the issue soon;)

---

### Post by FarEast on 2006-01-14
I usually use Gnome but KDE is also installed on my system.  So I tested if I can listen to sound on KDE.
I did the following and got sound.

[Control Center - Sound & Multimedia - Sound System]
Turn on 'Enable the sound system'.

[Control Center - Sound & Multimedia - System Bell]
Turn off 'Use system bell...'

[Control Center - Sound & Multimedia - System Notification]
Click 'Player Settings', select 'Use an external player' and specify '/usr/bin/artsplay' .
Drop down 'Event source', choose 'KDE System Notifications' and Click 'KDE is starting up'.
Click the 'play-back button' in the frame 'Actions'.

---

### Post by wsmoser2004 on 2006-01-14
Thanks FarEast,

Unfortunately I've been unable to reproduce the console beep:( .  I've tried lots of things, and I can't get it back.  I'm tempted to believe it was just a fluke...

As far as the settings you suggested in KDE, most of them were already set up that way by default for me.  Thanks for checking though :) .

I also tried you suggestions for **aplay** and **cat [filename] > /dev/dsp**.  **aplay** seemed to play the files fine, but I did not hear anything.  The **cat** command returned with "/dev/dsp: Device busy".  That could be because KDE takes complete control over the audio hardware, not allowing any programs to access it.

Until this problem is fixed and I can use ALSA, I'd like to use OSS (becuase I know of a module that works for OSS).  How would I go about disabling ALSA and making the OSS module load at boot?  Right now, I have to do **sudo modprobe -r snd_ens1371** to stop ALSA and **sudo modprobe es1371** to load the OSS module, and then restart the sound system in KDE.  If I could make the OSS module load at boot, that would make things easier...but I don't know how to go about making this module load.  If you know how to do this, that would be great :p.

---

### Post by FarEast on 2006-01-14
Hi,

> The cat command returned with "/dev/dsp: Device busy".

It is odd...  Here I can get sound with sound server (arts) running.
What *occupies* /dev/dsp ?:confused:  Processes which is using a device
can be detected with 'fuser'.  For example:

```
$ sudo fuser -v -m /dev/dsp
```

Anyway, it may be better to choose OSS driver for the moment :p .

> How would I go about disabling ALSA and making
> the OSS module load at boot?

It is easy.

Edit the files:
[/etc/hotplug/blacklist] Add 'snd-ens1371'
[/etc/modules] Add 'ens1371'

It was successful on my system with ymfpci.

---

### Post by wsmoser2004 on 2006-01-16
Thanks FarEast,

When I do **sudo fuser -v -m /dev/dsp** this is what I get:
```

trash: sudo fuser -v -m /dev/dsp
Password:

                     USER        PID ACCESS COMMAND
/dev/dsp             root          1 f....  init
                     root       2998 f....  udevd
                     root       6362 f....  dhclient3
                     root       6768 f....  rc
                     root       6813 f....  syslogd
                     root       6830 f....  dd
                     root       6845 f....  dbus-daemon
                     root       6858 f....  hald
                     hal        6871 f....  hald-addon-stor
                     hplip      6922 f....  python
                     root       6969 f....  apmd
                     root       7143 f....  kdm
                     root       7147 f...m  Xorg
                     root       7156 f....  hcid
                     root       7161 f....  kdm
                     root       7192 f....  anacron
                     root       7205 f....  atd
                     root       7218 f....  cron
                     root       7222 f....  S98usplash
                     root       7391 f....  chvt
                     wes        7395 f....  startkde
                     root       7428 f....  ssh-agent
                     wes        7457 f....  kdeinit
                     wes        7460 f....  dcopserver
                     wes        7462 f....  klauncher
                     wes        7464 f....  kded
                     wes        7473 f...m  artsd
                     wes        7475 f....  kaccess
                     wes        7476 f....  ivman
                     wes        7477 f....  kwrapper
                     wes        7479 f....  ksmserver
                     wes        7490 f...m  artsd
                     wes        7491 f....  kwin
                     wes        7494 f....  kdesktop
                     wes        7496 f....  kicker
                     wes        7498 f....  kbluetoothd
                     wes        7500 f....  klipper
                     wes        7501 f....  kio_file
                     wes        7502 f....  kio_media
                     wes        7505 f....  knotify
                     wes        7507 f....  kmix
                     wes        7508 f....  kio_uiserver
                     wes        7509 f....  kio_system
                     wes        7510 f....  kio_trash
                     wes        7519 f....  kio_trash
                     wes        7520 f....  konsole
                     root     kernel mount  /dev/.static/dev
                     root     kernel mount  /dev/pts
                     root     kernel mount  /dev/shm

```

I don't really understand this...there can't be that many processes using /dev/dsp...right?  I've also noticed this problem when using Kaffeine (a music player in KDE) with the OSS module.  It always tells me that /dev/dsp is busy, and that it can't play.  

> 
It is easy.

Edit the files:
[/etc/hotplug/blacklist] Add 'snd-ens1371'
[/etc/modules] Add 'ens1371'


Thanks!  That works quite nicely.

Also, thanks for all your help so far, FarEast.  I appreciate all the time and attention you've put into this problem.  :)

---

### Post by FarEast on 2006-01-17
Hi wsmoser2004,

> When I do sudo fuser -v -m /dev/dsp this is what I get:
> I don't really understand this...there can't be that many
> processes using /dev/dsp...right?

Below is what I get.
```
/dev/dsp             root          1 f....  init
                     root       3216 f....  udevd
                     root       6095 f....  dhclient3
                     root       6448 f....  acpid
                     root       6463 f....  syslogd
                     root       6476 f....  dbus-daemon
                     root       6489 f....  hald
                     hal        6494 f....  hald-addon-acpi
                     hal        6503 f....  hald-addon-stor
                     root       6813 f....  gdm
                     root       6814 f....  gdm
                     root       6870 f...m  Xorg
                     hplip      6970 f....  python
                     root       7133 f....  sshd
                     root       7146 f....  hcid
                     root       7198 f.c..  getty
                     root       7199 f.c..  getty
                     root       7202 f.c..  getty
                     root       7205 f.c..  getty
                     root       7206 f.c..  getty
                     root       7207 f.c..  getty
                     ms         8397 f....  startkde
                     root       8442 f....  ssh-agent
                     ms         8445 f....  dbus-launch
                     ms         8446 f....  dbus-daemon
                     ms         8472 f....  kdeinit
                     ms         8475 f....  dcopserver
                     ms         8477 f....  klauncher
                     ms         8480 f....  kded
                     ms         8488 f....  kxkb
                     ms         8494 f...m  artsd
                     ms         8496 f....  kaccess
                     ms         8497 f....  kwrapper
                     ms         8499 f....  ksmserver
                     ms         8500 f....  kwin
                     ms         8502 f....  knotify
                     ms         8504 f....  kdesktop
                     ms         8506 f....  kicker
                     ms         8507 f....  kio_file
                     ms         8511 f....  klipper
                     ms         8515 f....  scim-laun
                     ms         8519 f....  scim-help
                     ms         8520 f....  scim-pane
                     ms         8522 f....  scim-laun
                     ms         8524 f....  kcontrol
                     ms         8525 f....  konsole
                     ms         8526 f....  kio_file
                     ms         8527 f....  kio_file
                     ms         8528 f....  kio_file
                     ms         8529 f....  kio_file
                     root     Kernel einbinden  /dev/
                     root     Kernel einbinden  /dev/
                     root     Kernel einbinden  /dev/
```

A difference is that 2 'artsd's are listed on your system.
It may have something to do with the issue but I am not
sure...

> I appreciate all the time and attention you've put into this problem.

You are welcome;) .  I hope you will have control of your card with alsa.

---

### Post by wsmoser2004 on 2006-01-18
> 
A difference is that 2 'artsd's are listed on your system.
It may have something to do with the issue but I am not
sure...


That is an interesting observation FarEast...I have a vague memory of Kaffeine (which suffers from the same /dev/dsp problem) working shortly after I did a **killall artsd** at one point.  At the moment I'm using a different computer, so I can't try it right at this moment.  I will check later and see if it works.

---

### Post by FarEast on 2006-01-19
> I have a vague memory of Kaffeine (which suffers from the same /dev/dsp
> problem) working shortly after I did a killall artsd at one point.

I hope you will find a clue, wsmoser2004:) .

BTW Browsing the archive of ALSA mailing list, I found a 'friend' of you:) .
[http://article.gmane.org/gmane.linux.alsa.user/20918/match=ens1371](http://article.gmane.org/gmane.linux.alsa.user/20918/match=ens1371)

---

### Post by krinor1966 on 2006-01-20
Thank you FarEast !!

I needed a few tries, but now I enjoying my MP3 files from my dear Ubuntu!

But for some reason I still need to do 

sudo modprobe es1371

after boot up ...

I thought that by editing:

[/etc/modules] Add 'ens1371' 

I would get that ... 

any how: Thanks for a good newbie oriented and descriptive thread !

Kman

[FONT="Arial"][SIZE="1"]0000:00:00.0 Host bridge: Intel Corp. 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
0000:00:02.0 VGA compatible controller: Intel Corp. 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
0000:00:1d.0 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
0000:00:1d.1 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
0000:00:1d.2 USB Controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
0000:00:1d.7 USB Controller: Intel Corp. 82801DB/DBM (ICH4/ICH4-M) USB 2.0 EHCI Controller (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 81)
0000:00:1f.0 ISA bridge: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) LPC Bridge (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801DB/DBL (ICH4/ICH4-L) UltraATA-100 IDE Controller (rev 01)
0000:00:1f.3 SMBus: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
0000:02:01.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:05.0 Multimedia audio controller: Creative Labs Ectiva EV1938
0000:02:07.0 Ethernet controller: Digital Equipment Corporation DECchip 21041 [Tulip Pass 3] (rev 21)
0000:02:09.0 Serial controller: Timedia Technology Co Ltd PCI2S550 (Dual 16550 UART) (rev 01)

Creative Labs Vibra128 PCI soundcard ->Sound in Ubuntu

[/SIZE][/FONT]

---

### Post by krinor1966 on 2006-01-21
[QUOTE=krinor1966]
But for some reason I still need to do 

sudo modprobe es1371

after boot up ...

I thought that by editing:

[/etc/modules] Add 'ens1371' 

I would get that ... 
[/QUOTE]

Silly Me ! Add es1371 into  [/etc/modules] and it will load at BOOT ...

---

