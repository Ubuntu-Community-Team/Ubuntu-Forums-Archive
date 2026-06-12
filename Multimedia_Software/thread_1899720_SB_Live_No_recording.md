---
title: "SB Live No recording"
date: 2011-12-24
forum: Multimedia Software
---

### Post by Trompette83 on 2011-12-24
Hello,

My config
Desktop HP DC5750, AMD Athlon 64 X2 Dual Core Processor 4200+, 8 GB RAM, nVidia GeForce GT 240, SB Live! 5.1 [SB0060] emu10k1
Ubuntu 11.04 /64

After trying a lot of configurations, reading lot of threads, I still can't record from my SB card.
Record works fine with internal card but with statics, it's why I want to use the SB.

I use 
- Gnome Sound preferences > Hardware > SBLive! > Profile Analog Stereo Duplex

- Gnome Sound preferences > Input > device SBLive! > Connector Analog Line-In > Volume 100% > Unmute

- Gnome ALSA Mixer

I can hear sound perfectly in the output to amplifier but nothing can be recorded.
I think I should see the input level activity flashing in Gnome Sound preferences.
I can only see the level with the internal sound card.

Can someone tell me, with a similar config well working:
In Gnome Sound preferences, Input, can you see the Input level + or - activity regarding the Input volume?

Is there a bug? or a update to install?

Thanks for your help

---

### Post by Lampi on 2011-12-24
what happens if you disable your internal card? This can be done inside your BIOS.

---

### Post by Trompette83 on 2011-12-24
I did it. In both cases no recording.

I wrote 2 scripts with pacmd and amixer command lines to set-up as good as possible, but no success.

More and more I think the is a bug but I can't prove it.

Other suggestion?

---

### Post by Trompette83 on 2011-12-24
I tried with a microphone, no recording with the SB card

---

### Post by Lampi on 2011-12-24
check [https://bugs.launchpad.net/ubuntu/+source/alsa-driver](https://bugs.launchpad.net/ubuntu/+source/alsa-driver)

to find bugs concerning your card

consider to update alsa yourself using the alsa-update script redux

---

### Post by Trompette83 on 2011-12-24
I had a look on the bugs page.
Some seem to be similar but not exactly the same card.
ie: If you enter record soundblaster in the search, bug 465812.
Do you think I could post a bug? I never did it and I am basic with Ubuntu/Linux.
Could you have a look and let me know?

Regarding the update:
[http://ubuntuforums.org/showthread.php?t=1681577](http://ubuntuforums.org/showthread.php?t=1681577)
ATTN Ubuntu Natty/11.04 users: ALSA 1.0.24 is now the default for this version of Ubuntu. This script should be unnecessary unless you need to apply a special patch against vanilla ALSA sources.

I think I shouldn&#8217;t have to run it, should I? Why?
I have ALSA 1.0.24 this is the last version.

Thanks for your help

---

### Post by Lampi on 2011-12-24
agreed, you don't need to update alsa

bug #465812 is confirmed without a solution

does [URL="http://www.linuxquestions.org/questions/linux-hardware-18/the-microphone-doesnt-work-with-creative-sound-blaster-live-platinum-5-1-a-
813205/"]this[/URL] help change profiles?

Also read [this]("http://alsa.opensrc.org/Emu10k1") article in alsa-project wiki about your card.

---

### Post by Trompette83 on 2011-12-24
Your first link doesn't lead to the page. Could you post it again?

Could you confirm that in Ubuntu "Sound Preferences" it should have the bar-graph flashing with a valid input even when there is no recording application?

---

### Post by Lampi on 2011-12-24
nope, I can't confirm (don't have an external card)

---

### Post by Trompette83 on 2011-12-24
Thanks, I'll post a bug

Have a good evening

---

### Post by Trompette83 on 2011-12-25
Important information!!

I have run Ubuntu 11.04 on a USB live and .... it's working !!!
Just I have to select the right card and right input in Gnome Sound Preferences and I had the bar-graph flashing.
Recording with microphone works as well.

So, I would like to avoid a full re-install and need to compare the different package versions in the two 11.04 installs.

Could someone tell me what command line I have to use to get the packages versions in the sound area. I mean something like Ubuntu-bug report where all the information are gathered in one shot and I can copy in a file.

Thanks

---

### Post by Trompette83 on 2011-12-25
To answer my previous question, how to get the versions:

Open a terminal
Run ubuntu-bug
Answer the first question > You will have the PID of the process 
Run ubuntu-bug <PID> --save=<PATH>

I did that on the installed and Live versions. Bellow the difference:

[B]First line: Installed – No record
Second line: Live – Working fine[/B]

[B]Linux version 2.6.38-13-generic
Linux version 2.6.38-8-generic[/B]

dbus 1.4.6-1ubuntu6.1
dbus 1.4.6-1ubuntu6

dpkg 1.16.0~ubuntu7.1
dpkg 1.16.0~ubuntu7

initramfs-tools 0.98.8ubuntu3.1

 initramfs-tools-bin 0.98.8ubuntu3.1
initramfs-tools 0.98.8ubuntu3 [modified: usr/sbin/update-initramfs]

 initramfs-tools-bin 0.98.8ubuntu3

initscripts 2.87dsf-4ubuntu23.1
initscripts 2.87dsf-4ubuntu23

libbz2-1.0 1.0.5-6ubuntu1.11.04.1
libbz2-1.0 1.0.5-6ubuntu1

libdbus-1-3 1.4.6-1ubuntu6.1
libdbus-1-3 1.4.6-1ubuntu6

libpam-modules 1.1.2-2ubuntu8.4 libpam-modules-bin 1.1.2-2ubuntu8.4 libpam0g 1.1.2-2ubuntu8.4
libpam-modules 1.1.2-2ubuntu8 libpam-modules-bin 1.1.2-2ubuntu8 libpam0g 1.1.2-2ubuntu8

libplymouth2 0.8.2-2ubuntu23
libplymouth2 0.8.2-2ubuntu22

libpng12-0 1.2.44-1ubuntu3.1
libpng12-0 1.2.44-1ubuntu3

libpulse-browse0 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1 libpulse0 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1
libpulse-browse0 1:0.9.22+stable-queue-24-g67d18-0ubuntu3 libpulse0 1:0.9.22+stable-queue-24-g67d18-0ubuntu3

libsndfile1 1.0.23-1ubuntu0.1
libsndfile1 1.0.23-1build1

perl-base 5.10.1-17ubuntu4.1
perl-base 5.10.1-17ubuntu4

plymouth 0.8.2-2ubuntu23
plymouth 0.8.2-2ubuntu22

pulseaudio-utils 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1
pulseaudio-utils 1:0.9.22+stable-queue-24-g67d18-0ubuntu3

sysv-rc 2.87dsf-4ubuntu23.1
sysv-rc 2.87dsf-4ubuntu23

sysvinit-utils 2.87dsf-4ubuntu23.1
sysvinit-utils 2.87dsf-4ubuntu23

tzdata 2011n-0ubuntu0.11.04
tzdata 2011f-1

upstart 0.9.7-1.1
Upstart 0.9.7-1

x11-common 1:7.6+4ubuntu3.1
x11-common 1:7.6+4ubuntu3

[B]Package: pulseaudio 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1
Package: pulseaudio 1:0.9.22+stable-queue-24-g67d18-0ubuntu3[/B]

ProcVersionSignature: Ubuntu 2.6.38-13.53-generic 2.6.38.8
ProcVersionSignature: Ubuntu 2.6.38-8.42-generic 2.6.38.2

Obviously Pulseaudio is not the same. Is there any other package to change?
Could you tell me how to go to the Pulseaudio previous version?

---

### Post by Lampi on 2011-12-25
that would be:
```
aptitude install pulseaudio=0.9.22+stable-queue-24-g67d18-0ubuntu3
aptitude hold pulseaudio #otherwise it will reinstall the faulty one when you update your system. it**'s important to remember you put it on hold should you decide to dist-upgrade the installation.

```
Yesterday I found bug reports concerning your card, pulseaudio, and **playback**, maybe it also affects recording?

---

### Post by Trompette83 on 2011-12-25
I just tried to downgrade with Synaptic and Force version option.
Unfortunately I still had the same issue. Maybe I did not change all the packages.

I try your way right now

Thanks

---

### Post by Trompette83 on 2011-12-25
From my second PC

I downgraded with CLI, a lot easier.
Unfortunately, I restarted my PC but can't boot any more.
I had no chance to test sound

Error message:
Could not update file /home/xx/.ICEauthority
and after
there is a problem with the configuration server ...

I tried to fix for more than 2 hours with no success

Any idea?

Nota: I am not sure if I reinstall to get the login fixed. Your opinion?

---

### Post by Lampi on 2011-12-25
IIRC this file can be removed, X will recreate it.

Can't help you there, but I guess you are better of reinstalling, if possible into a new partition?

---

### Post by Trompette83 on 2011-12-25
I did 
sudo apt-get install gnome-session

and I can now login

but I have not top panel...

---

### Post by sgtGarcia on 2011-12-25
As for mic recording:

Install

```
Gnome Alsa Mixer
```

Go to the tab with Audigy ( it will be labelled something like SigmaTel STAC ).

Check for Mic, activate it, set it for max volume.

The problem is that on my Audigy 4 in Sound Preferences ( PulseAudio ), in the tab "Input", only one input ( listed as Audigy2 Value Analog Input ) is Line-In not Mic.
---------------------

P.S.

What do You want to record??

Line In?
Mic?
All?

---

### Post by Trompette83 on 2011-12-26
Finally I had to reinstall all from USB Live.
Hopefully I have a separate /home directory.

And now it's working fine for all inputs!!! and moreover I have pulseaudio 1:0.9.22+stable-queue-24-g67d18-0ubuntu3.1  :)

I can't understand for what reason it was not working.

BTW: Ubuntu Sound Preferences, tab Input shows the bar-graph flashing for internal or plugged input card

Thanks for your help

How to tag "SOLVED"?

---

### Post by Lampi on 2011-12-26
Glad you came to a working installation! I assume something must have been wrong in your sound/mixer configuration? Maybe you can try to compare the sound/mixer settings with the one in the old install, so you understand what was wrong there. But that's just me, I always prefer to understand what was wrong, so I might a chance to fix it in the future and don't need to reinstall.

"Mark as solved" is in the Thread Tools (red coloured box at the forum top)

Happy Holidays to you

---

