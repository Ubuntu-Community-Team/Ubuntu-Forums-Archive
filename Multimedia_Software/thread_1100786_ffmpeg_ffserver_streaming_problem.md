---
title: "ffmpeg ffserver streaming problem"
date: 2009-03-19
forum: Multimedia Software
---

### Post by d2009 on 2009-03-19
Hi,

I am trying to stream video files using ffserver. I am able to stream audio and video for mpeg, mp3, flv, swf, rm formats properly..

But i am badly stuck with avi, 3gp, mov, mp4.. when i try to play it in the browser using [http://localhost:8096/test.avi](http://localhost:8096/test.avi), it just keeps waiting endlessly or saves a file with 0 bytes.

My FFmpeg version SVN-r17942..

I am using these in my ffserver.conf file..

<Stream test.mov>
Feed feed1.ffm
Format mov
VideoSize 720x480
VideoFrameRate 30
AudioCodec ac3
AudioChannels 1
AudioSampleRate 48000
</Stream>

<Stream test.avi>
Feed feed1.ffm
Format avi
VideoFrameRate 24
Audiocodec mp2
AudioSampleRate 44100
</Stream>

<Stream test.3gp>
Feed feed1.ffm
Format 3gp
VideoSize 176x144
Audiocodec libfaac
AudioSampleRate 44100
</Stream>

Could anyone pleaseee help me with these formats..

Thanks in advance

---

