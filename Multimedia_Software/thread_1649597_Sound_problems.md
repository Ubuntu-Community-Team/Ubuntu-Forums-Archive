---
title: "Sound problems"
date: 2010-12-20
forum: Multimedia Software
---

### Post by aj5string on 2010-12-20
Hi.

I have been using Ubuntu as my main OS on my desktops for a couple of years now.  Started off with a HP with a Creative Labs XiFi soundcard, but am now using a Dell with a Creative Labs Audigy.

Sound worked perfectly on the Dell since a clean install (about 7 months ago).

I turned it on a week or so ago, and no sound!  Even the little sound indicator in the notification area has gone.

Any ideas?!

Alex.

---

### Post by cchhrriiss121212 on 2010-12-20
Try working your way through this guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by aj5string on 2010-12-20
Yeah - I had a look at that.

I did the first point (General Help - Start here if you have no idea why sound is not playing) and it all seems good.  I moved onto the next bit (Getting the ALSA drivers from a *fresh* kernel) and rebooted but made absolutely no difference.

In alsa (I got it up from terminal) the sound is not muted...

any more ideas?

Alex.

---

### Post by aj5string on 2010-12-29
Bump - anyone!?

I really don't want to have to re-install Ubuntu if I can help it!

---

### Post by lidex on 2010-12-29
A clean install, but did you upgrade to 10.10 after?
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by aj5string on 2010-12-29
Yep - upgraded to 10.10 after the install... sound issues did start before then tho...

[http://www.alsa-project.org/db/?f=00dacad363a87ea6bc66e33c4ae82c3ba8793294](http://www.alsa-project.org/db/?f=00dacad363a87ea6bc66e33c4ae82c3ba8793294)

HTH - I have tried some different things, but, am probably missing something!

---

### Post by lidex on 2010-12-29
Something probably got reset. See these:
[http://ubuntuforums.org/showthread.php?t=1567445](http://ubuntuforums.org/showthread.php?t=1567445)
[http://www.futuredesktop.org/maverick/images/audigy2-fix.png](http://www.futuredesktop.org/maverick/images/audigy2-fix.png)

---

### Post by aj5string on 2010-12-30
Hi - meant to say, I do really appreciate all this help!

Still no joy... I can't help thinking that part of the problem is the fact that the volume/sound icon has totally disappeared from the notification area - or am I just being stupid!?

---

### Post by lidex on 2010-12-30
According to markbuntu:
> The big problem with the audigy cards is that by default the analog/digital switch is set to digital. Open the sound mixer ( the little speaker) and uncheck the analog/digital switch. You may need to check it in preferences first to make it visible.

Try running in a terminal:
```
gnome-volume-control
```
to access. Post any error output.

Also. > **dMaggot said:**
> Hi all,
I have a SoundBlaster Audigy card too and had muting problems. You might want to try this:
On alsamixer, the second channel, named S/PDIF, should be muted while everything ese is unmuted/full volume
That solved my problem. My kernel is 2.6.32-25-generic, btw.


Try gnome-alsamixer.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

