---
title: "VLC stops playing .MOV - only audio"
date: 2015-04-03
forum: Multimedia Software
---

### Post by thombark2 on 2015-04-03
Ubuntu 10.04

Until recently VLC played all of my .MOV files. Now it only has the audio playing. I have different .MOV files from different cameras. All of them are now sound-only but played perfectly before. I am fairly certain that it is not really a VLC problem. I installed some video editor programs and this might have impacted the codecs used by VLC.
 
When I try "movie player" I get "Internal GStreamer error: negotiation problem."

When I try Avidemux the first frame of the .MOV file appears but takes up the whole screen, then it stops working.

I cannot install Mplayer on my PC due to relocation errors.

Another clue - in Nautilus the .mov files now have the same filmstrip icon but all of the other formats (avi, mp4, mkv, m4v) have an actual frame from the video as an icon.

Any suggestions?

Thanks.

---

### Post by dino99 on 2015-04-03
it's time to move to an alive ubuntu release; 10.04 is now dead

---

### Post by thombark2 on 2015-04-03
Moving to a later version of ubuntu will cost me too much time at the moment. My old laptop will soon be replaced and then I will go for 16.04

---

### Post by howefield on 2015-04-03
Try Tools > Messages (verbosity = 2) before playing the file, do you get any clues in the log ?

---

### Post by thombark2 on 2015-04-03
It seems to play the file automatically so I stopped it after a short time. The only message was:
  [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR][COLOR=#000000]control type=1[/COLOR]

However when I loaded VLC and opened the file using the advanced open file option it gave me lots of messages. The attached file has all of the level 2 messages.

Here are the codec details from "Codec Information"

Stream 0
Type: Video
Codec: avc1
Resolution: 640x480
Display resolution: 640x480
Frame rate: 29.970029

Stream 1
Type: Audio
Codec: sowt
Language: English
Channels: Stereo
Sample rate: 48000 
HzBits per sample: 16

Thanks.

---

### Post by mc4man on 2015-04-03
10.04 is quite removed from my memory but it seems you caused this by installing some unnamed 'video-editors'
So figure out what changed because of those installs, from a package install & or removal perspective would be a good starting place.

It appears to be scaling issue so maybe check which version of libswscale is installed - 
```
apt-cache policy libswscale*
```

---

