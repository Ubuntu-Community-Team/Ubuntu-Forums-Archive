---
title: "mediatomb ffmpeg transcoding flac to mp3 player says non-supported format"
date: 2011-08-07
forum: Multimedia Software
---

### Post by sev1985 on 2011-08-07
Hi

I'm trying to get mediatomb to work with my Samsung blu-ray player, (bd-5300) 
I have mediatomb setup to transcode my flac files to mp3s with ffmpeg. 
Whenever I try to play one of them my player says that the file format isn't supported. 

Here's a copy of the transcoding profile

<profile name="flac2mp3" enabled="yes" type="external">
        <mimetype>audio/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <agent command="ffmpeg" arguments="-y -i %in -acodec libmp3lame -aq 0 %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>

Any help would be appreciated.

---

### Post by FakeOutdoorsman on 2011-08-07
Perhaps you need to install **libavcodec-extra-52** to enable libmp3lame* support in FFmpeg.*

Also, *-aq 0* might be considered a little overkill. See [recommended LAME settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Detailed_explanation_.28long_answer.29) for a nice chart.

---

### Post by sev1985 on 2011-08-07
Thanks for replying. I'll try lowering the bitrate and/or quality setting. 
I've compiled mediatomb from source and enabled ffmpeg support at compile time.

---

### Post by sev1985 on 2011-08-07
I tried lowering the bitrate. Unfortunately that didn't help matters. Any more ideas?

---

### Post by FakeOutdoorsman on 2011-08-07
Sorry, but I misread your first post thinking that FFmpeg or mediatomb (or whatever is using FFmpeg) was having trouble creating the mp3 files. As for your blu-ray player, I have no idea, but I do have access to a similar model and may try a few files myself in a few days. I'll post here if I figure anything out.

---

### Post by sev1985 on 2011-08-08
Thanks.

---

