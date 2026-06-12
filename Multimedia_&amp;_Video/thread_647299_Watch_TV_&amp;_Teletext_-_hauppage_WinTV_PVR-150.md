---
title: "Watch TV &amp; Teletext - hauppage WinTV PVR-150"
date: 2007-12-22
forum: Multimedia &amp; Video
---

### Post by farmfield on 2007-12-22
So I "accidentally" ordered a hauppauge WinTV PVR150 and I'm not really into using MythTV and alike, but having the card I might as well enable it as I accasionally use teletext - I only watch downloaded TV as Sweden are months after the US schedules anyway, not to mention broadcasted TV sucks as you actually have to keep the time, hehe, not my thing... :tongue:

But back the subject at hand. I tried the install the IVTV drivers from Synaptic but TVTime couldn't find any stream. Some say this is due to TVTime only being able to find uncompressed streams where the PVR150 offer an mpeg-encoded stream, but the I heard someone say as the card works with MythTV it must offer an uncompressed stream as well - so anyone know whats what?

---

### Post by fenian on 2007-12-22
TVTime won't work with your card you have to use mplayer or something else (VLC,Kaffeine,etc...).Also IVTV is installed by default in Feisty you just will need to add the tools package (to manually tune channels) ,you can do that with the comand...

> sudo apt-get install ivtv-utils

to watch tv using mplayer open a terminal aand type...
> 
mplayer /dev/video0

you may get onlt static that ok you just need to tune in a channel to do that open another terminal and type...

> ivtv-tune -c # -d /dev/video0

replace # with the channel number you want to watch.

---

