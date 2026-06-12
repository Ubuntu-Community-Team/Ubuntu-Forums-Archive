---
title: "&quot;Native&quot; ogg player -- canberra?"
date: 2009-03-09
forum: Multimedia Software
---

### Post by squidx on 2009-03-09
I'm trying to find the best way to play the most sound formats possible from a base install of Intrepid, from the command line.

I have been able to use aplay from the CLI to play .wav, etc., but not .ogg.

I understand that, at least at install, aplay cannot play .ogg -- can it ever?

I thought that something else might be needed to play ogg files, but I see that the startup sounds for Ubuntu are ogg. So I poked around (inexpertly) and found that they use "libcanberra" to play them, and in fact, with a command like

/usr/bin/canberra-gtk-play --id="desktop-logout" --description="GNOME Logout" 

the standard system sounds can be played. Of course the files must be in a particular place: /usr/share/sounds/ubuntu/stereo

I imagine that other .ogg files could be put in there or soft-linked from there, but what I want to figure out is what application "canberra" is using so I can control it better from the command line. Also, is there a chance that this is/can be routed through another player such as aplay in order to have a single player that can use all of the important sound formats?

It doesn't seem like common knowledge, at least on message boards, that no new program such as vorbis-tools/ogg123 is needed to play these files.

Of course, I may have missed a historical post on this subject. If so, please provide a link, and sorry!

Does anyone know what's up with this?

Alex

---

### Post by Unkuiri on 2009-07-08
Hi, I'm new to Ubuntu too and what I've discovered is that you can just use this comand:
> canberra-gtk-play --file="[any .ogg file path]"
and it will just play...:)...hope this helps...

---

