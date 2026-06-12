---
title: "Convert WVP2 to anything else?"
date: 2008-11-18
forum: Multimedia Software
---

### Post by decoherence on 2008-11-18
I have a WMV file that uses the WVP2 codec. It will not play, even after installing the suggested codecs for WMV files (the gstreamer "ugly" set.) Nor will it play in VLC (it will play in VLC for Windows, but transcoding doesn't seem to work.)

These files are created by Microsoft PhotoStory. Has anyone had any luck converting them to something usable?

ADD: I have converted the movie to a WMV3 using Microsoft's Windows Media Encoder. Unfortunately it still does not play properly in Linux (constant flickering.) Also, I have installed Medibuntu's w64codecs... no luck there either.

Every time MS comes up with one of these stupid formats, they should be sued. For crying out loud -- how many video codecs are there out there? And I bet there are a dozen people working on a dozen new ones that are all functionally the same! Grrr.... Stupid MS and Apple futzing the HTML5 spec...

---

### Post by cariboo on 2008-11-18
Becuase of **drm** you may not be able to view the files in Linux. If you have access to a windows computer you could probably convert the file to an avi.

JIm

---

### Post by decoherence on 2008-11-19
> **cariboo907 said:**
> If you have access to a windows computer you could probably convert the file to an avi.


Hi Jim,

Can you suggest such a program? I'm not very familiar with what's available for Windows. I do know that VLC for Windows can play it but not convert it, and MPEG Streamclip for Windows can't even read it.

As I said above, I tried Windows Media Encoder but it produced an unusable file. I suppose I can try tinkering with the settings.

---

### Post by FakeOutdoorsman on 2008-11-19
ffmpeg doesn't seem to support this codec, but I was able to get mplayer (1.0rc2-4.3.2 ) to play it and mencoder to convert (in Arch linux).  I'm not much of a mencoder user, so I can't give you any useful converting options.  I converted this [sample]("http://samples.mplayerhq.hu/V-codecs/WVP2/") (WVP2.wmv).

---

### Post by waldir on 2010-08-16
FYI, I had to install mplayer and also its [binary codecs]("http://www.mplayerhq.hu/design7/dload.html#binary_codecs") package.

Contrary to the instructions on the README, I had to place the files in the /usr/lib/codecs/ folder, rather than /usr/**local/**lib/codecs/ so that mplayer could find them.

After this, my WVP2 file played fine.

---

