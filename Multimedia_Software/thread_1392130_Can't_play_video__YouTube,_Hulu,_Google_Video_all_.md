---
title: "Can't play video:  YouTube, Hulu, Google Video all broken"
date: 2010-01-27
forum: Multimedia Software
---

### Post by mbobak on 2010-01-27
Hi all,

Fresh install of Karmic x86-64.

Went to YouTube, tried to play video.  Followed link to Adobe to install latest flashplayer.  Selected "APT for Ubuntu 9.04+".  Installed it.

YouTube seemed to work, but not reliably.  (Often couldn't get a video to maximize to fullscreen.)  Now, after futzing around for a while, I can't get video to play at all.  When I go to YouTube, it doesn't tell me that flash player isn't installed, like it did before.  All it does is give me a big white square, where the video should appear.

Help!  It shouldn't be this hard to configure video to reliably work!

-Mark

---

### Post by llawwehttam on 2010-01-27
You need to install all the restricted extras.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

If you have done this then the 10.1 alpha from the adobe labs is very stable.

---

### Post by mbobak on 2010-01-27
Ok, downloaded 10.1 Alpha, removed all flash related stuff (flashplayer-installer, flashplugin-nonfree), copied .so file to /usr/lib/mozilla/plugins and that solved *most* of my problems.  Hulu now says "Sorry, we are unable to stream this video.  Please check your Internet connection and try again."

So, everything works except Hulu.  Any thoughts on Hulu?

-Mark

---

### Post by mbobak on 2010-01-28
Ok, solved my own problem.  Still no Hulu through web browser, but I discovered the Hulu Desktop, which is actually really nice.

-Mark

---

### Post by MooPi on 2010-01-28
Hulu is broken for 64 bit users. Something about changing to the latest Flash and 64 bit is still lagging behind the other versions. Latest version for 64bit does not work.

---

### Post by Foxcow on 2010-01-28
> **mbobak said:**
> Ok, solved my own problem.  Still no Hulu through web browser, but I discovered the Hulu Desktop, which is actually really nice.

-Mark



Initially, did you get the following error?

"Hulu Desktop could not locate the Flash plugin.  If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so."


I don't really know where to go from here.

---

### Post by llawwehttam on 2010-01-28
> **Foxcow said:**
> Initially, did you get the following error?

"Hulu Desktop could not locate the Flash plugin.  If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so."


I don't really know where to go from here.

Pretty much go to your home folder, press Ctrl+H to see hidden files and folders, open .huludesktop and find the flash line and change it so it shows the location of libflashplayer.so ( usually in the mozilla directory). Hope that helps.

---

### Post by Foxcow on 2010-01-28
> **llawwehttam said:**
> Pretty much go to your home folder, press Ctrl+H to see hidden files and folders, open .huludesktop and find the flash line and change it so it shows the location of libflashplayer.so ( usually in the mozilla directory). Hope that helps.

Kudos to you man!  Thank you very much.  I had no idea about the hidden files in /home!

---

### Post by llawwehttam on 2010-01-28
> **Foxcow said:**
> Kudos to you man!  Thank you very much.  I had no idea about the hidden files in /home!

Your welcome. To hide a folder in linux just start its name with a full stop.

---

### Post by Foxcow on 2010-01-28
> **llawwehttam said:**
> Your welcome. To hide a folder in linux just start its name with a full stop.

Good to know info.  Thanks again :popcorn:

---

### Post by mbobak on 2010-01-30
For those of us on this side of the pond:

full stop = period

 :-)

---

