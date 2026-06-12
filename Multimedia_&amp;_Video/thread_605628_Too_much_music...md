---
title: "Too much music.."
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by slyfox on 2007-11-07
G'day all,

I'm currently trying to get my music collection into some semblance of order, can anyone recommend apps that can help me do the following (bear in mind there's 60GB+ of music, so all of them need to operate in a bulk fashion):

[LIST]
[*]Pull ID3 tags down from the internet for individual tracks, maybe even fetch cover art
[*]Convert every track into MP3, regardless of original format
[*]Restructure folders so each artist has a folder dedicated to them, and then album folders reside under that directory
[*]Delete duplicate tracks if they exist in the same folder
[/LIST]

I know that's a pretty heavy set of demands, but they're ones I thought everybody must want, and so my hunt would be for the common good (not least my friend who wants to do exactly the same thing :) )

I've googled for a couple of hours, and so has my brother in arms, but short of homebrew scripts that sort of do the job and lack necessary features (tried using mplayer and lame to convert m4a tracks, and it works, but doesn't copy ID3 tag info) we've yet to find anything that does any of the above..

What'd be reeeeally nice would be a GUI for each of these apps - but then are we asking too much? :p

TIA

---

### Post by tubasoldier on 2007-11-07
Sounds like you need to get into your music folder and do some cleanup work yourself. It would be well worth your time. Only You could restructure your music folder like that. Mine is ridgidly formatted not only on my ID3 tags but also in folder setup. It is much easier to maintain that way.

/home/~/Music/GENRE/ARTIST/ALBUM

I dont know of any Linux apps that could accomplish all of that for you. Plain and simple, you will have to do a little work.

---

### Post by slyfox on 2007-11-07
Yeah, I was thinking that the restructuring app was a bit of a longshot - but it must be something that a lot of people want, which normally means the app exists..

Any ideas on the other points? I'm currently looking at Quod Libet/Ex Falso for the ID3 tag handling, but its saying the CDDB plugin isn't installed, despite me apt-get'ing quodlibet-plugins.. will Google some more..

---

### Post by hugmenot on 2007-11-07
First of all, CDDB works only if you have all tracks of an album, selected in the right order. This is because the disc-id is calsulated from the track number and track lengths.

Did you install python-cddb too? It&#8217;s needed but I guess it is not pulled in with a "depends" or "recommends".

---

### Post by surfed on 2007-11-07
Amarok can do:    

with MusicBrainz:
* Pull ID3 tags down from the internet for individual tracks

Native:
fetch cover art

with the transfer to media device option (just use /dir) via transcode:    
* Convert every track into MP3, regardless of original format
 * Restructure folders so each artist has a folder dedicated to them, and then album folders reside under that directory
* Delete duplicate tracks if they exist in the same folder

---

### Post by kayosiii on 2007-11-08
In Amarok you can use the Organise Collection by right clicking on tracks in the playlist or collection and selecting "manage file(s) -> organise file(s)"... This will organise your collection into either Artist/Album or Letter/Artist/Album...

Also avoid converting files from one lossy format to another - it really does hurt the quality. Amarok can transcode files to mp3 on the fly if you need to transfer the files to a device that can only play mp3 files... I reccomend doing it this way.

---

