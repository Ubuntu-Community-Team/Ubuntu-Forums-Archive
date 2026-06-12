---
title: "audio/video downloading from web"
date: 2012-01-03
forum: Multimedia Software
---

### Post by xtgyal on 2012-01-03
Is there an open-source or nonspammy freeware app or plug-in available to download audio and/or video content from the web (e.g. YouTube)?  I used to use RealPlayer on Windows, which showed as a pop-up to download whenever videos played in my web browser (regardless of site or format).  I installed the Firefox plug-in Easy YouTube Video Downloader, but that has advertisements and runs very slowly and unreliably, and only works on YouTube.  I couldn't find anything for Chromium or Chrome.  I'd like to find something that can download universally from the web (at very least the major formats like Flash Videos from YouTube).  I can convert to audio files separately on my desktop, but being able to download just the audio component directly would be convenient as well.

---

### Post by SteveDee on 2012-01-03
> **xtgyal said:**
> Is there an open-source or nonspammy freeware app or plug-in available to download audio and/or video content from the web (e.g. YouTube)?....

Take a look at MiniTube.

You can type in the name of a band or singer and it will dish up a continuous stream of videos. The download button allows you to grab anything you like the look of.

Make sure you download the latest version (not necessarily the one from the Ubuntu repo). I think v1.6 is OK.

---

### Post by lisati on 2012-01-03
Legal downloads are fine, but please be aware that we don't support violations of another site's TOS here. See the sticky in the resolution center for more information: [http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)

---

### Post by andrew.46 on 2012-01-03
As lisati has mentioned you should not violate youtube's Terms of Service, or similar restrictions by other websites. Bearing that in mind there are 2 excellent commmandline applications that you might like experimenting with, [get-flash-videos]("http://code.google.com/p/get-flash-videos/") and [youtube-dl]("http://rg3.github.com/youtube-dl/documentation.html"). Despite its name youtube-dl can be used as:
> 
A generic downloader that works in some sites.

and I would advise that you limit your use to this rather than breaking Forum rules and violating youtube's TOS. For extraction of audio components alone you might be interested to see this:

```

andrew@skamandros~$ **[COLOR="Red"]youtube-dl -h | grep 'extract-audio'[/COLOR]**
    --extract-audio          convert video files to audio-only files (requires ffmpeg and ffprobe)

```

although this still requires that both audio and video be downloaded.

---

### Post by xtgyal on 2012-01-03
I didn't know that about YouTube, but I was only inquiring regarding generic usage for downloading web videos, nothing that specifically violated any particular site's TOS.  Thank you Andrew.46 for those suggestions, get-flash-videos isn't listed in Ubuntu Software Center, but youtube-dl is (so it looks like Canonical supports it).  I still have to play around with it, but it looks like youtube-dl should do the job, thanks.

---

### Post by lisati on 2012-01-03
> **xtgyal said:**
> Is there an open-source or nonspammy freeware app or plug-in available to download audio and/or video content from the web (e.g. YouTube)? 

> **xtgyal said:**
> I didn't know that about YouTube, but I was only inquiring regarding generic usage for downloading web videos, nothing that specifically violated any particular site's TOS. 
Did you read the [sticky]("http://ubuntuforums.org/showthread.php?t=1850955") in the resolution center?

---

### Post by xtgyal on 2012-01-03
Yes, from your earlier post?  Like I replied, my inquiries are only of a generic legal nature not intended to violate any particular site's TOS.  I didn't know YouTube had that restriction in theirs; the "Easy YouTube Video Downloader" provided by Firefox was listed as their #2 most popular plug-in, and RealPlayer has been doing the same on Windows for years.  There are lots of other sites besides YouTube where you can access videos without restriction though.  "youtube-dl" appears to be supported by Canonical on their Ubuntu Software Center, so I'll stick with that.  Like Andrew.46 said, the name appears to be a bit of a misnomer, since its designed for any webvideos, not specifically YouTube.

---

### Post by SteveDee on 2012-01-04
> **lisati said:**
> ...but please be aware that we don't support violations of another site's TOS....[/url]

Sounds like MiniTube shouldn't be in the Ubuntu repository

---

