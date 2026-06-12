---
title: "Ripping to Ogg in Grip"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by Sweet Spot on 2007-07-15
So, finally installed Feisty, and everything was a total cakewalk. Totally got rid of Windows, and am now 100% Ubuntu Linux. :guitar:  So far, I've been getting along with Feisty, especially considering that I'm taking my time in choosing my apps, and purging those that I won't use. I'm going to try and keep this install as clean and lite as possible now. 

I got rid of Sound Juicer for my ripping needs, and installed Grip just a short while ago. But now I'm faced with the ugly and dysfunctional GUI again, and I'm confused about how to set up my encoding options. 

Besides not knowing where to put the encoding arguments, I'm also WAY behind on what the newest arguments even are...  I have decided that I want to encode to Ogg for the time being, and I don't see the instructions for that in the How To tutorial. 

So my question is, in which box does the argument go ?  There's the "Encoder Command-line" box, and then the file extension box followed by the "encode file format" box. What are the differences between those two sections ? (of course the encode file extension is self explanatory ) Let's say I want to encode @ Q7, where would I enter that, and what would the argument be ?

For the record, I already have all of the encoders downloaded. 

Doug

---

### Post by Sweet Spot on 2007-07-15
Also, I just ripped an album to FLAC in Grip, but as far as tags goes, it only added the name of the songs, and none of the other info, so the songs in Rhythmbox are listed under "Unknown", and obviously in the wrong order...  I made sure that the box which is used to add Id3 tags, was unchecked, as it had instructed.  (besides, did it with the button ticked the first time, and got the same results). 

Is it possible to have GRIP tag FLAC files properly ?

---

### Post by kinghowdy on 2008-04-01
I'm not sure if you still need this but I have GRIP tagging my FLAC using these encoder options:

-8 -V -P -o %m %w -T "ARTIST=%A" -T "TRACKNUMBER=%t" -T "ALBUM=%d" -T "TITLE=%n" -T "GENRE=%G" -T "DATE=%y"

Enjoy!

---

### Post by shirilover on 2008-04-01
You need the vorbis-tools package to be installed.
Here is a thread which should give you what you want -> [http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

---

