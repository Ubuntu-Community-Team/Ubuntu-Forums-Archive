---
title: "Converting video using ffmpeg"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by FleetAdmiral74 on 2007-12-07
So I got a new mp3 player with the video files intact, so I can finally right click and see what the properties are. Well...forget about the backstory. Heres what I need,

AVI Video

Video
Dimensions: 160 x 128 (don't know how variable this is though)
Codec: XVID MPEG-4
Framerate: 12fps
Bitrate N/A (should this really be na?

Audio
Codec: MPEG-1 layer 3
Stereo
44100Hz sample rate
128kbps bitrate

MIME type: video/x-msvideo

Most of the videos I want converted are ~700mb avi type stuff, but flvs would be cool too, if its possible. I hope all the stuff I provided makes sense...

*kneels and prays to linux gurus*

edit: I'm on 7.10, not feisty. just have not updated my profile in a bit

---

### Post by DarkStarAeon on 2007-12-07
Pick the third one down on this list, the Debian logo (spiral):
[http://biggmatt.com/winff/downloads/winff-version-0.31.html](http://biggmatt.com/winff/downloads/winff-version-0.31.html)

Your prayers are answered ;)

---

### Post by FleetAdmiral74 on 2007-12-08
Hmm...when I press convert the terminal comes up for a sec, then disappears...not converting at all.

Nothing shows up in the output folder either. 

I would trouble shoot this more, but I have to get to work...maybe someone can tell me what I have to put in the input boxes? I thought I did everything right...I would not have to install extra ffmpeg codecs or something, would I?

Cheers!

---

### Post by DarkStarAeon on 2007-12-08
Only because you didn't mention it, did you actually install ffmpeg in synaptic? Because you do need it. It never hurts to install ffmpeg2theora, but I can't think of anything else you would be missing.

---

### Post by ron999 on 2007-12-08
Hi
I think this command will work:-

ffmpeg -i <infile> -vcodec xvid -r 12 -s 160x128 -acodec mp3 -ab 128 <outfile>

Substitute your own file names.
Try it with a short clip first.

When I ran this command:-

**ffmpeg -i /home/ron/copy.mpg -vcodec xvid -r 12 -s 160x128 -acodec mp3 -ab 128 trial4.avi**

This was the results from MediaInfo:-

ron@ron-desktop:~$ MediaInfo /home/ron/trial4.avi
General #0
Complete name        : /home/ron/trial4.avi
Format               : AVI
Format/Info          : Audio Video Interleave
Format/Family        : RIFF
File size            : 2.70 MiB
PlayTime             : 1mn 5s
Bit rate             : 338 Kbps
Writing application  : Lavf0d.50.5.0

Video #0
Codec                : xvid
PlayTime             : 1mn 5s
Bit rate             : 197 Kbps
Width                : 160 pixels
Height               : 128 pixels
Aspect ratio         : 5/4
Frame rate           : 12.000 fps
Resolution           : 24 bits
Bits/(Pixel*Frame)   : 0.803

Audio #0
Codec                : MPEG-1 Audio layer 3
Codec profile        : Joint stereo
PlayTime             : 1mn 5s
Bit rate             : 125 Kbps
Bit rate mode        : CBR
Channel(s)           : 2 channels
Sampling rate        : 48 KHz
Resolution           : 16 bits
StreamSize           : 1001 KiB
Writing library      : Lame 


If you need MediaInfo get mediainfo_0.7.5.4-1_i386.deb from here [http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612]("http://sourceforge.net/project/showfiles.php?group_id=86862&package_id=90612")

---

### Post by FleetAdmiral74 on 2007-12-08
Mission control, I think I've found the problem. 

```
Unknown codec 'xvid'

```

I did a quick check in the repos, but didn't see one that I was sure would work. Then I googled...no luck though.

And ff is installed.

---

### Post by ron999 on 2007-12-08
Hi
I used Automatix to install all the non-free Audio and DVD codecs. But maybe someone else will advise a different way.

---

### Post by FleetAdmiral74 on 2007-12-08
The last time I was in the loop (more then a few months ago), Automatix was *not* usually recommended. Tended to be messy, and break the system on upgrades. This hasn't changed, has it?

---

### Post by ron999 on 2007-12-09
> **ron999 said:**
> Hi
 But maybe someone else will advise a different way.

Bumpity bump.
:lolflag:

---

### Post by Keith Hedger on 2007-12-09
try this:
[http://homepages.tesco.net/kdlahedger/pages/mpegconv.html](http://homepages.tesco.net/kdlahedger/pages/mpegconv.html)
you will have to alter the script slightly, the web site is still unfinished so be kind:)

---

### Post by FleetAdmiral74 on 2007-12-09
Hey guys, sorry to be so picky, but I really would rather do this with ffmpeg. One I start installing a bunch of different things to try and see if they work, my system just becomes a mess. 

Plus, I would not know how to correctly modify the scripts. At this point, I think I just need the correct package for xvid as noted earlier. 

But thanks for the suggestions none-the-less.

---

### Post by ron999 on 2007-12-09
Hi
I let Automatix install my codecs because it worked for me - and maybe I'm a bit lazy.

There's information in this link here how to fix ffmpeg by using an 'unlocked' one from Mediabuntu.
Perhaps that's what is needed to get ffmpeg to use xvid. And no-one else has come up with anything.
 
If it's no good then perhaps post a new thread in this or another section 'How do I get ffmpeg to use xvid?'.
This is the link:-[https://help.ubuntu.com/community/iPodVideoEncoding]("https://help.ubuntu.com/community/iPodVideoEncoding")

Good luck
:cool::guitar::cool:

---

