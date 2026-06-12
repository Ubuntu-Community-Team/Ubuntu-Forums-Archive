---
title: "[SOLVED] Rhythmbox and Songbird works on GNOME, but not on KDE 4.1. Help!"
date: 2008-11-04
forum: Multimedia Software
---

### Post by boom2k1 on 2008-11-04
Rhythmbox and Songbird works on GNOME, but not on KDE 4.1. Help!
When I attempt to play a song in songbird, it gives me a gstreamer error.

However, I have gstreamer installed. I have no idea why both rhythmbox and songbird 0.7 only works on KDE. Please help!

Thanks

---

### Post by boom2k1 on 2008-11-04
I think I "fixed" it partially...
When I run it in command line with "sudo", the songs play in both Rhythmbox and Songbird.

However, the interface and all the custom setting pertinent to Rhythmbox disappeared, as expected. Moreover, we shouldn't really be using sudo when we want to make local user changes.

"http://ubuntuforums.org/showthread.php?t=374725"

Does anyone have more insight into why adding sudo makes the players work?


I don't think it is a general songbird thing... rhythmbox would work after typing sudo .


Songbird and Rhythmbox without sudo would work under GNOME.

---

### Post by boom2k1 on 2008-11-04
Okay, I solved it myself.

I downloaded songbird 1.0RC and attempted to play a song without using sudo.
It still gave me an error message, but it was a more informative one.
It was a connection fail... connection refused or something.
I recognized that error message was thrown to me when pulseaudio couldn't be used. [IT IS A MUCH MORE INFORMATIVE MESSAGE THEN SOME MISLEADING GSTREAMER ERROR MESSAGE!]

Therefore, I went into the command line and ran pulseaudio (type pulseaudio)

I then started running songbird without sudo, and it worked!
Rhythmbox and everything else should work too.

I am guessing why sudo works is because the root load pulseaudio by default.

[http://ubuntuforums.org/showthread.php?p=4333126](http://ubuntuforums.org/showthread.php?p=4333126)




Now I only need to make sure KDE 4.1 will start pulseaudio at login.


I strongly suggest that the integration team make sure pulseaudio would start automatically in KDE, because any of those "bugs" would drive people crazy. It took couple of hours and finally one informative error message to understand why the songs don't play for me.

---

