---
title: "VLC audio playback - pops, crackle"
date: 2008-07-12
forum: Multimedia Software
---

### Post by logos34 on 2008-07-12
I normally use amarok, but I really like the VLC ncurses terminal interface for audio playback, but I'm getting occassional pops and static on high notes almost like it's clipping...I've turned down vlc's default volume to ~75%, but still doesn;t help.  It's not the PCM level, I've got that set right.  All the files are ogg 

Is there a good config guide someone can recommend other than vlc manual?

---

### Post by sakis on 2008-07-13
> **logos34 said:**
> I normally use amarok, but I really like the VLC ncurses terminal interface for audio playback, but I'm getting occassional pops and static on high notes almost like it's clipping...I've turned down vlc's default volume to ~75%, but still doesn;t help.  It's not the PCM level, I've got that set right.  All the files are ogg 

Is there a good config guide someone can recommend other than vlc manual?
If you have the same problem as here [http://ubuntuforums.org/showthread.php?t=842875](http://ubuntuforums.org/showthread.php?t=842875) try Settings--> Preferences--> mark "Advanced options"--> Audio--> Output modules--> Audio output audio--> set it to "ALSA audio output"

Hope it helps :)

---

### Post by mc4man on 2008-07-13
You could look thru the wiki though alot is outdated, maybe something relevant in videolan forum
[http://wiki.videolan.org/Main_Page](http://wiki.videolan.org/Main_Page)

 This may be of no value but while playing look in view -> stream and media info -> statistics to see if your dropping buffers ect. and also enable messages (takes several secs to catch up) to see if anything unusual occurs at moment of issues,  downmix mess. are normal  (maybe only available with wx interface ?)

---

### Post by logos34 on 2008-07-13
Thanks for the response.

Unfortunately it's already set to ALSA.  That is to say, ALSA is the default, and VLC output is set to 'default'.  Unless PulseAudio is introducing noise before it pipes the sound through to alsa.  I kind of doubt it (because I had same prob in feisty and gutsy).  Anyway, I'll try it set to explicitly to 'ALSA' and see how it goes.  

In the meantime I glanced through the official vlc user docs and wasn't terribly impressed with the level of detail for a media app which has more options than you can shake a stick at.  I guess I was expecting something like that of Mplayer.  

add: I've also been having glitches in audio track of dvd playback--I thought it must be the disk (most are library copies horribly scratched) but maybe it is vlc

---

### Post by mc4man on 2008-07-13
> Anyway, I'll try it set to explicitly to 'ALSA' and see how it goes.
In hardy it must be set to alsa (meaning vlc settings)

---

### Post by logos34 on 2008-07-13
> **mc4man said:**
> In hardy it must be set to alsa (meaning vlc settings)

Ok, I hope that's the ticket...I'll test it right now

---

### Post by logos34 on 2008-07-14
That's better.  But now another problem...

I notice that when I draw up my own playlist (vs. just loading whole album), there's invariably a hiccup at the start of nearly every track.  It even happens on tracks that naturally follow one another on the same album.  What the hell?  VLC works great as a dvd player, but has gives me nothing but problems wit audio playback.  Oh, and that reminds me of something else I have to be careful to avoid: gapless track transitions.  It's never been able to handle it.  (nor does Amarok--or rather the xine engine).  The only player that handles gapless playback seems to be Audacious with the crossfade-plugin.

Any ideas?

---

### Post by mc4man on 2008-07-15
> gapless track transitions..... (nor does Amarok--or rather the xine engine Never had a problem in that regard with amarok. Don't know what the difference could be. I have music stored in dir/subdir's (artist/albums) and just use them to a create play time list w/ several r. click actions, though that doesn't seem like it should matter.  ?

---

### Post by logos34 on 2008-07-15
> **mc4man said:**
> Never had a problem in that regard with amarok. 

Really...I've read a lot of gripes about that, and half a dozen statements blaming the xine backend for it (I'm talking specifically ogg files here, which is what nearly all my lossy are)...I gave up a while back trying to fix it.  Because if it's a live album or classical album with no gaps between tracks or movements, then I get the 1 sec silence (or half sec or whatever). 

I'll keep experimenting with VLC playlists, see if I can iron this out...

---

### Post by mc4man on 2008-07-15
> specifically ogg files 
my son ripped most of our cd's a while back on his win box and used wma lossless, I didn't bother to redo, just copied over. Maybe that's the difference.
Saw a post a few weeks ago @ videolan complaining about gapless so what you get for vlc may be the way it presently is. I can't try vlc cause it won't play the lossless wma format.

---

### Post by zipperback on 2008-07-17
Perhaps this might help.

[http://ubuntuforums.org/showthread.php?t=789578&highlight=vlc+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=vlc+problem)

- zipperback
:popcorn:

---

### Post by logos34 on 2008-07-17
> **zipperback said:**
> Perhaps this might help.

[http://ubuntuforums.org/showthread.php?t=789578&highlight=vlc+problem](http://ubuntuforums.org/showthread.php?t=789578&highlight=vlc+problem)

- zipperback
:popcorn:

thanks, i'll look that over

---

