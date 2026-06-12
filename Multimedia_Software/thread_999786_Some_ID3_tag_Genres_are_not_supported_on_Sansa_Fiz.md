---
title: "Some ID3 tag Genres are not supported on Sansa Fize"
date: 2008-12-02
forum: Multimedia Software
---

### Post by lil_rich on 2008-12-02
Hi All,

I've been having an interesting ID3 tag problem with my Sansa Fuze. I found that a lot of the genres came up as either unknown, or some random integer (22, 52 etc.). The files were tagged as id3v2.4 (as they should be), but I found that converting them to id3v2.3 ISO didn't work either. 

Re-tagging files didn't work. I used all of the linux programs that tag in id3v2.3 that I could find. That's eyeD3, KID3 and EasyTag. I was only working with "Indie" genres, and all of them gave the same result of "Unknown" genre (artist and album are fine). Although at one point, I got "Unknowndie"!!

Here's the interesting part. If I use a custom genre tag, such as "Indie Rock", which isn't on the genre list provided by.. um libid3tag (I think), it works! So, although the issue isn't fixed, I can work around it.

This looks like it's coming from some incompatibility between the fuze and the id3 libraries. All of the pre-defined genres are associated with a code number, so, for example, if I tag something with "Indie", and look at the tag, eyeD3 says something like:
genre = "Indie (id#131)"
If I tag it as "Indie Rock" it gives me:
genre = "Indie Rock"
This only seems to happen for some genres. Blues and Rock work fine, but Sountrack doesn't either. This must be some difference between linux and windows implementations of id3v2.3 (people using MP3Tag on windows have no trouble), which is a little worrying. 

I can get around the issue by using non-standard genres, even "Soundtrack." (with a period) might do it. I was just wondering if anyone knows anything about this problem. I'm getting a little out of my depth now.

Cheers,
lil_rich

P.S. I'm using Ubuntu Hardy Heron.

---

### Post by Vryko Lakas on 2008-12-31
I'm also using Ubuntu Hardy, and I'm trying to get my mom's 2 GB Sansa Fuze (Christmas present) to work with MP3s I ripped and encoded for her. 

I used two approaches to get the final MP3 files:
A) Ripping the track straight into 128 kbps MP3s using Audio CD Extractor and the gstreamer ugly plugins necessary for MP3 support (provided here: [http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/](http://soundconverter.berlios.de/gstreamer-mp3-encoding-howto/) ). I tried to alter the bitrate to 192 by editing the MP3 profile, but it apparently still reported as 128. 
B) Ripping them into FLAC first and then transcoding them with Sound Converter 1.0.1, setting the results to MP3 with Variable Bitrate, target  bitrate ~192 kbps. 

After transferring all the track files to the Fuze, none of the Artist, Genre, or Album tags show up in their respective menus, and only browsing by Song Title seems to work. This is in regards to files I got from both methods. 
She also reports that the tracks themselves seem to skip and stutter, I don't know if that's from the MP3s, the player, or the source CDs.


I would appreciate any help or insight!

---

### Post by ArgentSilver on 2009-01-07
> **lil_rich said:**
> Hi All,

I've been having an interesting ID3 tag problem with my Sansa Fuze. I found that a lot of the genres came up as either unknown, or some random integer (22, 52 etc.). The files were tagged as id3v2.4 (as they should be), but I found that converting them to id3v2.3 ISO didn't work either. 

Re-tagging files didn't work. I used all of the linux programs that tag in id3v2.3 that I could find. That's eyeD3, KID3 and EasyTag. I was only working with "Indie" genres, and all of them gave the same result of "Unknown" genre (artist and album are fine). Although at one point, I got "Unknowndie"!!

Everything I've seen about the Fuze says it's very picky about needing v2.3 iso-8859-1 tags. I had about 950 songs tagged with v1 and used id3v2 to convert them all to v2.3 before loading onto my Fuze. No problems there. And 'Indie' is a standard genre tag. Were you using some custom tags?

---

### Post by ArgentSilver on 2009-01-07
> **Vryko Lakas said:**
> I'm also using Ubuntu Hardy, and I'm trying to get my mom's 2 GB Sansa Fuze (Christmas present) to work with MP3s I ripped and encoded for her. 

I would appreciate any help or insight!

If you're using Ubuntu, try ripping the tracks to .ogg instead of mp3. As long as you put the latest firmware on the Fuze, it will play ogg files too, and the ogg format is supported much better natively under Ubuntu.

If you still want to rip to mp3, try Grip with the Lame encoder. With the right command line, Lame will give a nice straightforward variable bit rate encode at around 192Kbps, and you won't have to fool around with conversions.

---

### Post by Vryko Lakas on 2009-01-07
Whoa, apparently I didn't have LAME installed, and I didn't even know the Fuze supports ogg! Good news, but I think I'll keep her music in MP3 format just for compatibility with other players and programs. I, of course, use FLAC and Ogg for all my audio needs. ;)
Thanks for the suggestion to use Grip. I'll give that a shot and share the results later.

---

### Post by Vryko Lakas on 2009-01-07
Just checked, and I have both Grip and LAME installed on my laptop. 
However, looking at the rip/encoding options, I feel like a complete failure as a geek. I can't make sense of them, and wading through pages of guides doesn't make them any more clear. 

Any settings I can use to simply rip the CD tracks into VBR MP3s at about 192Kb/s, without screwing up? :P

---

### Post by ArgentSilver on 2009-01-07
On the Grip config tab, make sure that on the rip tab it is set to use "grip (cdparanoia)". The encode tab should have lame set as the encoder. The executable is /usr/bin/lame. The lame command line should be:
--preset standard %w %m
(Gives you an excellent quality vbr of about 192kbps)

For the lame file format, try:
~/%a - %n.mp3
That puts the encoded mp3 into your home directory with the format 'artist - trackname.mp3'

On the id3 tab, make sure to have it add id3v2 tags with encoding type ISO_8859_1. (Fuze only likes v2.3 iso-8859-1)

That should do it, I think. If you need to mess around any further with the id3 tags, kid3 works well and is easily configured.

Good luck!

---

### Post by lil_rich on 2009-01-08
> **ArgentSilver said:**
> Everything I've seen about the Fuze says it's very picky about needing v2.3 iso-8859-1 tags. I had about 950 songs tagged with v1 and used id3v2 to convert them all to v2.3 before loading onto my Fuze. No problems there. And 'Indie' is a standard genre tag. Were you using some custom tags?
Yep, Indie is a standard tag, and it was still having problems on the fuze. In fact, using custom tag names always works fine (so I can get around this by tagging it as "Indie." (with the period), which shows up fine. All I can guess is that there's some incompatibility between the genre id and the Fuze. By the way, I'm using ID3 v2.3, and iso-8859-1. Apparently this is only a problem when transfering as a UMS device. MTP apparently works fine.

I actually switched to using ogg files for all of my CDs, so I haven't checked this issue since the firmware was updated in December. 

I'm not the only one, by the way. A detailed test was done here by daytona955:
[http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=8025&view=by_date_ascending&page=2](http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=8025&view=by_date_ascending&page=2)

Cheers,
Rich

---

### Post by soapbubblenebula on 2012-02-19
More than three years later and a little bit wiser =): It seems that Sansa Fuze has problems i.e. does not recognise the ID3 genre extensions by Winamp—in this [ID3 genre tag table]("http://it.wikipedia.org/wiki/Lista_di_generi_musicali_ID3") these are the genres #80 and above. However, if the genre tag is saved as text instead of number, my Sansa Fuze recognises the genres. Using Kid3, the problem can be solved activating the option (Settings &#8594; Configure Kid3…) *Genre as text instead of numeric string* and rewriting the ID3 tags.

---

