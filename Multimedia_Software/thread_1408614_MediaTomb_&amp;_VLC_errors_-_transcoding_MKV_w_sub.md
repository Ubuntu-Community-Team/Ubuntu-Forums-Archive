---
title: "MediaTomb &amp; VLC errors - transcoding MKV w/ subs anyone?"
date: 2010-02-16
forum: Multimedia Software
---

### Post by zabby on 2010-02-16
Hi,

I'm trying to use VLC to transcode unsupported formats (in this case MKV) to my PS3 via Mediatomb.   I've tried 3 scripts I've found online, but they all fail somewhere despite giving each of them a really good go.  If anyone could give some advice on my current error I'd appreciate it.  Or if anyone has a solution for transcoding mkv w/ subs (I'm an Anime fan), to a PS3 via Mediatomb, I'd really like to hear it.

The one that works the best seems to be the one I found on the gentoo wiki ([http://en.gentoo-wiki.com/wiki/MediaTomb#VLC](http://en.gentoo-wiki.com/wiki/MediaTomb#VLC)).  

I get the following error message, I'm not sure what's up with the permission error since I'm running as root:

```
[0x8af60e8] main interface error: no interface module matched "globalhotkeys,none"
[0x8af60e8] main interface error: no suitable interface module
[0x8a59140] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8af6080] dummy interface: using the dummy interface module...
[0x8b0b5f0] access_output_file access out error: cannot open `/tmp/mt_transcode_IKKA8U' (Permission denied)
[0x8b08808] stream_out_standard stream out error: no suitable sout access module for `file/ps:///tmp/mt_transcode_IKKA8U'
[0x8b07b50] stream_out_transcode stream out error: cannot create chain
[0x8b053b0] main stream output error: stream chain failed for `transcode{vcodec=mp2v,vb=4096,fps=25,acodec=mpga,ab=192,samplerate=48000,channels=2,audio-sync,soverlay}:standard{access=file,mux=ps,dst=/tmp/mt_transcode_IKKA8U}'
[0x8b04198] main input error: cannot start stream output instance, aborting
[0x8b0acf8] dummy demux: command `quit'
```

I use the following transcoding profile and script.

```

<profile name="video2mpeg" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="/usr/local/bin/mediatomb-video2mpeg" arguments="%in %out"/>
        <buffer size="10485760" chunk-size="262144" fill-size="524288"/>
      </profile>

```

```

#!/bin/bash

VLC_PATH="/usr/bin/vlc"
INPUT="$1"
OUTPUT="$2"
VIDEO_CODEC="mp2v"
VIDEO_BITRATE="4096"
VIDEO_FRAMERATE="25"
AUDIO_CODEC="mpga"
AUDIO_BITRATE="192"
AUDIO_SAMPLERATE="48000"
AUDIO_CHANNELS="2"
FORMAT="ps"

exec "${VLC_PATH}" "${INPUT}" -I dummy --sout="#transcode{vcodec=${VIDEO_CODEC},\
vb=${VIDEO_BITRATE},fps=${VIDEO_FRAMERATE},acodec=${AUDIO_CODEC},ab=${AUDIO_BITRATE},\
samplerate=${AUDIO_SAMPLERATE},channels=${AUDIO_CHANNELS},audio-sync,soverlay}:\
standard{access=file,mux=${FORMAT},dst=${OUTPUT}}" vlc://quit

```

---

### Post by zabby on 2010-02-16
bump?

---

### Post by zabby on 2010-02-17
bump

---

### Post by zabby on 2010-02-17
The error seemed to be centered around the fact I was running Mediatomb as root in a terminal window for debugging purposes.  When I ran it as a service instead, the problem went away.  Not sure why you would ever get a perm error as root though.

Unfortunately I have an entirely new problem - this time with subtitles being delayed over 30 seconds from the audio and video.  I decided to ask the VLC forums instead, but in the spirit of "linking is what keeps the internet running" you can read that [here]("http://forum.videolan.org/viewtopic.php?f=4&t=72423") if you happened to stumble upon this thread with a similar problem as mine (or if you have an idea about how to fix it :P).

---

### Post by LazarusHC on 2010-04-10
Have you made any progress with this problem?  I'm having this same issue, and I've found almost nothing about it, let alone a solution.

---

### Post by zabby on 2010-05-12
Yeah as far as the audio delay problem goes I've got nothing, sorry.  I couldn't find anything else about it online.  Let me know if you figure it out, I'll be monitoring this thread.

---

### Post by encore2097 on 2010-06-14
I used mencoder, works fine and audio/video is in sync. Most of it is copied from somewhere else, but I changed it to autoscale subs relative to video width.

Here is the encoder profile that mkvs use in my *config.xml*
```

<profile name="mencoder-720" enabled="yes" type="external">
        <mimetype>video/mpeg</mimetype>
        <accept-url>yes</accept-url>
        <first-resource>yes</first-resource>
        <accept-ogg-theora>yes</accept-ogg-theora>
        <agent command="mencoder" arguments="%in -aid 0 -sid 0 -oac lavc -ovc lavc -of mpeg -lavcopts vcodec=mpeg2video:keyint=1:vbitrate=200000:vrc_maxrate=12000:vrc_buf_size=1835 -mpegopts muxrate=12000 -subfont-autoscale 2 -slang en -noautosub -ofps 24000/1001 -o %out"/>
        <buffer size="1000000" chunk-size="512000" fill-size="20480"/>
</profile>
```

---

### Post by zabby on 2010-06-14
Thanks, I'll give that a try as soon as I can!

---

