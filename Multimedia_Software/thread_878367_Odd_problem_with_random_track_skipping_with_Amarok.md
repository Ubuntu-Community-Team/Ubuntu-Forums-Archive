---
title: "Odd problem with random track skipping with Amarok"
date: 2008-08-02
forum: Multimedia Software
---

### Post by JillSwift on 2008-08-02
While playing, Amarok will occasionally start playing a new track and after about the first thirty seconds to a minute it skips on to the next track.
If I skip back to the abridged track, it plays all the way through.
I can't determine if there's any pattern to it, it seems to be entirely random, and somewhat rare.
Anyone have any ideas why this is happening?

Amarok 1.4.9.1 under KDE 3.5.9 (Kubuntu)
Play list has 3682 tracks, is on repeat play list, random shuffle favor not recently played.
Machine is a Pentium D 2.8Ghz with 2Gb
Sound is 82801G (ICH7 Family) High Definition Audio Controller
Xine engine, "Autodetect" (probably using ALSA, maybe ESD).
SQLite database.

---

### Post by redradish on 2008-09-02
Hey, I've been getting pretty much exactly the same thing- except that whenever it skips it does it within the first 5 seconds, just enough so that I can here the song fade in and then immediately switch to the next one. But as with JillSwift it seems very random, and doesn't happen very often, maybe once out of a playlist of 30.. 

Amarok 1.4.9.1 under Gnome 2.22.2 (Ubuntu)
Set to random shuffle and crossfading of 500ms, but otherwise should all be default/auto
Notably my audio controller is also:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02), maybe that has something to do with it?

---

### Post by TWO on 2008-09-18
> **redradish said:**
> Hey, I've been getting pretty much exactly the same thing- except that whenever it skips it does it within the first 5 seconds, just enough so that I can here the song fade in and then immediately switch to the next one. But as with JillSwift it seems very random, and doesn't happen very often, maybe once out of a playlist of 30.. 

Amarok 1.4.9.1 under Gnome 2.22.2 (Ubuntu)
Set to random shuffle and crossfading of 500ms, but otherwise should all be default/auto
Notably my audio controller is also:
Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02), maybe that has something to do with it?

Same problem here under Kubuntu Hardy, but it has only started happening today. I too have a track play for like 5 seconds before it skips ahead. 

I can't determine a pattern either but mine seems to be happening more regularly than you guys. I turned the 'repeat' option off but the problem still continues. Actually, that reminds me. Before I changed that setting, Amarok starting playing certain tracks twice. 

My audio controller is: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03) if that has any impact on anything?

#Xine engine, ALSA.
#MySQL database

Current playlist is just over 1500 tracks. 

Machine is 1.6GHz and 1GB of RAM.

---

### Post by gregphil on 2008-09-20
I had similar problems with Amarok until I found 

"Main menu==>Computer==>System Settings==>Computer Administration==>Sound==>Backend tab

There were two "backend" options, Xine and Gstreamer.  Xine was the default.  When I switched to "Gstreamer" the Amarok problems went away.

(but banshee stopped working....)

Good Luck.

---

### Post by redradish on 2008-09-28
That sounds like you've nailed it, I remember fiddling around with that stuff ages ago, but where do Ubuntu users find these backend settings?

---

### Post by TWO on 2008-09-28
> **gregphil said:**
> I had similar problems with Amarok until I found 

"Main menu==>Computer==>System Settings==>Computer Administration==>Sound==>Backend tab

There were two "backend" options, Xine and Gstreamer.  Xine was the default.  When I switched to "Gstreamer" the Amarok problems went away.

(but banshee stopped working....)

Good Luck.

Which version of Kubuntu are you using? I don't seem to have a 'backend' tab in Kubuntu Hardy Heron and KDE 3.5.9.

---

### Post by jdoublep on 2008-12-08
I only seem to notice this issue with extremely large playlists. I haven't yet tested to determine what constitutes extremely large, but I have a playlist currently with 1400+ tracks with no issue. If I up that to 40K+ tracks, I experience the issue. Following the instructions above (I'm on Kubuntu 8.10) didn't help resolve the problem, unfortunately.

---

### Post by armware on 2008-12-15
kubuntu intrepid (kde 4.1.3)
amarok 1.4.10

it hasn't happened to me since i disabled crossfading between tracks.

---

