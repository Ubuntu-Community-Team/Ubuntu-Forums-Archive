---
title: "ffmpeg help"
date: 2007-02-08
forum: Multimedia &amp; Video
---

### Post by treehouse on 2007-02-08
So I got some nice looking mp4s to put on a dvd, but I need to make them mpeg-2s first. So I do:

ffmpeg -i in.mp4 ./out.mpg

I get a perfectly playable .mpg out of it, except it makes the length of the file 1s, instead of nearly 30m, which means it'll play back when I test it, but if I touch the seeker bar, Totem self-destructs. The other problem is that it doesn't look as good any more. The mp4 is all pretty and the mpg has those blocky artifact looking things.

I need to get the same quality out as I got in, at 720*480 resolution, and I'm confused by the documentation for ffmpeg. If anyone could point me towards what I need to be doing, I'd be super grateful. Thanks.

---

### Post by david_2001 on 2007-02-08
I got fed up messing about with the long and intricate command lines that seem to be necessary for video conversion and went for [KmPg2]("http://kmpg2.sourceforge.net/view.php/page/Voorpagina").  You need to work a little to get it installed - it needs Kommander from KDE, y4mscaler has to be compiled from source and the installer doesn't reliably copy the conversion profile files to your home account - but I've found it really useful.

An alternative is [Tovid]("http://tovid.wikia.com/wiki/Main_Page"), which I've also tried.  Installation is easier - there are Ubuntu-specific instructions - and the main conversion script works well but the gui still has a few problems.

---

### Post by majoridiot on 2007-02-08
> **treehouse said:**
> So I got some nice looking mp4s to put on a dvd, but I need to make them mpeg-2s first. So I do:

ffmpeg -i in.mp4 ./out.mpg

have you tried using the "target type" option and let ffmpeg figure it all out for you? (this example
assumes ntsc dvd format... change to pal-dvd as needed)

```
# ffmpeg -i in.mp4 -target ntsc-dvd out.mpg
```

this works equally as well for targets of vcd, svcd, etc. and with any input file format you have
the appropriate codecs for.

take some time and look over the man page for more info.  ffmpeg is VERY powerful.

```
# man ffmpeg
```

---

### Post by RomeReactor on 2007-02-08
I suggest trying **avidemux** if you haven't already; it's in Synaptic...

---

