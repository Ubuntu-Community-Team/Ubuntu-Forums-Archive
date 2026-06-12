---
title: "Video playback problems on Gutsy"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by whayong on 2007-10-28
Hey everyone, I'm not sure how to decribe my problems, but I will try...

I upgraded to Gutsy last friday.  Since then my video play back (DVD or other) has been less then perfect.  I get these lines on my screen every now and then, enough to be noticed (and annoyed) when watching a video.  The lines appear in different locations at different times.  It seems to happen mostly when the scene is fast paced and there's a lot of camera movement.  Sometimes it happens when the scene is calm as well.

I am running the exact same box as I did wih Fiesty without any problem,  Graphics card is a Nvidia 7600.  Ny RAN is 2GB.  I tried turning down the effects but it still does the same thing.  Is there a solution for this already?  Anything I should be trying?  I am using the restricted drivers BTW.

Thanks!

---

### Post by slythfox on 2007-10-28
I am having a video problem, too, with my upgrade from Gutsy, when trying to play an avi. I get weird colors on top, and a sort of shadow.

I'm pretty sure this is a problem with whatever library plays avi files, because it happens with all my video players.

---

### Post by whayong on 2007-10-28
Yes, I did forget to mention it happens on all players.  Could it not be a driver issue?

---

### Post by opferstad on 2007-10-28
I'm having problems playing .avi files too. In the default Ubuntu video player the colors go all blue and the video itself "drops" halfway out of the video player window. In VLC the same things happen exept for the colors. Also, in VLC, the framerate is really messed up, white lines appear out of nowhere and in fullscreen mode I only see the top half of the video while the rest of my screen is blank.

---

### Post by sublimespot on 2007-10-28
I also have video problems in gutsy. The whole video is blue with lines.

---

### Post by TSP on 2007-11-13
i also have the same problem with all the video player i tried (mplayer, Xine, VLC, Kaffeine) and all the fortmats (avi/dvd,mpeg) the sunds is ok, but the vdeo is blue. It might be somethong with the X

---

### Post by imnotryan on 2007-11-13
I'm also having this problem.

The video during certain parts will break up and turn all sorts of funny colors and have a bright purple shadow of what the video previously was.  It makes watching videos completely impossible.

It does it to some movies and not others, and does so consistantly in every way.  It does it to some of every video format.  WMV's seem to get it worst i guess.

---

### Post by Krallus on 2007-11-13
Just wanted to add my own experience here.  Happens with all players, both AVI and MPG: green snow/static appears in shadowy areas of the images.  I was going to attach a screenshot from MoviePlayer but, interestingly, the resulting screenshot displays none of the green pixelation that is visible in the paused video.  I've also had some stability problems, particularly with some of the screensavers.  I am not using Compiz or any visual effects at all.  I have an older video card: ATI All-In-Wonder Radeon 7200, but I had none of these problems prior to the upgrade to 7.10.  If I could easily go back, I would.

---

### Post by whayong on 2007-11-21
Wow, no one has any ideas?

Anyway, here's what I noticed:

After getting tired of seeing the lines, I decided to move back to Feisty.  Did a fresh install.  DVD playback was back to normal on all players.

Last weekend, I installed compiz-fusion.  My first DVD play back since then was last night and noticed the lines are back.

So, this obviously leads me to believe that the problem lies in either compiz-fusion or the nvidia drivers.  I'm more leaning towards compiz-fusion causing all this mess, but I'm no expert.  What video card is everyone running?  Does anyone have any suggestions?  Any links on how to remove compiz-fusion and reinstall the standard desktop effects of Feisty?  That way I can check it out and see if it fixes it.

---

### Post by annda on 2007-11-21
today i started having a problem too.

i my case it was green lines across the screen in all players (except xine-based kaffeine, which refused to play anything).

i solved it in VLC by changing the video output module in preferences to X11. MPlayer works with X11 too but does not scale the videos to full screen - Open GL works best for me (but it kills VLC, go figure).

maybe this will help somebody.

---

### Post by Genio on 2007-11-21
Same problem here, when using the system after a moment all my videos look like this :

[IMG]http://img143.imageshack.us/img143/4136/capture5tf6.png[/IMG]

And after this the only solution to play videos correctly again is to restart the X server.

I am on Kubuntu 7.10 with a Nvidia Geforce Go 7900 and using compiz-fusion.

---

### Post by mdpalow on 2007-11-21
It's possible many of you have not loaded the proper DVD / Codecs files. Please click link in my signature for a possible solution.

---

### Post by fart_flower on 2007-11-22
The pink screen shown above is a known nVidia driver bug.  It has been acknowledged by nVidia and the current beta drivers do not have this problem.  (Note: they are not in the Ubuntu repos.)

---

### Post by tommyp on 2007-11-22
If it is a bug in the nvidia drivers, how come the Feisty versions didn't seem to have the problem?

Would reverting to the legacy driver fix this?

---

### Post by geoffp on 2007-11-23
This bug is causing me major headaches; I'm surprised there aren't more complaints posted here.  Maybe it only affects certain configurations or chipsets.

It's being discussed in [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=4").  I hope the gutsy maintainers can be convinced to backport this driver when it's done.

---

### Post by cutlerite on 2007-11-24
I am really surprised that this has not been resolved...?

Anyone have the link for the working beta drivers?

---

### Post by Joco on 2007-11-24
I too have been experiencing these issues with the same screen display as posted in this thread. I moved from a working MythTV install based on 7.04 to Mythbuntu 7.10 thinking it would be better integrated and more stable than my previous setup.  Well I was right about the integration part.


After fighting with this and being able to reproduce the issue at will I found using synaptec to install the nvidia-glx driver has worked.  The nice thing about using synaptec is it clearly shows the intent to remove the nvidia-glx-new driver.


Both the machines I have done this to are using Geforce 6xxx series gpus and are connected to TVs via either S-Video or Component.  Fortunately the TV settings in xorg.conf are honored by both drivers.


Hopefully a finalised (non-beta) nvidia-glx-new will come out asap that has this problem clearly fixed.


It's been a real problem which has severely dented the WAF (Wife Acceptance Factor) at home.

Cheers.

---

