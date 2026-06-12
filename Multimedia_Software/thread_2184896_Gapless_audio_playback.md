---
title: "Gapless audio playback"
date: 2013-10-31
forum: Multimedia Software
---

### Post by bachtobach on 2013-10-31
I don't understand this. I'm a new xubuntu user and this is one thing that is driving me crazy. I've learned that there is or was a bug in gstreamer that prevents gapless playback with audio files. For me this narrows the options down considerably for music players. I did try MPD and a client for a while, these do play back gaplessly but they all just seemed to have something missing although ncmpcpp looks promising with some configuration. I'm not keen on the text based approach in general, I like to see cover art and browse my collection by covers if possible. I accepted this and decided to use Foobar2000 in Wine. It works pretty well and I do really like the customization. 

Then today I found out two things 1) that the bug in gstreamer was supposed to have been fixed about a year ago and 2) there there was an update to Clementine. I read the changelog and sure enough it mentions that gapless playback has been fixed. I got very excited and downloaded it but unfortunately this doesn't seem to be the case, it is still not gapless. 

Now I'm starting to wonder whether this is just a problem I have or whether there is a fix for it? I don't see many people posting about here or elsewhere which seems odd, there must be other people who listen to live or mix albums. 

I have tried Audatious and deadbeef, they do play gaplessly but they're too basic for me. 

I'm using 12.04LTS xubuntu if that makes any difference.

---

### Post by vanadium on 2013-10-31
Gapless and linux unfortunatelly is a pain for many years. We are overwhelmed with media players, but few seem to care about quality.

Even if media formats that support gapless by design, such as flac and ogg, now should play gapless indeed, gappless playback of mp3 files still may not be seamless. As far as I am aware, only mpd with its own playback system does it perfectly right for a couple of years now. Indeed, Audacious may also work perfectly nowadays.

I am using mpd and sonata. While the setup is always some trouble, it is a lightweight combo that for me works very well. It does not allow you to browse collections by cover, but uses cover art while playing back.

---

### Post by Yellow Pasque on 2013-10-31
> that the bug in gstreamer was supposed to have been fixed about a year ago

Please link to the bug. Also, note that you're using an older version of (x)Ubuntu, so it would be better to to test a LiveUSB of Xubuntu 13.10 to see if the issue has been fixed.

---

### Post by bachtobach on 2013-10-31
[**[COLOR=#000000]Temüjin[/COLOR]**]("http://ubuntuforums.org/member.php?u=327594")  	 I don't have a link to the bug, this is just what I've gathered from searching this forum for hours trying to find a solution. I did have a full install of 13.10 and it was doing the same thing in that.

---

