---
title: "Rotate .3fp video from Andriod phone"
date: 2011-04-14
forum: Multimedia Software
---

### Post by BandD on 2011-04-14
I have a video I recorded on my cell phone in portrait instead of landscape.  I've googled and figured out how to rotate the video using mencoder, but I can't seem to get the audio track to record along with the video track

Here are the commands I've tried in the terminal:
```
 mencoder -speed .5 -vf rotate=1 -ovc lavc -oac pcm input.3gp -o output.avi
```
```
mencoder -speed .5 -vf rotate=1 -ovc lavc -oac lavc input.3gp -o output.avi
```

Any advice?

---

### Post by gotamangoflavouredrat on 2011-05-21
Welcome to the club

Tried this first : [http://ubuntuforums.org/showthread.php?t=825971](http://ubuntuforums.org/showthread.php?t=825971)
no video and cannot import in to PiTiHiVi

Scratching my head; will have to do it on a windows machine tomorrow

---

### Post by zander1013 on 2011-10-09
i see this thread has gone quiet. i ~can~ import the 3gp video from android htc into ubuntu 11.? but it is still sideways.

is there a way to rotate it in pitihvi once you get it there?

please advise.

---

### Post by zander1013 on 2011-10-09
okay sports fans,

it seems that if one installs OpenShot and then applies the rotate effect to the clip then right click on the clip to pop up a floating menu. click on Properties, Effect tab, set the Rotate X, Y and Z to 0.00. next set the Fixed Rotate X variable to 90.0. apply and this seems to deliver the required magic..

it would be great if you could mark this one solved:popcorn:

thank you :D

---

### Post by zander1013 on 2011-10-09
the problem now is the audio becomes unsynced...:(

which is another problem that might be resolved with study of OpenShot

---

### Post by zander1013 on 2011-10-09
the work around is here...
[http://ubuntuforums.org/showthread.php?t=1565073](http://ubuntuforums.org/showthread.php?t=1565073)

using WinFF convert the 3gp to DV -> "Raw DV for NTSC fullscreen" edit as above then export.

that seems to keep things synced up.:guitar:

---

