---
title: "[SOLVED] avi widescreen to mpg (w/ffmpeg) = squished screen"
date: 2008-12-14
forum: Multimedia Software
---

### Post by ClarkePeters on 2008-12-14
I have an avi that is widescreen which I need in mpg to make an iso and burn to dvd.
Problem is, the result is a squished screen for the mpg. Any advice would be appreciated.

here is the code I used for conversion.

 ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpg

Here is my video info:

$ ffmpeg -i out.avi
...
Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'out.avi':
  Duration: 01:53:04.8, start: 0.000000, bitrate: 856 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 640x272, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 96 kb/s
Must supply at least one output file

---

### Post by ClarkePeters on 2008-12-14
Okay, I scavenged the net and found nothing to help me. 

I didn't want to have to play around with the settings to 
"experiment," as it takes more than an hour and a half to do the conversion, and that's a painfully slow process.  
However, I took a chance and simply added padding to the ffmpeg command (see below), and I got really very close to a normal picture.  Good enough to watch, however, I'm going to try just one more time by setting top and bottom padding to 64 next time.  (I haven't actually converted it to an iso and burned it yet)

Here's what I did
```

ffmpeg -i out.avi -padtop 60 -padbottom 60 -y -target ntsc-dvd -sameq -aspect 16:9 out2.mpg

```

---

### Post by ClarkePeters on 2008-12-15
Okay, that was a no go, my dvd player wouldn't read the dvd after I burned it.

Any advice?

---

### Post by eye208 on 2008-12-16
If your DVD player has MPEG4 + MP3 playback capability (most recent players do), you need not convert anything at all. Just burn the AVI to DVD or CD.

However, if you want to create a "true" DVD, there are a lot more things to consider besides aspect ratio. Your video must be scaled to 720x480, telecined to 29.97fps and encoded to MPEG-2 (.vob), not MPEG-1 (.mpg). You also have to set up the proper file/folder structure expected by DVD players. This is complex stuff, so I recommend using a DVD authoring tool.

---

### Post by ClarkePeters on 2008-12-16
My DVD doesn't support MPEG-4 or MP3 playback :(

I've tried using DVD authoring tools before--the last one being DeVeDe, but it always hangs and others have failed me too (maybe a radeon videocard problem, not sure).

I've suceeded in the past in making a very basic DVD by simply converting my avi like so:

```
step1: 
mencoder -o out.avi -noidx -oac copy -ovc copy /home/rex/in.avi

step2: 
ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpg

step3: 
dvdauthor --title -o dvd -f out.mpg

step4: 
dvdauthor -o dvd -T

step5: 
mkisofs -dvd-video -o /home/rex/dvd/MickeyCC.iso /home/rex/dvd

step6:
burn iso to dvd (right click the iso file and choose "write to disk")
```

It's really easy and never fails.  I've just been lucky in the past because my avi's have always scaled well.  This it the first time I've tried to burn one of those widescreen avi versions. So at the end of the conversion, the movie works great except every one has a long face and all things appear stretched or squished.  If someone could direct me on how to get the right size scaled and the right padding that a standard DVD will accept, then I'd be good to go.

thanks.

---

### Post by FakeOutdoorsman on 2008-12-16
Try this:
```
ffmpeg -y -i input.avi -target ntsc-dvd -padtop 104 -padbottom 104 -s 720x272 out.mpg
```
I'm not sure if it will work.  If you want to keep testing without needing to encode the whole video then use the vframes option.  For example "-vframes 300" will encode just the first 300 frames.  I also don't think you need sameq with the target option.

---

### Post by ClarkePeters on 2008-12-16
thanks for the heads up on the -vframes options.
That will save oodles of time.

I'll give it a try (but now, it's 5am in Taiwan, so I'm heading to bed after an all-nighter of computer programming).  Will get back as soon as I can.

---

### Post by ClarkePeters on 2008-12-18
[as I changed to a different avi, the resolution that applies to my information below was 608x256 for the avi file]

Thanks again to FakeOutdoorsman for the -vframes suggestion. I also discovered that I could do -ss  and -t options to compile a specific segment, this way I avoid the opening credits and get straight to the movie at some specific place.  For example, to view 60 seconds of movie starting at four  minutes into the movie do:
 ```
 ffmpeg ...  -ss 00:4:00:00  -t 60 ... out.mpg 
``` 

After testing, I settled on:

```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 720x440 -padbottom 20 -padtop 20 out.mpg
```

I basically offset the the standard NTSC DVD size (720x480) by the number of pixels in my padding (480-20-20=440) for a 720x440 size. This worked perfectly for my dvd player on the computer but was a little off on the final burn and on my DVD machine (explained later below).

After the ffmpeg conversion, when I did dvdauthor, it gave me a mass of warnings about frame rate being off or something, and then nothing seemed to be happening but after a bit, it finished up doing it's job. Then I did the final step of the dvdauthor as outlined in the previous post, and then I did mkisofs to make an iso, and then I burned it.

It almost worked. The adjustment made automatically by dvdauthor made the images automatically cropped left and right on the DVD machine, and the images were still only slightly stretchy, so I think my padding should have been somewhere between 30 and 40 pixels. I'll give it one more shot at around 34 or 36 padding and see how that finally translates. It should be just fine. Actually, the final DVD was watchable, I mean, my wife, who's pretty picky, said the stretching was only slight enough I didn't need to try again, but since this is my favorite movie, I want to get it more precise.

---

### Post by FakeOutdoorsman on 2008-12-18
Try this:
```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 684x256 -padbottom 112 -padtop 112 -padleft 18 -padright 18 out.mpg
```
The video doesn't stretch to 720 because then the vertical resolution would be a fractional value.  I suppose you could add the croptop (cropleft, etc) options to get it to properly stretch to 720, but my arithmatic skills suck.  You could also just round to the nearest number and hope it looks good:
```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 720x269 -padbottom 106 -padtop 105 out.mpg
```
[list][*] [DAR - or how to make the DVD look right](http://www.doom9.org/index.html?/aspectratios.htm)
[*] [Resizing AVIs for DVD encoding](http://www.doom9.org/mpg/avistretching.htm)
[*] [Working with anamorphic video and ffmpeg](http://howto-pages.org/ffmpeg/#anamorphic)
[/list]

---

### Post by ClarkePeters on 2008-12-19
thanks FakeOutdoorsman.

I settled on padding top and bottom at 36.  I don't mind losing the outside edges of the movie. It plays just fine.

```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 720x410 -padbottom 36 -padtop 34 out.mpg
```


thanks again.

---

### Post by perspectoff on 2009-04-21
> **eye208 said:**
> If your DVD player has MPEG4 + MP3 playback capability (most recent players do), you need not convert anything at all. Just burn the AVI to DVD or CD.

However, if you want to create a "true" DVD, there are a lot more things to consider besides aspect ratio. Your video must be scaled to 720x480, telecined to 29.97fps and encoded to MPEG-2 (.vob), not MPEG-1 (.mpg). You also have to set up the proper file/folder structure expected by DVD players. This is complex stuff, so I recommend using a DVD authoring tool.

That's what the parameter -target ntsc-dvd (or -target pal-dvd or -target film-dvd) does. It sets all those miscellaneous parameters for you.

-target ntsc-dvd outputs to 720x480, with a a framerate of 24 fps

-target film-dvd outputs to 720x480, but with a framerate of 30 fps

-target pal-dvd outputs to 720x576, with a framerate of 25 fps

All three use MPEG-2 for video and ac3 for audio.

Also, I noted these useful settings that can be used to trim a video:

-ss 00:00:01  will start recording at the time selected (hh:mm:ss) for the input file; and

-t 00:15:04 determines how long of a clip to record, in hh:mm:ss

---

### Post by perspectoff on 2009-04-21
> **ClarkePeters said:**
> thanks FakeOutdoorsman.

I settled on padding top and bottom at 36.  I don't mind losing the outside edges of the movie. It plays just fine.

```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 720x410 -padbottom 36 -padtop 34 out.mpg
```


thanks again.

Wouldn't a 16:9 ratio would be 720x405? (For FFMPEG the frame size must be an even integer, so 720x404 would be the closest.) 480 - 404 = 76, so that top and bottom padding of 38 would be required to make up the difference to 720x480.

I tried the convert commands:

```
ffmpeg -i samplevideo.flv -target ntsc-dvd -s 720x404 -padtop 38 -padbottom 38 samplevideo.mpg
```

All the faces and characters looked almost normal.

I then tried 

```
ffmpeg -i samplevideo.flv -target ntsc-dvd -s 720x360 -padtop 60 -padbottom 60 samplevideo.mpg
```

and the faces and characters looked completely normal. 

[I found -padcolor 000000 (which specifies the pad color to be the default black) was not necessary, and that -sameq is only necessary if using VBR (not common). -y just means to overwrite any output file of the same name.] 

But with both, about 10-15% of the widescreen picture on each side was cutoff when viewing it on my TV (but not on my computer). I have read that this is due to the TV overscan, but surely there must be some way around it?

> **FakeOutdoorsman said:**
> Try this:
```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 684x256 -padbottom 112 -padtop 112 -padleft 18 -padright 18 out.mpg
```
The video doesn't stretch to 720 because then the vertical resolution would be a fractional value.  I suppose you could add the croptop (cropleft, etc) options to get it to properly stretch to 720, but my arithmatic skills suck.  You could also just round to the nearest number and hope it looks good:
```
ffmpeg -y -i ScroogeFinney.avi -target ntsc-dvd -s 720x269 -padbottom 106 -padtop 105 out.mpg
```
[list][*] [DAR - or how to make the DVD look right](http://www.doom9.org/index.html?/aspectratios.htm)
[*] [Resizing AVIs for DVD encoding](http://www.doom9.org/mpg/avistretching.htm)
[*] [Working with anamorphic video and ffmpeg](http://howto-pages.org/ffmpeg/#anamorphic)
[/list]
 
If I assume that the horizontal overscan is 10%, then I would need to pad 10% horizontally, or 5% on each side. For a 720 pixel wide screen, this would mean the picture would need to be 720 - 72 = 648 pixels wide, with 36 pixel padding both left and right.

So my target for my video would be 648 pixels wide. 

Let's say my original video is 424x234. To upsize this original video so that the final horizontal width is 648, I would have to multiply by a factor of 648/424. To keep the aspect ratio intact, I would have to multiply the vertical size by the same factor. In other words, the vertical resolution would have to be 234 x (648/424), or  358. 

So my final size of the video would be 648x358. To pad the image to a final size of 720x480 (required for NTSC), I would have to use left and right padding of 36 (always), and 480-358/2 for top and bottom padding, or 61.

Because FFMPEG requires even integers for frame and padding sizes, I would have to tweak this to 648x356 with top and bottom padding of 62. 

Then my convert command would become

```
ffmpeg -i samplevideo.flv -target ntsc-dvd -s 648x356 -padleft 36 -padright 36 -padtop 62 -padbottom 62 samplevideo.mpg
```

In general, a true 16:9 widescreen picture would almost always be upsized to 648x364, requiring top and bottom padding of 58 each. In general, then, a safe command (for 10% horizontal overscan) would be 

```
ffmpeg -i samplevideo.flv -target ntsc-dvd -s 648x364 -padleft 36 -padright 36 -padtop 58 -padbottom 58 samplevideo.mpg
```

If overscan is 15% (uncommon), then the horizontal would be 612. which a 16:9 image would be 612x344. This would require left and right padding of 54 and top and bottom padding of 68. The general command would be, therefore

```
ffmpeg -i samplevideo.flv -target ntsc-dvd -s 612x344 -padleft 54 -padright 54 -padtop 68 -padbottom 68 samplevideo.mpg
```

I end up doing a lot of these conversions. I like the GUI WinFF (as a front end for FFMPEG), which is now available in the Jaunty Repositories (or alternatively as a .deb file from the project website):

 sudo apt-get install winff

I added a preset in WinFF for this routine conversion of 16:9 Widescreen to 4:3 Letterbox:

    Video converter (WinFF) -> Edit -> Presets ->
      Preset Name: Letterbox
      Preset Label: 16:9 Widescreen to 4:3 Letterbox 
      Preset command: -target ntsc-dvd -s 648x364 -padleft 36 -padright 36 -padtop 58 -padbottom 58 
      Ouput file extension: mpg
      Category: DVD
        -> Add/Update -> Save 


========================================================================
I was born with 2 arms and 3 legs. As a schoolboy, Maths for me was always hard. The only thing I knew for sure was three feet made a yard. To count to ten I used my fingers -- and if I needed more, by getting my shoes and socks off I could count to twenty four!

---

### Post by aaronLund on 2010-10-01
The new ffmpeg is missing critical info in its docs.
> 
late versions of ffmpeg changed command line options from padright/padleft, etc to -vf "pad=w:x:y:z,crop=...". 

I did this:

```
ffmpeg -i my-vid.ogv -target ntsc-dvd -s 648x364 -vf pad=648:364:black ntsc-648x364-with-padding.avi
```

.....and it seemed to work (i.e. no more vertically stretched video).

To be honest though, I'm not 100% convinced that I know what "pad=w:x:y:z,crop=." means even though "-vf pad=648:364:black" seems to do the trick.

What have I just told it?

The man page says:

> All the pad options have been removed. Use -vf
           pad=width:height:x:y:color instead.

I'm not sure I"m grokking why the man page has 4 values:  width, height, x, y ???

I would've thought this would work
```

ffmpeg -i input.ogv -target ntsc-dvd -s 648x364 -vf pad=648:364:36:58:black  ntsc-648x364-with-padding.avi
```

....since I wanted 36 units of x padding and 58 of y.

It's late, I'm getting cloudy.

Thanks for any input.

---

### Post by aaronLund on 2010-10-01
Hmmm....seems like my audio is a bit late now.  Probably only a couple of samples.

Anyone know of a "delay audio by x samples" flag?

Thanks again.

---

### Post by FakeOutdoorsman on 2010-10-01
You could try the *-itsoffset* option.  (S)MPlayer lets you change audio delay in playback so you can get a better idea of how much of an offset you need.

---

### Post by aaronLund on 2010-10-09
> You could try the -itsoffset option. (S)MPlayer lets you change audio delay in playback so you can get a better idea of how much of an offset you need. 

Thanks for the reply, fakeoutdoorsman.  Haven't tried that yet.

Simply because I'm really curious about what's causing this?

It would almost seem like the sample rate and/or frame rate is not being set correctly on the newly created file.

Like this.....

```
ffmpeg -ss 00:04:00 -t 60 -i myvid.ogv -target ntsc-dvd -s 648x364 -vf pad=648:364:black myoutputvid.avi

```

....isn't "good enough".  My avi gets output at a sample rate of 48000.  And if I'm experiencing an odd audio/video synch issue.  Therefore, I would think that this......

```
ffmpeg -ss 00:04:00 -t 60 -i myvid.ogv -target ntsc-dvd -s 648x364 -vf pad=648:364:black -ar 44100 myoutputvid.avi
```

....(notice the newly added "-ar 44100") would fix it.  But even though the properties of this newly created file report a sample rate of 44100 the audio is still significantly delayed.

Even more bizarre is the fact that looking at the frame rate of both of the above says '30 fps' which is the same setting as on the original ogv file.

Is the fact that I'm doing this....

> -target ntsc-dvd

...overriding the sample rate?  As in, 'even though I'm seeing 44100 in the properties, it's not?'

Driving me crazy!

Thanks for any input.

---

