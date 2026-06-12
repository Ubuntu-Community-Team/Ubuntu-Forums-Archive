---
title: "What other than mpeg is recommended for HD TV?"
date: 2011-01-28
forum: Mythbuntu
---

### Post by nhtrader on 2011-01-28
I'm interested to learn what other HD recording formats are available.

The mpeg format works fine, but the file sizes are too large for streaming out over the internet. 

I am a comcast cable customer and comcast limits my outbound bandwidth to 700Kbs. So I'm trying to find another recording format that will work with this limitation.

I look at this way. A one hour HD program uses about 6 Gb. So this then implies that I must be able to stream about 100Mb per min. Or 1.7 Mb per sec. By my calculation the same program needs to be reduced by 60% from the original size for me to stream it out over the internet. So I'm looking for a file size near 2.4Gb.

Is their such a format? If so how do I change MythTV's recording format?

---

### Post by nickrout on 2011-01-28
> **nhtrader said:**
> I'm interested to learn what other HD recording formats are available.

The mpeg format works fine, but the file sizes are too large for streaming out over the internet. 

I am a comcast cable customer and comcast limits my outbound bandwidth to 700Kbs. So I'm trying to find another recording format that will work with this limitation.

I look at this way. A one hour HD program uses about 6 Gb. So this then implies that I must be able to stream about 100Mb per min. Or 1.7 Mb per sec. By my calculation the same program needs to be reduced by 60% from the original size for me to stream it out over the internet. So I'm looking for a file size near 2.4Gb.

Is their such a format? If so how do I change MythTV's recording format?

(Assuming digital TV transmission) You don't change your recording format. Myth dumps the transmitted stream to hard drive. You get what you are sent.

If you want to change that you need to transcode. That's a whole new story, but there is a recent thread with the title "help with transcoding" which has some good scripts for transcoding to h.264. The author claims (IIRC) a 2.5:1 saving in disk space.

---

### Post by tgm4883 on 2011-01-28
> **nhtrader said:**
> I'm interested to learn what other HD recording formats are available.

The mpeg format works fine, but the file sizes are too large for streaming out over the internet. 

I am a comcast cable customer and comcast limits my outbound bandwidth to 700Kbs. So I'm trying to find another recording format that will work with this limitation.

I look at this way. A one hour HD program uses about 6 Gb. So this then implies that I must be able to stream about 100Mb per min. Or 1.7 Mb per sec. By my calculation the same program needs to be reduced by 60% from the original size for me to stream it out over the internet. So I'm looking for a file size near 2.4Gb.

Is their such a format? If so how do I change MythTV's recording format?

I haven't seen a home connection that provides enough upstream bandwidth to watch shows while I am away. I tend to think it's a lost cause.

Just copy the shows to your laptop before you leave, it's a much better solution. 

There is also mythexport to assist in that sort of thing.

---

### Post by nhtrader on 2011-01-28
Well, has anyone tried viewing an SD program? These recordings are one-tenth the size of HD programs. These certainly should work over the internet.

---

### Post by BicyclerBoy on 2011-01-29
There is nothing stopping you from transcoding to a lower resolution or lower quality (higher compression) in the same mpeg2-ts container.

The common encoding of HD video is H264 (mpeg4/10), this is very efficient compression.
You can just increase the compression & reduce the PQ  to get the required bitrates..

You can not change the recording format from a dvb tuner card (mpeg2-ts).
You can reduce the capture res on capture cards (STB) (will be mpeg2-ts for HD)

---

### Post by tgm4883 on 2011-01-29
> **BicyclerBoy said:**
> There is nothing stopping you from transcoding to a lower resolution or lower quality (higher compression) in the same mpeg2-ts container.

The common encoding of HD video is H264 (mpeg4/10), this is very efficient compression.
You can just increase the compression & reduce the PQ  to get the required bitrates..

You can not change the recording format from a dvb tuner card (mpeg2-ts).
You can reduce the capture res on capture cards (STB) (will be mpeg2-ts for HD)

Correction, you cannot change the capture res for digital cards. You can change it for analog tuners.

---

### Post by BicyclerBoy on 2011-01-29
Assuming you mean 'digital card' == dvb tuner card..

That's what I said.
Analogue tuners are just capture cards with some glue.

I do not know if digital capture cards (HDMI input etc) allow different capture resolutions.

Any resolution changes were w.r.t transcoding.

---

### Post by nhtrader on 2011-01-29
got it.

Now, do you know how automate the conversion of my mpeg HD TV recordings to H264?

---

### Post by BicyclerBoy on 2011-01-29
They probably already are..H264. but makes little difference.

Most of the world (outside US) is using H264 inside mpeg2-ts.

You should study the x264 presets with ffmpeg.
You would need to build it from source to get x264 encoding.
The "fakeoutdoorsman"'s build guide is invaluable.

Then set up a userjob in MythTV..
Expect real-time encoding on core2duo.

---

### Post by nickrout on 2011-01-30
> **nhtrader said:**
> got it.

Now, do you know how automate the conversion of my mpeg HD TV recordings to H264?

[http://ubuntuforums.org/showthread.php?t=1673463](http://ubuntuforums.org/showthread.php?t=1673463)

---

### Post by ian dobson on 2011-01-30
Hi,

Also have a look at handbrake, I've used it afew times to transcode mpeg2 to h264, and it works very well.

Regards
Ian Dobson

---

