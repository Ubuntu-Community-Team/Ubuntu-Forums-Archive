---
title: "Amarok iPod Playlist transfer"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by lsutiger on 2007-06-30
OK..I read every post here that returned from a search of the above title. there ere 9, and none of them actually answered my question. So here it goes...
I have a playlist in Amarok that I want to transfer to my iPod. When I right click on the playlist, it gives me 2 options to 'transfer'. One is 'Transfer to Media Device'. When I choose this, it seems to want to transfer the actual music to the iPod. Well, the music is already on the iPod. That would defeat the purpose.

The other is 'Synchronize to Media Device'. Now I am not sure what this will do. Will it ovewrite everything on my iPod? I have some things that are on the iPod that are not in Amarok, so that would not be wise. I have a backup on my server at work, but I don't want to go through the hassle.
Could somebody school me?
Thanx!

---

### Post by lsutiger on 2007-07-01
Bump

---

### Post by lsutiger on 2007-07-03
bump

---

### Post by lsutiger on 2007-07-14
Calling all Amarok fans! ANybody have a clue?

---

### Post by sproaticus on 2007-08-10
Another bump.  Can anyone explain the difference?

I couldn't find anything in KDE's wiki, and the Amarok Handbook briefly states that "Synchronize" synchronizes, and "Transfer" transfers.

After playing with things a bit, I don't think "Synchronize" does what it suggests it does - keep the collection on the device synchronized with the collection in Amarok.  In fact, I can't make it behave any differently from "Transfer".

[_This thread_]("http://amarok.kde.org/forum/index.php?topic=14230.0") in the Amarok forums doesn't clear things up - what's the difference between "make the same tracks appear on both device and computer" and "only copy the tracks"?

"Synchronize tracks" sounds **very** appealing.  The only feature that iTunes has that I miss is automatic sync on connect.  Based on all the rave reviews I've read for Amarok, it sounded like Amarok did this.  Unfortunately, I don't think it does, which makes maintaining a 35+gb collection in Amarok - and keeping a copy of my tracks and playlists on my iPod - a **lot** of work.

Apparently they plan on adding an auto-synchronize feature.  However, the most recent info I could find from the Amarok team was from last year, in [_another post_]("http://amarok.kde.org/forum/index.php?topic=13014.0") on the Amarok forums where Mark Kretschmann wistfully states that it'll appear in "later versions."

---

### Post by AlexFoster on 2007-08-10
I'm having the same question. <waits with others for definite answer before pressing the button>

---

### Post by NoCoolName_Tom on 2007-08-12
Transferring means that it will simply *put* the songs on the iPod without checking the iPod database to see if there is a duplicate song.

Syncing a playlist will go through the playlist, song by song, and compare the track in question against the iPod's database.  This can take a long time because it reads the database for each track for comparison.  If Amarok thinks that the tracks are the same then it simply moves on to the next song in the playlist without doing anything.  Otherwise, the song gets copied and appended to the iPod database.

At least, that's how it works when things work out alright.  In practice there are occasional bugs.  A good rule of thumb is after any large transfer or sync to check the iPod in Amarok for "orphaned" songs, or songs that are on the iPod's hard drive but are not in the iPod's database.  Then try to append the songs to the database.  For some of them it will tell you that a duplicate entry already exists, and at that point feel free to delete the orphaned track from the device.

We're not quite "there" yet when it comes to Amarok and the iPod, but we're getting closer.

---

