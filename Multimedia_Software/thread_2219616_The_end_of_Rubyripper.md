---
title: "The end of Rubyripper"
date: 2014-04-24
forum: Multimedia Software
---

### Post by Yahoé on 2014-04-24
As of 2014-03-10 the main contributor of Rubyripper as stopped working on the project which is now orphan.

What would be a good alternative to Rubyripper giving the same high quality ripping?

---

### Post by andrew.46 on 2014-04-24
> **Yahoé said:**
> As of 2014-03-10 the main contributor of Rubyripper as stopped working on the project which is now orphan.

As Bouke Woudstra has mentioned in[ his announcement ]("https://code.google.com/p/rubyripper/")the time of the audio cd is perhaps coming to an end :(.

---

### Post by shantiq on 2014-09-04
hmmmm    just saw this     anyway there was a rubyripper 0.7.0 about and it still works a treat   ...    and nowadays when Bluray carries 24/96 as audio     yes cds   look a tad prehistoric :)

to [get it]("https://code.google.com/p/rubyripper/wiki/Git") use

```
git clone https://code.google.com/p/rubyripper/
``` then cd to rubyripper folder

and enter :

```
./bin/rubyripper_cli
```

or if you are happier tinkering with gui ```
./bin/rubyripper_gtk2
```


**you may need thes**e if you have not got them on your system   ```
sudo apt-get install cd-discid ruby-gettext 
```

great choice of codecs in 0.7

[IMG]http://s20.postimg.org/4p11zjs4d/codecs_rubyripper_0_7_0.png[/IMG]


[URL="http://ubuntuforums.org/showthread.php?t=1533534&p=12757438#post12757438"]more info here
[/URL]======
and to answer the OP belatedly :)


[EAC   under Wine]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") is the obvious route or if you want an identical Linux solution [Morituri]("http://ubuntuforums.org/showthread.php?t=2219616&p=13115624#post13115624")

---

### Post by mc4man on 2014-09-04
The only issue with 0.7 is don't rip/encode to flac if using flac 1.3 as it will produce virtually nothing.
(there are some workarounds that are less than ideal.

---

### Post by shantiq on 2014-09-04
oh yes mc   good to mention that    all good apart from flac only tried wav and HE-AACv2    better check the rest   ....    will get back with findings
edit:   yes and all good apart from flac which leaves you with a 20k file;  so if flac is your poison stay away from 0.7.0   everyone else   happy trails

---

### Post by MartyBuntu on 2014-09-04
You can always rip to WAV then convert to .flac

Should be fairly lossless...

---

### Post by SuperFreak on 2014-09-04
> **mc4man said:**
> The only issue with 0.7 is don't rip/encode to flac if using flac 1.3 as it will produce virtually nothing.
(there are some workarounds that are less than ideal.

I am using Ruby Ripper .62 with Flac 1.3.02 and have not had any issues ripping tracks. I don't even see RR 0.7 on the official dl site[https://code.google.com/p/rubyripper/downloads/list]("https://code.google.com/p/rubyripper/downloads/list")

---

### Post by mc4man on 2014-09-05
> **SuperFreak said:**
> I am using Ruby Ripper .62 with Flac 1.3.02 and have not had any issues ripping tracks. I don't even see RR 0.7 on the official dl site[https://code.google.com/p/rubyripper/downloads/list]("https://code.google.com/p/rubyripper/downloads/list")
It's only here - [https://code.google.com/p/rubyripper/source/checkout](https://code.google.com/p/rubyripper/source/checkout)
by & large 0.6.x is fine, 0.7 has a different interface & some built-in support that 0.6 doesn't
I use 0.6.2 here or [latest abcde]("https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media")

---

### Post by shantiq on 2014-09-05
[SIZE=2][FONT=arial]well yes 0.6.2 is the last official release but 0.7.0 is the furthest it ever went as it is now no longer maintained still one of the best rippers for Ubuntu;  so use 6.2 if you want  flac otherwise 0.7.0 is indeed very good
[Morituri]("http://thomas.apestaart.org/morituri/trac/") is also a great one   to answer the OP   i somehow had forgotten and it will do ALL that EAC does giving you an identical log to EAC

**Basic Log**
[/FONT][/SIZE]```

Logfile created by: morituri 0.2.2
Logfile created on: Sep 05 09:01:58


Album: Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove


CDDB disc id:           090fcb11
MusicBrainz disc id:    CJONpkhnHSK_mQG55ASHXayjPrY-
MusicBrainz lookup URL: http://mm.musicbrainz.org/bare/cdlookup.html?toc=1+17+303394+150+16822+29417+52037+72715+89874+109409+121259+149724+166252+177989+194544+233244+249907+263067+277899+292022&tracks=17&id=CJONpkhnHSK_mQG55ASHXayjPrY-


Drive: vendor _NEC    , model DVD_RW ND-3550A 


Read offset correction: 48


Table of Contents:


     Track |   Start           |  Length
     ------------------------------------------------
        1  |      0 - 00:00:00 |  16672 - 03:42:22
        2  |  16672 - 03:42:22 |  12595 - 02:47:70
        3  |  29267 - 06:30:17 |  22620 - 05:01:45
        4  |  51887 - 11:31:62 |  20678 - 04:35:53
        5  |  72565 - 16:07:40 |  17159 - 03:48:59
        6  |  89724 - 19:56:24 |  19535 - 04:20:35
        7  | 109259 - 24:16:59 |  11850 - 02:38:00
        8  | 121109 - 26:54:59 |  28465 - 06:19:40
        9  | 149574 - 33:14:24 |  16528 - 03:40:28
       10  | 166102 - 36:54:52 |  11737 - 02:36:37
       11  | 177839 - 39:31:14 |  16555 - 03:40:55
       12  | 194394 - 43:11:69 |  38700 - 08:36:00
       13  | 233094 - 51:47:69 |  16663 - 03:42:13
       14  | 249757 - 55:30:07 |  13160 - 02:55:35
       15  | 262917 - 58:25:42 |  14832 - 03:17:57
       16  | 277749 - 61:43:24 |  14123 - 03:08:23
       17  | 291872 - 64:51:47 |  11372 - 02:31:47




Track  1


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/01. James Taylor - Mean Old Man.flac


  Peak level 100.0 %
  Extraction Speed (Copy) 4.1316 X
  Extraction Speed (Test) 3.5799 X
  Copy CRC 5FF11A89
  Test CRC 5FF11A89
  Copy OK
  Accurately ripped (confidence 20) [34B7CE6A]


Track  2


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/02. Brian Wilson - God Only Knows.flac


  Pre-gap: 00:00:51


  Peak level 99.8 %
  Extraction Speed (Copy) 5.1334 X
  Extraction Speed (Test) 4.5186 X
  Copy CRC 51183341
  Test CRC 51183341
  Copy OK
  Accurately ripped (confidence 20) [D415730C]


Track  3


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/03. Chinmaya Dunster & Vidroha Jamie - Chance Meeting.flac


  Peak level 98.0 %
  Extraction Speed (Copy) 6.8443 X
  Extraction Speed (Test) 3.5427 X
  Copy CRC D11B2149
  Test CRC D11B2149
  Copy OK
  Accurately ripped (confidence 20) [C9899AF2]


Track  4


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/04. Nitin Sawhney - Sunset.flac


  Pre-gap: 00:02:57


  Peak level 86.8 %
  Extraction Speed (Copy) 3.6826 X
  Extraction Speed (Test) 3.3515 X
  Copy CRC 29A03290
  Test CRC 29A03290
  Copy OK
  Accurately ripped (confidence 20) [DB323867]


Track  5


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/05. Nat King Cole - The Very Thought of You.flac


  Pre-gap: 00:01:61


  Peak level 94.3 %
  Extraction Speed (Copy) 4.9873 X
  Extraction Speed (Test) 5.3803 X
  Copy CRC 1D29E954
  Test CRC 1D29E954
  Copy OK
  Accurately ripped (confidence 19) [1DBBA4BB]


Track  6


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/06. Maria João Pires - Nocturne #2 in Eb Major.flac


  Pre-gap: 00:02:14


  Peak level 94.4 %
  Extraction Speed (Copy) 4.1782 X
  Extraction Speed (Test) 5.5263 X
  Copy CRC 10203BC9
  Test CRC 10203BC9
  Copy OK
  Accurately ripped (confidence 20) [B6C83FF3]


Track  7


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/07. Colin Hay - Going Somewhere.flac


  Pre-gap: 00:01:19


  Peak level 89.1 %
  Extraction Speed (Copy) 10.0184 X
  Extraction Speed (Test) 2.8948 X
  Copy CRC 53960F7F
  Test CRC 53960F7F
  Copy OK
  Accurately ripped (confidence 20) [D1245970]


Track  8


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/08. Paul McCartney - Temporary Secretary (Radioslave Mix).flac


  Peak level 100.0 %
  Extraction Speed (Copy) 10.8481 X
  Extraction Speed (Test) 9.6764 X
  Copy CRC E5034383
  Test CRC E5034383
  Copy OK
  Accurately ripped (confidence 20) [31194E71]


Track  9


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/09. Steadman - Carried.flac


  Pre-gap: 00:00:19


  Peak level 79.4 %
  Extraction Speed (Copy) 11.1812 X
  Extraction Speed (Test) 9.4134 X
  Copy CRC 4E436FE9
  Test CRC 4E436FE9
  Copy OK
  Accurately ripped (confidence 20) [665956BB]


Track 10


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/10. Julian Bream Consort - Galliard.flac


  Pre-gap: 00:01:52


  Peak level 100.0 %
  Extraction Speed (Copy) 11.2069 X
  Extraction Speed (Test) 6.8829 X
  Copy CRC 942FEF80
  Test CRC 942FEF80
  Copy OK
  Accurately ripped (confidence 20) [86EEBAF3]


Track 11


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/11. George Harrison - Marwa Blues.flac


  Pre-gap: 00:01:53


  Peak level 88.6 %
  Extraction Speed (Copy) 11.7702 X
  Extraction Speed (Test) 11.7633 X
  Copy CRC 7848B9DA
  Test CRC 7848B9DA
  Copy OK
  Accurately ripped (confidence 20) [BDF61CC4]


Track 12


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/12. London Symphony Orchestra - Spiral (feat. conductor - Lawrence Foster).flac


  Pre-gap: 00:01:55


  Peak level 94.1 %
  Extraction Speed (Copy) 12.2270 X
  Extraction Speed (Test) 12.1072 X
  Copy CRC 1EDA407D
  Test CRC 1EDA407D
  Copy OK
  Accurately ripped (confidence 20) [6AE307D1]


Track 13


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/13. Glenn Aitken - The Way.flac


  Pre-gap: 00:01:65


  Peak level 94.4 %
  Extraction Speed (Copy) 12.5995 X
  Extraction Speed (Test) 10.3938 X
  Copy CRC 9DC4E3C4
  Test CRC 9DC4E3C4
  Copy OK
  Accurately ripped (confidence 20) [DAD3E47B]


Track 14


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/14. Donovan - Sunny Goodge Street.flac


  Pre-gap: 00:01:59


  Peak level 74.1 %
  Extraction Speed (Copy) 12.1173 X
  Extraction Speed (Test) 9.5416 X
  Copy CRC C604E5E8
  Test CRC C604E5E8
  Copy OK
  Accurately ripped (confidence 20) [A14C97FB]


Track 15


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/15. Fred Astaire - Cheek to Cheek.flac


  Pre-gap: 00:01:45


  Peak level 89.6 %
  Extraction Speed (Copy) 12.5577 X
  Extraction Speed (Test) 12.6024 X
  Copy CRC 39E7B0C9
  Test CRC 39E7B0C9
  Copy OK
  Accurately ripped (confidence 20) [C36A4B17]


Track 16


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/16. Frank Sinatra - A Lovely Way to Spend an Evening.flac


  Pre-gap: 00:01:52


  Peak level 66.4 %
  Extraction Speed (Copy) 13.2471 X
  Extraction Speed (Test) 10.3474 X
  Copy CRC 5E76F6A7
  Test CRC 5E76F6A7
  Copy OK
  Accurately ripped (confidence 20) [0E998BD7]


Track 17


  Filename Music/compilation/Various Artists - Something For The Weekend... Paul McCartney's Glastonbury Groove/17. Paul McCartney - Calico Skies.flac


  Pre-gap: 00:01:60


  Peak level 94.4 %
  Extraction Speed (Copy) 12.8606 X
  Extraction Speed (Test) 8.7226 X
  Copy CRC FB56086A
  Test CRC FB56086A
  Copy OK

  Accurately ripped (confidence 20) [E8EAA5F3]
```[SIZE=2][FONT=arial]

[B]more detailed log
[/B]
```
morituri version 0.2.2

morituri extraction logfile from 5. September 2014, 8:51


The Radha Krishna Temple / The Radha Krsna Temple (Originally recorded in 1969)


Used drive  : TSSTcorpBDDVDW SE-506BB  TS00


Read mode                : Secure
Use cdparanoia mode      : Yes (cdparanoia III 10.2)
Defeat audio cache       : Yes
Make use of C2 pointers  : No


Read offset correction                      : 6
Overread into Lead-In and Lead-Out          : No
Fill up missing offset samples with silence : Yes
Delete leading and trailing silent blocks   : No
Null samples used in CRC calculations       : Yes
Gap Detection                               : cdrdao version 1.2.3
Gap handling                                : Appended to previous track


Used output format              : flac
GStreamer pipeline              : flacenc name=tagger quality=8
GStreamer version               : 0.10.36
GStreamer Python version        : 0.10.22
Encoder plugin version          : 0.10.31




TOC of the extracted CD


     Track |   Start  |  Length  | Start sector | End sector 
    ---------------------------------------------------------
        1  |  0:00.00 |  4:46.18 |         0    |    21467   
        2  |  4:46.18 |  3:13.30 |     21468    |    35972   
        3  |  7:59.48 |  8:27.43 |     35973    |    74040   
        4  | 16:27.16 |  3:36.65 |     74041    |    90305   
        5  | 20:04.06 |  4:05.56 |     90306    |   108736   
        6  | 24:09.62 |  8:55.14 |    108737    |   148875   
        7  | 33:05.01 |  6:07.05 |    148876    |   176405   
        8  | 39:12.06 |  4:00.18 |    176406    |   194423   
        9  | 43:12.24 |  4:59.62 |    194424    |   216910   




Track  1


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/01. The Radha Krishna Temple - Govinda.flac


     Pre-gap length  0:00:02.00


     Peak level 99.8 %
     Track quality 100.0 %
     Extraction Speed (Test) 6.9916 X
     Extraction Speed (Copy) 6.5957 X
     Test CRC 65CB462F
     Copy CRC 65CB462F
     Accurately ripped (confidence 7)  [F3BCD404]
     Copy OK


Track  2


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/02. The Radha Krishna Temple - Sri Guruvastak.flac


     Pre-gap length  0:00:02.16


     Peak level 87.7 %
     Track quality 100.0 %
     Extraction Speed (Test) 2.4112 X
     Extraction Speed (Copy) 3.9566 X
     Test CRC 20B58E3D
     Copy CRC 20B58E3D
     Accurately ripped (confidence 7)  [67CAF38F]
     Copy OK


Track  3


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/03. The Radha Krishna Temple - Bhaja Bhakata - Arotrika.flac


     Pre-gap length  0:00:01.66


     Peak level 99.8 %
     Track quality 100.0 %
     Extraction Speed (Test) 4.9203 X
     Extraction Speed (Copy) 3.1191 X
     Test CRC 350CF48B
     Copy CRC 350CF48B
     Accurately ripped (confidence 7)  [8E78A714]
     Copy OK


Track  4


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/04. The Radha Krishna Temple - Hare Krsna Mantra.flac


     Pre-gap length  0:00:02.35


     Peak level 93.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 3.3826 X
     Extraction Speed (Copy) 4.1883 X
     Test CRC E8FABF58
     Copy CRC E8FABF58
     Accurately ripped (confidence 7)  [BDA61BE6]
     Copy OK


Track  5


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/05. The Radha Krishna Temple - Sri Isopanisad.flac


     Pre-gap length  0:00:02.31


     Peak level 78.8 %
     Track quality 100.0 %
     Extraction Speed (Test) 4.5293 X
     Extraction Speed (Copy) 3.9312 X
     Test CRC 405E83A2
     Copy CRC 405E83A2
     Accurately ripped (confidence 7)  [71EBFD93]
     Copy OK


Track  6


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/06. The Radha Krishna Temple - Bhaja Hure Mana.flac


     Pre-gap length  0:00:01.39


     Peak level 58.6 %
     Track quality 100.0 %
     Extraction Speed (Test) 4.9931 X
     Extraction Speed (Copy) 4.1072 X
     Test CRC F471A0A7
     Copy CRC F471A0A7
     Accurately ripped (confidence 7)  [A4685158]
     Copy OK


Track  7


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/07. The Radha Krishna Temple - Govinda Jai Jai.flac


     Pre-gap length  0:00:02.59


     Peak level 89.0 %
     Track quality 100.0 %
     Extraction Speed (Test) 3.5393 X
     Extraction Speed (Copy) 3.4375 X
     Test CRC 2FB18E58
     Copy CRC 2FB18E58
     Accurately ripped (confidence 7)  [0C8E5454]
     Copy OK


Track  8


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/08. The Radha Krishna Temple - Prayer to the Spiritual Masters.flac


     Pre-gap length  0:00:09.59


     Peak level 74.3 %
     Track quality 100.0 %
     Extraction Speed (Test) 4.8193 X
     Extraction Speed (Copy) 5.3811 X
     Test CRC B1024871
     Copy CRC B1024871
     Accurately ripped (confidence 7)  [2EB25A86]
     Copy OK


Track  9


     Filename Music/album/The Radha Krishna Temple - The Radha Krsna Temple (Originally recorded in 1969)/09. The Radha Krishna Temple - Namaste Saraswati Devi.flac


     Pre-gap length  0:00:01.50


     Peak level 98.0 %
     Track quality 100.0 %
     Extraction Speed (Test) 5.0165 X
     Extraction Speed (Copy) 4.2931 X
     Test CRC 5A8A5485
     Copy CRC 5A8A5485
     Accurately ripped (confidence 7)  [19E03A6F]
     Copy OK




Wall clock time to rip all tracks: 23.068 minutes


All tracks accurately ripped


No errors occurred


End of status report
```


======

THIS HERE IS A HOW-TO I have adapted [Thanx to hard work of and all credits to the original writer]
I think I have covered all basics here for Ubuntu

[B]Features
[/B]
support for MusicBrainz for metadata lookup
support for AccurateRip verification
detects sample read offset of drives
performs test and copy rip
detects and rips Hidden Track One Audio (HTOA)
templates for file and directory naming
support for lossless encoding and lossy encoding or re-encoding of images
tagging using GStreamer, including embedding MusicBrainz IDs
retagging of images
for now, only a command-line client (rip) is shipped

**To Prepare** READ FIRST


Morituri will exit or may appear to crash if you try to rip a CD that is not in the MusicBrainz database. If this happens, you will have to create a MusicBrainz account, add the disc to the database on their site, and then re-attempt the rip. Alternatively, you may use the --unknown flag to the rip command, which will proceed without metadata

**Dependencies**


cdparanoia, for the actual ripping
cdrdao, for session, TOC, pregap, and ISRC extraction
GStreamer and its python bindings, for encoding
python musicbrainz2, for metadata lookup
python-cddb
pycdio, for drive identification
git-core, to fetch logger plugin


you may also need these:
```
sudo apt-get install python-musicbrainz2 libcdio-cdda1 libcdio-utils libcdio-cdda-dev python-gst0.10 python-gst0.10-dev
``` 


**Next**


[COLOR=#444444]pycdio 0.17 and python-pycdio need be added ... i took the 'alien' route to convert some fedora rpm i found on the net to debs since there are NO version readily available for Ubuntu[/COLOR]


[B][COLOR=#444444]and Fetch libcdio[/COLOR]
[/B]
```

wget https://launchpad.net/ubuntu/saucy/+source/libcdio/0.83-4/+files/libcdio_0.83.orig.tar.gz

unpack

tar -xzf libcdio_0.83.orig.tar.gz

./configure
make
sudo make install
```

[COLOR=#444444]a full house looks like this in synaptic [this was a screenshot on 13.10 but I have checked and is identical on 14.04][/COLOR]

[[IMG]http://img845.imageshack.us/img845/9360/et2b.th.png[/IMG]]("http://img845.imageshack.us/img845/9360/et2b.png")




[B]Install Morituri
[/B]

If your package manager has the latest version available, you can use it instead of downloading and installing by hand. 
Install morituri manually:


Download the latest version of morituri from [http://thomas.apestaart.org/download/morituri](http://thomas.apestaart.org/download/morituri) and verify its integrity:


```
wget http://thomas.apestaart.org/download/morituri/morituri-0.2.2.tar.bz2{,.md5}
md5sum -c morituri-0.2.2.tar.bz2.md5
tar -xjf morituri-0.2.2.tar.bz2
cd morituri-0.2.2
./configure && make
sudo make install
```

[B]morituri is now installed on your system ...

[/B]
[B]Collect drive statistics
[/B]
First, find your drive's offset if you do not already know it **if you do just skip and enter on your rip line** . This step only needs to be done the first time you rip. If you use an incorrect offset, you will not get perfect rips (or 100% logs, so this step is important)! Load a CD, but be sure to select a CD present in the AccurateRip database. Otherwise morituri will try every possible offset before giving up. Then type:


```
rip offset find
```

This will take a few minutes. When finished, it will (hopefully) display your drive's offset.

Next, you should determine if cdparanoia is capable of defeating the audio cache on your CD-Rom. Again, this step only needs to be done once. To do this, type:


```
rip drive analyze
```


If cdparanoia can defeat audio cache on your drive, morituri will be configured to do this.




**Ripping Examples**



for default drive (of course your offset depends on your drive results those are mine)
```
rip cd rip --offset 48  --output-directory=Music
``` 

for external drive
```
rip  cd -d /dev/sr1/  rip  --offset 6 --output-directory=Music
``` [/FONT][/SIZE]

---

