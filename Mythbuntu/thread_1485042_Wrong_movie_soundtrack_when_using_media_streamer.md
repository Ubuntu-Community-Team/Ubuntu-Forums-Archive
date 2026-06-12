---
title: "Wrong movie soundtrack when using media streamer"
date: 2010-05-16
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-16
I have a strange problem when I try to watch a particular movie using a Zyxel media streamer. I get the wrong soundtrack. Rather than the usual soundtrack, I have a voice giving a commentary on everything that is happening (presumably intended for blind people).

It only happens when I watch it via my media streamer. If I watch it directly from my MythTV box (Mythbuntu 9.10), everything is fine and I get the correct soundtrack.

I originally recorded the movie from the TV, edited out the adverts by marking them manually and using mythtranscode, and then manually moved the file to my videos folder.

Other movies (mostly ripped from DVDs) in my videos collection play OK with the correct soundtrack over the media streamer.

Any ideas what's going on here and how I can fix it?

Thanks
NM

---

### Post by ian dobson on 2010-05-16
Hi,

You should be able to change the audio stream played by your media streamer. On my frontend I can select between German,English,French for some programs/channels.

Regards
In Dobson

---

### Post by NautiusMaximus on 2010-05-16
Sadly, my media streamer is probably less sophisticated than yours, and doesn't allow any means of selecting a specific audio track.

I opened up the file in VLC player on my Mythbuntu box, which also played the commentary soundtrack by default, although it allowed me to switch tracks. It seems that the commentary soundtrack is track 1, and the proper soundtrack is track 2.

I guess track 1 is used by default.

Is there any way either to delete track 1 or to switch the order of the tracks?

Thanks
NM

---

### Post by NautiusMaximus on 2010-05-29
Bump

---

### Post by ian dobson on 2010-05-30
Hi,

Are you sure you can't change the sound track (it maybe called "Audio Language") on your media player.

I have a 100Euro DVB-c reciever and even that allows me to swap between the Audio languages(sound tracks).

The only other way would be to transcode the video cutting out all the unnecessary sound tracks.

If you have a link to a PDF version of the usermanual for your player I'm willing to have a look at it.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-30
Well, I couldn't find any way of choosing the audio track in my media player, but I guess it's possible I've missed something.

The manual for my player can be downloaded [here]("http://www.zyxel.co.uk/web/support_download_list.php?indexflag=20040906173729&ModelIndexflags=0,420051115090505").

---

### Post by ian dobson on 2010-05-30
Hi,

Your right, I can't see anything in the user manual to allow you to choice the audio track to play, apart from the audio button but that only seems to be for mono/stero. On my itgate dvb reciever when I press the audio button on the remote I get a list of available auto languages.

Maybe ask the manufacturer if it's possible.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-30
Many thanks for looking, Ian, much appreciated.

I've emailed the manufacturer and await their response.

If they say it's not possible, then is there an easy way to transcode the movie file deleting the unwanted audio tracks?

Thanks
NM

---

### Post by NautiusMaximus on 2010-06-17
Well, no reply from the manufacturer's tech support (note to self: don't buy anything from Zyxel again), although it really doesn't look from the documentation or from randomly pressing buttons on the remote that it would be possible anyway.

So does anyone know of a way to reorder the sound tracks or delete the unwanted ones?

Thanks
NM

---

### Post by ian dobson on 2010-06-17
Hi,

The only way is to transcode the video removing the unwanted audio channels, maybe with ffmpeg (not sure about this).

Have your supplier brought out an updated firmware? Maybe next time have a look at a xstreamer (my assistant at work love them, he says that it can play anything he throws at it including MKV).

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-06-18
Thanks Ian, I shall check out the documentation for ffmpeg and see where that takes me.

---

### Post by nickrout on 2010-06-19
what filetype is it? container and codecs? try avidemux.

---

### Post by NautiusMaximus on 2010-06-20
It's an mpeg file. I originally recorded it of the TV using MythTV.

It turns out that ffmpeg did the job nicely, once I'd read the documentation. The moral of this story is that sometimes the only answer you need to a question is "RTFM", as long as that information is accompanied by the crucial piece of information about which FM to read (not that anyone on this forum would ever be so bad mannered as to actually say "RTFM", of course!)

If anyone else needs to accomplish the same thing, the syntax was as follows:

```
ffmpeg -i oldfile.mpg -map 0:0 -map 0:2 -sameq -ab 192k newfile.mpg
```

The key to doing what I wanted to do was the -map option. 0:0 is the video track, and 0:2 is the second audio track, so the above command tells it to combine those 2 into the new file.

The -sameq option in theory does it all losslessly, although that only seemed to apply to the video encoding. The default options took the audio bitrate from the original 192 kbit/s to 64 kbit/s. Specifying the -ab option sorted that out.

Many thanks for pointing me in the direction of ffmpeg: looks like a very useful little command.

---

