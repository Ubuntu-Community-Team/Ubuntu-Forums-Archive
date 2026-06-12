---
title: "jack took all my sound (installed and removed jack now i have no playback on 8.04)"
date: 2008-05-22
forum: Multimedia Software
---

### Post by tich on 2008-05-22
hi.
i recently installed, then uninstalled jack. i intended to do some audio editing but i never got jack and pulse to work nicely together. now that i have uninstalled jack i don't have any sound at all.

i followed these forum posts for installing jack:
[http://ubuntuforums.org/showthread.php?t=646869&page=2](http://ubuntuforums.org/showthread.php?t=646869&page=2)
[http://ph.ubuntuforums.com/showthread.php?t=775144](http://ph.ubuntuforums.com/showthread.php?t=775144)

and i followed this to attempt to get pulse working again:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

i didn't do everything the post suggests but i did check the boxes in my users and group section and the stuff in the "configure pulseaudio" section


This is the warning i get when i attempt to start totem:
An error occurred.
Failed to connect stream: Invalid argument


This is all the info from my pulseaudio manager (tab by tab):

server information tab:

server name pulseaudio
server version 0.9.10
default sample type s16le 2ch 44100hz
host name my-laptop
default sink not set
default source not set

client info
linked to library version 0.9.10
compiled with library version 0.9.8

devices tab:

sinks
sources

clients tab:

esound client (unix socket client)
esound client (unix socket client)
pulseaudio manager

modules tab:
many many

sample cache tab:

pulse-hotplug


And this is the info from pulseaudio preferences:
network access tab:

enable network access to local sound devices
allow other machines...
don't require authentication
make discoverable network sound devices...

multicast tab:
enable multicast receiver
enable multicast sender
send audio from local speakers
(if i change from local speakers to -->create separate audio device for multicast and loopback audio to local speakers
the warning disappears but there is still no audio)

everything else is unchecked.

although totem and firefox don't have sound vlc player works no problem.

Any suggestions will be greatly appreciated!!

---

### Post by cor2y on 2008-05-22
check this thread about setting up Pulse
[http://ubuntuforums.org/showthread.php?t=776739&highlight=Pulse](http://ubuntuforums.org/showthread.php?t=776739&highlight=Pulse)
As for jack , go to synaptic and go to File->History to see all the installs/uninstalls you have done since the install of 8.04.
Then just reverse that by installing all the Jack appropriate things

---

### Post by tich on 2008-05-22
thanks, i will check out that thread.

actually i am going to leave jack uninstalled;
i hear that jokosher is going to be revamped and maybe i will create a partition and install ubuntu studio.

edit:
i did look at the thread and although i may fall back on it i don't think the whole thing should be necessary.

pulseaudio was working immediately after i installed hardy right up to when i removed jack so i should have all the necessary components on my computer already.  i am in the process of comparing the config files though to see if they are the same as in the thread.

---

### Post by tich on 2008-05-23
i just tried everything in that thread and my sound did not come back.

---

### Post by cor2y on 2008-05-23
Take a look at your synaptic history of what might have been removed along with jack.

---

### Post by Drunky on 2008-05-23
Quirky idea:

Uninstall Pulseaudio and reinstall it.

---

### Post by tich on 2008-05-26
i've had no luck with this for some reason.  the only piece of luck that i have had is that i installed jack right after a fresh install so it will be uber easy to reinstall ubuntu.

normally reinstalling seems like killing an insect with a hand grenade (not that i would actually know what that is like) but in this particular case it seems to be the simplest, easiest thing to do!

thanks for all you suggestions.

i am not going to mark this as solved seeing as reinstalling is not a reasonable solution for most people/situations.

---

