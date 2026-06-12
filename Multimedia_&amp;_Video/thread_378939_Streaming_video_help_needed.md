---
title: "Streaming video help needed"
date: 2007-03-07
forum: Multimedia &amp; Video
---

### Post by 75sausage on 2007-03-07
I have been trying to get streaming wmv video to work in my edgy

I followed the RestrictedFormats instructions including the troubleshooting links as well as done some other things suggested by members.

I am a total newbie only having used Ubuntu for 2 weeks.

FIrst the stream would not even open in Totem. I installed the codecs and got it to open my files with sound ONLY, no video. I then followed the gstream rf/inspect procedure only to disable Totem somehow. It would buffer the stream but then hang.

I then un-installed and re-installed Totem to no effect (still hanged)

When I had TOtem uninstalled, I installed Mplayer but could not change the file association even after creating a dummy wmv file and changing Open With property.

Moreover, puting the link manualy into Mplayer produces a Fatal Error: Error openning/initializing the selected video device ( I am not sure which video device to choose, but several produced the same error.)

I then uninstalled all vid players, re-installed Mplayer and restarted. THe link I use does not get processed now with a system error that mms protocol is not recognised (mms://....wmv) even though Totem did in fact recognise it.

I got Mplayer to work by selecting GL as the Video Driver in preferences, but Video is extremely choppy at any size above normal.

I need to enable the streaming content to start in a player by clicking the link, not by inputing the link manualy.

I am at a loss. My comp is a Athlon XP 2700 with 1 GB ram and Riva TNT2 Ultra vid (distro driver).

help?

---

### Post by panch0 on 2007-03-09
Run this in a console window:

mplayer -vo xv 'mms://...whatever.wmv'

If it doesn't work, post the output you get.

---

### Post by 75sausage on 2007-03-11
I got the Video to work!:guitar: 

I added an mms handler to firefox config and set it to mplayer.

> Set as url: about:config
Rightclick in the main window --> new --> string --> network.protocol-handler.app.mms --> mplayer
Rightclick in the main window --> new --> boolean --> network.protocol-handler.external.mms --> true

THis is all and good the window opens up and plays videos but there are no controls for playback (play, pause, stop). Is there a way to enable this?

Secondly, will installing the binary driver files for my vid make the playback any better from your collective experience?

---

### Post by panch0 on 2007-03-12
> **75sausage said:**
> THis is all and good the window opens up and plays videos but there are no controls for playback (play, pause, stop). Is there a way to enable this?

Do you really need the video to be in the browser window? I usually open a standalone player (KPlayer) so I have all the controls under the sun.

> **75sausage said:**
> Secondly, will installing the binary driver files for my vid make the playback any better from your collective experience?

No, those only make difference for 3D gaming of whatever.

---

### Post by 75sausage on 2007-03-12
I have regular Ubuntu Edgy with Gnome distro. Isn't Kplayer for KDE?

---

### Post by panch0 on 2007-03-13
All the best programs are for KDE, and KPlayer is for KDE too, yes. Doesn't mean you can't run it on Gnome.

I don't think there is a Gnome frontend for MPlayer. MPlayer's own GUI is GTK based, but it's OK at best. Of course there are other engines like xine, vlc, gstreamer, but why settle for the second best? Just my opinion though.

---

