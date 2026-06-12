---
title: "Transcoding ogv to ogv"
date: 2010-07-28
forum: Multimedia Software
---

### Post by sdaau on 2010-07-28
Well, in essence the problem is: say I have a ogv file, with 5MB/s video rate and 128 KB/s audio rate. Lets say that I'd like to keep the audio track as is - and I'd simply like to re-encode the video to a lower bitrate. Usually I use [ffmpeg2theora]("http://v2v.cc/%7Ej/ffmpeg2theora/"), as it both accepts stdin, and has a very nice compression algorithm (and is being updated)

I thought there was some easy command line way to transcode this, but couldn't find any - then only thing I could find, was to use ffmpeg to play the original ogv file to stdout, and then pipe that to ffmpeg2theora: 
```

ffmpeg -i ../path/to/test.ogg -f ogg - | ../path2/to/ffmpeg2theora-0.27.linux32.bin -v 8 -a 3 -o ../path3/to/test.ogv -

```However, this doesn't preserve the 'original' audio... 

Well, if someone has an idea about how to preserve the original audio stream while reencoding the video - or you have other command line examples of transcoding ogv to ogv - please post here :D

Cheers!

---

### Post by K.Mandla on 2010-07-28
Moved to Multimedia and Video.

---

### Post by sdaau on 2010-07-29
Hi K.Mandla,

> **K.Mandla said:**
> Moved to Multimedia and Video.

Thanks for the move! 

Btw, while going through [[all variants] 10.04: Video overlay/composite editing with Theora ogv - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1541822"), I found that there is now a tool written specifically for the purpose: it is 'oggTranscode', part of [The Ogg Video Tools]("http://dev.streamnik.de/oggvideotools.html") - a page introducing the two toolsets, 'Oggz Tools' and 'Ogg Video Tools', is at  [TheoraCookbook (en): LosslessIntro]("http://en.flossmanuals.net/TheoraCookbook/LosslessIntro"). 

As per [Version 0.8a of Ogg Video Tools - release notes]("http://freshmeat.net/projects/oggvideotools/releases/318013"), oggTranscode is a new version of a tool previously known as oggResize: 

[quote=http://freshmeat.net/projects/oggvideotools/releases/318013]the oggResize tool was renamed to oggTranscode and was rewritten completly to have some more features.
[/quote]

... and it seems to work OK so far :) For more about oggTranscode, see also: 

[LIST]
[*] [Video Comparison - yorn]("http://www.mentby.com/yorn/video-comparison.html")
[*] [oggvideotools/trunk/README]("http://oggvideotools.svn.sourceforge.net/viewvc/oggvideotools/trunk/README")
[*] [[Streamnik-server-dev] Compile Errors Using Fedora 10]("http://lists.streamnik.de/pipermail/streamnik-server-dev/2009-December/000045.html")
[*] [oggvideotools/trunk/ChangeLog]("http://oggvideotools.svn.sourceforge.net/viewvc/oggvideotools/trunk/ChangeLog?revision=177")
[/LIST]


Cheers!

---

