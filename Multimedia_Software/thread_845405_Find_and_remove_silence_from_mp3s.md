---
title: "Find and remove silence from mp3s"
date: 2008-06-30
forum: Multimedia Software
---

### Post by Kimos on 2008-06-30
So.. I have a fairly large mp3 library and am looking to scrub silence from some of the files. Specifically, I'm looking for an automated way of flagging tracks with big gaps of silence at the end or in the middle. Some CDs simulate a hidden track from a record or cassette by just recording a few minutes of silence and they really mess up my playlists! 

I'm also looking for a tool that will let me cut up the files with the silence in them without having decode and reencode the files. No transcoding.

I started by looking for Amarok scripts but didn't find anything worthwhile. I looked at the API for some mp3 libraries to write something myself, but decided there must be some kind of tool that exists. That cuts out tools like Audacity. 

I'm looking for suggestions of any type. I'm a programmer so if something doesn't exist, I'm open to tools and libs that will make this job easier.

Thanks!

---

### Post by eryksun on 2008-07-01
> **Kimos said:**
> So.. I have a fairly large mp3 library and am looking to scrub silence from some of the files. Specifically, I'm looking for an automated way of flagging tracks with big gaps of silence at the end or in the middle. Some CDs simulate a hidden track from a record or cassette by just recording a few minutes of silence and they really mess up my playlists! 
....
I'm looking for suggestions of any type. I'm a programmer so if something doesn't exist, I'm open to tools and libs that will make this job easier.

Check out [[COLOR="Blue"]this example[/COLOR]]("http://pymedia.org/tut/recode_audio.html") on using Pymedia to transcode an audio stream. You could insert some code to analyze the mean value of decoded frames and drop long sequences of silent frames or, as you mentioned, flag the mp3 in an ID3 tag, qualified with start/stop times of silent periods. Then you can just re-mux the metadata, without transcoding, and save a new MP3.

---

### Post by Kimos on 2008-07-02
Cheers. I'll check out PyMedia. Thanks.

---

