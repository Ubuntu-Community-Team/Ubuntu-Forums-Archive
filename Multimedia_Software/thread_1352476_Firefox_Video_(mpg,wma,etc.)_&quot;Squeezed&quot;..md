---
title: "Firefox Video (mpg,wma,etc.) &quot;Squeezed&quot;..."
date: 2009-12-11
forum: Multimedia Software
---

### Post by Noobs*McGee on 2009-12-11
I'm not really sure how best to describe this issue, but whenever I play a video file in Firefox -- that is, click on a link to play an mp3, wma, etc. file within the browser (as opposed to downloading and playing, or playing streaming/flash video on a website) -- the firefox video player extension opens the video, and it (usually) plays okay, but it is always squeezed into a square, even when the video itself is designed to be played widescreen, or at least wider than the confines of the square.  This gets kind of irritating given that with many videos, it causes very noticeable distortion (a "squeezing" effect) in the video itself.  I was just wondering if anyone else has noticed this issue, and, moreover, if anyone knows of a fix for the problem?

Best regards,
-NM

---

### Post by lovinglinux on 2009-12-11
I'm not sure why this happens, but I have noticed this once on another computer. Since the problem went away by itself, I believe the video did not have the embedded aspect ratio information. See the quote below for explanation:

> from [http://www.transcoding.org/cgi-bin/transcode?Aspect_Ratio](http://www.transcoding.org/cgi-bin/transcode?Aspect_Ratio)

When transcoding a video, it is important to take both of these aspect ratios into account. For example, most NTSC DVDs use a video frame size of 720x480 pixels but a DAR of either 4:3 or 16:9, meaning that the PAR is not 1:1. If you transcode that DVD to an AVI file without changing the size, the resulting video may look "squished" in one direction. This is because most video playing software (with the notable exception of MPlayer) assumes that AVI files have a PAR of 1:1, resulting in a DAR of 720:480, or 3:2, for the displayed video frame. 

What video plugin are you using? I recommend using gecko-mediaplayer. See the [Comprehensive Multimedia & Video Howto](http://ubuntuforums.org/showthread.php?t=766683). I guess this plugin is capable of displaying the video aspect correctly (since it uses mplayer backend), even if this is not encoded in the video itself.

---

