---
title: "Detecting camcorder woes...dv1394"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by yogo on 2007-08-06
As always I like to read through before adding a new thread, but after looking at several I did not find the answer.

My camcorder is connected but is not running correctly in Kino. I used everything from the [Ubuntu Firewire page ]("https://help.ubuntu.com/community/Firewire") and ran Kino as root.  I was able to capture a bit of video but I had mostly a black window that covered 3/4 of the video capture. 

I am not sure how to get rid of the black screen, I went thru the routine for VLC when watching videos and setting the correct output settings but thats a whole nother ballgame.



Any ideas?, also when I run Kino as root, there are many errors that show up in Konsole.

TIA

---

### Post by yogo on 2007-08-06
Ok I know the camcorder can connect thru Kino as I have captured two short clips, however now when I run Kino normally and as root, it does not connect to the camera and all options are grayed out to stop capture etc, the only capture I can click is from the right side panel of Kino.

What is missing?

Thanks

---

### Post by yogo on 2007-08-06
I have the camcorder capturing, what seems to be the problem is when Kino is run normally, it does not see the camcorder, when I run as root, Kino properly identifies camera IE Edit-preferences-dv1394 and my camera is listed in devices, the nomal method of Kino does not display anything for camcorder.

I still have the black preview covering almost the entire preview but it does not show in actual video.

Any ideas?


Also the playback has no audio and is pretty crappy, not smooth looks choppy and distorted.

---

### Post by yogo on 2007-08-06
Now the black window has disappeared from Kino in preview so that is good, hopefully the quality will not be choppy however what can be added to smooth this out, it looks great in the preview window now so I am hoping....just checked it

Playback is choppy and grainy and still no audio?

---

### Post by yogo on 2007-08-06
Here is somewhat of a resolution, VLC had problems with the video but produced the audio, the default media player had no audio and was choppy and grainy.

Kino produced good clean video and audio but these players could not handle it despite my tweaking setting for VLC in the Ubuntu wiki tips.

Xine played flawlessy the video and audio, not choppy or grainy, PERFECT.

So it was a player issue

However I get a "There is no MRL" error each time I run Xine but it displayed perfectly.

---

