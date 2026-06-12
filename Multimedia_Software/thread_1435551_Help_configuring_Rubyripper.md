---
title: "Help configuring Rubyripper?"
date: 2010-03-21
forum: Multimedia Software
---

### Post by oxf on 2010-03-21
OK I just installed Rubyripper.  Please could someone experienced with Rubyripper set me straight on the following  questions :)

This is ripping to MP3

Previously I used Sound Juicer with the gstreamer pipeline:
"name=enc mode=0 vbr=4 vbr-quality=0 ! id3v2mux"
critical variables being mode=stereo, vbr=lame new algorithm, vbr quality=0 highest quality.

With Ruby it seems slightly different and I followed (lame --longhelp) to try and duplicate the same results. In Codecs> Lame MP3  I entered:
"-q 0 -m s --vbr-new -V0 --id3v2-only"

Have I done this correctly? i.e for simple stereo, VBR new, and highest vbr quality?

Also when I look at the properties of the ripped track its lists the bitrate as 251kbps.
Is this consistant with vbr?

If you could review my resulta and  put my mind at rest please. Many thanks!

---

### Post by mc4man on 2010-03-21
Don't use mp3's much but that seems fine. One or more of the parameters are redundant, won't particularly matter if they're there
This would probably give you the same thing
-m s -V 0 --id3v2-only

The reported vbr is fine

---

### Post by ron999 on 2010-03-21
@0xf
Yes, **-q 0** and **-V 0** and **--id3v2-only** are needed.
But **--vbr-new** isn't needed, it's the default.

I haven't used the **-m s** options, so it's left at default.
Longhelp says "default is (j) or (s) depending on bitrate". I don't understand the difference.

I hope you're happy with RubyRipper.

---

### Post by oxf on 2010-03-21
@mc4man
@ron999

OK thanks, I do believe I've got it! 

 My initial impressions of Rubyripper are that it will give me what i need. Despite warnings of a slow rip at the higher quality settings it still was faster than I expected. So I think it will be fine :)

---

### Post by Andrew Golightly on 2010-04-20
Hi there,

I've installed rubyripper.. and configured the codecs tab for lame mp3 to be

-q 0 -V 0 --id3v2-only

After encoding a cd, I noticed when I right clicked on a track, chose properties and viewed the audio tab 

the bitrate seems to be mainly 96kbps for tracks.

This seems really low for the highest quality rip right?

Thoughts?

---

### Post by ron999 on 2010-04-20
Hi
It's using variable bit rate.
So it won't encode at a high rate in the parts where it's not necessary. For example in quiet sections of the music.
That's what I think.:neutral:

---

