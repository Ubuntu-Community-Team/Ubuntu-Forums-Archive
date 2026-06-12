---
title: "ATIIXP AC97 not working... I have tried many things"
date: 2008-06-12
forum: Multimedia Software
---

### Post by bdoobie on 2008-06-12
I am running a new Kubuntu Hardy install and cannot get a peep out of my ATIIXP AC97 onboard sound. The system is recognizing the card when I do lspci -v and I can modprobe snd-atiixp with no fatal errors
:confused:
I have been scouring the net for the past day and night doing different things to no avail. Such as attempting to blacklist the modem, etc..

I would very much appreciate someone helping me get this solved :)

---

### Post by markbuntu on 2008-06-13
I don't know if this works for Kbuntu but it is what I use to fix my sound when it gets all messed up, usually after fooling around with pulseaudio or jack. You may need to use some other methods but basically this is how I do it.

Also, I have the same ATIIXP AC97 onboard sound so I know it works in Ubuntu.

Emergency Sound Repair

1. Stop pulseaudio from loading at boot.
2. Start alsa-utils at boot.

I stopped pulseaudio by using Boot Up Manager (available in the repos as bum) to deselect it at startup.

and reenabled the alsa-utils in Sytem/Adminstration/Services

3. make sure all these are installed.

aconnectgui  (ALSA MIDI connection utility), optional
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome), optional
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

4. Set default alsa sound card to your sound card and change all the sound settings everywhere to alsa. 


5. Reboot 

6. Use gnome-alsamixer to set things up. (Gnome-alsamixer is easier for me but you can use alsamixer.)

NOTE: the firefox flash sound hijacking problem will be fixed with the new libasound2 and flash 10. ( It really does, I have tried it).

---

### Post by 5dolla on 2010-08-15
im having the same problem im getting no sound either

my out put from lspci -v 
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 2a25
    Flags: bus master, 66MHz, slow devsel, latency 64, IRQ 17
    Memory at fe02a000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ATI IXP AC97 controller
    Kernel modules: snd-atiixp

---

