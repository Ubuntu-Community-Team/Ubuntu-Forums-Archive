---
title: "tvtime bombs on an Acer Aspire One"
date: 2009-09-12
forum: Multimedia Software
---

### Post by Infoteksec on 2009-09-12
Hi, I was delighted to get encouraging messages in DMESG when I plugged in my Tevion 6530 so I installed TVTIME, poured a glass of wine, opened a packet of crisps and got comfortable.

I was disappointed to find TVTIME bombed almost as soon as it started. Others who had the same problem suggested XawTV. I tried it and it aborts in the same way.

Is there any way to watch TV on my AOA running Ubuntu 9.04?

Peter

---

### Post by rob-ward on 2009-09-12
You could try mplayer, it allows you to watch tv inputs, or vlc does, they do however take a bit more setting up and trial and error than tvtime but should be more stable to errors.

---

### Post by Infoteksec on 2009-09-14
> **rob-ward said:**
> You could try mplayer, it allows you to watch tv inputs, or vlc does, they do however take a bit more setting up and trial and error than tvtime but should be more stable to errors.

Thanks for this ... however, the plot thickens. I have since discovered that pretty much all multi-media apps now break on my system. AVI files which I downloaded and watched weeks ago now fail. For example, VLC (now of my favourites for watching Shoutcast TV) crashes within milli-seconds of its starting up. 

I think I have received a bad update somewhere along the line. Its time to recover to an earlier backup.

Peter

---

### Post by rob-ward on 2009-09-14
I am assuming that it is just the media application that is crashing and not the operating system from what you are saying, this seems really strange to me because multiple applications arn't even using the same codecs do decode the media. Could you try playing back a file using VLC but activating it from the commandline and seeing what output VLC produces.

---

