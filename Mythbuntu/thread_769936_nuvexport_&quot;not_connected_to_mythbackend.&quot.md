---
title: "nuvexport &quot;not connected to mythbackend.&quot;"
date: 2008-04-27
forum: Mythbuntu
---

### Post by axcairns on 2008-04-27
Hey all,

I'm building a new mythtv backend on Hardy and Mythbuntu and am trying to get auto-transcode up and running with no luck. Previously I used this [howto]("http://ubuntuforums.org/showthread.php?t=346778") but it is really out of date.

I tried building an old version of nuvexport (0.4) which I had used successfully in the past but that refused to find any recordings -

```
Loading MythTV recording info.
No valid recordings found!


Cleaning up temp files.
```

I then tried installing nuvexport from the standard repositories and now I get the following -

```
Not connected to mythbackend.

Cleaning up temp files.
```

Any ideas?

Thanks,


Allan

---

### Post by axcairns on 2008-04-27
Looks like I've solved it. I downloaded version 0.5 from [here]("http://forevermore.net/files/nuvexport/") unzipped it and built it and it appears to work fine. I suspect 0.4 was not compatible with the latest MythTV while the version in the repos is just crap.

Cheers,

Allan

---

