---
title: "Devede output too small"
date: 2009-01-10
forum: Multimedia Software
---

### Post by pyromanic123boom on 2009-01-10
I create a regular ntsc dvd with Devede - 2 hr movie, for example.
The destination size is around 4.3 gb, a full dvd for best quality. Once it's finished, however, it's around 2 gb instead of 4. 

I've been reading around, and this is what I've found: mencoder ignores bitrates from devede, and insists on using a vbr of 2000. Since the disc is 4 gb, I'd like to use the full disc and get the best quality. I don't include a menu with Devede- you can turn it off in the older versions, and set it to go to the first title in the newest version. By the way, the older versions don't seem to make a difference.

I'm willing to try a different program, but I don't want menus. I don't want a pain in the neck. Call me lazy, but I just want a easy to use avi-to-dvd encoder with subtitle support. 


other posts with this problem:
[http://ubuntuforums.org/showthread.php?t=855945](http://ubuntuforums.org/showthread.php?t=855945)
[http://ubuntuforums.org/showthread.php?t=921899](http://ubuntuforums.org/showthread.php?t=921899)
[http://ubuntuforums.org/showthread.php?t=455832](http://ubuntuforums.org/showthread.php?t=455832)

---

### Post by mc4man on 2009-01-10
Maybe this thread will better explain it for you, the basic fact is when you are going from an avi to dvd format the quality is not determined by the size or even bitrate. The best quality possible is achieved from the least amount of "quality' loss from the reencoding (transcoding).

The size and bitrate are just the end result.

[http://ubuntuforums.org/showthread.php?t=929250](http://ubuntuforums.org/showthread.php?t=929250)

In one of the posts you linked there was a quote from  a mplayer forum that pretty much answered the question though no one there seemed to realize it

quote of a quote 
[http://ubuntuforums.org/showthread.php?t=921899](http://ubuntuforums.org/showthread.php?t=921899)


"...if the source file being converted does not have enough inherent quality to achieve the bitrate set by the user, it will not 'pad' the file with zeros, it will simply encode at the highest possible bitrate for the given source material."

---

### Post by pyromanic123boom on 2009-01-10
Well, I understand about not being able to increase the quality of the avi - because the quality is already maxed.

It just seems like a waste of space. I could put two movies on single dvd at the rate devede creates them, but I don't want to. 

Using virtualbox, I've used dvd flick and turned the same avi into a 4gb dvd. So, I just know it can be done. I don't do this now, because coping over the iso is really slow over the network, and it times out. Maybe I will try ConvertXtoDvd with Wine, unless anyone has a fix.

Thanks for the help so far

---

### Post by mc4man on 2009-01-10
That's your choice, it's just a psychological thing. You should base your choice of what encoder and settings does the best job of minimizing the inherent loss from re-encoding.

---

### Post by pyromanic123boom on 2009-01-11
Yeah, I've decided it's not a big deal to me. However, last night I was reading devede's version history, and I noticed a interesting entry in version 3.7-

"# Version 3.7
   # The final size of the ISO image is now much more accurate."

So, I downloaded it ([http://www.videohelp.com/tools/DeVeDe/old-versions](http://www.videohelp.com/tools/DeVeDe/old-versions)) and am testing a movie right now. Currently, it's halfway through encoding, and the mpg file is already 2 gb. Maybe it will work after all...but I'll re-post when the final ISO is  generated.

---

### Post by pyromanic123boom on 2009-01-11
SOLVED!

Download DeVeDe version 3.7 from [http://www.videohelp.com/tools/DeVeDe/old-versions](http://www.videohelp.com/tools/DeVeDe/old-versions), and run the install script. It will create a menu icon.

I put the video/audio bitrates at MAX for an 1.5 hour movie, and it gave me a 4.0 GB ISO. Estimated size was, however, 5.3 GB. So I gather it's roughly a GB or a little more off track in this version.

---

