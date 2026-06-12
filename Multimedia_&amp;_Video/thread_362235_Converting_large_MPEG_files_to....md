---
title: "Converting large MPEG files to...?"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by davebgimp on 2007-02-15
Here's my situation:

I have a TiVo and occasionally pull a show off to one of my linux boxes and use the program tivodecode to convert the file from .tivo to .mpg. The result is totally usable, but huge in size. An hour worth of video is about 1.3-1.4 gigs, which is a bit extreme as I usually do this to watch a show on my laptop when out and about.

I've been looking around various threads and was wondering if someone had a recommendation for a conversion utility. I'd like these files to be much smaller. I'm used to dealing with hour long video being about 350 megs (usually .avi) and that seems like a doable file size. Really, anything under 500 megs would be welcome, the format not really being an issue for me, I guess.

Any ideas for a GUI/CLI conversion program? Which format should I go for? AVI?

Ideally, a CLI program would be awesome because then I could script the whole get-decrypt-compress-and-convert business, but I'll take anything.

---

### Post by highneko on 2007-02-15
sudo apt-get install mencoder transcode
Both good programs. Don't know the difference. I think they would be good for your situation.

---

### Post by davebgimp on 2007-02-15
> **highneko said:**
> sudo apt-get install mencoder transcode
Both good programs. Don't know the difference. I think they would be good for your situation.

Funny, I was just reading the man-page for that. I'll try it. Thanks.

---

### Post by highneko on 2007-02-15
I should be more helpful, just mentioning packages isn't much. Here's what a wiki says:
>  XviD Two-Pass Encoding

Ripping a DVD with a two-pass encoding will result in higher quality than in simply one pass.

Single pass will take your clip and encode it at once. It takes each frame of the clip, checks that frame's compressibility, and then encodes it.

Two-pass uses the first pass to make an estimation of how well your clip compresses and then uses the compressibility data gathered during the first pass to really encode the clip during the second pass.

Which one to choose depends on what you desire from the result. Two-pass does a much better job at evenly distributing bits where they are needed and therefore gives you a much better looking end result. Generally what you do when you use this option is to calculate motion compensation and other non lossy compression related tweaks (qpel, trellis, gmc. bframe placement. etc) and then on the second pass where the compression is done. Single pass is really for those type of uses that can only be done with single-pass, like for instance real-time encoding a live feed, like a TV-capture or a security camera. Unless you absolutely have to go for single pass for a specific reason there really is no other way but two-pass."

Taken and enriched from The Unofficial XviD FAQ

Here's an example of ripping a DVD using two passes:

mencoder dvd:// -oac mp3lame -ovc xvid -xvidencopts pass=1 -o /dev/null
mencoder dvd:// -oac mp3lame -ovc xvid -xvidencopts pass=2:bitrate=800 -o <filename.avi>

SourceWiki: [http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

Sounds like this will compress it good. Correct me if wrong. Good luck, have fun.

---

