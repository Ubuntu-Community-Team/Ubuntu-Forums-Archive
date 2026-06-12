---
title: "flac to V0?"
date: 2007-11-18
forum: Multimedia &amp; Video
---

### Post by bionnaki on 2007-11-18
what can I use to convert flac to V0? any app recommendations? or how can I just use lame through the CL?

thanks

---

### Post by disturbedite on 2007-11-19
this isn't really recommended unless entirely necessary.  (going from lossless (flac) to lossy (mp3)).  and if you have to, ogg would be a better lossy format.

that being said, you could convert the mp3 file(s) to wav first and then convert to mp3 with lame.

---

### Post by bionnaki on 2007-11-19
there's nothing wrong with converting flac to mp3 - the original flac is not touched and the resulting mp3 does not lose information like a lossy-to-lossy transcode. you should read up on lossless before posting. 

that being said, I'd like to create V0 from my flac collection. Not ogg - it is not necessary better than a lame V0 rip.

I realize that you'd need to decode the flac first and then compress the wav into mp3. I know how to do this one track at a time via CL, but how would I do entire albums at a time?

---

### Post by ron999 on 2007-11-19
Hi
I'm confused.
What is V0?

---

### Post by disturbedite on 2007-11-19
> **bionnaki said:**
> there's nothing wrong with converting flac to mp3 - the original flac is not touched and the resulting mp3 does not lose information like a lossy-to-lossy transcode. you should read up on lossless before posting.
i'm sorry but you are the one who is wrong.  FLAC Is *[COLOR=Lime]lossless [/COLOR](meaning no quality is lost from the original source)*. MP3 is [COLOR=Red]lossy[/COLOR] *(meaning quality is thrown away and is not as good as lossless).*  there is no MP3 lossless quality.
i guess you're the one who should read up before posting.  ;)

@ ron999
V0 is a lame/mp3 preset for quality.

---

### Post by bionnaki on 2007-11-20
> **disturbedite said:**
> i'm sorry but you are the one who is wrong.  FLAC Is *[COLOR=Lime]lossless [/COLOR](meaning no quality is lost from the original source)*. MP3 is [COLOR=Red]lossy[/COLOR] *(meaning quality is thrown away and is not as good as lossless).*  there is no MP3 lossless quality.
i guess you're the one who should read up before posting.  ;)



I know what flac and mp3 are. 

your first post was cautionary as if converting flac to mp3 was somehow dangerous and not recommended. converting from lossless to lossy is quite common and is no different from ripping a cd to mp3. zero difference. do you warn people not to rip cds too?

you seem to not understand that lossless-to-lossy is ok, while lossy-to-lossy is not.

---

### Post by bionnaki on 2007-11-20
so, to convert from the commandline, this is what ive been doing:

> 
flac -d test.flac
lame -V 0 --vbr-new test.wav test.mp3


obviously doing this one track at time is tedious. how can I do this per album at a time?

thanks.

---

### Post by Squabsy on 2007-11-20
for a in *

do
      OUTF=`echo "$a" | sed s/\.flac/.mp3/g`

      ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
      TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
      ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
      GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
      TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`

      flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1  - "$OUTF"
      id3 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" "$OUTF"

done

---

### Post by Squabsy on 2007-11-20
save the above as flac2mp3.sh & make it executable then run it in the folder your flacs (and only your flacs) are in

---

### Post by bionnaki on 2007-11-20
thanks for the script.

ok, so I saved the following into a txt file & made it executable:

> 
OUTF=`echo "$a" | sed s/\.flac/.mp3/g`

ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
id3 -t "$TITLE" -T "$TRACKNUMBER" -a "$ARTIST" -A "$ALBUM" -g "$GENRE" "$OUTF"


and I get the following:

> 
bionnaki@ubuntu:~/test_directory$ ./flac2mp3.sh
: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.
: ERROR: reading metadata, status = "FLAC__METADATA_CHAIN_STATUS_ERROR_OPENING_FILE"

The FLAC file could not be opened.  Most likely the file does not exist
or is not readable.

flac 1.1.4, Copyright (C) 2000,2001,2002,2003,2004,2005,2006,2007  Josh Coalson
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.


: ERROR initializing decoder
  init status = FLAC__STREAM_DECODER_INIT_STATUS_ERROR_OPENING_FILE

An error occurred opening the input file; it is likely that it does not exist
or is not readable.
Assuming raw pcm input file
LAME 3.97 32bits ([http://www.mp3dev.org/](http://www.mp3dev.org/))
CPU features: MMX (ASM used), SSE, SSE2
Using polyphase lowpass filter, transition band: 19383 Hz - 19916 Hz
Encoding <stdin> to <stdout>
Encoding as 44.1 kHz VBR(q=0) j-stereo MPEG-1 Layer III (ca. 5.7x) qval=0
 &#65533; 4&#65533;UUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUUid3: Track: : Expected a number.
bionnaki@ubuntu:~/test_directory$ 



any idea?

---

### Post by Squabsy on 2007-11-20
you need to install metaflac in order for the script to be able to read your tags and pass them on to the mp3 tags

---

### Post by disturbedite on 2007-11-20
i'm saying that audiophiles don't recommend it cuz there is a reason a file was ripped to flac, to preserve the source quality, and if you convert to a lossy format like mp3 you lose that quality.  thats why a lot of archives you find have a text file included where the ripper demands it not be converted to a lossy format if you're going to be redistributing it.  some boards even require lossless.

---

### Post by ron999 on 2007-11-20
> **disturbedite said:**
> 

@ ron999
V0 is a lame/mp3 preset for quality.
Thanks for that.:)

I think too that an mp3 file will be lossy even if it is V0.
But it looks as though V0 is the best quality VBR mp3 available.
So let's call a truce and see if we can get Squabsy's script to run.:lolflag:

How do you install metaflac in Ubuntu?:confused:

---

### Post by nick_h on 2007-11-20
> How do you install metaflac in Ubuntu?

Install the flac package:
```
sudo apt-get install flac
```
This gives you flac and metaflac.

---

### Post by ron999 on 2007-11-20
Thanks nick_h
I already have flac installed. But I get an output like bionnaki's.

And the description in Synaptic says:-
[B]This package contains the command-line tools flac (used for encoding and
decoding FLACs) and metaflac (used for manipulating FLAC metadata.)
[/B]
(I should have read this before I asked) :oops:


So there might be some other problem why that script doesn't deliver.

---

### Post by nick_h on 2007-11-20
I tested the script and it worked for me.  Check that you have read permission on the flac files.

The only change I made to the script was to the id3 line as follows:
```
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -g "${GENRE:-12}" "$OUTF"
```

This defaults the track number to 0 and the genre to 12 (other) if the tags were not defined in the flac file.

---

### Post by ron999 on 2007-11-20
Yes, it's working ok for me too now.
(Throws up errors about meta data, but maybe it's because there is no meta data with my files)

Me and bionnaki have made the same mistake.
We omitted
[B]for a in *
do

done[/B]

:):):)

---

### Post by bionnaki on 2007-11-21
> **disturbedite said:**
> i'm saying that audiophiles don't recommend it cuz there is a reason a file was ripped to flac, to preserve the source quality, and if you convert to a lossy format like mp3 you lose that quality.  thats why a lot of archives you find have a text file included where the ripper demands it not be converted to a lossy format if you're going to be redistributing it.  some boards even require lossless.

well, I obviously want mp3 otherwise I wouldnt want to convert my archived flac so I can play them on my **mp3** player. and if you go to hydrogen audio and ask how many people convert flac to mp3, I'd say a majority of people do it for the same reason. 

like I said, there is zero difference between ripping a cd to mp3 and converting flac to wav to mp3.

---

### Post by disturbedite on 2007-11-21
right, maybe i misunderstood you.  i thought you were saying converting a flac file to mp3 would remain lossless.
but yes, there is no difference between ripping a cd to mp3 and converting flac to wav to mp3.

---

### Post by Spenzer4Hire on 2007-11-30
I just wanted to chime in with a perl script I found.

[http://robinbowes.com/projects/flac2mp3](http://robinbowes.com/projects/flac2mp3)

Works great.  Defaults to --preset standard (V2) but that is easy to change.  Open up the perl script and towards the top of the file the lame settings are properly labelled.  Change --preset standard to --preset extreme (which is V0)

---

### Post by bionnaki on 2007-12-01
cool script, thanks. 

but aps does not *exactly* equal V2, and apx does not *exactly* equal v0 - there is a slight difference. maybe someone else can chime in about that...

---

### Post by ron999 on 2007-12-01
> **bionnaki said:**
>  maybe someone else can chime in about that...
Maybe you should read post #17

---

### Post by bionnaki on 2007-12-01
why?

---

### Post by bionnaki on 2007-12-27
> **nick_h said:**
> I tested the script and it worked for me.  Check that you have read permission on the flac files.

The only change I made to the script was to the id3 line as follows:
```
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -g "${GENRE:-12}" "$OUTF"
```

This defaults the track number to 0 and the genre to 12 (other) if the tags were not defined in the flac file.

so this script works great. however, the year tag does not transfer from flac to mp3. any ideas on how to make it transfer?

this is the script I am using:

> 
for a in *

do
OUTF=`echo "$a" | sed s/\.flac/.mp3/g`

ARTIST=`metaflac "$a" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$a" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$a" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$a" --show-tag=GENRE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$a" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$a" | lame -m j -q 0 --vbr-new -V 0 -s 44.1 - "$OUTF"
id3 -t "$TITLE" -T "${TRACKNUMBER:-0}" -a "$ARTIST" -A "$ALBUM" -g "${GENRE:-12}" "$OUTF"

done


I also get these errors at the end:

> ./flac2mp3.sh: line 16: unexpected EOF while looking for matching `"'
./flac2mp3.sh: line 17: syntax error: unexpected end of file


and is there anyway to run this from /usr/bin instead of a local script? 

thanks!

---

### Post by nick_h on 2007-12-28
I don't get any errors.

Why do you want to run the script from /usr/bin?  Just create a bin directory under your home directory.  It will be included in your path in your .profile file.

---

