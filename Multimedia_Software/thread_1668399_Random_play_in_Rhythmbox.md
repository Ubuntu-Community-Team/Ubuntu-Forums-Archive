---
title: "Random play in Rhythmbox"
date: 2011-01-16
forum: Multimedia Software
---

### Post by Scunnered on 2011-01-16
Can you please advise if there is a problem with random play in Rhythmbox as my experience with it is driving me daft. Normally when working I like to play music but the continual playing of one CD is too much to bear. 

I had re-installed my OS and initially just dragged and dropped over all my music from my backup only to find that having set the system to randomly play music that it did not.  Initially it selected from 3 CDs of the same artist.  There were over 300 tracks available to select but it only chose from approx 20% of those available.  No matter what I tried the selection would revert to this one artist.

Gave up on things and started everything fresh.  Removed Rhythmbox and re-installed it.  Took all the CDs (14) and installed them directly into it the from the devices display in the side panel.

Tried to play again only to find that this time round it would only select from one artist and from a dual CD. Previously I had a choice of 4CDs by Capercaillie.  Now I have a random selection of 33 tracks by them. Much as I like the artist it was getting a bit too much to bear.  Deleted all 33 tracks only to find that the next random selection stuck on another artist and as before the one CD.

This is totally beyond a joke. As my car radio often fails as the signal is blocked by the mountains I had hoped that I could use an iPod to play my music but if all it will play is the one CD it is a complete waste of time. 

Can anyone offer a solution to my problem as I would like to have matters resolved before I switch cars in May. Additionally I would like to listen to Rhythmbox when working on my system as happened before the re-installation of my OS.

Thanking you in anticipation

---

### Post by cerda on 2011-01-16
I'm having the same issue here (i guess). When i open Rhythmbox and press play it plays the same artist (not the same song), if the song finishes it will play another song from the same artist (even if random play is enabled from the menu). If i press next song, it will jump to another song from the same artist as well. Random is completely broken for me now

---

### Post by Scunnered on 2011-01-17
Thanks for your advice.  I was begining to think that it was me.

Hope someone can fix things as it is so frustrating.

Edit:  Have followed up with a bug report, anything positive will be passed on

---

### Post by grumpyoldgit on 2011-01-24
Nice to hear that it is not just me. Random play really does have a mind of it's own. It will spend ages cycling round the same few albums but even then will ignore certain tracks completely. Out of a playlist with 400 tracks, today it is fixated with Them Crooked Vultures, Led Zeppelin and Van Morrison, and is completely ignoring Pink Floyd, Santana and Jimi Hendrix. Tomorrow it will do something completely different. I've added the playcount column to keep some sort of tally. Some tracks on some albums have now been played 6 times and others on the same album have yet to be played.
Rather irritating.

---

### Post by Scunnered on 2011-01-24
**grumpyoldgit**

As advised 1 week ago I reported this at the following link:

[https://bugzilla.gnome.org/show_bug.cgi?id=639766](https://bugzilla.gnome.org/show_bug.cgi?id=639766)

So far things are at a standstill.  I am not aware of any proticol on bugs so could I suggest that you reinforce my complaint.

This with any luck will highlight that this is not an isolated incident.


EDIT. Ripped out Rhythmbox, left it for a day or two and re-installed. Now works.

---

### Post by chayzer on 2011-03-29
A little bit late, but maybe this will help someone who finds this thread. After being completely frustrated I found a little write up that basically states the following.

- open gconf-editor
- navigate to apps/rhythmbox/state/play_order
- change it to random-by-age

and it will tend to favor songs that haven't been played in awhile. It seems much better and I'm only about 4 songs in.

[http://www.last.fm/group/Rhythmbox/forum/8096/_/288791]("http://www.last.fm/group/Rhythmbox/forum/8096/_/288791")

---

