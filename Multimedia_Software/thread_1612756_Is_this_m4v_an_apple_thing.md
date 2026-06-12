---
title: "Is this m4v an apple thing??"
date: 2010-11-03
forum: Multimedia Software
---

### Post by f3nr1c on 2010-11-03
Hi all, 
       I have a rather large DVD collection, which for the sake of space, I am going to rip to an external drive so I can put the disks in the loft. 

Anyway, it has been some years since I ripped a DVD, and back then Xvid was the way to go. Since I have decided to do this now, I thought I would give handbrake a go. I was surprised to find it no longer supported xvid, but it is also encoding my videos as m4v files using the H.264 codec. Is this the right way to go?? I though m4 files were Apple related. Also, the quality seems a little off, but that might just be me being fussy. 

Anyway, I am not TOO fussed about file size, a couple of gig for a 90 minute vid is fine by me. I only care really about quality and compatibility (especially for the long term, as I don't want to have to re-encode!)

Any tips or advice on what I should be doing/using??

---

### Post by jocko on 2010-11-03
Don't know about handbrake, but other dvd-rip software should encode to xvid (or whatever format you chose) as long as you have the appropriate codec installed...
dvd::rip (package name dvdrip) and acidrip should definitely do it.
m4v is apple's "almost mp4" format, but I think it can be played by any player that is capable of playing mp4 files (as long as there is no DRM protection).
But are you sure it's really m**4**v files? The files I have seen encoded with H.264 have been m**k**v...

---

### Post by f3nr1c on 2010-11-03
> **jocko said:**
> Don't know about handbrake, but other dvd-rip software should encode to xvid (or whatever format you chose) as long as you have the appropriate codec installed...
dvd::rip (package name dvdrip) and acidrip should definitely do it.
m4v is apple's "almost mp4" format, but I think it can be played by any player that is capable of playing mp4 files (as long as there is no DRM protection).
But are you sure it's really m**4**v files? The files I have seen encoded with H.264 have been m**k**v...

Yes, it is m4v for some odd reason. It also offers mkv as well though. I tried them both, but the mkv would only play in VLC, while the m4v played in totem, MPlayer and VLC. No difference quality wise though. I am wary of anything that is encumbered by an Apple/MS patent or standard.... :D

I am only worried because I am so out of the loop! 5 or 6 years ago, I knew what I as doing, but I feel like I am in over my head now, with all these formats, codecs and extensions.

Is there a defined standard in what constitutes the best quality compressed rip?? I know you lose some quality, that is inevitable, but I want to keep it minimal, and like I said, compatible with ANYTHING!!

I'll give DVD::rip a try! Cheers :)

---

### Post by cchhrriiss121212 on 2010-11-03
I use handbrake to rip my DVDs, the setting I find best is mkv on the "high profile" default. I tried out m4v but the quality was lower with a higher file size. I can play mkv on all software players and it seems to have a good level of support with newer media devices. 

2GB is quite large for a DVD quality 90min film, 700MB with high profile mkv is indistinguishable from source to me.

---

### Post by moore.bryan on 2010-11-03
m4v is just the iPad/Phone/Pod-optimized mkv container.

---

### Post by f3nr1c on 2010-11-03
> I use handbrake to rip my DVDs, the setting I find best is mkv on the "high profile" default. I tried out m4v but the quality was lower with a higher file size. I can play mkv on all software players and it seems to have a good level of support with newer media devices.

2GB is quite large for a DVD quality 90min film, 700MB with high profile mkv is indistinguishable from source to me.

> m4v is just the iPad/Phone/Pod-optimized mkv container.

Thanks for the input guys. I tried DVD::rip. A little to much of a learning curve givn th tsk I have ahead of me :D

I'll try handbrake with MKV again, and tweak the settings a bit, see how it goes. 

Cheers. :)

---

### Post by moore.bryan on 2010-11-03
Have you thought about just ripping your DVD's with VLC?

---

### Post by Chronon on 2010-11-03
> **moore.bryan said:**
> m4v is just the iPad/Phone/Pod-optimized mkv container.

This is incorrect.  It is one of several aliases for an MP4 container.  Apple started using various extensions to distinguish mp4 files with various types of content:

m4a = mp4 with audio streams only
m4v = mp4 containing a video stream
m4p = mp4 containing encrypted content (generally from the iTunes store)
m4b = mp4 containing audio streams and allowing bookmarking
m4r = mp4 containing audio streams but used as a ringtone on iPhone.

---

### Post by moore.bryan on 2010-11-04
> **Chronon said:**
> This is incorrect.
How so? When I uncheck "iPod/iPhone support" in Handbrake, it can only save the file with an .mkv extension; however, when I check that same box, it saves it with .m4v.

---

### Post by Chronon on 2010-11-04
From the HandBrake user manual:
> By default, output video is stored on your Desktop, and named with the title of the DVD followed by the .m4v extension. It's the same thing as an .mp4 file&#8212;the default preset uses chapter markers, and by naming it .m4v, QuickTime sees them.

> By default HandBrake saves all files in the MP4 container, which is both widely compatible and offers many advanced features. MP4 is the native file format for a number of consumer devices (iPod, PSP, Apple TV) and is supported out of the box by QuickTime and iTunes. If you are encoding for playback in any of those situations, it is recommended.

If you need features not found in MP4, HandBrake can also save files in the widely popular MKV container.

---

### Post by moore.bryan on 2010-11-05
Interesting Chronon... thanks for the info!

---

### Post by Chronon on 2010-11-05
:)  No problem.  I just wanted to clear up any possible confusion for people who find this topic via a search.

---

### Post by moore.bryan on 2010-11-06
I'd also suggest anyone read the Wikipedia pages for [m4v]("http://en.wikipedia.org/wiki/M4V") and [mkv]("http://en.wikipedia.org/wiki/Mkv").

---

