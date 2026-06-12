---
title: "Converting to and playing tak files in Ubuntu"
date: 2011-02-04
forum: Multimedia Software
---

### Post by shantiq on 2011-02-04
I like to know that i can play EVERY audio format in Ubuntu and move between those formats with ease


Latest one that has occupied my attention is[ tak]("http://wiki.hydrogenaudio.org/index.php?title=TAK") which has been much derided since it will natively only work on windows and even there not on many players; but it is a nice format and i like to use it

worked out a quick way to move from flac to tak( first place Takc.exe [attached below] in system 32 folder in your C:drive )   cd to folder of flacs then

```
flac -d *flac && wine takc -e -pMax \* && rm *wav && mkdir "tak" && mv *.tak "tak"
```

but this leaves me with no tags as files are turned to wav then tak losing tags in the process


I was also given this a few weeks ago 

```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.tak/g`

ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
TRACKTOTAL=`metaflac "$f" --show-tag=TRACKTOTAL | sed s/.*=//g`
DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | wine takc -e \* "$OUTF"
 "$OUTF"  -meta:artist="$ARTIST" -meta:title="$TITLE" -meta:album="$ALBUM" -meta:genre="$GENRE" -meta:year="$DATE" -meta:track="$TRACKNUMBER" -meta:totaltracks="$TRACKTOTAL"
done
mkdir "$ALBUM" && mv *.tak "$ALBUM"
```


but this script on my system refuses to go through as it says (see attached image)


Any idea about how one could change that so that it reads wildcard input   how would I/one modify the script



thanx    shan


Ps those files play beautifully on foobar2000 under wine

---

### Post by NFblaze on 2011-02-04
I do not know of this TAK format, nor do I know why one would want to use it for though,

Perhaps you can create a readline loop to read in the name of the actual files in the directory to a variable, than you could just substitue the variable instead of the wildcards.

Also, the FLAC commandline option also supports AIFF output which if I remember correctly is basically a Lossless compression with a few features one being metadata capability. May also want to look into that.

---

### Post by cascade9 on 2011-02-04
Have you ever met a lossless codec you dont like shantiq? :lolflag:

> **shantiq said:**
> Latest one that has occupied my attention is[ tak]("http://wiki.hydrogenaudio.org/index.php?title=TAK") which has been much derided since it will natively only work on windows and even there not on many players; but it is a nice format and i like to use it

Of course its derided. Only has foobar and winamp decoders last I checked, closed source,overly complicated encoding settings, not worth it compared to flac..... 

[http://www.synthetic-soul.co.uk/comparison/lossless/](http://www.synthetic-soul.co.uk/comparison/lossless/)

> **NFblaze said:**
> Also, the FLAC commandline option also supports AIFF output which if I remember correctly is basically a Lossless compression with a few features one being metadata capability. May also want to look into that.

AIFF is lossless, but not compressed. 

[http://en.wikipedia.org/wiki/Audio_Interchange_File_Format](http://en.wikipedia.org/wiki/Audio_Interchange_File_Format)

---

### Post by NFblaze on 2011-02-04
> **cascade9 said:**
> 
AIFF is lossless, but not compressed. 

[http://en.wikipedia.org/wiki/Audio_Interchange_File_Format](http://en.wikipedia.org/wiki/Audio_Interchange_File_Format)

No, I was wondering if he could convert from AIFF to TAK with this takc program, and perhaps save the tags since WAV has none. I dont know what input formats this takc thing understands the (documentation I found for it was in German.)

---

### Post by cascade9 on 2011-02-04
> **NFblaze said:**
> No, I was wondering if he could convert from AIFF to TAK with this takc program, and perhaps save the tags since WAV has none. I dont know what input formats this takc thing understands the (documentation I found for it was in German.)

You can have sort of tags in wav files- 

> Metadata

 As a derivative of the Resource Interchange File Format (RIFF), WAV files can be tagged with [metadata]("http://en.wikipedia.org/wiki/Metadata") in the INFO chunk. In addition, WAV files can embed [Extensible Metadata Platform]("http://en.wikipedia.org/wiki/Extensible_Metadata_Platform") (XMP).


[http://en.wikipedia.org/wiki/WAV](http://en.wikipedia.org/wiki/WAV)

[http://www.sno.phy.queensu.ca/~phil/exiftool/TagNames/WAV.html](http://www.sno.phy.queensu.ca/~phil/exiftool/TagNames/WAV.html)

But its not a good idea, and way more sodding around than just transcoding without tags and then using easytag to put the tags in.

---

### Post by shantiq on 2011-02-04
cascade i love them all:KS:KS:KS:KS:KS even ape sometimes. :KS maybe not

well aiff would be the same problem   


since one would have to go through wav first. 

but the bashscript i enclosed earlier should work but there is an issue around the * wildcard  and i do not know enough coding to rectify it or find a workaround



so how what you do this here   > readline loop to read in the name of the actual files in the directory to a variable, than you could just substitue the variable instead of the wildcards.


it may be a basic question but i am not sure how to do this


the original line is  ```
for f in *.flac

```     what do i change this to?

---

### Post by mc4man on 2011-02-05
shantiq - 
2 things - 
in that script the flac pipe to tak is wrong, more like this w/ just the e option
```
flac -c -d "$f" - | wine takc -e - "$OUTF"
```
2nd you don't have anything specified to tag with, figuring it (tak) uses ape tags not sure what you'll do there, you'll need to research that. (E. - unless tak can do that itself?

---

### Post by shantiq on 2011-02-05
hi mc4man


as mentioned earlier no idea where i found this script


this is the takc info

```
TAKC V2.0.0
Copyright 2006 by Thomas Becker, D-49080 Osnabrueck, Germany

TAKC -mode [-p# -fsl# -wm# -md5 -ihs -v -overwrite -fim# -l# -silent -w -lp]
     [-tt #] infile [outfile]

-mode      -e encode, -d decode, -t test decode, -te test encode,
           -fi file information
-p#        select encoder preset #: 0-4 (fastest to strongest, default is 2).
           Append E/M (-p2m) to increase the evaluation level to Extra/Max.
           pMax is a synonym for the strongest setting.
-fsl#      Set the frame size limit to # samples per channel. Valid values:
             512, 1024, 2048, 4096, 8192, 16384
-wm#       Control saving(encode)/restoring(decode) of wave file meta data:
             0 = disable
             1 = enable and use default values for maximum size (default)
             46 to 1048576 = enable and set maximum size (encoding only)
-md5       add (encoding) / verify (decoding) MD5 of the raw wave data
-ihs       ignore (wave) header size entry (pipe encoding only)
-v         verify encoded frames (when encoding)
-overwrite overwrite existing output files (without confirmation!)
-fim#      select file information mode #
             0 = any information (default)
             1 = encoder
             2 = wave meta data
             3 = MD5
-l#        select log file level #
             0 = no log file (default)
             1 = log results
             Append A (-l1a) to append new results to an existing file.
-silent    silent operation: Write nothing to StdOut/the screen.
-w         wait for enter key when finished
-lp        Execute with low priority. Nice for background processing.
-tt #      Add textual tag item #, where # is a key/value pair: "key=value",
           for instance "TITLE=A nice song". "key=@file" will read the value
           from the text(!) file "file" in the source directory.
infile     Specify file or directory (Dir\*) to be processed.
           - selects StdIn (encoding only, requires outfile specification).
outfile    Specify output file or directory (Dir\*).
           - selects StdOut (decoding only, requires infile specification).
```

---

### Post by mc4man on 2011-02-05
I guess you could use tak for "tags"?, don't have anything currently installed to play or tell. (other than mediainfo

So, before had stripped/edited your script down to only what would work, then added one metaflac line back and 2 add. options to use the metaflac "ALBUM" and "TITLE" with a -tt

It seems to have worked according to mediainfo. IF so, the add back some other 'metaflac' lines and try/add some more -tt options and see what works, doesn't ect.
```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.tak/g`

    ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
    TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`

flac -c -d "$f" - | wine takc -e -tt ALBUM="$ALBUM" -tt TITLE="$TITLE"  - "$OUTF"
done
mkdir "$ALBUM" && mv *.tak "$ALBUM"
```

scrn 1 - without -tt ..., scrn 2 with
(Note: - this is an odd example where the artist name is actually part of the track name so that's not a 'tag' mistake, was intended

---

### Post by shantiq on 2011-02-06
works like a dream    i never saw the  -tt thing in tak  :KS

thanx a lot mc4man    so final script with more tags is   (of course and i had not realized that previously but i had a der!!! realization the script will only run if all the tags one wishes to transfer are present in the flac file; otherwise the script will return an error when run through the terminal
so looking at properties of the flac file first and amending the script adding or taking away tags accordingly)



```
#!/bin/bash
for f in *.flac
do
OUTF=`echo "$f" | sed s/\.flac$/.tak/g`


    ARTIST=`metaflac "$f" --show-tag=ARTIST | sed s/.*=//g`
    ALBUM=`metaflac "$f" --show-tag=ALBUM | sed s/.*=//g`
    TITLE=`metaflac "$f" --show-tag=TITLE | sed s/.*=//g`
    DATE=`metaflac "$f" --show-tag=DATE | sed s/.*=//g`
    GENRE=`metaflac "$f" --show-tag=GENRE | sed s/.*=//g`
    TRACKNUMBER=`metaflac "$f" --show-tag=TRACKNUMBER | sed s/.*=//g`

flac -c -d "$f" - | wine takc -e -pMax  -tt ARTIST="$ARTIST"   -tt ALBUM="$ALBUM" -tt TITLE="$TITLE" 
 -tt DATE="$DATE" -tt GENRE="$GENRE"  -tt TRACKNUMBER="$TRACKNUMBER"  - "$OUTF"
done
mkdir "$ALBUM" && mv *.tak "$ALBUM"
```


( -pMax takes it up to the highest quality/compression )

---

### Post by cascade9 on 2011-02-06
> **shantiq said:**
> ( -pMax takes it up to the highest quality )

No, highest compression. 

If its lossless, quality will be the same no matter the compression level.

---

### Post by shantiq on 2011-02-06
yes cascade highest compression :KS

---

### Post by shantiq on 2011-02-11
how would i do [**this**]("http://ubuntuforums.org/showpost.php?p=10448749&postcount=1")?

---

### Post by cascade9 on 2011-02-11
You never cease suprising me shantiq. 

I can almost understand playing with .tak 'just to see' but bulk conversion? That makes no sense at all.....

---

### Post by shantiq on 2011-02-11
hi cascade   i really love that one   it is something to experiment with

av you any idea how to enter all of the folders within one folder


with sox     you can play all files by doing

```
play */./*flac
```   or ```
play */./*
``` simply entered in your Music folder


but what i want here is a similar command to allow the flac2tak.sh script to work in all of them

any offers anyone?

              =====================================

ok the answer kindly [offered by Daithif]("http://ubuntuforums.org/showpost.php?p=10448942&postcount=2") is


```
for i in */
do
 cd "$i"
 ../flac2tak.sh
 cd ..
done
```

---

