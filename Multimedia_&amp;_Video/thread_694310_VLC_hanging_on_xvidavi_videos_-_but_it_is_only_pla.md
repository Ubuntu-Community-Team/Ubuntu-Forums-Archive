---
title: "VLC hanging on xvid/avi videos - but it is only player that does surround..."
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by hotani on 2008-02-11
Videos are hanging in VLC when there is a lot of movement. The image will hang while the sound keeps going. Sometimes the hang will last for 10 seconds or so. This only seems to happen on xvid/.avi files ripped from DVDs. Downloaded content - even HD (720p) plays fine.

Other video players such as gxine/totem/mplayer do not do this at all. Unfortunately, none of them will play 5.1 sound (read: I have not had success getting them to do anything other than stereo).

any suggestions? Sound/video/both?

---

### Post by linuxisfree on 2008-02-11
> **hotani said:**
> Videos are hanging in VLC when there is a lot of movement. The image will hang while the sound keeps going. Sometimes the hang will last for 10 seconds or so. This only seems to happen on xvid/.avi files ripped from DVDs. Downloaded content - even HD (720p) plays fine.
 
Other video players such as gxine/totem/mplayer do not do this at all. Unfortunately, none of them will play 5.1 sound (read: I have not had success getting them to do anything other than stereo).
 
any suggestions? Sound/video/both?
 
Kinda weird... VLC normally works for me... but, anyway... try Kaffeine, it also works for me (its KDE based, though).
 
Also try checking if you have all the codecs and libs you need...

---

### Post by The Avatar of Time on 2008-02-11
I had some similar trouble with VLC and .avi's. How compressed are yours? My trouble was just that 45 minute shows were compressed down to 120MB. The lips didn't match the sound they were choppy etc.. If that is the problem I don't think there is anything that can be done. 45 minute shows should be at least 350MB to be decent. Also I can't say as I have had a problem using surround sound (7.1 well sort of, side speakers just copy the back ones so 5.1 would be more accurate). Do you have all the right things unmuted in alsamixer?

---

### Post by hotani on 2008-02-11
yeah the 5.1 in VLC works great - no problems there. In other players it is just stereo over 6 speakers.

These videos are DVD movies compressed with xvid to about 1GB or so. They are not too heavily compressed I don't think. I have not had any issues with sound getting out of sync in VLC - usually that happens with gstreamer apps.

I'll give Kaffeine a shot and see how it does.

EDIT:
Good News Everyone! Kaffeine, even though it is using the same xine engine as Totem, picks up the 5.1 sound! So that is a relief. At least I have a backup when VLC is acting up. Plus it seems to play my HD stuff with no problem which is essential. This is a full-time HTPC BTW, so A/V is #1 priority.

---

