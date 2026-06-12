---
title: "setting sound device order? (Dapper)"
date: 2008-01-14
forum: Multimedia &amp; Video
---

### Post by tparker on 2008-01-14
I need to find the file to edit that controls which sound device is "0", "1", "2", etc. A while ago I made a change to this file to fix a conflict between my USB headset, WoW, and Teamspeak. I have changed headsets and now need to go back to the line I commented out in the file instead of the one I added and for the life of me I cannot find the file I edited! :)

I know that I made the change by opening the file from command line (nothing GUI), I used gedit, it was a small file (<10 lines) that seemed to map my sound devices to the 'number' the computer assigned them.

I know (by process of elimination over the last couple days) that it is not:
etc/esound
etc/modules
etc/sound
etc/modprobe.d/alsa-base
etc/modprobe.d/options
etc/asound.conf
etc/X11/xorg/conf
asoundconf-gtk
/proc/asound/devices or/cards
I did not use asoundconf set-default-card<name>

Any ideas on what file I need? Without changing it back my new headset makes WoW and Teamspeak conflict and WoW is not playable. :(

Thanks.

Running Ubuntu Dapper amd64
onboard AC97 sound
was USB headset, now back to non-USB headset

---

### Post by tparker on 2008-01-14
I found it, it was a .sh that was setting the devices for me. In case anyone needs to do this in the future:

The shell script (mine is creatively titled 'defaultsound.sh') lists both my sound devices and I can switch between the two by commenting out the one I don't want:

#! /bin/sh -f

sudo asoundconf set-default-card CK804
#sudo asoundconf set-default-card Headset

---

