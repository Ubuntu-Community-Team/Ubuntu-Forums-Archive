---
title: "new HE AAC+ Encoder for ubuntu: Aacplusenc"
date: 2007-12-04
forum: Multimedia Production
---

### Post by rootkit on 2007-12-04
Hi,
I made an HE AAC+ encoder named aacplusenc.
You can found it here: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/) with other tools still in development stage.
However I put some packages on PPA, this is the repo:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main

I hope you get it useful, feedback is welcome

Cheers,
Matteo Croce

---

### Post by nomentero on 2007-12-05
Repository down...?404 not found error

---

### Post by rootkit on 2007-12-05
> **nomentero said:**
> Repository down...?404 not found error
Damn, the page on launchpad.net gives me a wrong link.
It should be:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main

---

### Post by MetalMusicAddict on 2008-02-09
As the man page only contains 23 lines of credits can you please link to command-line usage for aacplusenc?

---

### Post by rootkit on 2008-02-09
> **MetalMusicAddict said:**
> As the man page only contains 23 lines of credits can you please link to command-line usage for aacplusenc?
SYNOPSIS
aacplusenc inputfile.wav outputfile.aac bitrate

example:
aacplusenc song.wav song.aac 32

---

### Post by MetalMusicAddict on 2008-02-11
> **rootkit said:**
> SYNOPSIS
aacplusenc inputfile.wav outputfile.aac bitrate

example:
aacplusenc song.wav song.aac 32

I need documentation beyond that example. Setting VBR/CBR/Tagging options/etc. All the items the come with most encoders.

I want to support this codec but can't if people don't know how to use it.

---

### Post by rootkit on 2008-02-11
aacplusenc is CBR only, ans AAC doesn't supports tags.
AAC is different than MP4...

---

### Post by eye208 on 2008-02-12
> **MetalMusicAddict said:**
> I need documentation beyond that example. Setting VBR/CBR/Tagging options/etc. All the items the come with most encoders.

I want to support this codec but can't if people don't know how to use it.
Use MP4Box to put the AAC stream into an MP4 container. Then you can add tags, bitmaps, video etc. There's no way to add tags to a raw AAC file.

---

### Post by theacoustician on 2008-02-12
> **rootkit said:**
> Hi,
I made an HE AAC+ encoder named aacplusenc.
You can found it here: [http://teknoraver.campuslife.it/software/mp4tools/](http://teknoraver.campuslife.it/software/mp4tools/) with other tools still in development stage.
However I put some packages on PPA, this is the repo:

deb [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/teknoraver/ubuntu](http://ppa.launchpad.net/teknoraver/ubuntu) gutsy main

I hope you get it useful, feedback is welcome

Cheers,
Matteo CroceOutstanding work.  Thanks for the contribution.  Some questions for you since the website is lite on details.

-Why just HE AAC+ encoding?  Are you planning on supporting all levels of AAC?
-Is VBR in the future?  How about multichannel?  Other planned features?

One nitpicky thing though.  You state on your website :
> mp4tools quality is good since it uses x264 (the best h.264 encoder ever) or
xvid (the best mpeg4 encoder ever).
H.264 is MPEG4 part10.  So the statement xvid is the best MPEG4 encoder ever conflicts with the statement on x264 somewhat.  You may want to change that to say "xvid is the best MPEG4 ASP encoder ever".  Just a suggestion.

Once again, thanks for the work and I'm looking forward to future releases.

---

### Post by rootkit on 2008-02-12
> **eye208 said:**
> Use MP4Box to put the AAC stream into an MP4 container. Then you can add tags, bitmaps, video etc. There's no way to add tags to a raw AAC file.
Sure but it's not aacplusenc work
The other scripts in the mp4tools package does, also I have a Nokia tagger :)

---

### Post by rootkit on 2008-02-12
> **theacoustician said:**
> -Why just HE AAC+ encoding?  Are you planning on supporting all levels of AAC?
-Is VBR in the future?  How about multichannel?  Other planned features?

One nitpicky thing though.  You state on your website :

H.264 is MPEG4 part10.  So the statement xvid is the best MPEG4 encoder ever conflicts with the statement on x264 somewhat.  You may want to change that to say "xvid is the best MPEG4 ASP encoder ever".  Just a suggestion.

Once again, thanks for the work and I'm looking forward to future releases.
I use 3gpp sources, so i can't support other levels.
Dunno how to implement VBR or multichannel, any volunteer?

For the h.264/mpeg4 issue, these are common names for these codecs, "normal people" wouldn't understant the real ones:
MP3 really is MPEG1 layer3, while AAC is MPEG2 part7,
but saying "mpeg1" will them think about MPEG1 part 2 video
while saying "mpeg2" will do with MPEG2 part2 video

So sayng h.264 and MPEG4 is fine, everyone should get this :)

---

### Post by theacoustician on 2008-02-12
> **rootkit said:**
> I use 3gpp sources, so i can't support other levels.
Dunno how to implement VBR or multichannel, any volunteer?

For the h.264/mpeg4 issue, these are common names for these codecs, "normal people" wouldn't understant the real ones:
MP3 really is MPEG1 layer3, while AAC is MPEG2 part7,
but saying "mpeg1" will them think about MPEG1 part 2 video
while saying "mpeg2" will do with MPEG2 part2 video

So sayne h.264 and MPEG4 is fine, everyone should get this :)

Wait, did you just say I'm not normal?

...

Ok, fair enough :)

As for help with implementing features, I'm no coder :(  I'd gladly beta test for you though.  Perhaps looking at the source code from FAAC would be helpful?  You could also decompile Nero's AAC encoder for possible ideas.  This may or may not be legal in your country, so do be careful.  I'm not endorsing outright code theft, mind you, just getting some concept of how its done from others so you can implement your own coding scheme.

---

### Post by rootkit on 2008-02-12
Decompiling? Legal or not it' BORING and TEDIOUS so i won't decompile anything.

---

### Post by olavjunior on 2008-02-24
> **rootkit said:**
> Sure but it's not aacplusenc work
The other scripts in the mp4tools package does, also I have a Nokia tagger :)

What nokia tagger do you have? 
I'm looking for a way to convert my mp3s to aac+ with tags..

---

### Post by rootkit on 2008-02-24
It's linked in the page

---

### Post by cozmicharlie on 2008-02-25
Hey Rootkit - thanks so much for all the work you put into this.  I installed aacplusenc.  I am trying to convert a file to raw aac.  The file is .wav file already.  I use this command
```
aacplusenc source.wav destination.aac 32
``` 

and I get this error:
No valid SBR configuration found for:
                        bitrate=32000
                        channels=1
                        samplerate=22050

Thanks for you help and for all the work you put into this.

---

### Post by rootkit on 2008-02-25
aacplusenc supports only 32000, 44100 and 48000 Hz WAV files

---

### Post by olavjunior on 2008-02-26
Any good ways of getting album art embedded into the aac+ files?

---

### Post by keanu13 on 2008-07-15
Hi is this HE AAC+ encoder can be commercialized or free one? if not can it be licensed like what other companies does at some portals like design-win.net, [www.ipsupermarket.com]("http://www.ipsupermarket.com") or chip-estimate etc

---

### Post by rootkit on 2008-07-15
No, the encoder core is copyright by Coding Technologies

---

### Post by rootkit on 2008-07-17
Now with version 0.17.1 aacplusenc works fine on 64 bit builds.
the URL is the same: [http://teknoraver.net/software/mp4tools/](http://teknoraver.net/software/mp4tools/)

---

### Post by Takky on 2008-07-21
Ok.. I don't understand!
I want to put some .mp3 into .m4a with Tag to read it with my Nokia.. That's the point!

I used accplusenc to create the .acc file from a .wav, but now I don't know what to do, I tried to use MP4Box but I don't understand how it Works:(!!

And the Nokia don't play the Raw Acc File..

Pleeeeeeeease.. I don't want to need to go to Win everytime I have to create a new PlayList..:)

---

### Post by rootkit on 2008-07-24
try:

mks60 myfile.mp3

to convert it to myfile.mp4
then add tags with:

nokiatagger -t title -a author myfile.mp4

---

