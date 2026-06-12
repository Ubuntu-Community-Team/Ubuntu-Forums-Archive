---
title: "Weird buzzing noise"
date: 2007-04-03
forum: Multimedia &amp; Video
---

### Post by Splat on 2007-04-03
I have this weird issue with a buzzing sound being produced through speakers/headset on a clean install of Ubuntu 6.10 on my desktop. I can't figure it out at all. 

It starts buzzing early in the startup process. The buzzing changes tone/pitch depending on whether I'm doing something or not. Moving a window causes it to change slightly depending on how fast I move it. Running glxgears causes it to rise in pitch to a high screech. If the machine is just sitting there doing (pratically) nothing it's a steady, low-pitched buzzing.

At first I thought it might be the sound card / alsa drivers, so I played around with the sound settings. Even if I mute everything including master, the buzzing is still there.

It happens with both speakers and a headset plugged in, so it's neither of those.

It doesn't happen with windows xp on this very same machine, so I doubt it's a hardware flaw. The sound card, by the way, is the integrated nVidia nForce2 SoundStorm on the Asus A7N8X Deluxe motherboard.

By mere chance I discovered that for some reason when I start up the Totem Movie Player, it gets a little bit better. The sound disappears completely when the computer is idle, and is barely noticable (but still there) when moving stuff around, etc. This is without playing anything in the player, just starting it up. None of those effects happen with VLC, only Totem.

I'm totally lost, anyone have any ideas what could be causing this and/or how to fix it?

---

### Post by kolslorr on 2007-04-07
I am having this issue as well, its definitely a Ubuntu issue as my dual boot windows is having no issue.

he buzz noise are obvious when I simply turn the volume a bit louder.

---

### Post by eggdeng on 2007-04-07
You probably need to tweak the alsa driver. Post the output of
```
lspci
```
```
cat /proc/asound/cards
```
```
cat/proc/asound/version
```
so we can see what hardware / driver versions you are using.

---

### Post by mgmiller on 2007-04-07
One of my windows xp machines uses this motherboard and it will also produce weird buzzing noises.  I found muting the line in did the trick.  It was picking up some electrical interference somewhere.    Bring up your alsa mixer and try muting the line in part.  

I also had an illuminated keyboard that  would produce noises when my hands were near or on the keyboard, but not if I moved my hands away.

This mobo's integrated sound card seems to be very sensitive to emi.

---

### Post by kolslorr on 2007-04-07
```

kolslorr@kolslorr:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] SiS645 Host & Memory & AGP Controller (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS961 [MuTIOL Media IO]
00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
00:02.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 07)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:05.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AS [Radeon 9550]
01:00.1 Display controller: ATI Technologies Inc RV350 AS [Radeon 9550] (Secondary)

```

```
kolslorr@kolslorr:~$ cat /proc/asound/cards
 0 [CMI8738MC6     ]: CMI8738-MC6 - C-Media PCI CMI8738-MC6
                      C-Media PCI CMI8738-MC6 (model 55) at 0x9800, irq 17

```

```
kolslorr@kolslorr:~$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.14rc1 (Tue Jan 09 09:56:17 2007 UTC).
```

Please see screenshot for my volume control setting, I have already turned off all microphone or other unnecessary stuff...

Please help!!!

---

### Post by kolslorr on 2007-04-07
By the way, I found this and it makes most sense to me.

[http://www.experts-exchange.com/Hardware/Misc/Q_21850129.html](http://www.experts-exchange.com/Hardware/Misc/Q_21850129.html)

It basically not Ubuntu's fault, but I cannot explain why XP can get rid of the static/buzz while Ubuntu cant.

---

### Post by eggdeng on 2007-04-08
Ftom the output you posted, lspci identifies your soundcard's chip as a C-Media Electronics Inc CM8738 & your version of alsa is up to date. A guy on this thread

[http://ubuntuforums.org/showthread.php?t=385794&highlight=C-Media+PCI](http://ubuntuforums.org/showthread.php?t=385794&highlight=C-Media+PCI)

had a different set of problems with the same chip and solved them by replacing a configuration file called .asoundrc, which is a hidden file located in your home directory. There's no guarantee it will work for you but If you want to give it a try, open a terminal and first back up the file you are going to edit

```
sudo cp .asoundrc  .asoundrc_backup
```

Open the file in a text editor, e.g gedit

```
sudo gedit .asoundrc
```

replace the contents of the file with

```

# 6 channel dmix:
pcm.dmix6 {
type dmix
ipc_key 1024
ipc_key_add_uid false
ipc_perm 0660
slave {
pcm "hw:0,1"
rate 48000
channels 6
period_time 0
period_size 1024
buffer_time 0
buffer_size 5120
}
}

# upmixing:
pcm.ch51dup {
type route
slave.pcm dmix6
slave.channels 6
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}

pcm.duplex {
type asym
playback.pcm "ch51dup" # upmix first
capture.pcm "hw:0"
}

# change default device:
pcm.!default {
type softvol
slave.pcm "duplex"
control {
name "Software Master"
card 0
}
}

# for aoss
pcm.dsp "duplex"

pcm.dsp1 "duplex"

```

Save and reboot for changes to take effect. If you get no joy with this, just replace the file you edited with the original.

```
sudo mv .asoundrc_backup .asoundrc
```

Reboot and you are back where you started.

---

### Post by kolslorr on 2007-04-08
Solved my problem by setting mixer to this... see screenshot...

Hope it helps,

---

### Post by boast on 2007-11-24
> **kolslorr said:**
> Solved my problem by setting mixer to this... see screenshot...

Hope it helps,

dang, that didn't solve it for me :(

---

### Post by komputes on 2008-05-07
**I have the same issue on an Asus A7N8X** (nvidia chipset) tested with Ubuntu 8.04. The high pitched buzz is very low and I can't hear it when I play music, so I JUST END UP PLAYING MUSIC OVER IT ALL THE TIME!!!

:guitar:

@kolslorr - solutions on EE are for members, can you simply copy paste the part that made sense to you? Thanks. I don't have a CM8738, I have an A7N8X Deluxe like Splatt. I tried the screenshot instruction and this still didn't work for me.

@Splatt, I have reported a bug on launchpad, if you would like to add some comments, the address is: [https://bugs.launchpad.net/ubuntu/+bug/228024](https://bugs.launchpad.net/ubuntu/+bug/228024)
Please feel free to post or subscribe to that bug.

---

