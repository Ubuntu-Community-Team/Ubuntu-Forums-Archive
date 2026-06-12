---
title: "HD WMV Codec?"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by BattleGnome on 2007-12-07
I am trying to play back a HD WMV trailer and I get the following message from Totem Movie Player.

[INDENT][I]The playback of this movie requires the following decoders which are not installed:

video/x-asf-unknown decoder
Windows Media Audio 9 decoder[/I][/INDENT]

Where can I get these decoders from?

---

### Post by Penguinnerd on 2008-01-08
I seem to have the same problem mentioned here.

I tried VLC, Xine and Gstreamer. none work

---

### Post by cor2y on 2008-01-08
the latest mplayer and ffmpeg have successfully decoded the vc1 codec aka wmv-hd.
Totem gstreamer and libxine have not.those media players use a frozen stable version of ffmpeg (to avoid conflicts) will not be able to decode the codec yet.
Media players that use the svn version of ffmpeg like videolan and mplayer will be able to decode and playback those files.

---

### Post by Penguinnerd on 2008-01-08
Okay, I'll try Mplayer. Thanks.

Edit: I just finished trying Mplayer, and it gave me an error: Cannot find codec for audio format 0x162.
It did not play audio at all. Is there something that I don't have installed?

---

### Post by cor2y on 2008-01-08
the latest version of mplayer AND use the w32codecs for the audio.
Ffmpeg does not decode some wma audio as yet.
you will need to have the restricted repos active to get the w32codecs.

---

### Post by Penguinnerd on 2008-01-08
I have the mplayer that I got from the ubuntu add/remove applications thing. How far does it usually lag behind?

I'll get the latest one and try it tomorrow. gotta go to bed.

---

### Post by flick on 2008-01-08
Nice little HOWTO at UbunutGeek that worked perfectly for me : [http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecs-in-ubuntu-710-gutsy-gibbon.html)

I have yet to come across any video clips that mplayer won't play now.

Hope that helps a little.

---

### Post by Penguinnerd on 2008-01-09
Thanks for the howto, I followed the steps and gpt the latest Mplayer but my audio still doesn't work. I guess I have other problems.

---

### Post by disturbedite on 2008-01-09
anyone that hasn't read this should:
[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Penguinnerd on 2008-01-10
I already did that. I still get the following error in Movie Player:
The playback of this movie requires the following decoders which are not installed:

video/x-asf-unknown decoder
Windows Media Audio 9 decoder

And still no sound in any of the other players. I think it's a problem that only affects WMV HD

---

### Post by rdasilva on 2008-04-28
I'm getting the same 0x162 error and I'm running 64bit ubuntu.  I understand that the w32codecs package has the correct audio codec to decode the audio used in WMV HD.  Does anyone know if the w64codecs package will be updated to the same support?

---

