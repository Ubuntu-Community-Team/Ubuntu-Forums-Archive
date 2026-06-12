---
title: "Myth standalone for movies, music, games?"
date: 2009-02-19
forum: Mythbuntu
---

### Post by JoePolvino on 2009-02-19
Hi. I'm looking for some guidance on using Mythbuntu for serving up videos, listening to music, and playing mame games.

I have a 1.7 ghz p4 with 512mb ram, and installed Mythbuntu on it. The next thing I did was load a few avi files into /var/mythtv/videos (I believe that was the path), but they do not play...the machine freezes up. I checked the codec and they are either Divx or XviD. Is it a codec issue, or something else?

Also, I'd like to serve up music, which is stored on a windows box in another room. Is there an easy way to mount the windows folder into the music directory, or is there a better way?

Lastly, I'm looking for advice on using a remote control. Right now, I use the keyboard and mouse. When I move this under my TV, I'd like to use a remote. How would I go about adding a remote after install? Is the Microsoft remote adequate?

Thanks. It's been about 20 years since I've used unix, so I'm a bit green. Looking forward to using myth, it looks like a very robust system.

---

### Post by theophile on 2009-02-20
> **JoePolvino said:**
> Hi. I'm looking for some guidance on using Mythbuntu for serving up videos, listening to music, and playing mame games.

I have a 1.7 ghz p4 with 512mb ram, and installed Mythbuntu on it. The next thing I did was load a few avi files into /var/mythtv/videos (I believe that was the path), but they do not play...the machine freezes up. I checked the codec and they are either Divx or XviD. Is it a codec issue, or something else?
You'll want to configure MythTV to use an external player (such as mplayer) for such videos. It's a pretty simple option in the media setup menu.

> Also, I'd like to serve up music, which is stored on a windows box in another room. Is there an easy way to mount the windows folder into the music directory, or is there a better way?
You can mount the Windows share with Samba.
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

> Lastly, I'm looking for advice on using a remote control. Right now, I use the keyboard and mouse. When I move this under my TV, I'd like to use a remote. How would I go about adding a remote after install? Is the Microsoft remote adequate?
The Media Center Edition remote works for MythTV just fine. See here: [http://www.mythtv.org/wiki/MCE_Remote](http://www.mythtv.org/wiki/MCE_Remote)

Good luck! Unix has evolved a bit in the past 20 years. ;)

---

### Post by scary_jeff on 2009-02-20
> **theophile said:**
> You'll want to configure MythTV to use an external player (such as mplayer) for such videos. It's a pretty simple option in the media setup menu.

MythVideo played these kinds of files without issue for me. You could look in /var/log/mythtv/mythfrontend.log after trying to play one of these files, to see if it tells you what went wrong. You could also try choosing a different playback profile in the frontend setup menu.

---

