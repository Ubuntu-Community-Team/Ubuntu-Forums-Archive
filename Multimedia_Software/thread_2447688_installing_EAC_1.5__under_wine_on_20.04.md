---
title: "installing EAC 1.5  under wine on 20.04"
date: 2020-07-23
forum: Multimedia Software
---

### Post by shantiq on 2020-07-23
1. INSTALL WINE


2. Download latest version of [eac]("http://www.exactaudiocopy.de/en/index.php/resources/download/") 

and install then cd to wherever:

```
cd ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\)/Exact\ Audio\ Copy/       or

cd ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy /
```

or wherever you have chosen to install and run:


```
regsvr32 sql*
```
which will give you in your terminal


```

> Audio Copy$ regsvr32 sql*
> Successfully registered DLL sqlceca35.dll
> DllRegisterServer not implemented in DLL sqlcecompact35.dll
> Successfully registered DLL sqlceoledb35.dll
> DllRegisterServer not implemented in DLL sqlceqp35.dll
> DllRegisterServer not implemented in DLL sqlcese35.dll

```




IF YOUR DRIVE IS NOT SEEN BY SOFTWARE:

to remedy that [thanx mc4man]

```
sudo mkdir /media/cdrom0


``````
sudo gedit /etc/fstab

```Add this line at bottom on a new line

```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0

```save

AND


Go to:


Applications/Wine/Configure Wine/Drive/Add a new drive [ call it D or whatever is not already in use]


and do this


[When you browse Find your correct drive under Media]




[IMG]http://ubuntuforums.org/attachment.php?attachmentid=212116&d=1328473805[/IMG]




now your drive is visible!

PS:   this is what my wine install looks like in Synaptic if that is of use to some of you:
all i had to do then was to run ```
winecfg
```


[[IMG]https://i.postimg.cc/XGGVdFxZ/wine-in-synaptic.png[/IMG]]("https://postimg.cc/XGGVdFxZ")


Also this is what I have installed in wine if this helps too It seems EAC wants you to have Dotnet20 and winxp but not entirely sure as i understand very little of how wine works

```
winetricks list-installed
Executing mkdir -p /home/shan
Using winetricks 20200412 - sha256sum: 7651c93e39fcb080483c38836513bf912273a87ea97d137f6b958ed3d9628c3d with wine-5.0.1 and WINEARCH=win32
w_workaround_wine_bug-34803
winxp
dotnet40
dotnet_verifier
remove_mono
fontfix
dotnet20
```


so happy trucking with amazing latest EAC!    you can rip to 2 different formats at once now 
-- Freedb database no longer works so pick CuetoolsDB F12 [Metadata Options] for tagging




==============
Command line for Flac


```
-8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "COMMENT=%comment%" -T "BAND=%albuminterpret%" -T "ALBUMARTIST=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" %hascover%--picture="%coverfile%"%hascover% %source% -o %dest%

```

NOTA BENE: some folks said they do not need the last bit ```
-o %dest%
```

Try with and if problems try without


Command line for [Wavpack]("http://www.wavpack.com/downloads.html")


```
-hmx3 -w "Artist=%artist%" -w "Title=%title%" -w "Album=%albumtitle%" -w "Year=%year%" -w "Genre=%genre%" -w "Tracknumber=%tracknr%" -w "Performer=%albuminterpret%" -w "Composer=%composer%" %haslyrics%--tag-from-file=lyrics="%lyricsfile%"%haslyrics% -w "Albumartist=%albumartist%" -w "Discnumber=%cdnumber%" -w "Totaldiscs=%totalcds%" -w "Totaltracks=%numtracks%" -w "Comment=%comment%" %source% %dest%

```



Command line for Alac


From an [earlier thread]("https://ubuntuforums.org/showthread.php?t=2092214&p=12424257#post12424257")   

=======
Here is a sample of a log made with this setup   EAC 1.5 on 20.04 here to the Alac format

```
Exact Audio Copy V1.5 from 20. February 2020


EAC extraction logfile from 23. July 2020, 18:05


Raïna Raï / Raïna Raï


Used drive  : TSSTcorpBDDVDW SE-506BB   Adapter: 1  ID: 1


Read mode               : Secure
Utilize accurate stream : Yes
Defeat audio cache      : Yes
Make use of C2 pointers : No


Read offset correction                      : 6
Overread into Lead-In and Lead-Out          : No
Fill up missing offset samples with silence : Yes
Delete leading and trailing silent blocks   : No
Null samples used in CRC calculations       : Yes
Used interface                              : Native Win32 interface for Win NT & 2000
Gap handling                                : Appended to previous track


Used output format              : User Defined Encoder
Selected bitrate                : 896 kBit/s
Quality                         : High
Add ID3 tag                     : No
Command line compressor         : Z:\home\shan\eac-1.5 TRIAL\Exact Audio Copy\Flac\qaac.exe
Additional command line options : --no-optimize -A -i %source% -o %dest% --artist "%artist%" --title "%title%" --album "%albumtitle%" --date "%year%" --track "%tracknr%" --genre "%genre%" --band "%albumartist%" --compilation --comment "%comment%"




TOC of the extracted CD


     Track |   Start  |  Length  | Start sector | End sector 
    ---------------------------------------------------------
        1  |  0:00.00 |  4:54.42 |         0    |    22091   
        2  |  4:54.42 |  4:34.35 |     22092    |    42676   
        3  |  9:29.02 |  4:05.18 |     42677    |    61069   
        4  | 13:34.20 |  4:59.10 |     61070    |    83504   
        5  | 18:33.30 |  5:20.57 |     83505    |   107561   
        6  | 23:54.12 |  4:33.55 |    107562    |   128091   
        7  | 28:27.67 |  3:33.43 |    128092    |   144109   
        8  | 32:01.35 |  3:37.45 |    144110    |   160429   




Track  1 


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\01 Hada Chehal.wav


     Pre-gap length  0:00:02.00


     Peak level 98.0 %
     Extraction speed 1.1 X
     Track quality 100.0 %
     Copy CRC 7D4BDE08
     Accurately ripped (confidence 2)  [DB20FF85]  (AR v2)
     Copy OK


Track  2


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\02 Allah Yaali.wav


     Pre-gap length  0:00:02.17


     Peak level 98.0 %
     Extraction speed 1.3 X
     Track quality 100.0 %
     Copy CRC 6FF7AE50
     Accurately ripped (confidence 2)  [DDF0CE2F]  (AR v2)
     Copy OK


Track  3


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\03 Ouin Daouek.wav


     Pre-gap length  0:00:03.70


     Peak level 98.0 %
     Extraction speed 1.4 X
     Track quality 100.0 %
     Copy CRC 6D370618
     Accurately ripped (confidence 2)  [F178BEC1]  (AR v2)
     Copy OK


Track  4


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\04 Amarna.wav


     Pre-gap length  0:00:04.45


     Peak level 98.0 %
     Extraction speed 1.4 X
     Track quality 99.9 %
     Copy CRC 9E79C5EB
     Accurately ripped (confidence 2)  [B366463B]  (AR v2)
     Copy OK


Track  5


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\05 Mimouna.wav


     Pre-gap length  0:00:01.73


     Peak level 98.0 %
     Extraction speed 1.7 X
     Track quality 100.0 %
     Copy CRC E1075405
     Accurately ripped (confidence 2)  [8FBF46CD]  (AR v2)
     Copy OK


Track  6


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\06 Jawhar.wav


     Pre-gap length  0:00:00.45


     Peak level 98.0 %
     Extraction speed 1.8 X
     Track quality 100.0 %
     Copy CRC ACFE138C
     Accurately ripped (confidence 2)  [87654E1C]  (AR v2)
     Copy OK


Track  7


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\07 Maymi.wav


     Pre-gap length  0:00:02.55


     Peak level 98.0 %
     Extraction speed 1.8 X
     Track quality 100.0 %
     Copy CRC 9C5EC72A
     Accurately ripped (confidence 2)  [691C1F28]  (AR v2)
     Copy OK


Track  8


     Filename Z:\home\shan\Desktop\Raïna Raï - Raïna Raï 1983\08 Raïna Hak.wav


     Pre-gap length  0:00:02.53


     Peak level 98.0 %
     Extraction speed 1.9 X
     Track quality 100.0 %
     Copy CRC 42E21336
     Accurately ripped (confidence 2)  [0AEAECDB]  (AR v2)
     Copy OK




All tracks accurately ripped


No errors occurred


End of status report


---- CUETools DB Plugin V2.1.6


[CTDB TOCID: SoFLzBy7ICVULsz8QjMkuc_Apz8-] found
Submit result: SoFLzBy7ICVULsz8QjMkuc_Apz8- has been confirmed
Track | CTDB Status
  1   | (1/1) Accurately ripped
  2   | (1/1) Accurately ripped
  3   | (1/1) Accurately ripped
  4   | (1/1) Accurately ripped
  5   | (1/1) Accurately ripped
  6   | (1/1) Accurately ripped
  7   | (1/1) Accurately ripped
  8   | (1/1) Accurately ripped



```

---

### Post by shantiq on 2020-07-23
If any of you have different routes or ways to install please let us know

Thanx

===
ALSO  i collect all sorts of weird and wonderful Lossless formats most of them long gone :]

here are some of the settings if ANYONE ever wonders
The required codecs are shown here as well as the Commandline to be added (F11 in EAC)

I might add to that list if i play some more and find others ...


> 
Alac
----


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\qaac.exe
Additional command line options : --no-optimize -A -i %source% -o %dest% --artist "%artist%" --title "%title%" --album "%albumtitle%" --date "%year%" --track "%tracknr%" --genre "%genre%" --band "%albumartist%" --compilation --comment "%comment%"


Shorten
------


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\shortn32.exe
Additional command line options : %source% %dest%


la (Lossless Audio)
------


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\la.exe
Additional command line options : %source% %dest%


tak
---


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\wapet.exe
Additional command line options : %dest% -t "Artist=%artist%" -t "Title=%title%" -t "Album=%albumtitle%" -t "Year=%year%" -t "Track=%tracknr%" -t "Genre=%genre%" "C:\Program Files\TAK\takc.exe" -e -p2 %source% %dest%


tta
---


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\ttaenc.exe
Additional command line options : -e %source% -o %dest%

mp3HD
----


Command line compressor         : C:\Program Files\Exact Audio Copy\Flac\mp3hdEncoder.exe
Additional command line options : -if %source% -of %dest% %bitrate%=128k -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "COMMENT=%comment%"


---

### Post by monkeybrain20122 on 2020-07-25
Why not use k3b?

---

### Post by shantiq on 2020-07-25
> **monkeybrain20122 said:**
> Why not use k3b?


Hi there monkeybrain well EAC tries to deliver a perfect rip whereas k3b simply rips a disc once and does not match 2 rips against each other to make sure the data collected is the same twice so there can be many inaccuracies [not that I am a purist but it is a fun exercise :] ; it used to have access to FreeDB database which no longer trades after June 2020 but now has *[COLOR=#000000][FONT=sans-serif][CUETools db]("http://cue.tools/wiki/CUETools_Database") [/FONT][/COLOR]*[COLOR=#000000][FONT=sans-serif]which seems to do an even better job or at least as good a job as previously
[/FONT][/COLOR]We have/had native Linux programs which do a lot of what EAC does but the "cognoscenti" are agreed none of them quite to the same extent. All these Linux almost-as-good programs to this day although still available are no longer maintained and therefore do not grow; so EAC is still very vibrant and alive; the latest version 1.5 is really quite a sophisticated software ripper and works PERFECTLY under wine as shown in OP. It really depends what you want from a rip. I use pacpl ; ripit commandline tools when I want a quick rip; and I have used Rubyripper and Morituri at times too I love them both Morituri at one point was doing ALL that EAC does but again is no longer maintained ...


Also one can try [abcde]("https://ubuntuforums.org/showthread.php?t=2257705&highlight=abcde+andrew") a ripper Andrew on this site knows a lot about / does not do the double-rip check but excellent software in any case
[Rubyripper]("https://code.google.com/archive/p/rubyripper/wikis/Git.wiki")   very latest version that was about a while ago here is the [most recent]("https://launchpad.net/~spvkgn/+archive/ubuntu/rubyripper") PPA i find [goes only up to 19.04 so use software-properties-gtk to downscale if needed]

then you start it:
```
/usr/bin/rrip_cli

``````
/usr/bin/rrip_gui

```

worth a spin definitely :KS
nota bene: use cli the gui crashes most times in my experience and use ```
gedit ~/.config/rubyripper/settings
``` to modify codec settings; safer that way

it gives you this:

```
Rubyripper version 0.7.0rc2Website: http://code.google.com/p/rubyripper


Rubyripper extraction logfile from:
["Sat 25 Jul 09:47:03 BST 2020\r\n"]


The Velvet Underground / The Velvet Underground


Used drive     : TSSTcorp BDDVDW SE-506BB TS00   Device: /dev/sr1


Used ripper    : cdparanoia III release 10.2 (September 11, 2008)
Selected options : 


Matches required for all chunks       : 2
Matches required for erroneous chunks : 3


Read offset correction                      : 6
Overread into Lead-In and Lead-Out          : No
Fill up missing offset samples with silence : Yes
Null samples used in CRC calculations       : Yes


Used output encoder : flac 1.3.1
Selected options      : 


TOC of the extracted CD


     Track |   Start  |  Length  | Start sector | End sector 
    ---------------------------------------------------------
        1  | 00:00:00 | 04:04:32 |         0    |    18331   
        2  | 04:04:32 | 04:55:05 |     18332    |    40461   
        3  | 08:59:37 | 04:03:20 |     40462    |    58706   
        4  | 13:02:57 | 05:41:35 |     58707    |    84316   
        5  | 18:44:17 | 03:24:63 |     84317    |    99679   
        6  | 22:09:05 | 04:41:20 |     99680    |   120774   
        7  | 26:50:25 | 04:08:67 |    120775    |   139441   
        8  | 30:59:17 | 02:00:00 |    139442    |   148441   
        9  | 32:59:17 | 08:56:00 |    148442    |   188641   
       10  | 41:55:17 | 02:07:58 |    188642    |   198224   


Track  1


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/01 - Candy Says.flac


     Trial 1: 85 seconds (2.86x)
     Trial 2: 55 seconds (4.41x)
     All chunks matched!


     Peak level 99.8 %
     Trial 1 (Copy) CRC 5B51A285
     Trial 2 (Test) CRC 5B51A285
     Copy OK


     Copy MD5: 03c2bafc9fc7c18feb4125752ff21f0d


Track  2


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/02 - What Goes On.flac


     Trial 1: 58 seconds (5.00x)
     Trial 2: 92 seconds (3.20x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC A5F64B08
     Trial 2 (Test) CRC A5F64B08
     Copy OK


     Copy MD5: 129db66a473774649f222ed5192e07bb


Track  3


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/03 - Some Kinda Love.flac


     Trial 1: 76 seconds (3.18x)
     Trial 2: 45 seconds (5.38x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC B93A0F3B
     Trial 2 (Test) CRC B93A0F3B
     Copy OK


     Copy MD5: f4188766b2873f8fc649a9efd9768035


Track  4


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/04 - Pale Blue Eyes.flac


     Trial 1: 59 seconds (5.76x)
     Trial 2: 83 seconds (4.09x)
     All chunks matched!


     Peak level 99.8 %
     Trial 1 (Copy) CRC 7816CD1E
     Trial 2 (Test) CRC 7816CD1E
     Copy OK


     Copy MD5: 4b6212bc654b369dec332ef47bdb532a


Track  5


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/05 - Jesus.flac


     Trial 1: 38 seconds (5.38x)
     Trial 2: 32 seconds (6.39x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC E1093769
     Trial 2 (Test) CRC E1093769
     Copy OK


     Copy MD5: 346836b82278f568d106de978691b136


Track  6


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/06 - Beginning to See the Light.flac


     Trial 1: 41 seconds (6.75x)
     Trial 2: 41 seconds (6.74x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC AD52948A
     Trial 2 (Test) CRC AD52948A
     Copy OK


     Copy MD5: f3888d6c610f9a9c2b82cdbab0a91db1


Track  7


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/07 - I'm Set Free.flac


     Trial 1: 35 seconds (7.07x)
     Trial 2: 35 seconds (7.07x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC 2B05E2E6
     Trial 2 (Test) CRC 2B05E2E6
     Copy OK


     Copy MD5: ae359cc00fc50a2aa8e0bda5d5d32190


Track  8


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/08 - That's the Story of My Life.flac


     Trial 1: 17 seconds (6.92x)
     Trial 2: 17 seconds (6.91x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC 01ED3949
     Trial 2 (Test) CRC 01ED3949
     Copy OK


     Copy MD5: 610920faa84e4d79793ff0cc5b6d5342


Track  9


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/09 - The Murder Mystery.flac


     Trial 1: 99 seconds (5.38x)
     Trial 2: 114 seconds (4.70x)
     All chunks matched!


     Peak level 99.7 %
     Trial 1 (Copy) CRC 9C9B81D8
     Trial 2 (Test) CRC 9C9B81D8
     Copy OK


     Copy MD5: 67e1211efd3af0a543d7e08b913a3bdd


Track 10


     File name /home/shan/flac/The Velvet Underground (2009) The Velvet Underground/10 - Afterhours.flac


     Trial 1: 21 seconds (5.88x)
     Trial 2: 18 seconds (6.94x)
     All chunks matched!


     Peak level 99.5 %
     Trial 1 (Copy) CRC 905FAC55
     Trial 2 (Test) CRC 905FAC55
     Copy OK


     Copy MD5: 0e2a7e76fa27e456e1d51a8cf7130b76


No errors occurred



```


===
Morituri      stopped in 2014
If you check here you will see it can give a [rip similar ]("https://ubuntuforums.org/showthread.php?t=2219616&p=13115624#post13115624")to EAC


but you still can get it from Thomas's [site]("http://thomas.apestaart.org/download/morituri/")

```
wget http://thomas.apestaart.org/download/morituri/morituri-0.2.3.tar.bz2

```

OK

There are many threads on this site to help with installing/ using either

Also for me EAC apart from being truly excellent has the added bonus of being a piece of free software from a different OS which functions brilliantly here under wine; I see no reason not to play with it as well as as Rubyripper and Morituri

EDIT: played around a bit with RR today and very buggy always was too .
morituri  installs on 20.04 ; it is a bit of a performance and will link a howto [further down]("https://ubuntuforums.org/showthread.php?t=2447688&p=13975594#post13975594") this thread

---

### Post by monkeybrain20122 on 2020-07-25
Hi, I am not a big CD ripper and other than a 10 year old laptop I am going to give away my laptops don't even come with a CD/DVD drive, maybe that's why those Linux CD ripping software is no longer developed, CD are  not as common as they used to be (and video DVDs are going the way of the Dodo) I am only asking out of curiosity, thanks for the detailed explanation though.

---

### Post by Holger_Gehrke on 2020-07-25
Well, one alternative that still is in development is fre:ac ([https://freac.org](https://freac.org)). That had a release on June 20th. It's not in the repos, but a snap, a flatpak and an AppImage are available.

Holger

---

### Post by shantiq on 2020-07-26
> **Holger_Gehrke said:**
> Well, one alternative that still is in development is fre:ac ([https://freac.org](https://freac.org)). That had a release on June 20th. It's not in the repos, but a snap, a flatpak and an AppImage are available.

Holger

thanx Holger not many rippers still handle [Bonk]("http://www.logarithmic.net/pfh/bonk")[COLOR=#000000][FONT=verdana] format 

[/FONT][/COLOR]will have a look soon

---

### Post by Holger_Gehrke on 2020-07-26
> **shantiq said:**
> thanx Holger not many rippers still handle [Bonk]("http://www.logarithmic.net/pfh/bonk")[COLOR=#000000][FONT=verdana] format [/FONT][/COLOR]

... and I don't think this one does either. The 'Welcome'-posting at the top of the site which mentions bonk is from 2010 , the version I have (from December 2018) doesn't seem to handle Bonk any more. On the other hand there is a directory named 'codecs', perhaps if you drop the right shared object into that or an executable converter into 'codecs/cmdline' ...

Holger

---

### Post by shantiq on 2020-07-27
ha ok tried it now 
very nice did an album to alac and quick and smooth; of course it does not do what EAC or Rubyripper do [double check] but excellent software
Thanx will keep it on my machine

PS   also very kind on the disc drive something RR is not :]

Let's u rip to HE-AACv2 a format which altho it is hugely small still decent sound and an album UNDER 25MB as a single file too :KS would enjoin anyone to try [HE-AACv2]("https://en.wikipedia.org/wiki/High-Efficiency_Advanced_Audio_Coding")

```
mediainfo Bonzo\ Dog\ Band\ -\ The\ Doughnut\ In\ Granny\'s\ Greenhouse\ \(2007\ release\).m4a General
Complete name                            : Bonzo Dog Band - The Doughnut In Granny's Greenhouse (2007 release).m4a
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42 (mp42/isom)
File size                                : 24.5 MiB
Duration                                 : 52 min 49 s
Overall bit rate mode                    : Variable
Overall bit rate                         : 64.7 kb/s
Album                                    : The Doughnut In Granny's Greenhouse (2007 release)
Track name                               : The Doughnut In Granny's Greenhouse (2007 release)
Performer                                : Bonzo Dog Band
Genre                                    : Rock
ContentType                              : Music
Recorded date                            : 2007
Encoded date                             : UTC 2020-07-27 10:06:47
Tagged date                              : UTC 2020-07-27 10:10:39
Writing application                      : fre:ac v1.1.2
Comment                                  : fre:ac - free audio converter <https://www.freac.org/>


Audio
ID                                       : 1
Format                                   : AAC LC SBR PS
Format/Info                              : Advanced Audio Codec Low Complexity with Spectral Band Replication and Parametric Stereo
Commercial name                          : HE-AACv2
Format settings                          : NBC
Codec ID                                 : mp4a-40-29
Duration                                 : 52 min 49 s
Bit rate mode                            : Variable
Bit rate                                 : 64.0 kb/s
Maximum bit rate                         : 66.1 kb/s
Channel(s)                               : 2 channels
Channel layout                           : C
Sampling rate                            : 44.1 kHz
Frame rate                               : 21.533 FPS (2048 SPF)
Compression mode                         : Lossy
Stream size                              : 24.2 MiB (99%)
Encoded date                             : UTC 2020-07-27 10:06:47
Tagged date                              : UTC 2020-07-27 10:10:39
Menus                                    : 2


Menu
ID                                       : 2
Codec ID                                 : text
Duration                                 : 52 min 49 s
Encoded date                             : UTC 2020-07-27 10:10:39
Tagged date                              : UTC 2020-07-27 10:10:39
Menu For                                 : 1
00:00:00.000                             : We Are Normal
00:04:49.707                             : Postcard
00:09:13.587                             : Beautiful Zelda
00:11:39.054                             : Can Blue Men Sing The Whites
00:14:28.734                             : Hello Mabel
00:17:14.761                             : Karma Sutra
00:17:55.748                             : Humanoid Boogie
00:20:59.508                             : The Trouser Press
00:23:18.095                             : My Pink Half Of The Drainpipe
00:26:52.148                             : Rockaliser Baby
00:30:24.441                             : Rhinocratic Oaths
00:33:46.961                             : Eleven Mustachioed Daughters
00:38:46.441                             : Blue Suede Shoes (Previously Unreleased)
00:40:24.508                             : Bang Bang (Previously Unreleased)
00:43:04.561                             : Alley Oop (Girls Version)
00:45:36.734                             : Canyons Of Your Mind (Single Version)
00:48:39.267                             : Mr Apollo (German Version)



```

---

### Post by Holger_Gehrke on 2020-07-27
All the better rippers on Linux (including fre:ac) use cdparanoia to do the actual reading. Take a look at the [FAQ]("https://xiph.org/paranoia/faq.html") for that to get an idea of what it does and how it stacks up against EAC ...

Holger

---

### Post by shantiq on 2020-07-28
TO INSTALL MORITURI ON 20.04



Before anything:


Install GStreamer
Run the following command:

```
sudo apt-get install libgstreamer1.0-0 gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly gstreamer1.0-libav gstreamer1.0-doc gstreamer1.0-tools gstreamer1.0-x gstreamer1.0-alsa gstreamer1.0-gl gstreamer1.0-gtk3 gstreamer1.0-qt5 gstreamer1.0-pulseaudio
```

Dependencies you must have (of course it depends on what you already have installed you may need more or less these are musts)

python-musicbrainz &#9989; libcdio-cdda1&#9989; libcdio-paranoia1&#9989; libcdio-utils&#9989; libcdio-cdda-dev&#9989; python-gst0.10&#9989; python-gst0.10-dev&#9989; python-cddb&#9989;

To get those:

```
mkdir ~/Desktop/debs
```


```
cd ~/Desktop/debs
```


Copy list below Make a txt file and save to ~/Desktop/debs


```


http://mirrors.kernel.org/ubuntu/pool/universe/m/musicbrainzngs/python-musicbrainzngs_0.6-3_all.deb
http://mirrors.kernel.org/ubuntu/pool/main/libc/libcdio/libcdio-cdda1_0.83-4.2ubuntu1_amd64.deb
http://mirrors.kernel.org/ubuntu/pool/main/libc/libcdio/libcdio-paranoia1_0.83-4.2ubuntu1_amd64.deb
http://launchpadlibrarian.net/235409607/libcdio-utils_0.83-4.2ubuntu1_amd64.deb
http://mirrors.kernel.org/ubuntu/pool/universe/libc/libcdio/libcdio-cdda-dev_0.83-4.2ubuntu1_amd64.deb
http://mirrors.kernel.org/ubuntu/pool/universe/g/gst0.10-python/python-gst0.10_0.10.22-3ubuntu3_amd64.deb
http://mirrors.kernel.org/ubuntu/pool/universe/g/gst0.10-python/python-gst0.10-dev_0.10.22-3ubuntu3_amd64.deb
http://mirrors.kernel.org/ubuntu/pool/universe/p/python-cddb/python-cddb_1.4-5.3_amd64.deb
http://launchpadlibrarian.net/188238106/morituri_0.2.3-1_all.deb
```


Then inside folder run:
```
wget -i debs.txt
```


All dependencies and morituri deb downloaded &#9989;

Now install:

```
sudo dpkg -i morituri_0.2.3-1_all.deb
``` 

if all &#9989; you can now remove the deb folder :   ```
sudo rm -rf ~/Desktop/debs
```

==========

If all good now follow these instructions to configure your cd drive etc etc

```
rip offset find
```

This will take a few minutes. When finished, it will (hopefully) display your drive's offset.
Next, you should determine if cdparanoia is capable of defeating the audio cache on your CD-Rom. Again, this step only needs to be done once. To do this, type:

```
rip drive analyze
```

If cdparanoia can defeat audio cache on your drive, morituri will be configured to do this.

[SIZE=1][I]Ripping Examples:
[/I][/SIZE]

for default drive (of course your offset depends on your drive results those are mine)
```
rip cd rip --offset 48  --output-directory=Music
```
for external drive
```
rip  cd -d /dev/sr1/  rip  --offset 6 --output-directory=Music
```


=======
Be aware of the fact that morituri uses musicbrainz and if your disc is not in their dababase it will be ejected ; then you have to go to musicbrainz and register it; this can take an hour or so :]   so yea   that is not a great feature but overall a fine program and does ALMOST all that EAC does
=======


Log appears thus:

```
time rip  cd -d /dev/sr1/  rip  --offset 6 --output-directory=Music
Checking device /dev/sr1
eject: CD-ROM tray close command failed: Input/output error
CDDB disc id: 7d09ce09                        
MusicBrainz disc id iH1svwwchawPUyFXCZsBhuLDSwo-
MusicBrainz lookup URL http://mm.musicbrainz.org/bare/cdlookup.html?toc=1+9+188432+150+14567+30695+58267+73147+91212+130912+145027+160262&tracks=9&id=iH1svwwchawPUyFXCZsBhuLDSwo-
Disc duration: 00:41:50.426, 9 audio tracks


Matching releases:


Artist  : David Bowie
Title   : Christiane F.: Wir Kinder vom Bahnhof Zoo
Duration: 00:41:49.330
URL     : http://musicbrainz.org/release/9403f03a-e92c-3f32-b11d-8f696ad0df19
Release : 9403f03a-e92c-3f32-b11d-8f696ad0df19
Type    : Soundtrack


Creating output directory Music/soundtrack/David Bowie - Christiane F. - Wir Kinder vom Bahnhof Zoo
Ripping track 1 of 9: 01. David Bowie - V&#8208;2 Schneider.flac
Checksums match for track 1                        
Peak level: 98.70 %
Rip quality: 100.00 %
Ripping track 2 of 9: 02. David Bowie - TVC15 (single edit).flac
Checksums match for track 2                        
Peak level: 99.02 %
Rip quality: 100.00 %
Ripping track 3 of 9: 03. David Bowie - _Heroes_ - _Helden_.flac
Checksums match for track 3                        
Peak level: 97.75 %
Rip quality: 100.00 %
Ripping track 4 of 9: 04. David Bowie - Boys Keep Swinging.flac
Checksums match for track 4                        
Peak level: 97.94 %
Rip quality: 100.00 %
Ripping track 5 of 9: 05. David Bowie - Sense of Doubt.flac
Checksums match for track 5                        
Peak level: 89.96 %
Rip quality: 100.00 %
Ripping track 6 of 9: 06. David Bowie - Station to Station.flac
Checksums match for track 6                        
Peak level: 95.41 %
Rip quality: 98.28 %
Ripping track 7 of 9: 07. David Bowie - Look Back in Anger.flac
Checksums match for track 7                        
Peak level: 96.60 %
Rip quality: 100.00 %
Ripping track 8 of 9: 08. David Bowie - Stay (single edit).flac
Checksums match for track 8                        
Peak level: 97.20 %
Rip quality: 100.00 %
Ripping track 9 of 9: 09. David Bowie - Warszawa.flac
Checksums match for track 9                        
Peak level: 89.67 %
Rip quality: 100.00 %
AccurateRip URL http://www.accuraterip.com/accuraterip/3/2/9/dBAR-009-000d9923-0065a949-7d09ce09.bin
9 AccurateRip reponses found
Track  1: rip accurate     (confidence  31 of  83) [6aeb7671], DB [6aeb7671]
Track  2: rip accurate     (confidence  31 of  83) [6ca06de8], DB [6ca06de8]
Track  3: rip accurate     (confidence  32 of  83) [4ea82502], DB [4ea82502]
Track  4: rip accurate     (confidence  31 of  83) [98c7967d], DB [98c7967d]
Track  5: rip accurate     (confidence  31 of  83) [b8a71cbb], DB [b8a71cbb]
Track  6: rip accurate     (confidence  30 of  83) [e6a156ab], DB [e6a156ab]
Track  7: rip accurate     (confidence  31 of  83) [8f34fe32], DB [8f34fe32]
Track  8: rip accurate     (confidence  31 of  83) [56675116], DB [56675116]
Track  9: rip accurate     (confidence  31 of  83) [cb191a15], DB [cb191a15]


real    23m42.669s
user    1m57.634s
sys    0m35.309s

```

---

