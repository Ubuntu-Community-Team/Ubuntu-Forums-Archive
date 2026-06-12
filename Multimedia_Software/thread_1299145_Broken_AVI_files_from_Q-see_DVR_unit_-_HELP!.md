---
title: "Broken AVI files from Q-see DVR unit - HELP!"
date: 2009-10-23
forum: Multimedia Software
---

### Post by stevefpi on 2009-10-23
I'll try to keep this short and sweet.  I've got a Q-see DVR unit with winblows software included that converts the raw files to AVI.  Problem is that the software is so poorly written that the resulting AVI's are only viewable on winblows systems using the K-lite codec pack.
I got advice from different codec companies and here is what they said about the AVI files.
--------------
In the main AVI header, it reports 2 streams, yet there are 4 strl lists in
the file. This alone is sufficient to report an invalid file, but libavformat
does not stop there.

Secondly, of the 4 strl lists, only one actually has a stream header (strh),
yet they all feel the need to include a stream format (strf), which is all
zeros. Again, invalid.

Anyway, these invalid headers cause libavformat to parse the file as
containing one stream, video, 0x0 pixels in size, with no codec_it, and a
codec tag of 'IL\0\0', which is why QuickTime rejects the file as an invalid
format. If, I turn the LIST headers 3, 4, and 5 into JUNK headers (tells
parser to ignore them), this file plays perfectly fine in Perian (assuming
there is only video and no audio).

Considering the fact that libavformat has issues with this file, I'd say it is
time to get on the manufacturer's case about producing files which are so
horribly broken and demand they fix it. BTW, this file does not play in VLC.

I examined how libavcodec read the file and looked at it a hex editor. Stating
that their own windows based tool works fine so there's not issue with the
files is a poor argument at best. If they write the files, and they write the
tools to read it, that simply means that they simply made the same mistake in
both. The only argument that could possibly work is to check against the
specs, which is what I did.

BTW, VLC cannot play these files. The same holds true for the most popular
file format library (libavcodec) used by literally hundreds if not thousands
of tools. This means that the files are unusable for archive purposes because
eventually their tool will fall into obsolescence, leaving tools based on
projects like libavcodec as the primary source for reading these old files as
open source libraries are more likely to be used in the long term.

Maybe you should threaten loss of future sales, and/or returns of products
until they fix this as their product is severely lacking usefulness until they
provide an output file that's at least something close to the spec instead of
a file referring to 3 invalid streams.
--------------

Q-see has no interest in fixing the issue.  I'm running Ubuntu 9.04 and would lke to use mencoder or ffmpeg to resave the files into an AVI format that is playable in mplayer. VLC, Avidemux, etc.  Alternatively, I am also open to suggestions about trying to strip away the useless headers since the Perian codec designer said he got the sample video to play when he did that (see above).   Anyone have any suggestions as to how to strip away these broken and useless headers or to just convert the videos to a more standard useful AVI format?

Any help would be greatly appreciated!

Thanks

---

### Post by vinutux on 2009-10-23
Try DivFIX ++ for fixing brocken avi **[divfixpp.sourceforge.net]("divfixpp.sourceforge.net")**

---

### Post by stevefpi on 2009-10-23
Sorry, meant to mention that I have already tried Divfix and it did not work.

---

### Post by andrew.46 on 2009-10-23
Hi stevefpi,

Can you post one of these files somewhere? I would be interested to have a look.

Andrew

---

### Post by stevefpi on 2009-10-23
Either use anonymous FTP or a web browser

[ftp://ccar.colorado.edu/pub/shart/CH7_2009_10_03_22_34_06.avi](ftp://ccar.colorado.edu/pub/shart/CH7_2009_10_03_22_34_06.avi)

This is exactly how the Q-see software converter created the file.  It will only play in Windows media player with the K-lite codecs installed.

Thanks for looking!

(yes, I know...shart.  Been there, heard it.)  :P

---

### Post by andrew.46 on 2009-10-23
Hi steve,

> **stevefpi said:**
> Either use anonymous FTP or a web browser

[ftp://ccar.colorado.edu/pub/shart/CH7_2009_10_03_22_34_06.avi](ftp://ccar.colorado.edu/pub/shart/CH7_2009_10_03_22_34_06.avi)


Could not grab the file by ftp or browser, although I could 'see' it in the browser. Is the file accessible to anonymous users?

Andrew

---

### Post by stevefpi on 2009-10-23
Sorry, my bad.  Try it now.

---

### Post by andrew.46 on 2009-10-24
Hi steve,

> **stevefpi said:**
> Sorry, my bad.  Try it now.

I downloaded the file and unfortunately no linux tool I have at my disposal would either play it, repair it or transcode it. I tried the svn MPlayer and svn FFmpeg as well as avifix from the current transcode. Also cranked up my windows vm and attempted the same DivFix++ with total failure.

But as you mentioned the addition of the K-Lite codec pack enables playback on windows, which is very strange. I attach a screenshot of this. Somebody cleverer than me will have to have a look at this one :confused:.

Andrew

---

### Post by vinutux on 2009-10-24
Try mediainfo**[ http://mediainfo.sourceforge.net/en]("http://mediainfo.sourceforge.net/en")**

Media info PPA here : **[https://launchpad.net/~mediainfo/+archive/ppa]("https://launchpad.net/~mediainfo/+archive/ppa")**

---

### Post by stevefpi on 2009-10-24
Yeah, this is so F'd up.  Q-see basically said that they only support PC's running windows and K-lite "solves" the problem.  The problem is that the AVI's are jacked but since K-lite get's around it, Q-see considers the case closed.  

That's why I want to re-save, convert, something so that it's usable at least.  I went so far as to try Avidemux on windows to try and re-save the file but it does not really work.  The re-saved video starts and then ctops 5 seconds in.  

I'm hoping someone here will have some sort of solution that I can do with Ubuntu to get the files into a useable form.  We like the DVR but the software sucks!  I might try to play with the original DAT files that the DVR uses and see if those can be converted into a useable form.  That way I don't have to deal with the broken AVI's at all.  

It's funny because the original DAT files created by the DVR actually play using mplayer and are recognized as an AVI file but play too quickly.  Almost twice normal speed.  Maybe if I manually put in the framerate........

I'm grabbing for straws now.

Thanks for the input and keep it coming if anyone knows another solution!

---

### Post by ASC292 on 2010-08-06
Did you ever figure out your issues, I have used quite a few dvr's and am having more trouble with this P.O.S. Q-SEE DVR than I have ever had before. I don't know which is more of a daunting task, trying to watch the video on there shitty software or figuring out how to play it somewhere else. Please let me know if you have had any luck because I am pulling my hair out.

---

### Post by wurzite on 2011-11-22
I installed Blaze Media Pro, (I've always had that installed) then downloaded and installed the basic K-lite codec pack.  After the K-lite install, Blaze Media Pro was able to both edit the AVI (so I could just save the part I wanted) and then save or convert the edited AVI file to and MPEG file that seems happy to play on anything.:D

---

