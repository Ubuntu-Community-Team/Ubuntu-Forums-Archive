---
title: "Cinelerra does not recognize .mts video"
date: 2011-12-25
forum: Multimedia Software
---

### Post by ysaric on 2011-12-25
WHen I try to load .mts files as resources in Cinelerra it says 0001.MTS's format could not be determined, and it then tries to interpret it as raw PCM data which only comes through as audio file resources.  The video comes from a JVC camcorder and plays fine in the Ubuntu Movie Player and can be uploaded directly to YouTube also ok but Cinelerra is not recognizing it.  When I go to the Software Center, this is the version information:

cinelerra 2.1.1-git20100325~ppa5~lucid

Of course I'm trying to work with Christmas morning videos :)

Any help or advice is greatly appreciated.

---

### Post by ysaric on 2011-12-27
Newer versions of cinelerra support .mts files better (natively?), the newest of which at the time of this writing is version 4.3.  However version 4.3 as best I can tell is only available as source code and is a pain in the pitookus to properly get running although I have seen at least one thread say it is possible (dependencies and makes and error messages and all that).  The best available package you can get easily from Ubuntu repositories seems to be 2.1 or 2.2.  I had to add a repository and crack the terminal open to get 2.2, but super easy compared to trying to get 4.3 to work unless there are some instructions out there I haven't found yet.  Versions 2.1 and 2.2 do not like .mts files.

I'm downloading OpenShot now with my fingers crossed. (looks like it loads .mts files, which is great.  Just waiting now to run into the stuff people hate about OpenShot)

There seem to be a lot of users waiting on a new open source video editing program called Lightworks which is currently available for Windows in public beta and was going to be available at the end of November for Mac/Linux but that beta has been delayed with no current ETA.  Apparently it's so great that when it comes out we're all likely to drop whatever program we use to at least go try it if not take it home to meet our parents.

I liked working with cinelerra before I switched to this new camcorder which uses .mts.  If anyone has any info on getting cinelerra 4.3 up and running on 11.10 that would be sweet indeed.  In the meantime I will play with OpenShot and wait patiently for Lightworks.

---

### Post by stuartcnz on 2012-01-01
Cinelerra 4.3 is from the original branch, The 2.1 etc series is from the community version, which is run independently, by different people than the original branch.

It woulld appear that it is generally accepted that the community version is more stable, which would seem reasonable given that a number of people work on it, where as the original branch only has one developer.

When I run into trouble with a format not being accepted by cinelerra (I use the community versions), generally a clip that is over a certain length from my Canon 5DMK2, then I convert that particular clip into something like mpeg4 at full resolution, with KDEnlive, and then use the converted file in Cinelerra.

---

