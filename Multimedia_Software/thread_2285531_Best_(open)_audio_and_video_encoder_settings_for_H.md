---
title: "Best (open) audio and video encoder settings for HandBrake?"
date: 2015-07-06
forum: Multimedia Software
---

### Post by Rytron on 2015-07-06
Hi all.

I'd like to turn formats like flv and mp4 into open formats such as mkv and webm. Using HandBrake, I'm going through the settings and would like to choose the best and most open settings available. Of the settings for audio and video in the 2 attached images -- which should I choose?

Thanks.

---

### Post by TheFu on 2015-07-07
mkv is just a container.
mp4 is just a container.
flv is just a container.

You can put many different types of encoded video and audio into each and taking existing video/audio from one container to another is fairly easy. Just use a "copy" command.  Don't think handbrake supports that, but **avconv** and **ffmpeg** both do.  It is the difference between a 30 sec copy and a 45 min transcode. Much less processing with the copy since the video, audio, subtitles are just copied from 1 container to another.  mkv has some tools that will manipulate MKV containers - like mkvmerge and mmg (the GUI version).

I don't know anything about webm, sorry.

To copy the video and audio in a mp4 container into an mkv container, just use mkvmerge.

$ mkvmerge -o output.mkv input.mp4

Simple, fast.  The input can be almost anything. The mkv container is pretty amazing. That command will be relatively fast because it just copies and compresses the audio/video into the mkv container; no transcoding.

Also - "best" settings change based on the content.  Romance video would be encoded differently than high-action video.  Darker video different from a beach day video. It also depends on the source.  Encoding a low-resolution input file with very high quality settings designed for a pristine 1080p video is a complete waste. If you must transcode, the defaults for handbrake are reasonable. Just touch the CQ setting. Anything less than 19 is overkill (IMHO) and anything over 22 shows so many artifacts that I find the video unwatchable.   All of this is about finding the right trade-off between file size, file resolution and watchability. Each of those results is fluid based on the input.

---

### Post by TheFu on 2015-07-07
dup.

---

### Post by Rytron on 2015-07-07
Hi TheFu.

If I use the x264 (not sure if it's open format) as the video encoder and Vorbis for the audio encoder and use the MKV container -- is the resulting video in an open format? Can I view it without having to install restricted exras?

---

### Post by TheFu on 2015-07-07
x264 licensing: [http://x264licensing.com/](http://x264licensing.com/)
h.264 licensing: [http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx](http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx)

Not as open as you thought, I suspect.

To be open, you'll need Ogg Vorbis - [http://www.vorbis.com/faq/#flic](http://www.vorbis.com/faq/#flic)
However, I don't think most end-users recognize that file format or container. Support for the codecs is improving, but many commercial products still do not support either.

So ... guess what you need depends completely on what you (and your lawyer) consider "open."

You can definitely shove an OGV video file into an mkv container. Whether any specific device/browser/player will play it is a completely different question.

---

### Post by Yellow Pasque on 2015-07-08
You must be using an older version of Handbrake (< 0.10) because you don't have the option for VP8 video codec, which is probably what you want if you're looking to create a Matroska or WebM file.
If you set Handbrake to use a Matroska container, VP8 for video and Vorbis for audio, you can quickly/easily convert to WebM using avconv (or ffmpeg) without re-encoding:
```
avconv -i inputfile.mkv -c:v copy -c:a copy -flags global_header outputfile.webm
```

> To be open, you'll need Ogg Vorbis - However, I don't think most end-users recognize that file format or container.
Vorbis support is part of html5, so most browsers can play it. Well, except for Internet Explorer, which needs a little addon.

---

### Post by dino99 on 2015-07-08
One comment that looks important:
[COLOR="#0000CD"]HandBrake does not support external encoders. It is not possible to add an encoder to HandBrake at runtime. All the encoder libraries are built in and not dynamically linked/loaded at runtime.[/COLOR]
and some formats compared:
[https://trac.handbrake.fr/wiki/Encoders](https://trac.handbrake.fr/wiki/Encoders)

a convertion example   [http://www.howtogeek.com/199618/how-to-use-handbrake-to-convert-any-video-file-to-any-format/](http://www.howtogeek.com/199618/how-to-use-handbrake-to-convert-any-video-file-to-any-format/)

---

### Post by SeijiSensei on 2015-07-08
Cisco has purchased the rights to distribute a free H.264 decoder for use in web browsers.  It's now distributed as a plug-in by default with Mozilla Firefox.

The last fully-open, widely-used video codec I know of was XviD, a open-source clone of DivX.  Before H.264+Matroska became the default format for video files on the Internet, XviD in the AVI container was pretty much the standard.  It has somewhat lower quality than H.264, but probably the differences wouldn't be noticeable to most viewers.

---

### Post by TheFu on 2015-07-08
> **SeijiSensei said:**
> ... free H.264 decoder ...

And encoding? License?

---

### Post by Yellow Pasque on 2015-07-08
Xvid may be open-sourced and licensed under GPL, but it still uses MPEG patents which it hasn't received permission for: [https://en.wikipedia.org/wiki/Xvid#Patent_issues](https://en.wikipedia.org/wiki/Xvid#Patent_issues)
Google already battled with the MPEG patent group over VP8 and came to an agreement with them.

> If I use the x264 (not sure if it's open format) as the video encoder and Vorbis for the audio encoder and use the MKV container -- is the resulting video in an open format?
Does x264 have permission to use MPEG patents? ;)

> Openh264 encoding? License?
It can supposedly encode, but I've never tried it or read about anyone using the encoder. Cisco has reached an agreement with MPEG to use its patents.

> HandBrake does not support external encoders. All the encoder libraries are built in and not dynamically linked/loaded at runtime.
As long as you're using Handbrake 0.10.0 or later, it should have VP8 support built-in through libav. If you're not using 0.10.0 or later, finding a good PPA is highly recommended.

---

### Post by SeijiSensei on 2015-07-08
> **Temüjin said:**
> Xvid may be open-sourced and licensed under GPL, but it still uses MPEG patents which it hasn't received permission for: [https://en.wikipedia.org/wiki/Xvid#Patent_issues](https://en.wikipedia.org/wiki/Xvid#Patent_issues)
Google already battled with the MPEG patent group over VP8 and came to an agreement with them.

So is there no unencumbered codec for video with any support in mainstream player software?  Or does VP8 qualify because of this battle?

As for Cisco: [http://www.openh264.org/faq.html](http://www.openh264.org/faq.html)

---

### Post by Rytron on 2015-07-08
> **Temüjin said:**
> You must be using an older version of Handbrake (< 0.10) because you don't have the option for VP8 video codec, which is probably what you want if you're looking to create a Matroska or WebM file. ... 

Hi Temüjin.

Yes, I just add a PPA and went from HB rev5474 (x86_64) to HB 0.10.2 (x86_64). I don't get the version system but it now has VP8.

---

### Post by Rytron on 2015-07-08
> **TheFu said:**
> x264 licensing: [http://x264licensing.com/](http://x264licensing.com/)
h.264 licensing: [http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx](http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx)

Not as open as you thought, I suspect.

To be open, you'll need Ogg Vorbis - [http://www.vorbis.com/faq/#flic](http://www.vorbis.com/faq/#flic)
However, I don't think most end-users recognize that file format or container. Support for the codecs is improving, but many commercial products still do not support either.

So ... guess what you need depends completely on what you (and your lawyer) consider "open."

You can definitely shove an OGV video file into an mkv container. Whether any specific device/browser/player will play it is a completely different question.

RMS advocates ogg & webm.

No lawyer involved ;) -- I just like to use open formats and software as much as possible over proprietary ones. :KS

---

### Post by Rytron on 2015-07-08
I think I will go with HandBrake Vorbis Audio and V8 Video.

I may opt for 128kbps audio and is CQ 19 ok for V8?

---

### Post by Rytron on 2015-07-08
> **Temüjin said:**
> 

...

If you set Handbrake to use a Matroska container, VP8 for video and Vorbis for audio, you can quickly/easily convert to WebM using avconv (or ffmpeg) without re-encoding:
```
avconv -i inputfile.mkv -c:v copy -c:a copy -flags global_header outputfile.webm
```

...



Would it be ok to keep videos with Vorbis and V8 encoding and a mkv container? Is that video file fully compatible?

---

### Post by mc4man on 2015-07-08
> **Rytron said:**
> RMS advocates ogg & webm.

What does he/it advocate for a player? Seems to me your choices are very limited there.
(The terming in some of these recent threads using "open" is a bit confusing. I think you are really talking about 'free' not open or open source. (free being 'not encumbered by any copyrights, patents, trademarks or other restrictions'

---

### Post by Yellow Pasque on 2015-07-09
> **Rytron said:**
> Would it be ok to keep videos with Vorbis and V8 encoding and a mkv container? Is that video file fully compatible?

Fully compatible with what? What do you plan to do with the videos? If you want it compatible with HTML5 video, it would be best to use webm. I know Youtube will automatically stick your video in a WebM container when you upload it.

> So is there no unencumbered codec for video with any support in mainstream player software? Or does VP8 qualify because of this battle?
What would you consider mainstream player software? Windows Media Player? VLC? Web browsers?
I would say that VP8 qualifies, but Windows users need to install a codec pack to have it supported in IE and Media Player.
I think this is a good summary of video formats when it comes to browsers: [https://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats](https://en.wikipedia.org/wiki/HTML5_video#Supported_video_formats)

---

### Post by mc4man on 2015-07-09
I would consider any open source codec 'free' to an individual user. None of the licensing, patents, royalties ect. apply.
If you have previous content for example in h.264 & want to re-encode to webm because it's 'open & free' well you have to decode it first. Whole thing seems gratuitous to me..

---

### Post by TheFu on 2015-07-09
Yep - this is one of those "simple questions" that isn't simple because different groups/organizations have different agendas.

Years ago, I was looking for the "most compatible, extensible, usable, video format" to backup my home and TV recordings.  For me, that resulted in xvid/mp3/avi.  When HiDef video became more and more standard, I switched to h.264/ac3/mkv, but that audio format doesn't playback on all my devices, so I add aac audio tracks and leave the AC3 inside as well. Thanks to the MKV container, some of my files have 10 different audio tracks and 12+ captions/subtitles inside a single file to go with the video.  For awhile there, MKV wasn't supported at all on Windows and earlier android devices would accept only h.264/aac/mp4 files - not h.264/aac/mkv files (exactly the same codecs, just a different container).  

I was NOT looking to publish anything, so I didn't look too closely at the creation license requirements.

Plus many streaming devices these days do not support mpeg2 video anymore at all - that's the old DVD video codec and HW-based decoders have been around for 5+ yrs for that codec. ATSC TV is broadcast using mpeg2 video - so it is definitely a standard.

Simple question?

---

### Post by mc4man on 2015-07-09
> **TheFu said:**
>  so I didn't look too closely at the creation license requirements.

Well take a look here at h.264 > 'click here summary' or any of the media codec programs - an individual for their  own use is not 'affected' (you couldn't pay them even if you tried..
(- and many of the commercial uses are royalty free up to 100,000 devices/uses/ whatever
[http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx](http://www.mpegla.com/main/programs/AVC/Pages/Agreement.aspx)

---

### Post by Rytron on 2015-07-09
> **mc4man said:**
> What does he/it advocate for a player? Seems to me your choices are very limited there.
(The terming in some of these recent threads using "open" is a bit confusing. I think you are really talking about 'free' not open or open source. (free being 'not encumbered by any copyrights, patents, trademarks or other restrictions'

"he/it"?

What?

---

### Post by Rytron on 2015-07-09
> **Temüjin said:**
> Fully compatible with what? What do you plan to do with the videos? If you want it compatible with HTML5 video, it would be best to use webm. I know Youtube will automatically stick your video in a WebM container when you upload it.



I mean, would it be playable without having to install non-free codecs like restricted-extras?

---

### Post by TheFu on 2015-07-09
> **Rytron said:**
> "he/it"?

What?

Not everyone knows who/what RMS is. [https://en.wikipedia.org/wiki/Richard_Stallman](https://en.wikipedia.org/wiki/Richard_Stallman)
Hence the he/it question?

---

### Post by Rytron on 2015-07-09
> **TheFu said:**
> Not everyone knows who/what RMS is. [https://en.wikipedia.org/wiki/Richard_Stallman](https://en.wikipedia.org/wiki/Richard_Stallman)
Hence the he/it question?

I see. I erroneously thought you were being disrespectful to Mr. Stallman. :KS

I expect most people on these forums know who RMS is. At least I hope so. :KS

---

### Post by Yellow Pasque on 2015-07-09
> **Rytron said:**
> I mean, would it be playable without having to install non-free codecs like restricted-extras?

Ubuntu and Xubuntu both come come with gstreamer1.0-plugins-base and -good packages installed by default, and those will be all you need to play a VP8/Vorbis mkv file

---

### Post by mc4man on 2015-07-09
I'm all for people doing whatever they want so if you want to use just the so called free codecs & a player that only can play 'free' codecs that's great.
But in this case then I'd say you are either all in or your are not. If you are all in then delete all non self created media content you have that isn't done with these 'acceptable' codecs, (if any?) & just use content you create or has originally  been created using these 'so called free' codecs.

(- again from my perspective as an end user all of these codecs mentioned or commonly available  are 'free' to me, most are also open source

---

