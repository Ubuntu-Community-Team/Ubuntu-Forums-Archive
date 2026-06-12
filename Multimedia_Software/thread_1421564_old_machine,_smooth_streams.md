---
title: "old machine, smooth streams"
date: 2010-03-04
forum: Multimedia Software
---

### Post by degarb on 2010-03-04
The reality of today's house is one new machine and 4 old ones, operating over the wireless network, on a 768 isp.  So, on main hardwired machine with great hardware, much of the available streams work okay.  But anywhere where video would be useful, in more convenient locations, such as couch or bed, most streams are mere slide shows and not any pleasure to tune in or watch. 

Then there is the immaculate site like streamick.com > tune in classic.fm music stream.  I think I am watching ntsc.  The classical music channel is clear, smooth, and flawless.  But youtube videos are not watch-able, very choppy and horrible.   

I also do much h.264 encoding, and know I can make 240 kps video very watchable, and clearer than most 700 kps videos.  I also have played with wma9 vbr encoding and seen much sub 300 kps stuff look flawless (for practical purposes.)  So, I know what can be done.

Now my brother is a video editor for Turner, who would not work with anything less than 4mbs, probably not that.   But I know you can always get slightly better until you are eating 4 gigs a minute and then need more.   I approach things as what is minimum size possible, then improve on quality--doubling/tripling/quadrupling/ quality in same size.  Else, you seen only little functional improvements over huge overhead increases.  I also never want the video to be auto scaled, since while I might have 768, I need some bandwidth open for voip and surfing/and some video cards maynot decode higher resolution so smoothly: I need to choose my preferred bitrate.


My question is if there is a way to get the everyday old machines over wireless to work better on flash streams, to get quality up to the classic.fm quality.   And what exactly is causing the huge swings in smoothnesss/quality that can be easily fixed on the provider's end?  The embedding code/the required players/codecs/ video dimensions?  If we knew for sure, we could put more pressure the providers to provide real life useful streams.

I groan when Leo laporte recommended flash and 500 kps as the best streaming container and rate.  While this will work fine on two of my machines, the other three that i actually use, not.

---

### Post by no2498 on 2010-03-04
not sure this will help or not but i think it will you can undo same way as doing if it does not work
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to , x window system (no xv)
i do think you need to restart the computer now
if you get high cpu usages or memory spikes undo what we just did
but you should not get it
hope this helps
install gstreamer if you need to we all need it for webcams and things

---

### Post by tgalati4 on 2010-03-04
Flash can't advantage of gpu acceleration.  All single cpu machines  will suffer from interrupts  as a result.

Yes, Leo has been known  to say strange things.  His logo looks like a spaceship.  His advice  is helpful on other planets.

---

### Post by degarb on 2010-03-07
> **tgalati4 said:**
> Flash can't advantage of gpu acceleration.  All single cpu machines  will suffer from interrupts  as a result.

Yes, Leo has been known  to say strange things.  His logo looks like a spaceship.  His advice  is helpful on other planets.

Fortunately, I have an interplanetary IP.   To be fair to Leo Laporte, he does often recommend Ubuntu on his show. 

Now, when html 5 comes, will it too suffer from this interrupt?  Or have a better architecture than flash?

My desktop is xp single cor 3 gig hz, and My acer 1.6 ghz is single core.  These xp machines don't suffer as bad from flash's slideshow effect, but I can tell flash does suck in comparison to wma streams.

(We watch vlc h.264 movies all the time, served by the xp machine.  Works perfectly on this machine.)

---

### Post by degarb on 2010-03-07
> **no2498 said:**
> not sure this will help or not but i think it will you can undo same way as doing if it does not work
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to , x window system (no xv)
i do think you need to restart the computer now
if you get high cpu usages or memory spikes undo what we just did
but you should not get it
hope this helps
install gstreamer if you need to we all need it for webcams and things


Didn't see any difference, but only tested on one youtube stream.  Still more of a slideshow, and not real video.

---

### Post by degarb on 2010-03-07
> **no2498 said:**
> not sure this will help or not but i think it will you can undo same way as doing if it does not work
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to , x window system (no xv)
i do think you need to restart the computer now
if you get high cpu usages or memory spikes undo what we just did
but you should not get it
hope this helps
install gstreamer if you need to we all need it for webcams and things  
gstreamer doesn't do flash.  Or is there a way to use some alternate handler for flash, that would actually work on a single cpu?

---

