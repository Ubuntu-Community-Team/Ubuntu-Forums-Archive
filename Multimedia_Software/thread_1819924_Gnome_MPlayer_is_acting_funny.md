---
title: "Gnome MPlayer is acting funny"
date: 2011-08-07
forum: Multimedia Software
---

### Post by Ceipheed on 2011-08-07
Just started with Ubuntu this week, so I apologize in advance for my noobness.

Today, I started having problems playing various .mkv files. The files don't play at all; the player just stands there doing nothing. At most, it seems like the files start playing for half a second (I hear audio, but no vid) and then just die. Movie Player plays the files with no problems, tho.

These are not new files, but files that I've had since before and have presented absolutely no problems till yesterday. Also, I haven't made any changes to any settings/configurations in the past couple days either.

At the same time, I started having problems where only the video would play (no audio whatsoever; whats more, when I checked the sound preferences, it showed no programs where playing or recording audio). This, I solved by upgrading to the latest version of the Gnome MPlayer (I was using ver1.0.2), but I figured it might be a clue to solving my other problem. The files that wouldnt play audio used FLAC and AC3 encoding.

Other .mkv files play perfectly fine, both with MPlayer or Movie Player. So far, I can detect no pattern to the problem. 

if there is anything else I should post to make the issue more clear, please tell me and Ill do so as soon as I can.

Thanks in advance for the help.

---

### Post by Basher101 on 2011-08-07
Maybe you miss codecs. Search for Ubuntu restricted extras in the software manager and install them. Report back if it worked out
ps. Even i was a noob, like everyone else was, no need to shame for that

---

### Post by beew on 2011-08-07
Maybe the configuration is corrupted. Try removing the .mplayer folder and see if it gets better. (Go to your home directory and click View > Show Hidden Files and you will find the folder .mplayer)

---

### Post by Ceipheed on 2011-08-07
@Basher101, I alrdy have the restricted extras installed. Like I said, Ive been playing these files w/o a problem till today.

@beew, I tried removing the ./mplayer folder, but it was no good; same problem. to be specific, I cut the folder to somewhere else. not sure if that is what you meant by removing the folder.

---

### Post by Basher101 on 2011-08-07
Try deleting Mplayer and reinstalling it

---

### Post by Ceipheed on 2011-08-07
did that as well.

uninstalled
rebooted
installed
rebooted yet again for the sake of it

same situation.

---

### Post by SeijiSensei on 2011-08-07
The version of mplayer in the repositories seems to have [problems]("http://ubuntuforums.org/showthread.php?p=10848340") with some newer files that use "high profile" H.264 encoding.  The repo version is always considerably behind the most recent mplayer build.  You can use a [PPA]("https://launchpad.net/~motumedia/+archive/mplayer-daily") to get more recent builds, but some of us have begun using mplayer2 which handles these files without a problem.

See, for instance, [this thread](http://ubuntuforums.org/showthread.php?t=1793655) which gives some PPA's you can add to get mplayer2 and some help on building it from source if you prefer.

Update:  The mplayer2.org site times out this morning.  Perhaps it's undergoing maintenance.  If you try compiling from source, make sure the site works by visiting [http://www.mplayer2.org/](http://www.mplayer2.org/) before using git as described in the link above.

---

### Post by Ceipheed on 2011-08-07
Much obliged, SeijiSensei!

this got me my files working again. I'd still like to know what was the cause of it all, but for now thanks a lot for the help (Basher101 and beew too, ofc).

---

### Post by SeijiSensei on 2011-08-07
> **Ceipheed said:**
> I'd still like to know what was the cause of it all

There are many different "flavors" of H.264 called "[profiles](http://en.wikipedia.org/wiki/H.264#Profiles)".  Earlier versions of mplayer didn't have decoding support for some of the "high" profiles.  10-bit color is another new frontier; support for that feature only appeared in the ffmpeg code on which mplayer depends a few months ago.

---

### Post by Ceipheed on 2011-08-08
but like I said, the files are not new. heck, even files I had used the day before stopped working. I believe that would rule out a problem with codec support.

---

