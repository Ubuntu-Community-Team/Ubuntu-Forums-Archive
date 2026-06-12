---
title: "Strange Problem Ripping CDs"
date: 2009-12-02
forum: Multimedia Software
---

### Post by trapgate on 2009-12-02
I've been ripping CDs on Ubuntu for years, but with the demise of Grip in 9.10, I had to switch ripping software. I ended up setting up Sound-Juicer and Asunder, both of which can use the FLAC encoder.

Now for the weird problem: I've ripped a few CDs with both of these programs. One of them worked fine; on the others I've tried, I get repeated tracks. For example, tracks 1-8 will be fine, but tracks 9, 10, and 11 will be a copy of track 1.

Both Sound-Juicer and Asunder produced exactly the same results for the problem CDs (which are all brand new, by the way). Also, this machine has two optical drives (one's my old PlexWriter Premium, the other is a DVD writer). Both produce the same results.

The final bit of strangeness: I also tried the 'abcde' ripping script. It works perfectly: no errors, and no repeated tracks.

The only thing I can think of is that there's a problem with gstreamer. I think that both Sound-Juicer and Asunder use gstreamer to do encoding; abcde just rips to files and then encodes from there.

Does anyone have any suggestions for figuring out what's going on here?

---

