---
title: "Unknown encoder 'libfaac'"
date: 2012-06-21
forum: Multimedia Software
---

### Post by samaresh on 2012-06-21
I can't convert video in Winff. It says **Unknown encoder 'libfaac'**. This  problem happened  after update libavcode.I had already **Medibuntu Repository** added and **libavcode-extra-53** installed.
The output of **ffmpeg -formats | grep aac** was

```
ffmpeg version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:52:09 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
[COLOR=Orange]This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.[/COLOR]
 D  [COLOR=Red]aac[/COLOR]             raw ADTS AAC
```Please help.

---

### Post by DWright on 2012-06-21
This may help:

[http://dthatcher.blogspot.com.au/2011/08/winff-and-removal-of-libfaac-from.html]("http://dthatcher.blogspot.com.au/2011/08/winff-and-removal-of-libfaac-from.html")

In short libfaac has been removed from FFmpeg for licensing reasons. So instead of using the following option to encode AAC:
-acodec libfaac
Use FFmpeg's experimental encoder instead:
-acodec aac -strict experimental

---

### Post by FakeOutdoorsman on 2012-06-21
> **samaresh said:**
> I can't convert video in Winff. It says **Unknown encoder 'libfaac'**. This  problem happened  after update libavcode.I had already **Medibuntu Repository** added and **libavcode-extra-53** installed.

Ubuntu has updated its version of *libavcode-extra-53*; therefore its version number has surpassed what is available from Medibuntu. Either wait for Medibuntu to update its version, or you can go back to what is currently available from Medibuntu. See [this post](http://ubuntuforums.org/showpost.php?p=12038835&postcount=172) for one method of doing this.

---

