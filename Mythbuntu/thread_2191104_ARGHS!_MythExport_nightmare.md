---
title: "ARGHS! MythExport nightmare"
date: 2013-11-30
forum: Mythbuntu
---

### Post by dave65 on 2013-11-30
All right, I am getting really, really tired of this. Eventually I want to modify my MythExport scripts to query the database and add chapter marks for the commercial breaks in my exported shows, but I can't take the time to do that if MythExport breaks every time there is a minor system update!

I suppose I could treat this like my Avid appliance and disallow all updates, at least all updates to the export tools, but that doesn't seem to be the "right" solution. So I am looking for a little advice...

Shortly after I upgraded to 12.04, my export scripts mysteriously broke. This is when I learned about the apparently-nasty feud between ffmpeg and avconv. I changed all my export scripts from ffmpeg to avconv, and for a while at least, everything seemed to work.

Then I installed another round of updates, which apparently included updates to avconv and/or x264, and all my scripts broke again.

Well, apparently I'm not the only one frustrated by this, with what seem to be simple updates causing massive breakage in my MythTV setup. Apparently the Mythbuntu developers have seen fit to combat this by including with the Mythbuntu distribution an old-but-not-avconv version of ffmpeg, which is included on the system and called "mythffmpeg". 

"Great," I thought. "I can convert all my scripts to use mythffmpeg, and all will remain right with the world!"

Except that apparently mythffmpeg doesn't seem to work either. When I try to use my export script command 'as was' with the x264 and libaac codecs, I get an error about "broken ffmpeg default settings detected" and the export fails. The error message helpfully suggests using "-vpre [preset]" but no matter what preset I choose (based on the suggestions in x264 -help) I get an error that the preset files are missing. Web searches and a look at the ffmpeg man pages (but does that manual apply to mythffmpeg? or to the imposter that is the avconv prerelease?) suggests places where the preset files should be located, but none of those locations exists. So I create one, even downloading a set of x264-ffmpeg preset files and loading them into several locations, even setting the AVCONV_DATADIR to point to one of those collections. That didn't work either.

So for now, I'm fixing all my scripts so that they work (for now) with avconv. And quite frankly, I don't have a dog in the avconv/ffmpeg fight, so I don't really care what I use so long as it works, and keeps working. It seems to me that the best option (short of building my own private ffmpeg) is to use mythffmpeg. So here is the question:

What do I need to do to make mythffmpeg function correctly? Where is it looking for the preset files? Or how do I fix the "broken" default configuration so that x264 will work with it?

--Dave

---

### Post by dave65 on 2013-11-30
(oh, and I have no idea why I am suddenly "dave65". I've previously posted on this forum as "RideMan".)

---

### Post by QIII on 2013-11-30
With regard to your account, please start a thread in the Resolution Centre and the Admins will help you out.

---

### Post by dave65 on 2013-11-30
Just did. Thanks!

---

