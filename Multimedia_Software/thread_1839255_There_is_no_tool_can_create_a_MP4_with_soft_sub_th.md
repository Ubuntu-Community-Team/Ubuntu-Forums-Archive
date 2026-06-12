---
title: "There is no tool can create a MP4 with soft sub that iPhone can play?"
date: 2011-09-05
forum: Multimedia Software
---

### Post by beterhans on 2011-09-05
I'm trying to convert all my MKVs to MP4 and make them able to play on most devices. like Xbox or iOS.... 

I Googled and try to find a Tool that can change MKV to MP4 but not to reencode but just copy h264 and aac to MP4. and trying to add subtitle tracks.

FFMPEG is a powerful tool which can handle the audio and video but not subtitles.
MP4Box could input subtitles but only VLC could Recognize it iPhone / iPod won't. 

another post said you can use a Hex edit to replace the "text" to "sbtl" in a Mp4 that make iOS devices recognize the MP4 have Subtitle track but it's unknow and can't be displayed... :(

any one have idea?

it looks like the only tool can do the right subtitle on Linux is handbreak but it re-encode videos, can't use copy video or pass through...

---

### Post by KiMonte on 2011-09-07
Try Arista Transcoder

---

### Post by aeiah on 2011-09-07
have a look at MKVToolnix. it'll let you demux all the bits you need from the mkv container, and then you'll just need a way of packaging it into an mp4

---

### Post by SeijiSensei on 2011-09-08
> **beterhans said:**
> I'm trying to convert all my MKVs to MP4 and make them able to play on most devices. like Xbox or iOS.... 

I Googled and try to find a Tool that can change MKV to MP4 but not to reencode but just copy h264 and aac to MP4. and trying to add subtitle tracks.

You can't simply copy the video stream and add the subtitles.  You'll need to re-encode and convert the soft subs to hard ones.  Try using [Handbrake]("https://launchpad.net/~stebbins/+archive/handbrake-releases"). Even though it's primarily designed to rip DVDs and BDs, it will accept video files as input as well.  There are pre-defined configurations to create output for a variety of iThings.

(MP4 has limited softsub support; I don't know whether Handbrake converts subs to this format or "burns them in" to the output file.)

I've only used the GUI version, but there's also a command-line version that you could probably use in a script to convert a batch of files.

---

### Post by handy on 2011-09-08
HandBrake does create soft subs with .mp4 now (thankfully).

---

