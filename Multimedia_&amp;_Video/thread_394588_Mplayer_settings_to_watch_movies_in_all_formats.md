---
title: "Mplayer settings to watch movies in all formats"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by shivanand_v on 2007-03-27
hi 
i want mplayer configuration file to setup mplayer on Ubuntu. 
could please send the configuration setup files.

---

### Post by 1/0 on 2007-03-27
What config are you looking for? Why are you looking for a configuration? My config looks like this:

```
# Write your default config options here!

```

Are you installing from source or binary? Are you looking for codecs in order to watch different formats?

If you're looking for the codecs, [easyubuntu]("http://easyubuntu.freecontrib.org/get.html") might help.

---

### Post by shivanand_v on 2007-03-28
hi 
Thank you for replying me ..
i want setup mplayer on my laptop. 
i am using Ubuntu linux 6.10 version 
i have download the mplayer but when i am playing the dvd's using mplayer i am getting error message like "Error opening/initializing the selected video_out(-vo) device" 
how to setup this error. i want to play all type of formats on mplayer. 

please help me..

---

### Post by kinson on 2007-03-28
This should help you:

[https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2]("https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2")


Hope it helped.

Cheers,
Kinson :)

---

### Post by shivanand_v on 2007-03-30
Thank you very much ..
i am unable play the real player format applicaton using gxine.

---

### Post by kinson on 2007-03-30
Does it work if you try playing it in Totem? Cause real player files don't seem to play too well (for me ) in VLC or Mplayer. So currently I'm playing them in totem (after installing the codecs from the restricted formats link I posted earlier of course).

Cheers,
Kinson

---

### Post by 1/0 on 2007-03-30
Have you checked your drivers and video codecs in the preferences window? You could try x11 for the driver and FFmpeg for the codec and see if that helps.

---

