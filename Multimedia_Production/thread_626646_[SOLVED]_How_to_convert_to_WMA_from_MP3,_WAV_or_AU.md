---
title: "[SOLVED] How to convert to WMA from MP3, WAV or AU"
date: 2007-11-29
forum: Multimedia Production
---

### Post by Dafydd on 2007-11-29
**!!!!!!!! SOLVED !!!!!!!**

Hi,

Anyone know how to convert to WMA from MP3, WAV or AU?

I listen to BBC radio (via vsound which dumps it as a AU file).

I would love to listen to it on my new Olympus WS-110 (voice recorder with WMA playback).

Unfortunately, have no idea what tools/command (if any) to use to convert to WMA.

I know the format sucks (proprietary). Just 15 minutes of wasted time searching for WINDOWS converters on Wine convinced me of that. 

Can anyone help me?

Thanks

Dafydd

---

### Post by 900i on 2007-11-29
Can you use mencoder or ffmpeg, :)

---

### Post by Dafydd on 2007-11-29
> **900i said:**
> Can you use mencoder or ffmpeg, :)

Thanks for the quick reply.

Well, I sort of solved it (I think). I'm currently listening to a file converted by ffmpeg.

ffmpeg -i INPUTFILE.au -acodec wmav2 OUTPUTFILE.WMA

It works for AU files (but apparently also for MP3/WAV etc etc).

But I'm not sure about the quality of the WMA file (it seems a little bit touchy).

I should think twice before buying stuff. The WS-110 is a great machine (voice recorder that just shows up when you plug it it). The "only" problem is that it only plays back WMA files (no mp3 and of course no OGG files).

But at least I can now listen to recorded radio on the thing.

Cheers
Dafydd

---

### Post by olejorgen on 2007-11-29
You could also try sox.

Click thread tools -> mark as solved

---

### Post by Dafydd on 2007-11-30
> **olejorgen said:**
> You could also try sox.

Click thread tools -> mark as solved


Thanks. Have marked as "solved".

Do you know what would be the "sox" command to convert to WMA?

Also, listening to the WMA file produced I think the quality is just the same as LAME. But the only trouble with ffmpeg is that I cannot set the bitrate. If I try to set a bitrate I get an error message.

ffmpeg -i test.wav -acodec wmav2 -ab 128 test.wma

dafydd

---

### Post by olejorgen on 2007-11-30
whoops, seems like sox don't handle wma, sorry, must've misread wav.

It would probably be a good idea to post the error message :)

---

