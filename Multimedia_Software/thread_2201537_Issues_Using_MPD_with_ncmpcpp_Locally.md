---
title: "Issues Using MPD with ncmpcpp Locally"
date: 2014-01-24
forum: Multimedia Software
---

### Post by sam30 on 2014-01-24
I'm interested in setting up ncmpcpp / MPD as my local music player for Kubuntu 12.10. I have looked at various tutorials over the past two days and I probably now have some unholy combination of several different setups.

** Symptom**: While MPD is running, I press enter to play a song in ncmpcpp. Within a fraction of a second, ncmpcpp skips down to the bottom of the playlist (as though I were pressing ">>>>>>"). No sound is emitted.

**Relevant Log Message**:

In [FONT=courier new]~/.mpd/mpd.log[/FONT], this statement is inserted exactly twice for every song that is skipped over when I attempt to play a song in ncmpcpp, as described above. e.g. If I try to play the first song in a list of 25, there will be 50 more of these lines in my mpd.log
```
Jan 24 18:08 : decoder_thread: Unrecognized URI
```

So, what is the URI that is not being recognized? Is it the filepath to my music files? How do I fix it?

---

### Post by sam30 on 2014-01-25
Ah, I see it now. In [FONT=courier new]mpd.conf[/FONT] I had the variable music_directory set to /home/lombard/Music. Then in [FONT=courier new]mpdstate[/FONT] the filepaths were only Artist/Album/Song, when they really would need to be FLAC/Artist/Album/Song.

So indeed I was telling MPD to look in the wrong place. A simple 'mpc update' was all I needed to do.

---

