---
title: "rhythmbox doesn't read id3 tags?"
date: 2007-08-26
forum: Multimedia &amp; Video
---

### Post by Southeast First on 2007-08-26
Hello, everyone.

I just recently switched to the new Rhythmbox and noticed it has some problems with tags. I use EasyTAG to organize my ID3 tags and everyone is flawless in EasyTAG but when I load the songs in Rhythmbox it doesn't seem to read the changes. Furthermore I can't edit the tags IN Rhythmbox because when I do it changed temporarily then immediately reverts to the old tag. Does anyone else have this problem? Is it a bug? Is there anything I can do?

---

### Post by Southeast First on 2007-08-26
Bump!

---

### Post by julian67 on 2007-08-26
> **Southeast First said:**
> Hello, everyone.

I just recently switched to the new Rhythmbox and noticed it has some problems with tags. I use EasyTAG to organize my ID3 tags and everyone is flawless in EasyTAG but when I load the songs in Rhythmbox it doesn't seem to read the changes. Furthermore I can't edit the tags IN Rhythmbox because when I do it changed temporarily then immediately reverts to the old tag. Does anyone else have this problem? Is it a bug? Is there anything I can do?

This happens if the tags are for files such as ape, mpc, wma etc. It shouldn't happen with ogg, mp3 or flac.

---

### Post by Southeast First on 2007-08-26
It does.

---

### Post by Southeast First on 2007-08-27
Anyone?

---

### Post by aysiu on 2007-08-27
Are you using ID3 v. 1 or ID3 v. 2?

---

### Post by Southeast First on 2007-08-27
ID3v2

---

### Post by SoPa on 2007-08-27
Personaly I'm done with rhythmbox and easytag, never worked the way I wanted. Same as you and worst with non-standard characters (accents, japanese, etc...)

Now, I use Quod Libet and Ex Falso, it works like a charm and does everything I want. The only problem is that by default they don't use IDv1 ou IDv2, so you have to play around with the plugins to convert them. Everything is in the Ubuntu depository.

---

### Post by julian67 on 2007-08-27
I'm using Rhythmbox and Easytag and haven't found any tagging problems except for the occasional folder of wma or mpc or aac where Easytag can't handle the formats. Rhythmbox *reads* the tags without problems and as long as they are not wma,mpc, aac I can use it to edit the tags (though I don't, as a dedicated tagger is better).  I think I have around 250 albums in Rhythmbox, maybe another 100 on my portable   and I'm working my way through converting a really big collection of cue+wav/cue+flac/cue+ape archives (big windows hangover) into simple folders containing individual flacs. Easytag has been flawless batch tagging flacs and oggs for me and writing playlists and processing fields. It took a little while to figure out how to use it and set it up exactly how I want (I previously used mp3tag in Windows and kid3 in Linux, different styles) but now it's pretty much the perfect tagger for me.

@Southeast First: you still haven't mentioned what formats you are trying to tag and what id3 tools/libraries you have installed. Maybe you need to use synaptic, check you have Universe repo enabled and  have a look at what's available. btw did you install Rhythmbox from source?

---

### Post by bom28 on 2007-08-27
I think I saw this problem already. It was because the mp3 files have both an id3v2 and an ape tag. If that is the case here, it would mean that Easytag and rhythmbox both modify the id3v2 tag but for some reason rhythmbox read only the ape tag, whereas easytag read only the id3v2 tag.

---

### Post by hugmenot on 2007-08-27
APE tags do not belong in MP3s, just as ID3 tags do not belong in Flac files and EasyTag is a crap program known to pervert standards.

---

### Post by julian67 on 2007-08-27
> **hugmenot said:**
> APE tags do not belong in MP3s, just as ID3 tags do not belong in Flac files and EasyTag is a crap program known to pervert standards.

The flac developers seem ok with it. Flac supports different kinds of tags but only guarantees that its own flactags will work. In practice ID3 tags work fine. EasyTag is linked to from the flac site. 


From flac.sourceforge.net (my bolds)

> What kinds of **tags** does FLAC support?

FLAC has it's own native tagging system which is identical to that of Vorbis. They are called alternately "FLAC tags" and "Vorbis comments". It is the only tagging system required and guaranteed to be supported by FLAC implementations.

Out of convenience, the reference decoder **knows how to skip ID3 tags so that they don't interfere with decoding**. But you should not expect any tags beside FLAC tags to be supported in applications; some implementations may not even be able to decode a FLAC file with ID3 tags***.

> **FLAC supports tagging**, cover art, and fast seeking. FLAC is freely available and supported on most operating systems, including Windows, "unix" (Linux, *BSD, Solaris, OS X, IRIX), BeOS, OS/2, and Amiga.



> A large and growing list of software supports the FLAC format. This list is a sample of open-source software supporting FLAC. Some of the most popular non-free software can be found on the download page in the extras section.

Audio encoders/decoders/converters/taggers:

    * BonkEnc: Windows CD ripper, audio encoder and converter
    *** EasyTAG versatile tagger**
    * Entagged, a Java audio file **tagger**
    * etree-scripts: command-line tools for verifying, **tagging**, converting, and burning lossless audio files
    * FLAC frontend (Windows GUI)
    * Flac-Jacket: a set of scripts for creating FLAC files and an HTML index
    * **FLACTAG:** tags single album FLAC files with embedded CUE sheets using data from the MusicBrainz service
    * MacFLAC Mac OS X FLAC distribution
    * MediaCoder converts between many audio and video formats.
    * MP3FS, a read-only FUSE filesystem which can transcode FLAC to MP3 on the fly
    * rawrec/rawplay recording/playback tools
    * sonice FLAC to Vorbis transcoder
    * Split_wav WAV+CUE splitter
    *** Tag** comprehensive** tagger** (frontend available)
    * XLD (X Lossless Decoder), a Universal Binary command-line decoder for Mac OS X



If you make such statements you should provide some facts that can be referenced and verified otherwise it's just a noise.

---

### Post by trak87 on 2007-08-27
For years Easytag has been a great program.

---

### Post by hugmenot on 2007-08-28
> **julian67 said:**
> If you make such statements you should provide some facts that can be referenced and verified otherwise it's just a noise.

Saying that the reference flac decoder is designed with the ability to skip junk data when decoding and that other decoders might not do that is very much indicative that the author does not consider ID3 as a proper tag for FLAC files. Furthermore, skipping ID3 tags on decoding is not related to the amount of software that will try to read and interpret ID3 as metadata in FLAC files. Which would be only EasyTag, Rhythmbox and XMMS, as far as I know.

I counter your reference with a similar one. Note the added piece:

[QUOTE=http://flac.sourceforge.net/documentation_format_overview.html]As a convenience, the reference decoder knows how to skip ID3v1 and ID3v2 tags. Note however that the FLAC specification does not require compliant implementations to support ID3 in any form and their use is strongly discouraged.[/QUOTE]

---

### Post by hugmenot on 2007-08-28
Oh, about your last reference and your emphasis. Dude, get a clue. The word "tags" refers to items of meta data and is a generic term. ID3 (v1 - v2.4) is but one instance of a tagging standard. The tagging standard that flac desinger chose is the "vorbis comments" standard.

It is very unfortunate that people in general have to come to equate tags with ID3. This is wrong. ID3 is for MP3s and nothing else. 

Your standard of backing up your argument with links is very poor.
So, have another one that is proper:
[QUOTE=http://flac.sourceforge.net/format.html]VORBIS_COMMENT: This block is for storing a list of human-readable name/value pairs. Values are encoded using UTF-8. It is an implementation of the Vorbis comment specification (without the framing bit). This is the only officially supported tagging mechanism in FLAC.[/QUOTE]

---

### Post by hugmenot on 2007-08-28
And, for your appreciation, I dug up the other instance where people were stupefied when their software seemed broken because of EasyTag&#8217;s deviant behaviour.

[http://ubuntuforums.org/showthread.php?t=209371](http://ubuntuforums.org/showthread.php?t=209371)

This corrupt behaviour just has to stop.

---

### Post by julian67 on 2007-08-28
> **hugmenot said:**
> Dude, get a clue.

please don't call me dude, thankyou.


In the other thread you "dug up" (in which you taker part) the OP is not in any way stupefied...he/she just asks a simple question and you offer some insightful input and analysis and the problem is resolved...*and it's discovered that particular (one year ago) version of EasyTag does indeed support flac tags [I]as a switchable option*.
[/I]

You might also be interested to know that **now by default EasyTag writes Flac files with flac tags!!!!! ** I'm using version 2.0 btw


Your choice of terms/descriptions is rather extreme  > deviant behaviour > crap program > pervert standards > people were stupefied > corrupt behaviour

Sometimes people make mistakes, including the people who write applications. It's pretty obvious that this issue has been fixed in EasyTag for some time, this can be verified at the easytag sourceforge site changelogs. You and I may be perfect and get everything exactly correct 1st time every time but other people sometimes need a while to reach this sublime level of blissful brilliance. Meanwhile we can be patient and appreciate them anyway :lolflag:

---

### Post by Southeast First on 2007-08-31
lol@what this thread has become
> **julian67 said:**
> @Southeast First: you still haven't mentioned what formats you are trying to tag and what id3 tools/libraries you have installed. Maybe you need to use synaptic, check you have Universe repo enabled and  have a look at what's available. btw did you install Rhythmbox from source?
Yes, I have the universal repository enables, and I upgraded Rhythmbox with Gutsy.

I went from i386 Gutsy to x86 Feisty now though. I did, however, re-upgrade Rhythmbox to 0.11. Now on this new installation, Rhythmbox keeps the tags as I have edited them until I restart and then they are reverted like before. I think I'm going to try EasyTag and see if Rhythmbox will read tags set by EasyTag this time. I am also going to make sure the mp3s have only id3v2 tags.

---

### Post by julian67 on 2007-08-31
or revert to rhythmbox 10 and associated libraries while you use feisty

---

