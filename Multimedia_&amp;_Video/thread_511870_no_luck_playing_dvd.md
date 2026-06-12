---
title: "no luck playing dvd"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by DrScum on 2007-07-28
I have followed the instructions on this link

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

and several other instructions from the Medibuntu page but I can't get a DVD to run with neither VLC, Totem, MPLayer or gxine.

The DVD is browsable in the file manager. 

VLC opens, I select open DVD, VLC closes 
gxine opens, I select file DVD error message reads "the xine engine failed to start no input plugin was found [...]"
Mplayer opens I selext video_ts error message reads "Error opening/initializing the selected video_out (-vo) device"
Totem Movie Player opens I select Play Disc... error message reads: "Totem cannot play this tipe of media (DVD) because you do not have the appropriate plugins to handle it"

The DVD plays fine in VLC on a Windows machine

---

### Post by dfreer on 2007-07-28
Check out this link and see if it helps:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_DVD_playback_capability)

EDIT: This looks like it is the same procedure that you already followed. Did you add the mediubuntu repository and try installing libdvdcss2 from there?

---

### Post by tbroderick on 2007-07-28
For gxine. do you have libxine-extracodecs installed?

---

### Post by DrScum on 2007-07-28
to dfreer
yep, added medubuntu repository and installed libdvdcss2 from there

to tbroderick
is libxine-extracodecs the same as xine extra plugins? The latter are installed, the former don't show up under add/remove

---

