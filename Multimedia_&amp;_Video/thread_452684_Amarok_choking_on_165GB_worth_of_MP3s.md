---
title: "Amarok choking on 165GB worth of MP3s?"
date: 2007-05-23
forum: Multimedia &amp; Video
---

### Post by lowracer on 2007-05-23
I'm looking for a LInux based MP3 player that won't choke on 165GB worth of MP3s.  This load has been killing Amarok lately.  Or maybe it's just Amarok choking in general for reasons unrelated to the number of MP3s.  Lately Amarok has needed to be terminated unnaturally because it locks up.  This happens quite frequently and usually always on initial run of the program.   FWIW I usually just run a playlist with 50 random tunes so it's not like I'm asking it to list all of the music at once.

BTW I'm running an Intel core 2 duo system at 2.1GHz plus, with 1GB of RAM and it never touches the swap, so there should be plenty of horsepower. Latest version of Amarok, Feisty Kubuntu 7.04.  System kept updated religiously.  It used to work fine, now it doesn't.  

What could I be missing?

Thanks,

-Mark

---

### Post by onbongos on 2007-05-23
if amarok has an option to 'update library at startup' or something try disabling it

---

### Post by aidanr on 2007-05-23
mpd handles my 20gigs of music with ease on a less powerfull machine than yours, so i'd say give mpd a shot

---

### Post by onbongos on 2007-05-23
> **aidanr said:**
> mpd handles my 20gigs of music with ease on a less powerfull machine than yours, so i'd say give mpd a shot

++ i'm alternating between mpd and moc on ~100gb and it's ok

---

### Post by lowracer on 2007-05-23
OK I tried changing the database from SQLite to MySQL.  So far it looks good...

---

### Post by Ubuntwan on 2007-05-23
I don't think it is the number of tracks in your playlist.
My AMD 3000+ with 1G RAM runs Amarok fine with just a little more than 150G of music on a ntfs partition on the same Seagate 300G disk.
To put it to a little test, at the moment I run Listen music player with >23000 tracks in the Now Playing list, Rhythmbox with >23000 tracks in its Play Queue and Amarok which is even populating a playlist with all those same tracks at the moment, all simultaneous. All players are shuffling and play without any hickups....
Even the responsiveness of the players is just a little slower.

[edit appended]
My Amarok runs SQLite, but all players were not told to watch the directories continuoulsy however

---

### Post by lowracer on 2007-05-23
41374 tracks...  still rocking out OK with MySQL.  Maybe that was the problem.  I'll keep an eye on it.

---

### Post by ronocdh on 2007-05-23
> **lowracer said:**
> OK I tried changing the database from SQLite to MySQL.  So far it looks good...
This is exactly the issue. Upon initial install, Amarok asks you about this. For most people, SQLite is entirely sufficient. For your case, MySQL is necessary. Good luck to you.

---

### Post by TheMono on 2007-05-23
I noticed it slowing down around the 15000 track mark, so I switched to MySQL, and it has scaled perfectly since then.

---

### Post by lowracer on 2007-05-23
Make that 20480 tracks...  Had some duplicate entries in there that Amarok nicely cleaned up.  Still rocking.  Thanks for all the responses.   

Now if I could just get this kind of timely support for the commercial Windows-based software I have to use at work...   Not likely...

---

### Post by steevk on 2007-05-23
Mine has been choking, too, so I've been using Banshee. It works well.

---

### Post by lowracer on 2007-05-24
Well I spoke too soon.  Now Amarok won't load at all.  Tried completely uninstalling and reinstalling and no dice.  I'm giving up on Amarok and trying one of the other players suggested.  Hope the Amarok team can fix whatever is busted with it, because it was a nice player.

---

### Post by lowracer on 2007-05-24
Had Banshee working for about an hour, then I used it to delete a song and it died and won't restart.    It had the ability to share music tracks with my wife's iBook laptop over the wireless network too, that was useful and working well, now nothing.

What is it about 20,000 tracks that freaks these players out?   

Continuing my search for a usable player.  Looked at mpd but what I want is a single app that I can tell it, "hey here's my music directory, play these" and have it just play the songs.  I'm not interested in hooking up clients and servers and config files.  Just want something simple to use that can play music, lots and lots of music.

---

### Post by lowracer on 2007-05-24
Fingers crossed.  Rythmbox is working and sharing files across the net with iTunes.  It had the fastest load time for my whole mp3 collection too, even faster than Amarok.

---

### Post by (chubbstar) on 2007-05-25
ive got about 215gigs of music and my amarok suffers from the same faults. ill admit it has never come to the point of such extreme unuseability that you speak of but it certainly crashes from time to time and struggles when loading large playlists.

ive got my fingers crossed for amarok 2.0.... should be out late summer last i heard.

---

