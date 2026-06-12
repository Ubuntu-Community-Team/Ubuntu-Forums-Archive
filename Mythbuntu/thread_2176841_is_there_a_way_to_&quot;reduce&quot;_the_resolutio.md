---
title: "is there a way to &quot;reduce&quot; the resolution of recorded shows?"
date: 2013-09-26
forum: Mythbuntu
---

### Post by harold95 on 2013-09-26
i'm using hdhr3 and mythbuntu 12.04.3
it set up perfectly and i have it working.

the files that are recorded are huge. 

is there a way to record the shows in something less than 1080i ?

i just dont need that kind of resolution for what i am doing.

thanks!

Harold

---

### Post by tgm4883 on 2013-09-26
You would need to transcode after recording the show. You cannot reduce the resolution as it comes in because the device is simply writing the stream to disk. The show is coming down the wire as a format that is already compressed for mythtv.

---

### Post by harold95 on 2013-09-26
ok, thank you. i didnt know if i was missing something or if transcoding was the way to go.

---

### Post by bullwinkle2 on 2013-09-26
What I have found is that transcoding really doesn't do much to reduce the size of the recording.  You might want to look into Mythbrake, which transcodes the mpeg recordings using Handbrake:  [http://www.mythtv.org/wiki/Mythbrake](http://www.mythtv.org/wiki/Mythbrake)  This will take considerably longer that MythTV's built-in transcoders (which are primarily format convertors) but can produce files that are significantly smaller than the original size.  Or, you could just try running HandBrakeCLI manually or from a shell script, but good luck figuring out the correct options to use!

---

