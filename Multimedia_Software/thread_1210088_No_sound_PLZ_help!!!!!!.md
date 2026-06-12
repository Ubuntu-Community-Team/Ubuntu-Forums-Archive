---
title: "No sound PLZ help!!!!!!"
date: 2009-07-11
forum: Multimedia Software
---

### Post by ranjith.ts on 2009-07-11
Hi guys,,,,

I am new to this ubuntu so plz help me...

My laptop is HP cq40 model with intel processor x64 architecture with 1GB ram
I installed ubuntu 9.04 64 bit version within windows using wubi.it installed fine and i used update manager and finished the updates but i cannot get sound.But i can get sound from my viista side but not from ubuntu

i did do lspci -v and got this

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3607
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 5c800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

i checked in the ALSA and sound card list for intel ICH9 family is not listed there.. so i am stuck don know what to do next??? :(

ANY HELP WUD BE appreciated 

Thank u

---

### Post by prshah on 2009-07-11
> **ranjith.ts said:**
> 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 3607
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 5c800000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel



As a first step, let's see if your sound card is recognized and loaded in Ubuntu. Open a terminal (Applications-Accessories-Terminal) and give the commands as below and post back the output.```
aplay -l
lsmod | grep snd
```

This will tell us what sound devices are available on your computer, as well as what modules (drivers, in windows-speak) are loaded for it.


Most likely your sound card is detected and correctly setup, and the relevant modules are loaded (from the output you have already posted).

In that case, it may be a problem with the speaker configuration. Right click your volume icon, and choose "Open Volume Control". Choose "Preferences" and check everything shown.

Max out all volumes, and unmute everything.

Open the "Switches" tab, and, if you have a setting "External Amplifier", please check it.

Now check the sound.

If it works, try muting the various audio sliders one by one to find out which one is being used. For example, you may find that to get speaker output, you may have to use the "Headphone" volume slider. 

Post back with your results for further recommendations. If it doesn't work, a couple of screenshots of your Volume Control app showing all the sliders may be helpful.

---

### Post by ranjith.ts on 2009-07-12
Thanks for ur suggestion......

But while i was waitng for someone to reply i checked this link [http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu](http://ubuntuforums.org/showthread.php?t=1043568&highlight=markbuntu) and did this

sudo gedit /etc/modprobe.d/alsa-base.conf

added this in the configuration file:

options snd-pcsp index=-2
options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1


and did this in the terminal:

killall pulseaudio

sudo alsa force-reload

pulseaudio -D

thats it and it started working fine...
Thanks for ur help also PRSHAH..

---

### Post by igorzwx on 2009-07-12
You see, a person installed Ubuntu 9.04 with wubi.
And now he should combat such problems.
It is not a human treatment of living beings!!!

I had SUSE since 2003, and Ubuntu since 2006,
and only now I have managed to fix some problems with my Ubuntu 9.04

I am now making experiments with Ubuntu Lite 0.09 Alpha 
on the old box for experiments.
It seems that it uses Ubuntu 8.04 Repositories,
but no Pulse seems to be installed.

**Audio Noise in Ubuntu**
[http://ubuntuforums.org/showthread.php?t=1035892](http://ubuntuforums.org/showthread.php?t=1035892)

---

### Post by Iwavns on 2009-09-15
I have the same laptop as you and faced the same problem also. I posted a thread but no one replied..then I saw your thread, did what you did, and solved the problem! Thanks a lot. 

P.S. I found the troubleshooting guide before I saw your thread, I did the procedures, but after 

killall pulseaudio

sudo alsa force-reload

there was a message box asking me whether to  reload or not, I didn't know what to do, so I press not reload, that's why I couldn't get it right the first time..

---

