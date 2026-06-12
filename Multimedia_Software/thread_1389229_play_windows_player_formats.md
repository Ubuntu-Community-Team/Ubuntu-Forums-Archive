---
title: "play windows player formats"
date: 2010-01-24
forum: Multimedia Software
---

### Post by elliotbeken on 2010-01-24
hi all, 

i have ubuntu 9.10 and vidoes i want to play in wmv format, i then was asked to search for a codec/encoder but the search came back with this message..


video/x-asf-unknown decoder
Windows Media Speech decoder

does anyone know what i can do to play this format

---

### Post by mc4man on 2010-01-24
on a 32bit install [go here]("http://packages.medibuntu.org/"), pick whichever ubuntu release you have, and dl. and install w32codecs.

Then you can playback with mplayer (gui's if desired - smplayer, gnome-mplayer)
Most xine engine players will also work - totem-xine, xine-ui, gxine, ect. (xine players should have libxine1-ffmpeg installed also

gstreamer players may or may not with the gstreamer0.10-pitfdll plugin installed

64 bit install basically forget about it...

If you're running karmic you may have to do a restart after installing w32codecs, may not

---

### Post by elliotbeken on 2010-01-24
ahhh well i have 64bit ubuntu 9.10 :(

---

### Post by mwero001 on 2010-11-29
You can play .wmv codecs from both 32 (w32codecs) & 64 (w64codecs) bit machines.

You will need to enable some medibuntu repositories, though I advise you enable all.

Check out the url below on how to go about it:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)


Ciao!

---

