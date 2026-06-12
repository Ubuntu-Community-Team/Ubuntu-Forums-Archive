---
title: "Video playback doesn't work with visual effects enabled."
date: 2007-11-14
forum: Multimedia &amp; Video
---

### Post by Marco Polo on 2007-11-14
So, here is the problem:
I have Acer 5315-2153 notebook with Ubuntu 7.10 Gutsy installed. Chipset Intel 965GM (Intel X3100 graphics), 1 Gb Ram, Celeron M 1.7.
In the beginning everything worked OK, video was working perfectly in any player (VLC, totem, mplayer, etc.). But after i went to System->Parameters->Desktop Configuration and on tab "visual effects" enabled theese effects, video stopped working. This is how it happens: i open videoplayer, open a video file in it, and player just dissapears, just as if i clicked "close" button. If i switch effects off - video works again, but they just can't do it together :). Any ideas how to enable both video playback and effects? I like both of them a lot.
I have downloaded Compiz-Fusion configuration graphical interface and found some mysterious item, called "Video Playback", but switching it on or off doesn't change anything.
Any ideas?

---

### Post by Arizon_Dread on 2007-11-14
I have the same problem, the player just disappears.

although, I cannot get vlc to work with the desktop effects disabled either. 

the player disappears. 

help would be greatly appreciated.

---

### Post by yavez on 2007-11-15
> **Arizon_Dread said:**
> I have the same problem, the player just disappears.

although, I cannot get vlc to work with the desktop effects disabled either. 

the player disappears. 

help would be greatly appreciated.


Same exact thing happening here.  I'm sure I had this working fine when Gutsy was in beta, desktop effects and video.  But now it just won't work, the active window closes down as soon as the file is opened, whenever desktop effects are activated.

---

### Post by AbtZ on 2007-11-15
I think it has something to do with the video card I assume we're all using -- Intel 965GM (X1300).

Weirdly enough, I somehow managed to get video playback to work on a previous install, but due to other things being screwed up, I had to reinstall Ubuntu.

---

### Post by AbtZ on 2007-11-15
Bad news, guys:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833/comments/22](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/140833/comments/22)

:(

I wish I knew what I did to manage to get it working before I had to reinstall. Sadly, there's no way since I screwed around a lot with different settings trying to get widescreen to work properly...

---

### Post by ubuntu-freak on 2007-11-16
I posted a workaround for intel graphics users in the debian forums @ [http://forums.debian.net/viewtopic.php?t=21315](http://forums.debian.net/viewtopic.php?t=21315)
It lets you watch vids with compiz running and also fixes the mplayer plugin streaming problem. If you're gonna use x11 in mplayer add zoom=1 to the conf file in your home/.mplayer folder.

---

### Post by AbtZ on 2007-11-16
Thanks. It fixes the issue for mplayer (which is not a bad player). However, I would like for it to work on VLC too. If the fix is the same, i.e. x11 instead of xv, I cannot find the place to edit this setting.

---

### Post by Arizon_Dread on 2007-11-16
I've got it working!!!

I did this:

Open vlc properties. expand the video-menu in the  left pane.
check "advanced options" or something like that in the right pane.
click output modules in the left pane.
in the right pane, choose X11 as output module. save and exit the settings.

try playing now.

this worked for me.. if it doesn't work, try with some of the other output modules.:)

---

### Post by AbtZ on 2007-11-16
The ASCII art module is interesting...

Btw, for those who want it to work with Totem:
> I was able to circumvent the blacklist status by putting the text "SKIP_CHECKS=yes" in the file ~/.config/compiz/compiz-manager. Enabling Compiz on the 1420n causes video playback to fail consistently in Ubuntu's Totem video player. To work around that problem and make videos play while Compiz is running, I had to open the Multimedia Systems Selector (gstreamer-properties) tool and select "X Windows System (No Xv)" from the video output plugin list. Note that this extra step was only required because my graphics hardware is blacklisted by Compiz. Most users won't have video playback problems.

Ahh. Good ol' [Ars Technica]("http://arstechnica.com/reviews/os/ubuntu-gutsy-gibbon-review.ars/2").

---

### Post by Marco Polo on 2007-11-16
> **Arizon_Dread said:**
> I've got it working!!!

I did this:

Open vlc properties. expand the video-menu in the  left pane.
check "advanced options" or something like that in the right pane.
click output modules in the left pane.
in the right pane, choose X11 as output module. save and exit the settings.

try playing now.

this worked for me.. if it doesn't work, try with some of the other output modules.:)

Yay!!! Great job, Arizon_Dread, this sure does work!
Can't even imagine that the solution was so simple! :mrgreen:

Everyone, problem is solved, thanks to Arizon_Dread! =D>

---

### Post by Arizon_Dread on 2007-11-16
8-)

I'm glad I could help :)

Alas, I can't take all the credit. I found a guide that worked on the internet some where, I was gonna post the link but I can't find it again, so I just posted the directions.

---

### Post by samshi on 2007-11-16
The video plays but if you haven't noticed the video has less quality in that setting (X11). I tried OpenGl and other settings but video is blank as usual.

:KS:KS:KS:KS

---

### Post by Arizon_Dread on 2007-11-16
You might be right. 
well, it's a temporary solution. it's at least showing the picture, but a solution providing better quality would be much appreciated.

---

### Post by AbtZ on 2007-11-16
raessuringlyoffensive's fix is the best one as of yet. Video quality doesn't seem to suffer in mplayer.

Of course, if you don't like mplayer, you have a problem...

---

