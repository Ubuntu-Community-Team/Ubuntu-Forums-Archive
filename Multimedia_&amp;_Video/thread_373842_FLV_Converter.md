---
title: "FLV Converter"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Zeek00 on 2007-03-01
I recently have downloaded some movie files in a *.FLV format, I intend to burn them to a dvd to watch them on my dvd player or where ever. Does anyone know if Ubuntu has a FLV converter so my home DVD player can play the movies?

Thanks,
Zeek

---

### Post by nalmeth on 2007-03-13
Anyway, heres what you should do:
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240  video.mpg

I know it's not a GUI way of doing it, but it works great. There are some websites online that will actually encode the file and give it back to you, but I recommend this way.

Obviously, change video.flv and video.mpg to reflect the initial flv file, and respectively, the resultant video.mpg you want.

---

### Post by jdong on 2007-03-13
> **Zeek00 said:**
> I recently have downloaded some movie files in a *.FLV format, I intend to burn them to a dvd to watch them on my dvd player or where ever. Does anyone know if Ubuntu has a FLV converter so my home DVD player can play the movies?

Thanks,
Zeek

If the final destination is a DVD, you would benefit from the Tovid suite ( [http://tovid.wikia.com/wiki/Main_Page](http://tovid.wikia.com/wiki/Main_Page) ). It makes the process of making DVD player compatible discs go from torturous pain to less torturous pain (kidding, actually it's not that bad once you get the hang of it)

It is just a "front end" over the almighty ffmpeg tool, instructing the tool what kind of video to output.

---

### Post by nalmeth on 2007-03-13
Ga-LAX-y, you're right jdong, I didn't observe the OP wanted to make a DVD, tovid is the tool for the job.

---

### Post by GordSellar on 2007-03-16
> **nalmeth said:**
> Anyway, heres what you should do:
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240  video.mpg

I know it's not a GUI way of doing it, but it works great. There are some websites online that will actually encode the file and give it back to you, but I recommend this way.

Obviously, change video.flv and video.mpg to reflect the initial flv file, and respectively, the resultant video.mpg you want.


Is there any reason why this command might only be usable on a file once? It worked once, but the output was slightly lossy so I tried to run it a second time with a new output filename, and fiddling with the parameters of the command, and the computer wouldn't do it. Then I tried yet again, but with the original parameters and a new filename, and I got this output:

2055401.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

### Post by Icelandic24 on 2008-02-20
> **nalmeth said:**
> Anyway, heres what you should do:
ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240  video.mpg

I know it's not a GUI way of doing it, but it works great.

I'm a *total* Linux newbie, so please excuse me if i'm very stupid :confused:
I'd love a GUI tool with FFmpeg to do this. When working in *erh* Window$, I use FFmpeg as implemented in the freeware [Flv converter]("http://www.ripzor.com/flvconverter.html") but are there any similar GUI tools for Ubuntu?

---

### Post by jdong on 2008-02-20
I can't think of any off the top of my head. Usually for operations that can be done with a single or a very small set of CLI commands, nobody bothers to write a GUI for it because it's just spending a few hour's time to design a GUI for something that doesn't need it. It's only a popular thing on Windows because its default shell is so crippled in functionality nobody treats it seriously as a working environment.

---

### Post by ron999 on 2008-02-20
Hi
I agree with the above comments about using 'tovid'. That's what I use for authoring DVDs.
But there is a pretty good GUI for ffmpeg, it's called 'WinFF'.
From BiggMatt's website here:-[http://biggmatt.com/]("http://biggmatt.com/")
8)

---

### Post by kriukov on 2008-02-23
I am sure VLC can do that.

[http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)

I successfully converted WMV videos to OGG with it. As it plays FLV well, it should convert it too. Start File -> Wizard and choose Transcode/Save to file (further it is intuitive).

---

### Post by articpenguin on 2008-02-26
try
[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

