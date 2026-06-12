---
title: "Mp3s, multiple genre tags, and MPD"
date: 2013-07-11
forum: Multimedia Software
---

### Post by Witra on 2013-07-11
First things first, I'm still rather new to ubuntu, thus what I'm about to ask may seem rather basic. However, during the last few hours of googling & searching various forums, I failed to find a comprehensive answer. 

So, onwards: 
I know it is possible to store multiple genres in mp3 genre-tag. However, it is unclear to me how this is done precisely. 
From the reference material I've been able to dig up, the id3 v2.4 specifies genres should be separated by a null character. Now, how does one insert that, whatever it is, precisely? In, for example, [easytag]("https://projects.gnome.org/easytag/")? (I haven't tried it out yet and can't until this weekend)

And while we're on the subject, how do I get mpd to understand such multiple values? 
According to [this]("http://bugs.musicpd.org/print_bug_page.php?bug_id=2728"), the functionality should be available(I currently have 0.16.5 installed). 

Oh, and a third question. Is there a handy tool available for converting id3 tags from various older versions(mostly v1) to v2.4? Easytag could quite probably do it, but haven't yet tried it out. I'd much prefer a command line tool, so I could write a script and run through my entire library(around 30-40 000 songs) without much effort beyond writing the aforementioned script.

---

### Post by tgalati4 on 2013-07-11
Multiple genres will probably break more players than any benefit that you would derive.  Do you have some examples (use cases) as to how multiple genres is valuable?

*Easytag*, in its preferences, has several options for turning  ID3V2.4/3 on or off, or just using ID3V1.  There are also options for tailoring ID3V2.4/3 for specific purposes or players.  

I have not used *easytag* for inserting multiple genres, but post your experiences and let us know what breaks.

The bug that you reference in mpc could simply be reading both ID3V1 and V2 and filtering on genres.  Since mpc/mpd has been around a long time, it's not surprising that it doesn't handle multiple genres correctly.  

One work-around would be to use single genres and then use playlists (saved and named appropriately) to put tracks into sub-genres or additional genres.

```
apt-cache search ID3
```  brings up a few ID3 editors, but you will have to experiment to see what works for scripting.  My guess is that with that many tracks, any script will break down frequently simply due to errors in ID3 encoding.

*Easytag* can do multiple-file ID3 tag stamping, but you have to be careful how you use it and you have to test the files to make sure they work with all of your players.  Otherwise, you will fix tags to work with some players and break tags on other players.  It's a simple fact of too many players and too many frameworks to get a reliable tagging scheme that works with everything, all of the time.

---

### Post by Witra on 2013-07-12
> **tgalati4 said:**
> Multiple genres will probably break more players than any benefit that you would derive.  Do you have some examples (use cases) as to how multiple genres is valuable?

Subgenres, mostly. 
Folk metal serves as a rather good example in this case. It'd be exceedingly handy to have certain songs/Artists appear under heavy metal, folk metal as well as a given sub-genre of folk metal(celtic, for instance).

I'll test out easytag & multiple genres sometime over the weekend with one or two albums and report back. However, since there is a documented way to do just that(id3 v2.4), and according to the bug report I linked to in the previous post multiple genres has been implemented in mpd(or should be, since it was scheduled for 0.15.7) it should work, according to all reason, if easytag has the feature.
Now, I'm not familiar with the detailed workings of mpd, thus correct me if I am wrong, but do clients not simply connect to mpd and request, say, list of a certain genre/all available genres? 

Thus if mpd supports multiple ones, clients should not be the source of worry.

---

### Post by samfuzz on 2013-09-05
i'm using multiple genre value with MPD 0.16 with success for
- mp3 (id3v2.4, null character),
- OGG, Flac (Vorbis tag), 
- musepack MPC (APEv2 tag) 
- m4a : only if MPD is compiled with mp4ff plugin, don't work with ffmpeg plugin, but mp4ff will be disable for the future version because it's deprecated.

for the client side : it's OK with :
 - GMPC 
- MPDroid

i don't use others clients


for tagging i'm using for all format (mp3, ogg, flac, mpc, m4a) :

 - puddletag 
- gmusicbrowser 

with no problems


i'haven't seen any problems with others player (rythmbox, banshee ..) only the first genre value is recognized

---

