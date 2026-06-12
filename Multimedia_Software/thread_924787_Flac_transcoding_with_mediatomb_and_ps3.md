---
title: "Flac transcoding with mediatomb and ps3"
date: 2008-09-19
forum: Multimedia Software
---

### Post by raskolnik on 2008-09-19
Has anyone successfully got mediatomb transcoding flac files, so they're playable from a playstation 3? Getting this working has ended up being an epic project, and I've had no luck with anything. I've read that the ps3 needs transcoded pcm streams to be big endian, and that the package in the repositories "doesn't work." I've tried building the source files, getting the latest svn version (1881) and compiling that, using various arguments for ogg123, vlc, ffmpeg, flac, and using the scripts provided on gentoo's mediatomb wiki. The server's terminal output shows all of these to be working properly. I've tried an absurd number of tweaks to the /etc/mediatomb/config.xml file. I've been working on this off and on for months. Nothing I've read or tried has worked. The ps3 simply refuses to play these streams. It plays the files perfectly if they're transcoded manually first.

Can someone say definitively they have ever got this working? Is it possible?

---

### Post by raskolnik on 2008-09-25
I should mention transcoding in general works fine...audio/video, whatever. It's only flac files I'm having this issue with. Has anyone ever tried it?

---

### Post by amak79 on 2008-10-13
If you want to stream **any** transcoded audio to the PS3 then you will need the latest SVN code. There are a number of different methods for transcoding FLAC to RAW PCM but the following is how I do it.

**1.** Add the following to the **<mimetype-profile-mappings>** section.
```
      <transcode mimetype="audio/x-flac" using="audio-flac"/>
```

**2.** Add the following to the **<profiles>** section.
```

      <profile name="audio-flac" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <sample-frequency>44100</sample-frequency>
        <audio-channels>2</audio-channels>
        <agent command="flac" arguments="-dfs --force-raw-format --endian=big --sign=signed -o %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>

```

**3.** Install **flac** and restart MediaTomb.

---

### Post by raskolnik on 2008-10-18
Thanks for your response, amak79.

I installed the latest svn version and copied and pasted your transcode profile block, and it worked perfectly. I had been using flac with the same switches, and can't for the life of me figure out what's different now. Obviously I'd messed something up though.

Thanks, that was a huge source of frustration.

---

### Post by tom.clements on 2008-12-13
> **amak79 said:**
> If you want to stream **any** transcoded audio to the PS3 then you will need the latest SVN code. There are a number of different methods for transcoding FLAC to RAW PCM but the following is how I do it.

**1.** Add the following to the **<mimetype-profile-mappings>** section.
```
      <transcode mimetype="audio/x-flac" using="audio-flac"/>
```

**2.** Add the following to the **<profiles>** section.
```

      <profile name="audio-flac" enabled="yes" type="external">
        <mimetype>audio/L16</mimetype>
        <accept-url>no</accept-url>
        <first-resource>yes</first-resource>
        <hide-original-resource>yes</hide-original-resource>
        <accept-ogg-theora>no</accept-ogg-theora>
        <sample-frequency>44100</sample-frequency>
        <audio-channels>2</audio-channels>
        <agent command="flac" arguments="-dfs --force-raw-format --endian=big --sign=signed -o %out %in"/>
        <buffer size="1048576" chunk-size="131072" fill-size="262144"/>
      </profile>

```

**3.** Install **flac** and restart MediaTomb.

I'm having trouble with the above.. I'm currently experimenting by trying t get it to play to xbmc but ultimately I will be playing music on my ps3. XBMC can see my flac files (and will play them without transcoding turned on as you would expect) but it will not play them.

I have tried transcoding to a fifo using:

mkfifo /tmp/test
 
and then trying:

flac -df --force-raw-format --endian=big --sign=signed -o /tmp/mytest /path/fileA.flac

and flac returns:

ERROR while decoding metadata
                         state = FLAC__STREAM_DECODER_END_OF_STREAM

if I try:

flac -df --force-raw-format --endian=big --sign=signed -o /tmp/mytest /path/fileB.flac

It decodes ok so clearly there is a problem with some of my flac files although i don't seem to be able to stream it to fifo. If I then go through XBMC to pick up fileB through Mediatomb.. nothing happens when I ask it to play it fails.

I have also tried:

ogg123 -d wav /tmp/mytest /path/file.flac and this returns:

write buffer error

! Can anyone suggest some further testing strategies?!

Many thanks,

Tom.

---

