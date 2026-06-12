---
title: "Disable Screensaver During Video Playback"
date: 2009-01-18
forum: Multimedia Software
---

### Post by greyfox1 on 2009-01-18
Hi All,

Is there a way to disable the screensaver during video playback regardless of the app doing the playback?  I know some players like Totem have a setting to prevent the screensaver from activating but unfortunately the program I do most of my playback in (Banshee) does not.  I prefer Banshee because it has library support for both my audio and video files.  This leaves me with the only option of going into my screensaver preferences and turning it off every time I want to watch a movie, which is a bit annoying.  Am I out of luck or is there a better way?

---

### Post by greyfox1 on 2009-01-19
*Bump* Anyone?

---

### Post by greyfox1 on 2009-01-20
bump

---

### Post by greyfox1 on 2009-02-05
bump

---

### Post by jerrrys on 2009-02-05
a search on "Disable Screensaver" shows this and more

[http://ubuntuforums.org/showthread.php?t=1044841&highlight=Disable+Screensaver](http://ubuntuforums.org/showthread.php?t=1044841&highlight=Disable+Screensaver)

---

### Post by Coder543 on 2009-02-05
Have you tried the simple solution of making the screensaver come on after a longer duration? If that cannot suit your purpose, you could research if there is a way to disable screensaver from a script. (use the script to launch your movie player, when it exits, reenable screensaver)

---

### Post by mc4man on 2009-02-05
The features, ect. for banshee 1.x.x say ...?
> Disable the screensaver when in fullscreen mode

---

### Post by greyfox1 on 2009-02-06
> **jerrrys said:**
> a search on "Disable Screensaver" shows this and more

[http://ubuntuforums.org/showthread.php?t=1044841&highlight=Disable+Screensaver](http://ubuntuforums.org/showthread.php?t=1044841&highlight=Disable+Screensaver)

Thanks for the "tip" on searching, but that thread was started around the same time as this one.  It either did not exist or had no useful replies when I started this thread.  I did PLENTY of searching before starting this thread.


> **Coder543 said:**
> Have you tried the simple solution of making the screensaver come on after a longer duration? If that cannot suit your purpose, you could research if there is a way to disable screensaver from a script. (use the script to launch your movie player, when it exits, reenable screensaver)

I wouldn't really call increasing the duration a solution in this case.  I'm talking about full-length movies here and I don't want my screensaver to wait for hours before activating.  I'd also prefer not to have to change the settings depending on what I'm doing (that's a nuisance IMO).

The idea about scripting sounds interesting from a technical point of view.  Thanks for the idea.  I would really prefer this to work without a lot of tinkering but it seems that won't be possible.

> **mc4man said:**
> The features, ect. for banshee 1.x.x say ...?

I'll have to look into that one.  I've had this problem or a similar one with several different media players in the course of messing around trying to find a good solution-- maybe the problem with Banshee was with power management turning the monitor off rather than the screensaver.  I'll have to check.

---

### Post by jerrrys on 2009-02-06
yes, my comment was a bit too assertive, sorry

---

### Post by redroad55 on 2009-02-06
If you right click on applications and choose edit menus then in the new window on left choose "sound and video" .. Banshee should appear on the right > then right click on Banshee .. then select properties in drop down > the new window gives you a place to enter a command .. what the command line should be I'm not certain but I'm pretty sure it would give you what you want if entered there ..Post back

---

### Post by redroad55 on 2009-02-06
This was taken from VLC's How to:
>  Item-specific options

There are many options that are related to items (like --novideo, --codec, --fullscreen).

For all of these, you have the possibility to make them item-specific, using ":" instead of "--" and putting the option just after the concerned item.

Examples:

% vlc file1.mpg :fullscreen file2.mpg

will play file1.mpg in fullscreen mode and file2.mpg in the default mode (which is generally no fullscreen), whereas

% vlc --fullscreen file1.mpg file2.mpg

will play both files in fullscreen mode

% vlc --fullscreen file1.mpg :sub-file=file1.srt :no-fullscreen file2.mpg :filter=distort

will play file1.mpg in windowed (no-fullscreen) mode with the subtitles file file1.srt and will play file2.mpg with video filter distort enabled in fullscreen mode (item-specific options override global options) 

these examples show how it is possible to taylor what you want in whatever player you choose ..

---

### Post by mc4man on 2009-02-06
> was with power management turning the monitor off rather than the screensaver. I'll have to check.

It very well be that.

Power management doesn't kick in till the the computer is considered as idle.(set in screensaver) So you can set it to the maximum or never and it won't affect your use of a screensaver.

---

### Post by greyfox1 on 2009-02-24
I can't believe I did this, but I've come to realize I got my description wrong.  I failed to mention that while I *usually* use Banshee for video playback, there are times when I use other programs (typically Totem)-- specifically for DVD playback since Banshee doesn't play DVDs.  Sorry for my confusion.  

So in the case of Banshee and Totem, each can keep the screensaver at bay- which is good- but I still have to turn power management off.  Power management isn't a HUGE deal (I can just not use that feature and physically power the monitor off when I leave the room) but still, it would be nice not to have to worry about it.

What it boils down to is that I would really like it if BOTH screensaver and power management were app-agnostic.  That is, "smart" enough to recognize that a full-screen video is playing and not activate, regardless of the app doing the playback (that's how it works on certain other unmentionable OSes after all :P) but given the responses I've received, it seems to me that this isn't possible at this time and I have to do something specific, depending on the app I'm using.  It's a bit tedious but if this is the only solution I'll roll with it.  Thanks all for your responses.

---

