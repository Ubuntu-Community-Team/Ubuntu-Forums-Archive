---
title: "Cannot play MP4 Firefox media.fragmented-mp4 options not defined"
date: 2017-05-23
forum: Multimedia Software
---

### Post by 7-webmaster on 2017-05-23
I attempted to find other discussions of this issue but the UI on this forum rejects media.fragmented-mp4 as a search term.

I am trying to play mp4 videos, something that I used to be able to do.  I have run  sudo apt install ubuntu-restricted-extras to install the MP4 codecs, but Firefox 53 still will not view the videos although previous releases did.  The instructions for activating MP4 support include setting various Firefox media.fragmented-mp4 options to true, but those options are not available under Firefox 53 on Ubuntu 16.04 LTS.

How do I view MP4 videos through the HTML5 <video> tag on Ubuntu 16.04 LTS?

---

### Post by TheFu on 2017-05-23
mp4 is a media container.  It is not a codec.  Lots of different video and audio types can be put into an mp4 container.
That probably isn't helpful.

There are a few different ways to see the video and audio codecs required inside any container.  **vlc** or **mplayer** are how I'd do it. There are probably others.

Until we know that data, it isn't worth trying to figure out firefox playback.

IMHO.

---

### Post by ajgreeny on 2017-05-24
If you are not afraid of the command line I also suggest installing **mediainfo**.

Run the simple command ```
mediainfo /path/to/video.mp4
``` and you will see a lot of information about the file, including details of the audio and video types enclosed in the mp4.

---

### Post by vasa1 on 2017-05-24
> **7-webmaster said:**
> I attempted to find other discussions of this issue but the UI on this forum rejects media.fragmented-mp4 as a search term.

I am trying to play mp4 videos, something that I used to be able to do.  I have run  sudo apt install ubuntu-restricted-extras to install the MP4 codecs, but Firefox 53 still will not view the videos although previous releases did.  The instructions for activating MP4 support include setting various Firefox media.fragmented-mp4 options to true, but those options are not available under Firefox 53 on Ubuntu 16.04 LTS.

How do I view MP4 videos through the HTML5 <video> tag on Ubuntu 16.04 LTS?
Try```
site:ubuntuforums.org "media.fragmented-mp4"
```in your address bar (urlbar) if you're using Google Search. 

I found
[https://ubuntuforums.org/showthread.php?t=2295407](https://ubuntuforums.org/showthread.php?t=2295407)
[https://ubuntuforums.org/showthread.php?t=2271844](https://ubuntuforums.org/showthread.php?t=2271844)
[https://ubuntuforums.org/showthread.php?t=2297381](https://ubuntuforums.org/showthread.php?t=2297381)
[https://ubuntuforums.org/showthread.php?t=2300361](https://ubuntuforums.org/showthread.php?t=2300361)
[https://ubuntuforums.org/showthread.php?t=2301898](https://ubuntuforums.org/showthread.php?t=2301898)
etc

I don't have any issues playing _local_ mp4 via Firefox.

---

### Post by 7-webmaster on 2017-05-24
> **TheFu said:**
> mp4 is a media container.  It is not a codec.  Lots of different video and audio types can be put into an mp4 container.
That probably isn't helpful.

There are a few different ways to see the video and audio codecs required inside any container.  **vlc** or **mplayer** are how I'd do it. There are probably others.

Until we know that data, it isn't worth trying to figure out firefox playback.

IMHO.
The point is for OTHER people to be able to see the videos by visiting my web-site.

Firefox used to play these videos but now it insists that the format is unsupported.  What do I have to do to convince Firefox to play these videos.

---

### Post by 7-webmaster on 2017-05-24
> **vasa1 said:**
> Try```
site:ubuntuforums.org "media.fragmented-mp4"
```in your address bar (urlbar) if you're using Google Search. 

I found
[https://ubuntuforums.org/showthread.php?t=2295407](https://ubuntuforums.org/showthread.php?t=2295407)
[https://ubuntuforums.org/showthread.php?t=2271844](https://ubuntuforums.org/showthread.php?t=2271844)
[https://ubuntuforums.org/showthread.php?t=2297381](https://ubuntuforums.org/showthread.php?t=2297381)
[https://ubuntuforums.org/showthread.php?t=2300361](https://ubuntuforums.org/showthread.php?t=2300361)
[https://ubuntuforums.org/showthread.php?t=2301898](https://ubuntuforums.org/showthread.php?t=2301898)
etc

I don't have any issues playing _local_ mp4 via Firefox.

I searched all of those entries (most of which are pointers to this thread).  All of those discussions confirm that the media.fragmented-mp4 entries are present in the config options for those posters and once they set them to true their problems went away.  But there are NO media.fragmented-mp4 entries in the config on Firefox  on my Ubuntu system.

I am not concerned with playing these mp4 files locally.  They display fine in VLC and other players.  However I want my customers to be able to play these videos and if I cannot play them then undoubtedly there are some of my customers who cannot play them either.

---

### Post by TheFu on 2017-05-24
> **7-webmaster said:**
> The point is for OTHER people to be able to see the videos by visiting my web-site.

Firefox used to play these videos but now it insists that the format is unsupported.  What do I have to do to convince Firefox to play these videos.

And you haven't answered our questions about the video and audio codecs. Lacking that knowledge, I can only say, "Don't use proprietary/patent encumbered video or audio codecs."

So - h.264 for the video and (ogg or vorbis) for the audio.  I'd put them into an mkv container, not mp4.  You could probably use VP8 for the video codec too. I haven't tried it.  The webm standard would be a good choice. It is like mkv, but highly restrictive on the codecs it supports.

---

### Post by mc4man on 2017-05-24
Maybe offer an example url that doesn't play. As far as media.fragmented... there are currently now 2 options as in screen. Whether it matters anymore if they're set to 'true' not sure, I don't see any difference here.

---

### Post by 7-webmaster on 2017-05-24
> **mc4man said:**
> Maybe offer an example url that doesn't play. As far as media.fragmented... there are currently now 2 options as in screen. Whether it matters anymore if they're set to 'true' not sure, I don't see any difference here.

I give up.  Clearly nobody is interested in there being current accurate documentation provided to poor suffering users.  I deployed the videos as mp4 because that was the output format of the screen recorder tool that I used to create the videos.  In my opinion it is unfair to demand that non-specialist users on the web keep track of patent disputes or other political issues.  So I have recoded all of my videos into webm format which is supported by Firefox and changed my page at [https://www.jamescobban.net/videoTutorials.php](https://www.jamescobban.net/videoTutorials.php) to contain:
<source src="Videos/filename.webm" type="video/webm">
<source src="Videos/filename.mp4" type="video/mp4">

---

### Post by 7-webmaster on 2017-05-24
> **TheFu said:**
> mp4 is a media container.  It is not a codec.  Lots of different video and audio types can be put into an mp4 container.
That probably isn't helpful.

There are a few different ways to see the video and audio codecs required inside any container.  **vlc** or **mplayer** are how I'd do it. There are probably others.

Until we know that data, it isn't worth trying to figure out firefox playback.

IMHO.

How is a **non-specialist** user supposed to figure all of this out?  All I want to do is play the videos!  I do not know **anything** about codecs.  I do not understand, and do not **want** to understand, the **politics** that appears to be more important to everyone than serving the interests of customers.  When I look at these files I see:

Container: quicktime
Video codec H.264
audio codec mpeg-1 layer 3

---

### Post by wildmanne39 on 2017-05-24
We can not be expected to create and maintain documentation for every app out their, we are a small volunteer community and we do the best we can, but you see anyone can contribute, please feel free to do your part.
Thanks

---

### Post by TheFu on 2017-05-25
If you are a webmaster, then you should be prepared for issues like this. Asking someone else to help you do something illegal where they live is ... rude.

I provided a solution that avoids you having to know much at all. It seems to be working.  I is legal everywhere in the world and works cross-platform. 

Until last week, mp3 had a proprietary, patented, encoding scheme which was illegal to use without a license where I live.  Now that the patents have expired, software can be changed, but mp3 is effectively dead for web streaming uses, IMHO. There are better, freer, more efficient, well-supported, audio codecs.

BTW, I visited the webpage and none of the links worked for me. I am YOUR customer, but only a volunteer here. Nobody here works for Canonical. If you like, Canonical offers paid support: [https://www.ubuntu.com/support](https://www.ubuntu.com/support) who would be able to help navigate the different legal issues world-wide.

---

### Post by vasa1 on 2017-05-25
> **TheFu said:**
> ...
BTW, I visited the webpage and none of the links worked for me.
At least one link works for me. It takes quite some time to get started. Maybe that's why you think the links don't work? But it's a bit unusual: I've not encountered a site like this before.

Google Chrome dev (v60), no blockers, everything allowed.

---

### Post by Yellow Pasque on 2017-05-28
>  that was the output format of the screen recorder tool that I used 

Maybe you could tell us what screen recorder tool you're using?

> Container: quicktime

If your screen recorder is really outputting to a quicktime container, you would probably have better luck using an actual mp4 container (or a matroska/mkv container).

> How is a non-specialist user supposed to figure all of this out? All I want to do is play the videos! I do not know anything about codecs. I do not understand, and do not want to understand, the politics that appears to be more important to everyone than serving the interests of customers

No, you don't just want to play the videos. You are the one encoding them and choosing the container/codecs, so saying you don't want to know anything about it when an issue arises is silly.

---

### Post by SeijiSensei on 2017-05-28
Quicktime is a bad choice for something that needs to be accessible on a variety of platforms and browsers.  I recently re-encoded three QT videos and asked people specifically to report whether they worked properly on their devices.  I ended up using the WMV3 video codec and AAC audio codec and put the result in an mp4 container.  I used the remarkable ffmpeg for this task:

```
ffmpeg -i input.mov -vcodec wmv3 -acodec aac -2 -strict output.mp4
```

If you are responsible for posting video that is widely accessible, then you'll need to learn a bit about video and audio standards.

---

