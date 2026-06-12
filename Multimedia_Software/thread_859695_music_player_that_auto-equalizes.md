---
title: "music player that auto-equalizes"
date: 2008-07-14
forum: Multimedia Software
---

### Post by estyles on 2008-07-14
So, let me say first that I hate iTunes.  I was almost relieved to hear that you can't run iTunes under Linux - not even under Wine.  So, this isn't a "Windows/Mac has this feature, why doesn't Linux" thread.

Anyway, I'm currently running Amarok and I love it.  Even though it's designed for KDE and I run Gnome - it doesn't matter, it's still a great music player.  I've run into some minor annoyances, like Amarok can't tag m4a files, but I got Picard for that, and it's reasonably easy to use.  But the main thing is a feature that I don't think any music player has, and I'm not sure why - it seems pretty easy and like something that people would want.  And I tried desperately to find a list of features for music players before deciding to go with Amarok (let's face it, once you've got something set up, you'd rather stay with it, barring a major reason to switch), but to no avail.  So I'm using Amarok now, but there's one feature that I really, really want.

What I really want in a music player is an auto-equalizer.  iTunes has something where you can set equalizer settings for each song, but that's not really what I want either, because you have to do it manually.  I'm not even talking about different settings for different audio bands, like a true equalizer, although that would be cool.  I just want all my songs to play at the same volume, or relatively close.

Ideally, songs should get a loudness rating of, say, 1 to 10, which the music player should determine by scanning the song - an average of the volume of the recording from beginning to end.  The user should be able to specify a range, say between 5 and 7.  Especially loud songs (rated 10) should play at 7 (like an amplifier setting), and especially soft songs (rated 1) should play at 5, with songs falling in a range in the middle.  Thus, loud songs would still be loud, but not *as* loud.

Barring that, I'd could live with just equalizing all songs to the *same* average volume.  But I'm surprised that people just deal with turning volume up and down when listening to music.  Especially late at night, I want to be able to listen without waking up the wife or straining to hear *anything* at all, and I don't want to have to keep fiddling with the volume when I'm trying to work.

So yeah... does anyone know of a music player that can do that?  Or a script for Amarok?  I'm just amazed that no music player does this (not just Linux-based, I'm not sure anything does this, and even if iTunes did, it wouldn't be worth it to use that garbage, crippled bloat-ware).

The other thing I want, and this is more of a pipe dream, is to have a music player that can put together playlists of your music, picking songs that "go together", with some sort of more complex algorithm than just picking the same genre.  Especially if it could do beat-matching to really make the most of cross-fading.  Kind of a virtual DJ.  I think that this should definitely be possible, though not as easy as an auto-equalizer, and it's something that one could easily live without - it would just be cool to have.

---

### Post by robinl on 2008-07-14
You mean replaygain? I use Foobar2000 in Wine to scan and tag my collection, then run the script available on [http://users.servicios.retecal.es/maacruz/](http://users.servicios.retecal.es/maacruz/) to apply the gain. Works quite well really.

---

