---
title: "Does Mytharchive ever work?"
date: 2009-01-23
forum: Mythbuntu
---

### Post by movieman on 2009-01-23
I've been testing mytharchive over the last few days trying to build DVDs from TV shows using a mix of MPEG-2 files and files that have been transcoded to MPEG-4. Most times I just got 'Terminated' because mythtranscode threw a fit for some reason which is never explained. Other times it failed because it apparently tried to create chapters after cutting out the commercials and the last chapter was beyond the end of the file (I'm guessing it was using the uncut length rather than the cut length to determine where to put chapter breaks). When it did occasionally manage to produce a DVD .iso, the 'HQ transcode' files had been encoded to MPEG-2 at around 1Mbps, which meant they were basically just blobs moving around the screen.

Is there any way of getting it to work reliably with Mythbuntu 8.10, or should I give up and wait for the 9.x release? When it does manage to create a DVD they work OK, other than the lousy picture quality.

---

### Post by movieman on 2009-01-24
So it seems the transcoding failures are something to do with the .ICEAuthority file in my home directory, which is a file that k3b creates when I run it to burn .iso files to DVDs; delete that and the transcode completes.

Quite why that has anything whatsoever to do with transcoding is beyond me... it should just be reading one video file and writing another.

---

### Post by klc5555 on 2009-01-24
> **movieman said:**
> I've been testing mytharchive over the last few days trying to build DVDs from TV shows using a mix of MPEG-2 files and files that have been transcoded to MPEG-4. Most times I just got 'Terminated' because mythtranscode threw a fit for some reason which is never explained. Other times it failed because it apparently tried to create chapters after cutting out the commercials and the last chapter was beyond the end of the file (I'm guessing it was using the uncut length rather than the cut length to determine where to put chapter breaks). When it did occasionally manage to produce a DVD .iso, the 'HQ transcode' files had been encoded to MPEG-2 at around 1Mbps, which meant they were basically just blobs moving around the screen.

Is there any way of getting it to work reliably with Mythbuntu 8.10, or should I give up and wait for the 9.x release? When it does manage to create a DVD they work OK, other than the lousy picture quality.

Welcome fellow Mytharchive sufferer! :D

Short answer to the thread question: "Not very often".

Longer answer. 1) Mytharchive works nearly flawlessly when recordings are from analog sources. Particularly when recordings are already at a DVD-ready resolution and don't have to be reencoded.

2) Mytharchive may work with dvb recordings, but it's a real crap-shoot. Known problems include (but are not limited to):

a) Audio sync, which gets progressively worse the further into a recording you go. ffmpeg problem? I don't know of a real solution. Workarounds include cutting commercials from a recording by hand with mythtranscode prior to mytharchiving, but results (for me) still tend to be unsatisfactory for individual recordings longer than about 40 minutes. For longer recordings, after cutting I just automatically go for DeVeDe and mencoder. For the occasional recording that mencoder chokes on, I use nuvexport to code it to a different format, say .avi, and that in turn gets archived with DeVeDe and mencoder.

b) Mytharchive terminates at the ffmpeg stage. This happened for a while after Mythtv 0.21 came out, because the mythburn.py script was missing 4 lines pertaining to the handling of liba52. Editing in those 4 lines, as was documented last year by the user Psikotik, fixes this problem.

c)Mytharchive terminates at the demux stage. God knows why, but the presence of a .ICEauthority file in the user's home directory causes this when audio has to be reencoded. Since the .ICEauthority file is recreated every time X starts, many users just include a one-line script in the startup group, to delete this file every time X starts.

d)Mytharchive terminates at the growisofs stage, because it miscalculates the size of the dvd, and therefore how much individual recordings on the dvd have to be reduced in size to fit on the disk. This was supposedly caused by a faulty version of genisoimage (and therefore only exists in the Debian/Ubuntu world); and upgrading this package allegedly fixes the issue, as was discussed here about six months ago in the "mytharchive hell" thread.

If Mytharchive is terminating on you, the salient information will be at the end of the mythburn log, rather than the progress log that is displayed in the logviewer.

I wouldn't necessarily wait and expect Mytharchive to get much better in 'buntu 9.xx From reading the Mytharchive posts on Gossamer-threads over the past year since Mythtv 0.21 came  out, it would seem that Mytharchive is somewhat of a low development priority. The question seemed to be rather whether Mytharchive is to be included at all in future Myth versions. The maintainer himself mentioned in one post that he doesn't use the plugin. So we need to make the best of what we have.

Cheers! :)

---

### Post by movieman on 2009-01-24
Thanks! I'm tending towards leaving everything I intend to write on DVD as MPEG-2 on the disk rather than transcoding to MPEG-4 at a lower bit-rate; that seems likely to be the least painful method as it should avoid the second transcoding step.

I'll have to look at the liba52 thing.

---

### Post by movieman on 2009-01-24
Looking at the log file, it appears that even though I selected 'HQ' transcoding for the MPEG-4 files, it's used 'SP'; which explains the lower bit-rates. I have a suspicion that when I selected 'SP' before it was using 'LP', hence the very low bit-rate.

---

### Post by joshoekstra on 2009-01-25
Whack...
I normally use mytharchive to burn some programms for my little cousin, I first record the show, then transcode it with HQ profile(PVR500 recordings, commercials cut out with keyframe cutting) after that use mytharchive to put a couple of shows together on a disc. Per show you need to adjust the settings to the ones you want(EP, LP, SP or HQ) and after that you can burn it.
Works nice once the .ice thing got worked out...

---

