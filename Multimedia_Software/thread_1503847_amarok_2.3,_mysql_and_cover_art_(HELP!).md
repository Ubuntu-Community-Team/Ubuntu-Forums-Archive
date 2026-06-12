---
title: "amarok 2.3, mysql and cover art (HELP!)"
date: 2010-06-07
forum: Multimedia Software
---

### Post by chowanec on 2010-06-07
Hey all,

This is a bit of an OCD problem. And a bit of a database problem. And it involves a rather big music database.  I'm running Amarok 2.3.1 and am storing my database in mySQL on the local client machine (i.e. not the media server).

I've finally gone and completed my folder art for the 28,000 tracks I have in my database. What I failed to realize at the time was that it was putting the artwork for my albums in my .kde/ folder off my home directory when I actually want them in the folder of the music itself.

I play music off my Linux Mint box, running Amarok 2.3.1 with a mySQL database storing the database information.

I have all my actual music (mp3) living on a network share ~/Network/Music/<Artist>/<Album>/

I have 800 or so cover art .jpgs in: ~/.kde/share/apps/amarok/albumcovers/large

They have names (hashcodes?) like: 1fe7c6615002313ec20274b6967c35ed

I'd like to basically:
1) Query the Amarok mySQL database to get the folder art name for each album.
2) If the cover art file for an album is stored off of ~/.kde/ then I know it is local to the client machine.
3) If (2) is true then query the same entry to get the artist name and album name
4) Check ~/Network/Music/<artist>/<album>/folder.jpg to see if it exists.
5) If (4) is false, copy the local file to the location in step (4).

That's where I need your help -- anyone got any good ideas? I have tinkered with bash scripts in the past, but know NOTHING of mySQL.  I figure the entire thing involves a pretty big query loop and then a lot of copying. :P

This is a music collection that has spanned 20 or so years at this point, and once it is complete, it is going to be much easier to maintain. Any help is appreciated.

-Chow

P.S. I've seen some amarok scripts that copy the artwork from the currently playing track, but that will take, well on average 28,000 * 3.5 minutes to run through my whole database.

---

### Post by chowanec on 2010-06-10
Nothing?  If I offer to send you a beer (via legal means?)

-Chow

---

