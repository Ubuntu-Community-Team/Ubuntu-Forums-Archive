---
title: "Converting to H.264 from Flash"
date: 2011-05-31
forum: Multimedia Software
---

### Post by Lars Noodén on 2011-05-31
What is the best way to convert a Flash link, say at YouTube, from Flash to the file hidden inside the Flash?  Is there an alternate link or is there another way other than running the file through ffmpeg?

---

### Post by FakeOutdoorsman on 2011-05-31
I'm not totally sure what you are asking. Most YouTube videos (recent ones at least, IIRC) are already in the MP4 container with H.264 video and AAC audio.
[url=http://rg3.github.com/youtube-dl/]
youtube-dl[/url] is easy to use to retrieve the YouTube video:
```
youtube-dl -t http://www.youtube.com/watch?v=axFlQ093FU8
```
Just make sure you're using the latest version of youtube-dl to keep up with any bug fixes, etc.

If you don't like that method, then you can often find the video in */tmp* while it's open in your browser, but I'm not sure if that works with Firefox 4 (I don't actually have flashplayer installed, so I can't test this).

---

### Post by Lars Noodén on 2011-05-31
> **FakeOutdoorsman said:**
> I'm not totally sure what you are asking. Most YouTube videos (recent ones at least, IIRC) are already in the MP4 container with H.264 video and AAC audio.


That's what I'm looking for: the plain video and plain audio without the Flash wrapper.  

I vaguely remember that there were alternate URLs for each Flash movie that could serve up ogg or something else.

When I try **youtube-dl** and request -fmt=H264 or -fmt=WebM, it fails with an error of 'requested format not available' so it seems not to be able to peel off the nasty flash scripting and deliver a cleaned video.

---

### Post by WannabeFantasma on 2011-05-31
easy youtube video downloader -> Did the job for me couple of months ago :)

---

### Post by someitalian123 on 2011-05-31
I just use the downloadhelper plugin for firefox, it works on almost every site, not just youtube. And you can chose which resolution video you want to download if the video has different resolutions.

---

### Post by Lars Noodén on 2011-05-31
> **someitalian123 said:**
> I just use the downloadhelper plugin for firefox, it works on almost every site, not just youtube. And you can chose which resolution video you want to download if the video has different resolutions.

I'm looking for different formats not so much different resolutions.  Specifically I'm looking for a way to clean the Flash wrapper off the video for viewing.

---

### Post by FakeOutdoorsman on 2011-05-31
> **Lars Noodén said:**
> I'm looking for different formats not so much different resolutions.
What formats do you want? I don't think you mentioned anything in particular.
> **Lars Noodén said:**
> Specifically I'm looking for a way to clean the Flash wrapper off the video for viewing.
Most videos on YouTube using the default YouTube "fmt" value should not be in the FLV container. My example above using youtube-dl would provide: *World_Champion_Beard_2011-axFlQ093FU8.mp4*. If your desired video is in the FLV container then you can use FFmpeg to copy or re-encode the streams into whatever supported container you want.

---

### Post by Lars Noodén on 2011-06-01
Ok.  One way to do this is to use both youtube-dl and ffmpeg.  

```

youtube-dl {url}
ffmpeg -i {file}.flv -ar 22050 {file}.mp4

```

I'm still looking for other or shorter options to convert to MPEG, QuickTime or Ogg Theora.

---

### Post by andrew.46 on 2011-06-01
> **Lars Noodén said:**
> I vaguely remember that there were alternate URLs for each Flash movie that could serve up ogg or something else.

Not quite what you are after but the *--all-formats* option might at least be of some interest to you?

---

### Post by Lars Noodén on 2011-06-01
> **andrew.46 said:**
> Not quite what you are after but the *--all-formats* option might at least be of some interest to you?

I'm after the video minus the Flash wrapper. So H.264 in an MPEG wrapper rather than a FLV wrapper would be acceptable.

Yes thanks. The **--all-formats** does help a bit with that, though it is slow.   With this application it was the **--format=** option that was the most help.

---

