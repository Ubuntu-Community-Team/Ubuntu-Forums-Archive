---
title: "DVD - missing plugins"
date: 2007-04-21
forum: Multimedia &amp; Video
---

### Post by smartbei on 2007-04-21
I am having an odd problem with playing DVDs - When I first put the DVD in the drive, the movie plays, skipping the menu and anything before it. Also, trying any of the following: skipping chapters, returning to title/main menu,  does nothing.

If I close Totem, and then re-open it and try playingt he DVD, it gives me "Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it".

If I try with MPlayer Movie Player it gives me "Error opening/initializing the selected video_out (-vo) device."

I installed codecs, etc. according to:
[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)
[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

General info:
I am running Feisty 64bit.
Computer info is in the signature.

Thanks for all replies.

---

### Post by sharke on 2007-04-21
I had same problem with totem so i installed totem-xine and dvd now plays.
Take a look here.  
[http://geckorock.com/2007/03/30/howto-play-dvds-on-ubuntu/](http://geckorock.com/2007/03/30/howto-play-dvds-on-ubuntu/)

Regards
Sharke

---

### Post by niglch on 2007-04-21
I had the same issue with totem-gstreamer not being able to play DVD's. Installing totem-xine works very well for DVD's, but you can't really win because there seems to be a problem with WMV playback that only occurs on Totem-xine (see this [bug report.]("https://bugs.launchpad.net/xine-lib/+bug/108453")) I'll continue to look for a solution.

---

### Post by smartbei on 2007-04-21
Well, I was trying to get away from installing another audio engine, but perhaps I will be able to remove gstreamer then, if no application depends on it as long as there is xine.

---

### Post by niglch on 2007-04-21
Actually, I tried installing Ogle just for the heck of it, and it's able to play DVD's even if gstreamer can't. I would recommend installing it or VLC if you like that better because they both work pretty good.

Also, would anyone happen to know how to set the default package for playing DVD's? I want to change it from Totem to Ogle since totem-gstreamer won't play DVD's anyway.

---

### Post by notwen on 2007-04-21
VLC is what I use for just about all of my video formats.  Worth checking out. Highly recommended.

---

