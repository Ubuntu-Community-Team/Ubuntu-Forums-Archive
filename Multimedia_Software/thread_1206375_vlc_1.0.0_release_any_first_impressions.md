---
title: "vlc 1.0.0 release: any first impressions?"
date: 2009-07-07
forum: Multimedia Software
---

### Post by andrew.46 on 2009-07-07
Hi,

Looks like vlc 1.0.0 came out today. Any first impressions from eager compilers and packagers? My own copy is compiling away madly as I type this message :-).

Andrew

---

### Post by mc4man on 2009-07-07
Interesting, didn't know till your post, not posted yet on website. Much to late here except for a cursory look.

 Plus built on hardy which may or may not  be a factor. (though with some adjustments builds fine with virtually all plugins available,  exceptions being the mozilla plugin and nls

Seems to be some nice new features, though area's that had 'issues' continue to do so 
No change in dmo loader, and some types of dir.'s continue to load improperly, particularly from the vlc side.

The one instance and enqueue files when in one instance mode still don't appear able to co exist.

Something new (may be a local or syntax issue) is the --http-caching parameter doesn't work as well as in 0.9.9a

for instance this worked perfectly on 0.9.9a, but only allows  < 17 secs on 1.0.0 (and higher. Depending on time of day no caching is needed, others a bit higher (makes no diff. on 1.0.x

```
vlc --http-caching 3000 http://movies.apple.com/movies/universal/publicenemies/publicenemies-tlr1_h1080p.mov
```

Does play mlp files now, the record button is interesting and I'm sure much, much more.

Any deficiencies (whether local or actual) have workarounds and or other players that work as expected (mplayer, amarok, ect.

---

### Post by mc4man on 2009-08-12
Vlc 1.0.x is now up to 1.0.2 and most of what was mentioned in previous post hasn't changed
(( borked dmo loader, usually loads multiple files from a dir. in a seemingly random order, enqueue and 1 instance not co-existing, some others.

One I thought was a problem - a locally stored VIDEO_TS folder containing more than just the main title not loading correctly with navigation was simply a change in method
(( A VIDEO_TS folder should be opened from media -> open disc -> browse, certainly when it contains menu's, multiple titles. In 0.8.6.x you would open a dir.  

Overall though seems to run smoothly, though use 0.9.9a more often atm.

All of those minor issues have workarounds with the exception of http, though only have tried with HD streams. some others have mentioned the same behavior elsewhere, but curious if any have success with 1.0.x (0.9.9.x continues to be fine

Add. ex.'s,  1080p, 720p can be substituted in address's

during ideal times no add. caching is needed here, though usually use 3000 for all 1080p, sometimes a bit higher (4500 - 9000) for 1080p 
A small cache helps prevent dropped frames even if not needed for clip completion. (3000 = 3 sec's

If display size is smaller than video, for vlc it's best to open vlc, maximize the interface and then close. Then when it opens on the stream it will in a maximized window with video properly scaled. (otherwise may run off of screen.

```
vlc --http-caching 3000 http://movies.apple.com/movies/disney/aliceinwonderland/aliceinwonderland-tsr1_1080p.mov

```
```
vlc  http://movies.apple.com/movies/independent/balibo/balibo_720p.mov

```

 ```
vlc   --http-caching 3000 http://movies.apple.com/movies/paramount/star_trek/startrek-tlr2_h1080p.mov

```


A bit more 'challenging'

```
vlc   --http-caching 3000 http://movies.apple.com/movies/paramount/transformers2/transformersrevengeofthefallen-tlr2r_1080p.mov


```

In 1.0.x none will play much longer than 12 -17 sec's here.. plus when --http-caching is used seems to take twice as long to buffer and still fails

---

