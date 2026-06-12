---
title: "Audio Streaming Problem"
date: 2009-04-29
forum: Multimedia Software
---

### Post by MNGS on 2009-04-29
I'm trying to listen to live BBC Radio streams.

When I click on "Listen Live" at any of these
[http://www.bbc.co.uk/fivelive/](http://www.bbc.co.uk/fivelive/)
[http://www.bbc.co.uk/radio4/](http://www.bbc.co.uk/radio4/)
[http://www.bbc.co.uk/6music/](http://www.bbc.co.uk/6music/)

the new window opens the BBC "iPlayer," invokes the Realplayer I have installed...it buffers, the timer starts counting as if it was playing something, but there's no sound.

How do we fix this?

If the answer involves command line or very technical stuff, you'll have to give me specific, step-by-step instructions. And I'll be so grateful!

Thanks!!

---

### Post by rapsball4 on 2009-04-29
Probably related to the same problem I've got.  Just installed 9.04, don't remember it being a problem in 8.10 but honestly hadn't used it for a while.  Sound works fine in Rhythmbox and in tests, but nothing for Internet video attempts.  Creative Sound Blaster XtremeMusic, went to their site and got their drivers.

---

### Post by rapsball4 on 2009-04-29
Nevermind, shouldn't have jumped in on your thread too early.  Tried one of your links and it worked... not sure why, though so unfortunately can't help you.  Still nothing on YouTube, though.

---

### Post by andrew.46 on 2009-04-29
Hi MNGS,

> **MNGS said:**
> 
[http://www.bbc.co.uk/fivelive/](http://www.bbc.co.uk/fivelive/)
[http://www.bbc.co.uk/radio4/](http://www.bbc.co.uk/radio4/)
[http://www.bbc.co.uk/6music/](http://www.bbc.co.uk/6music/)


Half of the trick is to extract the actual urls for these broadcasts and they are respectively:
```

rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio5/live/r5_tl_int_g2.ra
rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio4/live/r4_dsat_g2.ra
rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/6music/live/6music_dsat_g2.ra
```

If you have a copy of vlc you can copy and paste these into: Media --> Open Network --> Address. This worked well for all three of the addresses on my own system.

All the best,

Andrew

---

