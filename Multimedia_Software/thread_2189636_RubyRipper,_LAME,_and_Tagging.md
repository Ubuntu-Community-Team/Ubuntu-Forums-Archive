---
title: "RubyRipper, LAME, and Tagging"
date: 2013-11-23
forum: Multimedia Software
---

### Post by Iggy64 on 2013-11-23
I've had pretty good luck with RubyRipper as a substitute for EAC, but I'm at a loss trying to understand how it adds tags to my mp3 files.

I'm running RubyRipper with LAME 3.99.3.  I rip to FLAC (for home play) and mp3 (for on-the-go).  

I was surprised to find that RubyRipper automatically adds ID3 tags to the mp3 files (and Vorbis Comments to the FLAC).  However, I cannot find any controls within RubyRipper to modify the tagging behavior.

By default, RR was adding both ID3v2.4 and ID3v1 tags to mp3s.  In the coded preferences for LAME, I added "--id3v2-only," which eliminated the ID3v1 tag, but now produced an ID3v2.3 tag instead of an ID3v2.4 tag. 

So now I wonder:
Does RR by default try to add ID3v2.4? 
And, if I pass "--id3v2-only" to the LAME options, does that now put LAME in charge of adding the tags?

Can anyone familiar with RR tell me how RR is handling this?  I have searched high and low for documentation on this, but can't find anything.  I'd like to be able to either turn the tagging off, or control how the tagging is done.

*************

Here is a second issue:

My ID3v2.3 and ID3v2.4 tags are coming out with track fields like 3/12, or 5/10 -- meaning "track 3 out of 12 track," etc.  This is something new to me.  I would prefer to simply have the track number, without the total number of tracks.  That's how I have done them for years.  Is there a way to control this -- either in RR or in LAME?

---

### Post by Iggy64 on 2013-11-24
After still more experimentation, I have concluded that:

For mp3 encoding, RubyRipper writes ID3v2.4 tags with zero padding.  Since I prefer ID3v2.3 tags, I have two options.

a) I can use Mp3tag (which runs great under WINE) to batch re-save the tags, automatically switching them to ID3v2.3 and adding padding, or

b) Let LAME do the tagging while running RubyRipper.  Lame 3.99.3 writes ID3v2.3, and can add padding as requested.  In the RubyRipper "Preferences," in the Codec tab, for mp3

V0 --id3v2-only pad-id3v2-size 2048

Either approach seems to get the job done OK.

---

