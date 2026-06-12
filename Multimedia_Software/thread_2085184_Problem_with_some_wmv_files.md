---
title: "Problem with some wmv files"
date: 2012-11-17
forum: Multimedia Software
---

### Post by TroubBle on 2012-11-17
Hi,

I'm having problems with SOME (not all) of my wmv files. 
I can play them with the standard movie-player. But when I click on the bar at the bottom of the window (to jump to a designated period), the video will no longer play, but simply stand still. I can click on other locations of the bar, and the video will also jump to these location, but it will never play, until I close the movie-player and start the video again (the only possibility which I have so far is to simply watch the movie from the beginning to the end)

The Video-Codec of those videos is "Microsoft Windows Media 9" and the audio codec "WMA Version 8" (but there are other videos with the same codexes that can be played just fine)

What can I do?

MfG

---

### Post by evilsoup on 2012-11-17
You could try a different video player; the standard recommendations are VLC and SMplayer (I prefer VLC, but they're both really good).

If that doesn't work, you can also try re-encoding the files, but that's really a last resort.

---

### Post by TroubBle on 2012-11-17
> **evilsoup said:**
> You could try a different video player; the standard recommendations are VLC and SMplayer (I prefer VLC, but they're both really good).

If that doesn't work, you can also try re-encoding the files, but that's really a last resort.
The last time I was using VLC was under Windows. At the time I used it, it had a lot of security holes. Is it similar under Linux?

---

### Post by evilsoup on 2012-11-17
I have no idea, sorry.

EDIT: [I think it's fine](http://www.h-online.com/security/news/item/VLC-Media-Player-2-0-1-closes-security-holes-1474770.html), assuming those are the same security holes you were referring to.

---

### Post by TroubBle on 2012-11-17
OK, thanks. I'll try those two players.
Just in case this doesn't work: What's a good way to re-encode the videos?

---

### Post by evilsoup on 2012-11-17
The way I do it is with a command-line program called avconv (a mostly-compatible fork of ffmpeg); I use the version from the [medibuntu repository]("http://www.medibuntu.org/"). There are GUI programs that can do the same thing: winFF and Avidemux are two that are often suggested, though I don't use those & so can't really give you any suggestions. Start a specific thread and I'm sure that others will pop in and help you.

For video there are container formats (MP4, AVI), which can contains several video (h.264, MPEG2, XVID) and audio tracks (AAC, MP3, Ogg Vorbis). Sometimes there is a problem with a container, but the actual video & audio tracks inside are perfectly fine; in this case, you can simply remux the video - take the tracks and put them in a new container. I would use the MKV file format for this. In a terminal:

```
avconv -i input.wmv -c:a copy -c:v copy output.mkv
```With this method, you won't lose any quality. Again, there are GUI ways of doing this, but I don't know them. If you are unfamiliar with the Linux command-line, but willing to learn, [this site]("http://linuxcommand.org/") will teach you the basics. If you don't want to learn (it's seriously not as hard as it looks), then you'd be better off using one of the GUI options.

If that avconv command doesn't work, then you'd have to actually transcode to video - that affects the video track (more properly called a stream) rather than just the container, and inevitably loses some quality - though not a noticeable amount, if you do it right. I would be happy to go into that a bit if you want/need it. But between using a different player and the above command, you probably won't.

---

