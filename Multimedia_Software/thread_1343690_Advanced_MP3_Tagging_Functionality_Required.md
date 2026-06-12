---
title: "Advanced MP3 Tagging Functionality Required"
date: 2009-12-02
forum: Multimedia Software
---

### Post by DJGibbon on 2009-12-02
Morning* all

I'm after a program to do some slightly more advanced tagging operations on MP3 (and hopefully OGGs and FLACs too). I use Picard for auto tagging and am generally very impressed with it, but I need to perform some operations which move data between tags, e.g. set the Composer tag equal to the Artist tag.

If anyone's familiar with it, the masstagger on foobar2000 on Windows is basically what I'm looking for. I've tried the tagger addon for Songbird but it doesn't like certain placeholders when updating tags (e.g. can't use Album Artist). I've also tried Ex Falso, easyTag, and Picard, and couldn't see any way to do what I wanted with them (but I'm happy to be proven wrong :)

Any advice and recommendations gratefully received!

*Depending on local timezone :)

---

### Post by DJGibbon on 2009-12-03
Bump

No-one? Can't believe there's not a Linux app out here to do this. Don't really fancy moving my collection to somewhere Windows-accessible to do it :)

---

### Post by DJGibbon on 2009-12-03
Whoops, somehow managed to double-bump :)

---

### Post by brookie on 2009-12-04
Hi,

I've been updating my music library recently and found that Banshee can do this if you have the preference checked to write to metadata. Right click on a song and click 'edit track information'. The tag is "Compilation Album Artist'. 

I've tried all those editors you mentioned as well, and could not see "album artist" tag anywhere, until I tried kid3-qt. I'm on Karmic and it's in the repos so it came up in synaptic package manager. 

I explained how to install kid3-qt with the plugins which don't get installed by default [here]("http://ubuntuforums.org/showthread.php?p=8439206#post8439206").  

Hope this helps. Wish easytag just did it for us! 
Cheers, 
brookie

---

### Post by DJGibbon on 2009-12-06
Hi Brookie

Cheers for the advice, but I'm not just after updating the Album Artist tag. What I want to do it update tags using the values from other tags - so for example, for all the songs in my library set the "Composer" tag equal to the value currently stored in "Artist", say. I can do this in foobar2000 in Windows but it seems like a lot of hassle to install Windows just for this, and I've not heard good things about FB2K under Wine . . . .

---

