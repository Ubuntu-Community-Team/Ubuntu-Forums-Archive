---
title: "I am so confused about outputting to different video formats"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by billdotson on 2007-02-25
I have started to record TV shows and movies from the TV using my DVD recorder and I have been struggling to know what to do with them.  I know that DVD compliant video files are vob files which are essentially mpeg (avidemux can read them)  I use vobcopy to get the vob file off of the DVD and then stick it in Avidemux and cut out all of the commercials.  I just hit auto to go to the default DVD setup as I would like to be able to burn my videos to a DVD later on.

I have seen and read so much about different encoding/decoding codecs and aspect ratios and different filetypes and on and on and on.  I am just completely lost.  

I have heard of DivX and xVid which are filetypes contained within an avi container or something and then there are mpeg ts and mpeg ps and mpeg raw and ogm and all these different audio formats like vorbis and ac3 and mp2 and the list goes on.  

My goal is to record all 3 back to the future movies to the DVD, cut out the commercials, compress them and then put them on a DVD with a menu where you can choose between the 3 movies, and possibly later split each movie into scenes you can choose from.

Problem is I know so little about anything multimedia I am just getting really confused about all of this.  I am trying to use qDVDauthor to do this and I don't understand how to make a menu and have it linked to a certain video file so when you press on it it takes you to that video.

Where do I start learning all this stuff about codecs and aspect ratios and the frame architecture and all this stuff?? (like what exactly is DivX and xVid)

---

### Post by chewearn on 2007-02-26
> **billdotson said:**
> I have started to record TV shows and movies from the TV using my DVD recorder and I have been struggling to know what to do with them.  I know that DVD compliant video files are vob files which are essentially mpeg (avidemux can read them)  I use vobcopy to get the vob file off of the DVD and then stick it in Avidemux and cut out all of the commercials.  I just hit auto to go to the default DVD setup as I would like to be able to burn my videos to a DVD later on.

Have not specifically use this Avidemux auto option.  I think editing out commercial from TV program should be easily done using the DVD recorder itself. 

> I have seen and read so much about different encoding/decoding codecs and aspect ratios and different filetypes and on and on and on.  I am just completely lost.
I have heard of DivX and xVid which are filetypes contained within an avi container or something and then there are mpeg ts and mpeg ps and mpeg raw and ogm and all these different audio formats like vorbis and ac3 and mp2 and the list goes on.    

Basically, popular video codecs can be loosely divided into mpeg1, mpeg2, and mpeg4 families.  VCD uses mpeg1; DVD/DVB is mpeg2; DivX, Xvid, H.264 is mpeg4.  This is a very simplistic description, but it gives the general idea.  As you go from mpeg1 to mpeg4, the technology/alogrithm advances and you get better quality while reducing data size.

Aspect ratio refers to the video horizontal vs vertical dimensions.  In DVD, only 4:3 and 16:9 are valid aspect ratios.

File types are another way of saying av container; these are "the outer wrapping" to the audio and video streams.  Typically, we have mpeg, avi, ogg, etc.

> My goal is to record all 3 back to the future movies to the DVD, cut out the commercials, compress them and then put them on a DVD with a menu where you can choose between the 3 movies, and possibly later split each movie into scenes you can choose from.


To squeeze 3 movies into one DVD, while retaining the best possible quality, you probably will want to use mpeg4 type codec.  mpeg1 and mpeg2 will look like crap.  Since you own a dvd recorder, I'm sure you know that HQ mode only allows 1 hours into one DVD (mpeg2 compression).  Three movies run around 6 hours; if you have tried the 6 hours recording mode in your dvd recorder, you will know what I mean.

Unfortunately, mpeg4 codec typically exist only on the computer side (discounting the HDDVD/Bluray) in form of xvid or divx, etc.  These do not have menu interface built in, except for divx ultra (which is not free $$$).


> Problem is I know so little about anything multimedia I am just getting really confused about all of this.  I am trying to use qDVDauthor to do this and I don't understand how to make a menu and have it linked to a certain video file so when you press on it it takes you to that video.

Where do I start learning all this stuff about codecs and aspect ratios and the frame architecture and all this stuff?? (like what exactly is DivX and xVid)

Anyway, this is such a complex subject, it is impossible not to oversimplify.

I think you might find the doom9 website useful:
[www.doom9.org](www.doom9.org)

---

