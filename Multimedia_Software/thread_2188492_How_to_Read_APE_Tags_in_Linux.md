---
title: "How to Read APE Tags in Linux"
date: 2013-11-17
forum: Multimedia Software
---

### Post by Iggy64 on 2013-11-17
In my Windows days, I ripped my CDs to both FLAC and mp3 files.  The FLAC files were for playing on my home system, while the mp3s were for use on portable devices and car stereo.  I used mp3gain to normalize volume on my mp3s, so that non-RG devices could play them with reasonably equal perceived volumes.  The mp3gain data (undo values) were stored in APE v2 tags.  I could use Mp3tag to check both the ID3v2 and the APE v2 tags, to make sure everything was OK.  

Now I am a Linux convert.  I use mp3gain at the CLI to adjust the global gain fields in my mp3s.  The equivalent to Mp3tag in Linux appears to be Puddletag.  However, I cannot find a way to make Puddletag show me the APE v2 tags.  This means I can't check my work.

Next, I tried mp3diags.  This great program shows me that an APE tag is present, but it does not show any info about the tag (a blank box).  So I don't know if I am writing blank APE tags, or if mp3diags simply doesn't choose to show the metadata.

My questions:

1) Does Puddletag have the capability to display APE tags?  If so, how do I get there?  I have explored at length, with no success.

2) How about mp3diags?  Does it display APE tag data if it is present?

3) Is there ANY Linux utility that will allow me to read my APE tags - either GUI or CLI?

Thanks much for any input.  I am really stuck here.

---

### Post by Iggy64 on 2013-11-17
Still no luck reading APE tags with Puddletag.

Since EasyTag advertises that it can work with Monkey's Audio (APE), I installed it and gave it a try.  I had no luck there, either.

Maybe I just don't know how to use these programs!  I'll keep at it.

Meanwhile, I went through the hassle of installing good-old Mp3tag under WINE.  With WINE 1.5.17 and Mp3tag 2.57, it seems to run like a champ.  It shows me my APE tags, and I can check my Replaygain and mp3gain metadata.  I don't know if I want to trust a WINE app to actually write tags in Linux, but at least I can use it to read the tags I create under Linux.

If anyone knows of a native Linux app that will read the APE tags, I'd be grateful to hear about it.

---

### Post by batguano999 on 2013-11-17
Post withdrawn.
Unwanted new account has been created.

---

### Post by Iggy64 on 2013-11-17
Thanks for your kind replay, Batguano.

I'll have to give EasyTag another look.  (I'm  away from my Linux box until tomorrow.)

I wonder if it only shows APE tags for Monkey's Audio files?

In my case, I am working with mp3 files that have APE v2 tags on them.  I'm trying to read the ReplayGain metadata.

I'll check in after I explore your suggestions.

Again, I thank you for your reply.

---

