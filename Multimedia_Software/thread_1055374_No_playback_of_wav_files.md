---
title: "No playback of wav files"
date: 2009-01-30
forum: Multimedia Software
---

### Post by gsxruk on 2009-01-30
Hi,

I have just upgraded to 8.10 today.  Everything went fine but as some other users have posted I have problems playing wav files.  I had a number of wav files under 8.04 that played without any problems.  After copying these files back to the freshly installed drive after the upgrade, they no longer play.

Pretty sure I have installed all the extra codecs etc e.g. mp3 files etc play perfectly.

Does anybody know if this is a problem or have I forgot to add something?

Thanks.

---

### Post by mc4man on 2009-01-30
I'm assuming your using a gstreamer player (rhythmbox, totem, banshee, ect.
A few things you can do.
Ck. and see if your fully updated, if so and still no playback, then I'm 100% sure players like Amarok, Audacious, totem-xine, vlc, (s)mplayer will be fine.

Otherwise install sox and do what I'd call a 'mock strip'

Ex. .wav in home folder
```

sox ~/test.wav test1.wav
```

The outputted .wav should be fine (probably will be 70 bytes smaller

Or re rip the .wavs in 8.10 and they should be fine

---

### Post by gsxruk on 2009-01-31
Hi,

Thanks for the response.

You are correct, I was using Rhythmbox to play the files.  After the install the system was fully updated.  I installed MPlayer and this plays the file.

Are you suggesting that there is a problem with gstreamer in 8.10?

Thanks.

---

### Post by mc4man on 2009-01-31
> Are you suggesting that there is a problem with gstreamer in 8.10
Not really, though when 8.10 first came out the issue's with .wav's was a bit more extensive and I may have thought so.
I have a few idea's why .wav's from other systems may not be playable in 8.10 via gstreamer but purely speculation.

At this point any .wav you rip in 8.10 should be playable in gstreamer whether you use a gnome ripper or not. (the sole exception would be if you were to copy a .wav directly from the cd. (as in browse the cd and drag a track to your desktop.

As mentioned if you install sox and run the .wav thru it it will then become playable in gstreamer. (and remove 70 bytes

Because I only use Amarok and Audacious it not much of a concern here.

---

### Post by gsxruk on 2009-01-31
Like you say, at least I have a way of playing them now.

Thanks for your help.

---

### Post by jaygo on 2009-04-17
Fixed for me. Thanks much mc4man! Quick description for other readers:

mplayer & VLC could play my wav's but nothing else. I used sox to re-encode the wav files and they now play in my usual player (exaile).

I created the wav's in 8.10 a month ago but might have simply dragged them off of the CD, which apparently causes the broken header issue.

Soundconverter was also choking on converting these wav files until I ran them through sox.

---

