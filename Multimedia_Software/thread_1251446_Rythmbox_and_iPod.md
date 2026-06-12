---
title: "Rythmbox and iPod"
date: 2009-08-27
forum: Multimedia Software
---

### Post by MrZehl on 2009-08-27
Just bought an iPod Classic 120GB and it's great. I connect it to my computer and Rythmbox can handle it. When I copy FLAC to my iPod Rythmbox automaticly converts it to mp3. Nice.

But I can't set anywhere the quality of the conversion and Rythmbox converts the flac files to mp3 with a bitrate of 128Kb! Of course I want better quality, especially for the albums I have in flac format. There is a reason why it's flac. I like to hear those albums in the best quality. Does anybody have a clue how to do that? I don't.

Sure I can check every file if it's flac or not before I copy it and when it is convert it myself, but that is a lot of unneccessary work. I like the way Rythmbox handles it, just want a higher bitrate.

Is there a settingsfile somewhere i can edit? Didn't find it. Or is there a better program I can use?

---

### Post by MrZehl on 2009-08-29
It seems to be a gstreamer problem. I changed the audio profile of MP3 to 

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 quality=0 vbr-min-bitrate=32 vbr-max-bitrate=320 lowpass-freq=20500 ! id3v2mux

But still I get 128Kb mp3. Any ideas?

---

