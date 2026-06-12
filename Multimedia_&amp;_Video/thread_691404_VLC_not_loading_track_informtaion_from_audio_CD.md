---
title: "VLC not loading track informtaion from audio CD"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by cyberblade3001 on 2008-02-08
Ok-my audio CD's load fine with VLC-and play fine-but for each track it shows:

Audio CD - Track #

Sound Juicer shows track number, Title, Artist, etc... 

What do I do to make VLC pull the same information?

---

### Post by HappyFeet on 2008-02-08
go to view>playlist. open the general folder

it should show up there.

---

### Post by cyberblade3001 on 2008-02-08
> **HappyFeet said:**
> go to view>playlist

it should show up there.

The playlist is showing-its in the playlist that its showing up as:

audio cd-track #

within the playlist, when I right-click and select "info" it shows the following:

URI: cdda:///dev/scd0
Name: Audio CD - Track 13

and all other fields are blank. 

This is this way with all cd's (yes, store bought) and sound juicer picks up the track info with no problem...

---

### Post by HappyFeet on 2008-02-08
after some research, go to settings>preferences>input/codecs>access modules>audio cd

make sure "advanced options" is checked off in the lower right. you'll see where to input cddb database address. you'll have to find one that works. shouldnt be too hard. i will also work on this and get back to you if i get it working.

---

### Post by cyberblade3001 on 2008-02-08
I see that... 

VLC is trying to pull the info from freedb.org

Sound juicer (according to wikipedia) gets its info from MusicBrainz

It seems that my cd's (currently have been listening to Ricardo Arjona, and RBD) are in the one database and not the other... 

I'm going to try to get VLC to connect to another database and see if that changes the results.

---

