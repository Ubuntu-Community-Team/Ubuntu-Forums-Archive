---
title: "How can I rip to FLAC with LOG?"
date: 2007-06-22
forum: Multimedia Production
---

### Post by bronze on 2007-06-22
You heard me, I wonder how I can rip my CDs into FLAC files, and also get a log that confirms that the ripping went well. This used to be easy in Windows. I just used EAC and FLAC.

The log used to look something like this:
```

EAC extraction logfile from 20. June 2007, 18:00 for CD
Panic! At The Disco / A Fever You Can't Sweat Out

Used drive  : HL-DT-STRW/DVD GCC-4522B   Adapter: 2  ID: 0
Read mode   : Secure with NO C2, accurate stream, disable cache
Read offset correction : 6
Overread into Lead-In and Lead-Out : No

Used output format : C:\Program Files\FLAC\flac.exe   (User Defined Encoder)
                    192 kBit/s
                    Additional command line options : -V -8 -T "artist=%a" -T "title=%t" -T "album=%g" -T "date=%y" -T "tracknumber=%n" -T "genre=%m" %s

Other options      :
   Fill up missing offset samples with silence : Yes
   Delete leading and trailing silent blocks : No
   Installed external ASPI interface


Track  1
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\01 - Panic! At The Disco - Introduction.wav

    Pre-gap length  0:00:02.00

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 86795249
    Copy CRC 86795249
    Copy OK

Track  2
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\02 - Panic! At The Disco - The Only Difference Between Martyrdom And Suicide Is Press Coverage.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 35EED87E
    Copy CRC 35EED87E
    Copy OK

Track  3
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\03 - Panic! At The Disco - London Beckoned Songs About Money Written By Machines.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC EE72E285
    Copy CRC EE72E285
    Copy OK

Track  4
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\04 - Panic! At The Disco - Nails For Breakfast, Tacks For Snacks.wav

    Peak level 99.8 %
    Track quality 99.9 %
    Test CRC 616B30D2
    Copy CRC 616B30D2
    Copy OK

Track  5
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\05 - Panic! At The Disco - Camisado.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC B61D316E
    Copy CRC B61D316E
    Copy OK

Track  6
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\06 - Panic! At The Disco - Time To Dance.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 7F588368
    Copy CRC 7F588368
    Copy OK

Track  7
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\07 - Panic! At The Disco - Lying Is The Most Fun A Girl Can Have Without Taking Her Clothes Off.wav

    Peak level 99.8 %
    Track quality 99.9 %
    Test CRC FDD60CA7
    Copy CRC FDD60CA7
    Copy OK

Track  8
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\08 - Panic! At The Disco - Intermission.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 98D9B899
    Copy CRC 98D9B899
    Copy OK

Track  9
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\09 - Panic! At The Disco - But It's Better If You Do.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 3C90C16E
    Copy CRC 3C90C16E
    Copy OK

Track 10
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\10 - Panic! At The Disco - I Write Sins Not Tragedies.wav

    Peak level 99.8 %
    Track quality 99.9 %
    Test CRC C3065DB0
    Copy CRC C3065DB0
    Copy OK

Track 11
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\11 - Panic! At The Disco - I Constantly Thank God For Esteban.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 568B3184
    Copy CRC 568B3184
    Copy OK

Track 12
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\12 - Panic! At The Disco - There's A Good Reason These Tables Are Numbered Honey, You Just Haven't Thought Of It Yet.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC 71E35FE7
    Copy CRC 71E35FE7
    Copy OK

Track 13
    Filename C:\Program Files\Exact Audio Copy\Panic! At the Disco - A Fever You Can't Sweat Out FLAC\13 - Panic! At The Disco - Build God, Then We'll Talk.wav

    Peak level 99.8 %
    Track quality 100.0 %
    Test CRC F70CA152
    Copy CRC F70CA152
    Copy OK

No errors occured


End of status report

```

How can I get a somewhat similar result on ubuntu? Is there an application that allows this without too much hassle, or what?

---

### Post by Ross1 on 2007-06-22
cdparanoia is the best ripping program for linux bar none, just like EAC is for windows. I have a friend who has managed to get it to produce non-compliant cue sheets too :)

IIRC rubyripper is a useful frontend for cdparanoia

---

### Post by honeydew on 2007-06-23
yah rubby ripper does a bit more than cdparanoia for secure ripping with logs.. here is some good information on it..
[http://wiki.hydrogenaudio.org/index.php?title=Rubyripper](http://wiki.hydrogenaudio.org/index.php?title=Rubyripper)

---

