---
title: "Trouble with .mov playback"
date: 2009-07-08
forum: Multimedia Software
---

### Post by trxgt05 on 2009-07-08
I've been trying to play some files with the .mov extension and am having difficulty getting them to play properly. Totem tries to open and then crashes. MPlayer opens and then gives a "Fatal Error" message saying "Error opening/initializing the selected video_out (-vo) device. After clicking ok on the message, it starts playing the only the audio from the video. VLC opens the video and brings up an error about not having the Qclp codec. After clicking ok the video plays but with no sound. I ran across some posts and the only solutions I found were doing sudo apt-get install ubuntu-restricted-extras and sudo apt-get install w32codecs. I've tried both and the only change was that VLC now goes straight to playing the video but still with no sound. Any ideas?

---

### Post by trxgt05 on 2009-07-08
I also just downloaded Smplayer and tried it. It plays the video along with the sound, only the video is choppy. Compiz isn't the problem because I turned it off and still had the same problem.

---

### Post by smuggly on 2009-07-09
Do You Have Restricted Formats Installed ? Try VLC Also

---

### Post by rvm4000 on 2009-07-09
> **trxgt05 said:**
> I also just downloaded Smplayer and tried it. It plays the video along with the sound, only the video is choppy. Compiz isn't the problem because I turned it off and still had the same problem.

Try setting the cache to 0 and see if that helps (preferences -> performance -> cache).

---

### Post by trxgt05 on 2009-07-09
> **smuggly said:**
> Do You Have Restricted Formats Installed ? Try VLC Also

Thanks for the reply and no offense but please look at my first post.

> **trxgt05 said:**
> VLC opens the video and brings up an error about not having the Qclp codec. After clicking ok the video plays but with no sound. I ran across some posts and the only solutions I found were doing sudo apt-get install ubuntu-restricted-extras and sudo apt-get install w32codecs. I've tried both and the only change was that VLC now goes straight to playing the video but still with no sound.

---

### Post by trxgt05 on 2009-07-09
> **rvm4000 said:**
> Try setting the cache to 0 and see if that helps (preferences -> performance -> cache).

The cache for local files was already set to 0. So was the cache for DVDs and the cache for streams was 1000 but I doubt that would matter since the file I'm dealing with is sitting right here on my desktop.

---

### Post by trxgt05 on 2009-07-09
I just got the error message again in VLC. And I quote "No suitable decoder module:
VLC does not support the audio or video format "Qclp". Unfortunately there is no way for you to fix this."

That doesn't sound very promising at all. And to be honest I don't see what all the hype is about VLC. I keep seeing so many people recommend it and talk about how much they love it but I've never gotten it to do anything for me. I may be the only one but I'm rather disappointed in VLC.

---

### Post by rvm4000 on 2009-07-09
> **trxgt05 said:**
> The cache for local files was already set to 0. So was the cache for DVDs and the cache for streams was 1000 but I doubt that would matter since the file I'm dealing with is sitting right here on my desktop.

Ok, some people reported similar problems with mp4 files and it seems the solution was to set the cache to 0.

Then try the opposite, increase the cache (4000 or so).

If that still doesn't fix the problem, see if changing the "correct pts" (in preferences->advanced) makes any difference.

---

### Post by mc4man on 2009-07-10
> "No suitable decoder module:
VLC does not support the audio or video format "Qclp". Unfortunately there is no way for you to fix this."

That's a semi generic and somewhat poorly composed error message for vlc.

What it should say is "This install of VLC....... There may or may not be any way to fix without rebuilding"

For the most part vlc can play "Qclp, though with at least one variant you'll get no sound. (but you shouldn't see the error message.

mplayer also should be able to play, uses I believe w32codecs by default while vlc will use avcodec

maybe see if ffplay can handle (ffplay /path/to/whatever.mov

or what ffmpeg reports (ffmpeg -i /path/to/whatever.mov

small snippet from vlc and .mov w/qclp

> [0x81d7200] main demux debug: using demux module "mp4"
,,,,,,,,,,,,,,
[0x81d16c0] main decoder debug: looking for decoder module: 33 candidates
[0x81d16c0] avcodec decoder debug: libavcodec already initialized
[0x81d16c0] avcodec decoder debug: ffmpeg codec (QCELP Audio) started
[0x81d16c0] avcodec decoder debug: Using 1130496 bytes output buffer
[0x81d16c0] main decoder debug: using decoder module "avcodec"


---

