---
title: "Poor Sound Quality w/ RecordMyDesktop"
date: 2011-10-28
forum: Multimedia Software
---

### Post by johnsmoke on 2011-10-28
I'm playing a music file in VLC player and want to capture the video with RecordMyDesktop. When I record it, the video looks great, but the sound is of significant less quality than the original MP3. Is there a way that I can set this so that the output video file has the same sound quality as the original Mp3? The sound setting is set to "Default" in RecordMyDesktop

---

### Post by shantiq on 2011-10-29
THE SHORT WAY
=============


WEll VLC will do that for you and keep the original quality of both sound and image


click  on view/advanced control


now you have a red button at the bottom of your VLC

press it at the start of your track and again at the end   and fish resulting file in Music folder :)







THE LONG WAY
============

try number 4 [**here**]("http://ubuntuforums.org/showpost.php?p=10579930&postcount=1") with ffmpeg


or this with [**sox **]("http://ubuntuforums.org/showthread.php?t=1805550")

---

### Post by johnsmoke on 2011-10-29
You know what, I was using Movie Player. I had no idea that you could record with VLC! That works for me! Although I looked at the visualizations and they're not that great. Any way to add more visualizations? I'll be searching for a way to do that, if anyone knows, I'm all ears. Thank you for that tip Shantiq! :D



> **shantiq said:**
> THE SHORT WAY
=============


WEll VLC will do that for you and keep the original quality of both sound and image


click  on view/advanced control


now you have a red button at the bottom of your VLC

press it at the start of your track and again at the end   and fish resulting file in Music folder :)







THE LONG WAY
============

try number 4 [**here**]("http://ubuntuforums.org/showpost.php?p=10579930&postcount=1") with ffmpeg


or this with [**sox **]("http://ubuntuforums.org/showthread.php?t=1805550")

---

### Post by johnsmoke on 2011-10-29
[LEFT]It looks like when you record with VLC player it just records it as an MP3 file, without the visualization.... I need to capture the audio with the visualization effects as the video. I'm stumped now, I was confused as to how to perform that code in #4.... any help at this point would be great. Basically it looks like I just need to configure RecordMyDesktop with my sound card to record from it and get the audio properly, but I have no idea how to do that. PLease help :(
[/LEFT]

---

### Post by shantiq on 2011-10-30
hi again john


use the long way explained there maybe. THAT will take it all in

not sure what you mean by vizualization   mp3 do not have those they are just a music file


If you want to capture desktop and onboard sound [playing audio] then use that LONG WAY explained in the link above...

---

### Post by johnsmoke on 2011-10-30
> **shantiq said:**
> hi again john


use the long way explained there maybe. THAT will take it all in

not sure what you mean by vizualization   mp3 do not have those they are just a music file


If you want to capture desktop and onboard sound [playing audio] then use that LONG WAY explained in the link above...

I just meant capture the video (visualization) that movie player displays. I used the long way, and basically managed to configure pavcontrol to record the audio properly when I use RecordMyDesktop, thanks to your instructions! THANK YOU so much.

---

