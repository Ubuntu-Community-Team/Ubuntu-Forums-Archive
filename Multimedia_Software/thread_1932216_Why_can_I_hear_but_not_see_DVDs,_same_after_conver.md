---
title: "Why can I hear but not see DVDs, same after conversion?"
date: 2012-02-27
forum: Multimedia Software
---

### Post by madscientist on 2012-02-27
Argh.  Why do things have to be so complicated?  I don't want to become an AV guru, I just want to share some video!

I went on a trip and they gave us a DVD with some fun video set to music.  First, I wanted to be able to watch the DVD on my Ubuntu system (Ubuntu 10.10).  I put the DVD into my system and I open it up and I see a bunch of files in AUDIO_TS such as .BUP files, .IFO files, and .VOB files.  I find the big one (VTS_01_1.VOB) which is the main video (it's about 18m long and 1G, and the Properties shows it as MPEG video (video/mpeg), and file(1) says it's "MPEG sequence, v2, program multiplex").  As far as I can tell it's not encrypted (how would I know?)

I tried opening it with MoviePlayer and various other tools and in all of them I get a video area that is completely black, but the slider shows the right time and I can hear the music being played.  Then I tried installing various packages like avidemux, VLC, and acidrip.  I can watch the .VOB file in all these packages and I can both see the video and hear the music fine--but MoviePlayer etc. still show just black.  What's going on here?

Second, I wanted to convert the DVD into an online format I can make available for download to some other family members so they can watch.  I've tried using acidrip and avidemux but the plethora of options is very confusing.  However no matter what options I choose, the resulting file always behaves the same: I can hear the audio just fine but there is no video, just a black screen (and this is with every player I have including VLC etc. that work with the original VOB file).  I've tried encoding it into MPEG-4 ASP (Xvid and avcodec) and some others but always with the same result.  I don't want to mess with filters or editing (at least not yet) or anything fancy, I just want to convert this 18m DVD into some kind of file that folks using Linux, Mac, and Windows systems can watch easily.  And I'd prefer to not spend the next 3 weeks of my life learning all the gory details of audio and video codecs, encoding formats, bitrates, etc. etc.

The fact that ALL my efforts, after watching various rippers and encoders churn away for 10 minutes at a time and generate 500M+ files, give me no errors or warnings and nothing to show for it but a black window and some music is VERY frustrating.

Is this possible?  Help!

---

### Post by wyliecoyoteuk on 2012-02-27
Try [Arista]("http://www.transcoder.org/")It should be in software centre.

---

### Post by BHEJU on 2012-02-27
Were you able to run this DVD in Windows / Mac / DVD Player / other machines?
Just asking to make sure that the DVD is not the culprit here.

Cheers,

---

### Post by madscientist on 2012-02-27
Hi all.  Sorry for the delay: work is always busy after a vacation.  So, I'm a little less travel-weary and I have a bit more information.  Some things make more sense.

First let me say "thanks" to wyliecoyoteuk for the Arista pointer.  That's more like the "easy to use" app I was hoping for!

Second, yes, I should have mentioned that the DVD does work in the DVD player and on my wife's Mac and the kids' Windows machine.  And I can get it to play on Linux using SOME apps (see below).  So it's not a DVD problem.

Third, I discovered that the transcodings I was doing with avidemux and acidrip WERE in fact working (although I still don't really understand most of the options I was choosing).

The problem was, and is, that the VIEWERS I was using won't show the video.  Somehow in the flurry of software I thought that VLC was working to show the VOB files and so that's mainly what I was using to check the transcodings.  When they didn't show any video either I thought the transcoding results were bad, but it was the viewers the whole time.

Others have commented here about missing codecs and that seems like the obvious answer.  However, I don't see how that can be the case.  First, I've had for a long time all the different codecs, including non-free ones, installed.  I have watched other DVDs and even mp4 files (for example we got a free download version of LotR when we bought the discs and that works).

Also, while I could not see any video with most viewers, including Totem, Banshee, VLC, Arista ("Live Preview" was black while transcoding) or even FireFox or Chrome (using file:///... to the transcoded .mp4, .avi, etc. files), I WAS able to watch the video just fine using the preview modes of both acidrip and avidemux...!  I believe those are just Perl front-ends to existing software so it's hard to believe they would have access to codecs that VLC etc. do not.

I'm beginning to wonder if it might be a configuration of my graphics card.  Do you think that Totem, VLC, etc. might be trying to use some special DMA features of the graphics card or something for the video?  Maybe the "simpler" tools like acidrip/avidemux are displaying the video using "normal" X facilities (for editing?) rather than any kind of direct access to the driver and so they work.  I switched graphics cards recently and come to think of it, I don't think I've tried watching any DVDs since then.  Just a thought.

When I get home I'll have to do more experimentation and see if I can nail it down.

---

