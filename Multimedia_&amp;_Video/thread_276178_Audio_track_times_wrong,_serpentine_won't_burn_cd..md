---
title: "Audio track times wrong, serpentine won't burn cd."
date: 2006-10-12
forum: Multimedia &amp; Video
---

### Post by Yleeyas on 2006-10-12
Hi folks,

I've just downloaded (legit) a music album, which I want to burn to cd.

When I use XMMS to play the tracks (mp3) from the hard drive, the play times are wrong, really huge eg; 30-40 min/track, with a total play time of 2 hours. When I start to play them XMMS resets the times to something more reasonable eg; 3-5 min/track, as each track is played. The total play time is finally shown as something reasonable eg; 45 minutes.

When I fire up serpentine to burn the tracks to cd, it sees the track times as the huge numbers (30-40 min/track), total play time of 2 hours, and will not allow me to burn the cd.

So the question is why is this happening, and how do I get serpentine to recognize the correct track times so I can burn the cd?

Notes:
1) I've seen this before on a per track basis in XMMS, but it wasn't a problem until now that I want to burn a cd.
2) When I use rhythmbox to play the tracks from the hard drive, it sees the huge times, but does not reset them to the correct values as it plays each track, the way xmms does.
3) I've used serpentine successfully before.


Any ideas?

Yleeyas

---

### Post by moore.bryan on 2006-10-12
*could be something about the files themselves from the site you purchased them... are you sure they're mp3's?*

---

### Post by Yleeyas on 2006-10-12
Hi moore.bryan,

All of my media players/burners see the files as .mp3
(xmms,rhythmbox,serpentine,gnomebaker...)

I don't think it's just these files, because I've had this huge track play time issue with some other audio files from different sources. I will however go back and see if I can't just re-download this album and clear it up that way.

thanx :-D 

Yleeyas

---

### Post by moore.bryan on 2006-10-12
*sorry i wasn't much help... it's a really weird issue.  if you reinstall xmms, does it still happen?  it might be something screwed up in the meta info for the file itself.  with easytag (repos) you could see some intense details for each file...*

---

### Post by Yleeyas on 2006-10-12
Hey bryan,

Thanx for the effort. I don't think the problem is xmms specific so reinstalling is WAY last resort ](*,) 

I'll look into easytag, must be something in file's metadata as you suggest.

Thanx again,

yleeyas

---

### Post by moore.bryan on 2006-10-12
*totally understand... make sure to post if you discover something weird to help out anyone else (even though i've never heard of this problem before!)  ;-)*

---

### Post by Yleeyas on 2006-10-12
Hey moore.bryan, if your still tuned in...8) 

Well easytag did the trick, but in a very bizarre way.:twisted: 

I examined the tag (meta) data for the album's mp3 tracks on my hard drive and found all of the times to be half (.5) of the actual play times :confused:  Well this is better than 3 to 4 times longer, which was my original problem!:mad: 

The play times can't be modified like the artist, album, title fields can be, but on a whim I decided to write the tag data back to the files without making any changes.:-| 

The players (xmms, rhythmbox) still see the play times on the hard drive as 3-4 times actual. HOWEVER ... the burners (serpentine, gnomebaker) now see the play times as the shorter (.5) values!!!!!!:-? 
So now they allow me to burn a CD because they see the total play time as 20 minutes instead of the actual 40 minutes and far less than the 2-3 hours as per the original problem!!!

I used gnomebaker and burned a CD, which when I play it with xmms, it now sees and displays the ACTUAL play times!?!?!?!?:-k

I don't pretend to understand what's going on, but I have my CD burned, and I'm content.

If someone can explain these magical mysteries to me, I'd be grateful. In the meantime, after 5 hours of messin' about, I'm off to listen to my new favourite album!:rolleyes:

Yleeyas

---

### Post by moore.bryan on 2006-10-13
*i've heard easytag can work magic, but that's frikkin' ridiculous!  i've no idea whatsoever what the real problem was, but our guess was right about something in the meta... congrats on getting a cd to burn!  maybe a really smart developer will accident onto this post and enlighten us on reasoning... ;-)*

---

