---
title: "How to View video bitrate in Edgy?"
date: 2007-01-17
forum: Multimedia &amp; Video
---

### Post by cor2y on 2007-01-17
Hello this is something i noticed today when i finished creating some vidos in both mencoder and avidemux.
But ALL of the videos even those from off the web seem to lack the information on video bitrate when you right click select properties->Audio/Video on the file in question, video bitrate is listed as N/A.
Even using the file cmd in terminal doesn't reveal the bitrate i had to use mplayer with -identify from the terminal to see the bitrate info.
Never had this problem in Dapper and just now noticed it in Edgy.

Any clues for a fix ?

---

### Post by crispy_420 on 2007-01-19
I just checked, and indeed Dapper does not show the bitrate of a video I encoded. Just an idea, but could this happen in a video with a variable bitrate. Just an idea though, maybe without a fixed rate, ubuntu/gnome doesn't know what to say.

---

### Post by cor2y on 2007-01-19
i am not tooa dept at understanding how to set up a constant bitrate for video encoding, its mostly two pass encoding i use or a fixed quantizer for one pass encoding.
Audio i  set for constant or variable bitrate that shows up clear enough in the audio section.
But not the video bitrate.

---

### Post by crispy_420 on 2007-01-21
With two pass encoding you will get a varible bitrate in video as you would in audio.

When you do a two pass, the video is analyzed for where more data is needed. That is the first pass. The second pass encodes based on the data collected.

For example:

If you encode, say a action dvd. The fight sequences with more moving objects use more data so the encoding knows to use more. But when it comes to slow scenes/credits, less is used. 

There is a good reason to do this. If you had a constant high bitrate, your video would look good but it would be a large file. On the other had, too low of bit rate will give you a small file size at a hit in quality. But variable does have a few drawbacks. Some time you get blockyness in the movie and some bluring on occasion. But it is worth the sacrifice.

Hope that helps shed some light.

---

