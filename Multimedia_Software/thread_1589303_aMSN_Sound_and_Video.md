---
title: "aMSN Sound and Video"
date: 2010-10-06
forum: Multimedia Software
---

### Post by shadowayex on 2010-10-06
My girlfriend is using Karmic and we're trying to get video and audio to work in aMSN.

We confirmed farsight is installed:

```
libgstfarsight0.10-0:
   Installed: 0.0.15-1ubuntu1
  Candidate: 0.0.15-1ubuntu1
  Version table:
 *** 0.0.15-1ubuntu1 0
        500 http://us.archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
```

And that gstreamer good plugins are installed:

```
gstreamer0.10-plugins-good:
  Installed: 0.10.23-4~karmic1
  Candidate: 0.10.23-4~karmic1
  Version table:
 *** 0.10.23-4~karmic1 0
        100 /var/lib/dpkg/status
     0.10.16-1ubuntu3 0
        500 http://us.archive.ubuntu.com karmic/main Packages
```

But when she does the video and webcam set up, she gets an error stating "could not create the valve element." I've looked around and it seems a popular error, but I cannot find a solution, and many posts I find are old and point to broken or irrelevant links.

I found a link that wanted to test for valve in gstreamer, and we tried it:

```
dpkg -L gstreamer0.10-plugins-good  | grep valve
```

That returned nothing. So, valve is not in the plugins that we have. Apparently, it is not in the farsight that we have either, if I've interpreted posts right.

My question is how do I get it? And my issue is that I've never built from source or package or anything. sudo apt-get install and adding to the sources.list file is the experience I have. So, if I need to do source building, I'll need guidance.

---

### Post by shadowayex on 2010-10-08
So, I'm leaning towards there's no solution for this, then?

---

