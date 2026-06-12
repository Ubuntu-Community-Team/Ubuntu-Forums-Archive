---
title: "installing EAC  1.0 beta 3 under wine"
date: 2012-12-07
forum: Multimedia Software
---

### Post by shantiq on 2012-12-07
**1.**  INSTALL WINE

**2.**  Download latest version of [**eac**]("http://www.exactaudiocopy.de/en/index.php/resources/download/") and install to ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\

**then**   run

> 

cd ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\)/Exact\ Audio\ Copy/
**regsvr32 sql***

or if not using x86

> cd  ~/.wine/drive_c/Program\ Files/Exact\ Audio\ Copy / 
regsvr32 sql*
 
which will give you in your terminal

>  ~/.wine/dosdevices/c:/Program Files/Exact
> Audio Copy$ regsvr32 sql*
> Successfully registered DLL sqlceca35.dll
> DllRegisterServer not implemented in DLL sqlcecompact35.dll
> Successfully registered DLL sqlceoledb35.dll
> DllRegisterServer not implemented in DLL sqlceqp35.dll
> DllRegisterServer not implemented in DLL sqlcese35.dll**3.**  ** At this point **   1.0 will appear but may not see your cd drive


to remedy that [thanx [**mc4man**]("http://ubuntuforums.org/showpost.php?p=11666541&postcount=6")]


```
sudo mkdir /media/cdrom0
``````
sudo gedit /etc/fstab
```Add this line at bottom on a new line

```
/dev/sr0   /media/cdrom0   udf,iso9660 user,noauto,exec   0 0
```save


**AND**

Go to:

Applications/Wine/Configure Wine/Drive/Add a new drive [ call it D or whatever is not already in use]  

  [B]and do this 
[/B]
[When you browse Find your correct drive under Media]


  [IMG]http://ubuntuforums.org/attachment.php?attachmentid=212116&d=1328473805[/IMG]



**now your drive is visible!**    


so happy trucking with amazing latest EAC  does picture now and Log checksum [whatever that is]


**PS**   settings for flac have all changed

> -8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T "COMMENT=%comment%" %source%

if you use earlier version than  1.3 [09-2016] you will need to use
> -8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T  "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T  "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%"  %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T  "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T  "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T  "COMMENT=%comment%" %source% -o %dest% 


so for wavpack now use [with [appropriate exe]("http://www.wavpack.com/downloads.html") of course]

 > -hmx3 -w "Artist=%artist%" -w "Title=%title%" -w "Album=%albumtitle%" -w "Year=%year%" -w "Genre=%genre%" -w "Tracknumber=%tracknr%" -w "Performer=%albuminterpret%" -w "Composer=%composer%" %haslyrics%--tag-from-file=lyrics="%lyricsfile%"%haslyrics% -w "Albumartist=%albumartist%" -w "Discnumber=%cdnumber%" -w "Totaldiscs=%totalcds%" -w "Totaltracks=%numtracks%" -w "Comment=%comment%"  %source% %dest%  

for ape

download [Monkeyaudio]("http://www.monkeysaudio.com/download.html") and place in home/yourname/.wine/drive_c/Program Files (x86)/

then tick the following:
[[IMG]https://s20.postimg.org/n58ueqkih/image.png[/IMG]]("https://postimg.org/image/n58ueqkih/")


 tta becomes   [tick add id3 tags for tagging]

 > -e %source% -o %dest%tak becomes

[FONT=Tahoma]Tak  requires 2 codecs wapet.exe which writes the tags and that you already have for ape and takc.exe [/FONT]

>  %dest% -t "Artist=%artist%" -t "Title=%title%" -t "CD artist=%albumartist%" -t "ALBUM=%albumtitle%" -t "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -t "Year=%year%" -t "Genre=%genre%" -t "TRACKNUMBER=%tracknr%" -t "TOTALTRACKS=%numtracks%" -t "COMMENT=%comment%" "C:\Program Files (x86)\Exact Audio Copy\Flac\Takc.exe" -e -p2 %source% %dest%full info on plugins attached

---

### Post by kimme on 2012-12-15
Thanks for this guide.

---

### Post by shantiq on 2012-12-27
finally cracked how to do EAC alac rip under 1.0.3 under Wine




the code line is [with all trimmings]




> --no-optimize -A -i  %source%  -o  %dest%   --artist "%artist%" --title "%title%" --album "%albumtitle%"  --date "%year%"  --track "%tracknr%" --genre "%genre%"   --band "%albumartist%"  --compilation  --comment "%comment%"




place the [COLOR=#b22222]**entire qaac folder**[/COLOR] from [**here**]("http://audiophilesoft.ru/commandline/qaac/qaac_2.46_CoreAudioToolbox_7.9.9.4.7z") into flac folder in EAC and use qaac.exe





[CENTER][IMG]http://i51.fastpic.ru/big/2012/1229/63/52f0cf2b89bb03cf5ec3a16779279c63.png[/IMG][/CENTER]


if you want an aac/m4a [330kbps about] with the same encoder run


>   -V 127 -i  %source%  -o  %dest%   --artist "%artist%" --title "%title%" --album "%albumtitle%"  --date "%year%"  --track "%tracknr%" --genre "%genre%"   --band "%albumartist%"  --compilation  --comment "%comment%" 



**PS**    since EAC is not linux but windows under Wine i have designed a more comprehensive guide and put it [**here**]("http://www.hydrogenaudio.org/forums/index.php?showtopic=98556")   you may want to check there for updates or improvements

---

### Post by Graham C Williams on 2013-01-02
Many Many Thanks. EAC has been the best for some years..

Graham.;)

---

### Post by cottfcfan on 2013-01-02
Being a bit of an Audiophile, I have been following this thread, & have used EAC under Windows 7.
Under Ubuntu though I use RubyRipper to rip to FLAC/mp3/aac/mp3HD/ogg, and I honestly can't tell any difference in quality.
What advantages are there (if any) to using EAC over a linux native ripper?

---

### Post by shantiq on 2013-01-02
ok Cott and trust i am no genius when it comes to these matters but what i am told and the reason why EAC is still seen as "higher" than RR and i too use RR a lot and love is that EAC gives a more accurate check of the 2 rips one against the other....   Apparently RR does not do that thoroughly at all in comparison [check both rips are identical]

:KS   all i have got on the matter...   no doubt there are people on the forum who can [and hopefully will] enlighten us further

1.0.3 on 12.04 runs better than on any previous combination i have experienced; it is really a marvel [picture now as well] and since totally free to all i see it as bone fide Linux if you see what i mean... [not open source] but i would not dare [or know how to]tinker with any of it anyway as it is pretty much perfect

RR is the best linux we have and it is pretty good but a slightly pale cousin to EAC    there is also a program called [Morituri]("http://thomas.apestaart.org/morituri/trac/") which can do all that EAC does but requires high knowledge to configure so it is as good as EAC

---

### Post by jeffsf on 2013-01-11
> **cottfcfan said:**
> What advantages are there (if any) to using EAC over a linux native ripper?

Between EAC's own methods, and being able to compare with AccurateRip and CUETools databases, you have a very high confidence in knowing the bits are the same as on the original CD. This goes past sonic quality, as bad PCM samples can cause transients that are painful to both ears and speakers/IEMs. (Audio players typically mask bad data, usually causing a drop-out, rather than a potentially damaging spike.)

Access to the GD3 and CUETools databases, make tags a lot more reliable and keep major re-tagging to a minimum.

CUETools' CUERipper is very good too, runs under VirtualBox, but doesn't have the GD3 access. CUETools itself is said to run under Mono, but I haven't had much success there.

Unfortunately, I'm not getting the various .dll plugins for EAC (CUETools, GD3, for example) to be recognized under Wine...

---

### Post by shantiq on 2013-01-11
There is a new codec which will give you a very high-grade aac/m4a.  It is called fdkaac; and i have placed it [**here** [Ubuntu cloud]]("http://ubuntuone.com/7DlYLvnmbo12FOeHHqbcdL")

to produce a small size but high audio quality file in HE-AACv2 use

> -b 38k -a 1 -p 29 --ignore-length %source% -o %dest% --artist "%artist%" --title "%title%" --album "%albumtitle%" 
--date "%year%" --genre "%genre%" --comment "%comment%" --composer "%albumcomposer%"



if you want a "normal aac" use

> -m 5 -a 1 -p 2 --ignore-length %source% -o %dest% --artist "%artist%" --title "%title%" --album "%albumtitle%" 
--date "%year%" --genre "%genre%" --comment "%comment%" --composer "%albumcomposer%"


run```
 wine fdkaac -h 
``` to find more settings

---

### Post by skralljt on 2013-01-27
In case anybody else is having trouble with this as I am and can't see Shantiq's pictures such as after the imperative, "DO THIS!" you have to log in to see pictures attached via the forum software.  He is just configuring the drive as a cdrom in wine.  Also fwiw it did not work for me.  Neither did going back to eac .99 pre beta.

edit: actually it did finally work.  As with many linux repairs, many bandaids were applied so it is hard to say for sure which one fixed the issue but no doubt Shantiq's method is the one that worked.  Thank you Shantiq!

---

### Post by shantiq on 2013-01-27
good you got there skralljt  it is a bit of a performance but still worth it as it does much other rippers can only dream of doing:KS

---

### Post by shantiq on 2013-03-18
just to say it also installs on 13.04 with these [instructions]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385")

---

### Post by feelfreetoblameme on 2013-04-07
Thanks for this, definitely a great find. I'm relatively new to Linux/Ubuntu so appreciate any patience with silly questions I might have. I'm trying to get EAC 1 beta 3 to run under Wine on Ubuntu 12.04. For some reason, the installer would not go under Wine, I would always get the NSIS error. I've tried to Google some solutions to that without any luck. I reinstalled Wine and all the packages that I read about but nothing changed. I succumbed to what may have been an easier solution, PlayOnLinux and this time, the installer worked like a charm. At launch, however, I got the same exception error that was solved in this thread. I tried the registering DLL trick as outlined here in the directories where PlayOnLinux installed EAC but I always got the message that the dll failed to load. I'm guessing that the virtual directory structure of PlayOnLinux is somehow interfering with Wine's regsvr32 command, but not sure. I also tried going through the PlayonLinux console and despite some error messages, it did say that it successfully registered the DLL but unfortunately the program still crashed. If Wine would just run the installer I wouldn't have to mess with  PlayOnLinux but if anyone can help with either problem, that would be  highly appreciated. Perhaps I did something wrong in the Wine install?

By the way, I'm running Ubuntu on a very old Compaq Pentium 4 desktop. Sometimes a little sluggish but overall running fine. Thanks in advance for any help. I noticed that PlayonLinux now officially supports Mp3Tag, another Windows favourite, so perhaps EAC is coming soon....

---

### Post by shantiq on 2013-04-07
well [SIZE=2]feelfreetoblameme [cool moniker [/SIZE]:)][SIZE=2]  personally readin what you have written i would remove and purge PlayonLinux  [it probably i am guessing places bits and pieces in different places] if you do not use it for other software and start again from scratch with earlier[ guide]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385")

I am not saying it will work for absolutely all setups on all types of machine   but with the latest version of wine you should be fine here [i first did this on 12.04 now using it on 13.04]

best of luck and please tell us how you fare[/SIZE]

---

### Post by feelfreetoblameme on 2013-04-07
Thanks for the quick reply (and the compliment!). I think I will probably end up wiping this 12.04 install altogether and start from scratch to try and solve the NSIS error. Redo Wine and go from there without messing with PlayonLinux. I'll post back, see if it works. Great guide on Hydrogen audio, by the way, thanks for that too.

---

### Post by -jay- on 2013-06-22
thanks your guide works wonders under 13.04

---

### Post by shantiq on 2013-10-30
if any of you want to install EAC on Saucy   you will likely require [this]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385")

---

### Post by lozanoje on 2013-12-11
Just my experience: Under Mint 16 x64, I have to update wine to 1.7 (development) using the oficial ppa.
 
Using the stable version 1.4.1, i was not able to install EAC 1b3.

Now, with 1.7 it works.

---

### Post by shantiq on 2014-04-09
Then i got a disc i wanted to back up in Flac for my personal use on my computer and found that my eight-year-old computer's cd drive NEC    DVD_RW ND-3550A

could not handle it; so since I had always wanted to add a bluray external to my setup I just did that and got a spanking new [COLOR=#000000][FONT=verdana]Samsung SE-506BB

So far very nice...

But EAC only seems to want and see the 'in house' piece of kit

Then readin around it appears that one needs to go to the Interface section in EAC options and click on ASPI instead of the default Native
And voila!   [the Note is probably from earlier times no longer an issue ASPI is in modern versions it seems]


see here:

[/FONT][/COLOR][IMG]http://s20.postimg.org/nfn80dlb1/EAC_options_Interface.png[/IMG]

---

### Post by Yellow Pasque on 2014-04-09
I think it's very interesting to read this (especially the table at the end): [https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip](https://thomas.apestaart.org/thomas/trac/wiki/DAD/Rip)

That said, I'm not about to redo my CD collection with EAC (originally used Audex, which uses cdparanoia). I really doubt I'll be able to hear any difference.

---

### Post by shantiq on 2014-04-09
:KS:KS:KS [[COLOR=#000000]Temüjin[/COLOR]]("http://ubuntuforums.org/member.php?u=327594")[COLOR=#000000] i hear no difference myself   i just like to play ::]]  but i do hear difference between lossless and lossy since i play all computer music through stereo  **PS** Morituri can now do ALL that EAC does but you need to be a Python coder to get all the settings right .... ouch ,,,, but see even more info in the log


example

[/COLOR]```
morituri version 0.2.2

morituri extraction logfile from 10. April 2014, 12:37


Neneh Cherry / Blank Project


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
        1  |  0:00.00 |  3:28.66 |         0    |    15665   
        2  |  3:28.66 |  4:04.71 |     15666    |    34036   
        3  |  7:33.62 |  3:57.02 |     34037    |    51813   
        4  | 11:30.64 |  4:18.38 |     51814    |    71201   
        5  | 15:49.27 |  5:46.63 |     71202    |    97214   
        6  | 21:36.15 |  4:10.23 |     97215    |   115987   
        7  | 25:46.38 |  5:20.72 |    115988    |   140059   
        8  | 31:07.35 |  5:15.21 |    140060    |   163705   
        9  | 36:22.56 |  5:11.73 |    163706    |   187103   
       10  | 41:34.54 |  7:20.66 |    187104    |   220169   




Track  1


     Filename Music/album/Neneh Cherry - Blank Project/01. Neneh Cherry - Across the Water.flac


     Pre-gap length  0:00:02.00


     Peak level 98.8 %
     Track quality 100.0 %
     Extraction Speed (Test) 1.7873 X
     Extraction Speed (Copy) 3.0328 X
     Test CRC B3B859FA
     Copy CRC B3B859FA
     Track not present in AccurateRip database
     Copy OK


Track  2


     Filename Music/album/Neneh Cherry - Blank Project/02. Neneh Cherry - Blank Project.flac


     Peak level 99.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 3.8452 X
     Extraction Speed (Copy) 3.8798 X
     Test CRC A8451C13
     Copy CRC A8451C13
     Track not present in AccurateRip database
     Copy OK


Track  3


     Filename Music/album/Neneh Cherry - Blank Project/03. Neneh Cherry - Naked.flac


     Peak level 99.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 2.4713 X
     Extraction Speed (Copy) 4.2585 X
     Test CRC 0F039D1E
     Copy CRC 0F039D1E
     Track not present in AccurateRip database
     Copy OK


Track  4


     Filename Music/album/Neneh Cherry - Blank Project/04. Neneh Cherry - Spit Three Times.flac


     Peak level 99.9 %
     Track quality 99.1 %
     Extraction Speed (Test) 3.5870 X
     Extraction Speed (Copy) 4.8406 X
     Test CRC BF4EED51
     Copy CRC BF4EED51
     Track not present in AccurateRip database
     Copy OK


Track  5


     Filename Music/album/Neneh Cherry - Blank Project/05. Neneh Cherry - Weightless.flac


     Peak level 99.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 3.3682 X
     Extraction Speed (Copy) 3.8593 X
     Test CRC D808CF97
     Copy CRC D808CF97
     Track not present in AccurateRip database
     Copy OK


Track  6


     Filename Music/album/Neneh Cherry - Blank Project/06. Neneh Cherry - Cynical.flac


     Peak level 99.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 4.4022 X
     Extraction Speed (Copy) 4.7740 X
     Test CRC 32E466AF
     Copy CRC 32E466AF
     Track not present in AccurateRip database
     Copy OK


Track  7


     Filename Music/album/Neneh Cherry - Blank Project/07. Neneh Cherry - 422.flac


     Peak level 99.9 %
     Track quality 100.0 %
     Extraction Speed (Test) 5.5024 X
     Extraction Speed (Copy) 4.5968 X
     Test CRC 279A5E64
     Copy CRC 279A5E64
     Track not present in AccurateRip database
     Copy OK


Track  8


     Filename Music/album/Neneh Cherry - Blank Project/08. Neneh Cherry feat. Robyn - Out of the Black.flac


     Peak level 99.9 %
     Track quality 97.9 %
     Extraction Speed (Test) 4.3767 X
     Extraction Speed (Copy) 4.0128 X
     Test CRC F7C60814
     Copy CRC F7C60814
     Track not present in AccurateRip database
     Copy OK


Track  9


     Filename Music/album/Neneh Cherry - Blank Project/09. Neneh Cherry - Dossier.flac


     Peak level 99.9 %
     Track quality 98.2 %
     Extraction Speed (Test) 4.2837 X
     Extraction Speed (Copy) 4.6562 X
     Test CRC 2C15E72D
     Copy CRC 2C15E72D
     Track not present in AccurateRip database
     Copy OK


Track 10


     Filename Music/album/Neneh Cherry - Blank Project/10. Neneh Cherry - Everything.flac


     Peak level 100.0 %
     Track quality 100.0 %
     Extraction Speed (Test) 5.7722 X
     Extraction Speed (Copy) 4.5768 X
     Test CRC 7183C0F4
     Copy CRC 7183C0F4
     Track not present in AccurateRip database
     Copy OK




Wall clock time to rip all tracks: 24.718 minutes


None of the tracks are present in the AccurateRip database


No errors occurred


End of status report




```[COLOR=#000000]




**PS2** a great way to do a rip is this here:

[/COLOR]> ```
cdparanoia -d /dev/cdrom -q -v --output-wav --batch 1-13 
``` [adjust number to number of tracks of course]


```
cdparanoia -d /dev/cdrom -Y -v --output-wav --batch --force-read-speed 1 1-10
``` IF SCRATCHED[COLOR=#000000]


also good if ripping twice and comparing both rips like **EAC Morituri and Rubyripper **sends one to yawn and sleep


[/COLOR]> RIP FROM WODIM===================


To copy an audio CD in the most accurate way, first run


```
icedax dev=/dev/cdrom -vall cddb=0 -B -Owav

```

and then to write run



```
wodim dev=/dev/cdrom -v speed=2 -dao -useinfo -text *.wav
```[COLOR=#000000]
[/COLOR]

---

### Post by andrew.46 on 2014-04-09
For cdparanoia I wonder if you would consider altering the *default* number of attempted reads for skipping:

```

       -z --never-skip[=max_retries]
              Do  not  accept any skips; retry forever if needed.  An optional
              maximum number of retries  can  be  specified;  for  comparison,
              default without -z is currently 20.

```

You have to love the commandline :)

---

### Post by shantiq on 2014-04-10
----------------

---

### Post by elkinsj210 on 2014-06-04
In Mint this has worked for me on the desktop icon, and I can not thank you enough, but when I try and use the menu icon it says "file not found" even after copying the path of the desktop icon to said menu icon.  It is just weird is all, I am one who likes to keep their desktop free of icons for one reason or another.  I just ended up moving the desktop icon to the tray.

---

### Post by shantiq on 2014-06-05
> **elkinsj210 said:**
> In Mint this has worked for me on the desktop icon, and I can not thank you enough, but when I try and use the menu icon it says "file not found" even after copying the path of the desktop icon to said menu icon.  It is just weird is all, I am one who likes to keep their desktop free of icons for one reason or another.  I just ended up moving the desktop icon to the tray.


well for me   it goes ths

```
/home/shantiq/.wine/drive_c/"Program Files (x86)/Exact Audio Copy/EAC.exe"
```    so change shantiq for your name

and add/change this to location in properties on your icon   should work ....

---

### Post by shantiq on 2014-08-11
hmm looking for clever advice here    I have realized that my favourite lossless format shorten is very happy to accept ID 3 tags ; which will display in Audacious and Deadbeef perfectly 

[ATTACH=CONFIG]255397[/ATTACH][ATTACH=CONFIG]255398[/ATTACH]

but for reasons I do not understand those tags do not show up in Foobar 1.1 under Wine

so i am trying to add APE 2 tags which i think should show up ...   or will they?

I have tried adding 

```
%dest% -t "Artist=%artist%" -t "Title=%title%" -t "Album=%albumtitle%" -t "Year=%year%" "/home/shantiq/.wine/drive_c/Program Files (x86)/Exact Audio Copy/Flac/shortn32.exe"  %source% %dest%
```

```
%dest% -t "Artist=%artist%" -t "Title=%title%" -t "Album=%albumtitle%" -t "Year=%year%" "/home/shantiq/.wine/drive_c/Program Files (x86)/Exact Audio Copy/Flac/shortn32.exe"  
```

to the Additional command-line option    having picked wapet.exe [the tak and ape route] for the Program used for compression line

but so far not there yet


Any ideas; thoughts; suggestions?
thanx   shan

---

### Post by feelfreetoblameme on 2014-11-22
> **shantiq said:**
> well [SIZE=2]feelfreetoblameme [cool moniker [/SIZE]:)][SIZE=2]  personally readin what you have written i would remove and purge PlayonLinux  [it probably i am guessing places bits and pieces in different places] if you do not use it for other software and start again from scratch with earlier[ guide]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385")

I am not saying it will work for absolutely all setups on all types of machine   but with the latest version of wine you should be fine here [i first did this on 12.04 now using it on 13.04]

best of luck and please tell us how you fare[/SIZE]

Long time coming, this reply, my apologies. Back then I ended up getting a new computer, installing Ubuntu 12.04, converting it to Xubuntu 12.04 and simply forgetting about running EAC on it as I got embroiled in Deluge and Plex. With the number of hard drives crammed into that machine I had no place to plug in a CD/DVD drive anyway. Long story short, with yet another new server just set up, and now having room on the motherboard for the DVD drive to plug in to, your EAC guide came in very handy. So far it works pretty well though the drive I am using seems a tad slow. By the way, any idea if I can use the latest version of FLAC (1.3 x64) or shall I just stick with the default included in the EAC installer (which I believe to be 1.2.1)? I am on an x64 machine. Thanks again for the guide and once again, apologies for the very tardy reply.

---

### Post by shantiq on 2014-11-22
yes FFTBM  just replace the flac.exe in the folder   ~/.wine/dosdevices/c:/Program Files (x86)/Exact Audio Copy/Flac    and carry on as before

1.3    >>   [http://www.free-codecs.com/FLAC_download.htm](http://www.free-codecs.com/FLAC_download.htm)

just tested it


```
Exact Audio Copy V1.0 beta 3 from 29. August 2011

EAC extraction logfile from 22. November 2014, 8:40


The Radha Krsna Temple / The Radha Krsna Temple (2010 Remaster)


Used drive  : TSSTcorpBDDVDW SE-506BB   Adapter: 2  ID: 0


Read mode               : Secure
Utilize accurate stream : Yes
Defeat audio cache      : Yes
Make use of C2 pointers : No


Read offset correction                      : 6
Overread into Lead-In and Lead-Out          : No
Fill up missing offset samples with silence : Yes
Delete leading and trailing silent blocks   : No
Null samples used in CRC calculations       : Yes
Used interface                              : Installed external ASPI interface
Gap handling                                : Not detected, thus appended to previous track


Used output format              : User Defined Encoder
Selected bitrate                : 32 kBit/s
Quality                         : High
Add ID3 tag                     : No
Command line compressor         : C:\Program Files (x86)\Exact Audio Copy\Flac\flac.exe
Additional command line options : -8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T "COMMENT=%comment%" %source% -o %dest%




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


     Filename C:\users\shantiq\Desktop\01 Govinda.wav


     Peak level 99.8 %
     Extraction speed 1.2 X
     Track quality 100.0 %
     Copy CRC 65CB462F
     Accurately ripped (confidence 11)  [C64987F6]  (AR v2)
     Copy OK




All tracks accurately ripped


No errors occurred


End of status report


==== Log checksum 4E38F75B27E3D34248FFF0EB10F1620A495CE4AC137198A8346C677ADDE62658 ====
```

```
AudioFormat                                   : FLAC
Format/Info                              : Free Lossless Audio Codec
Duration                                 : 4mn 46s
Bit rate mode                            : Variable
Bit rate                                 : 849 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 29.0 MiB (100%)
Writing library                          : libFLAC 1.3.0 (UTC 2013-05-26)



```

---

### Post by feelfreetoblameme on 2014-11-22
Awesome, thanks again!

---

### Post by feelfreetoblameme on 2014-11-22
Shantiq, I do have another question. It's not very important to me but on my Windows installs of EAC I used the Cuetools DB plugin. I think I installed that when I installed EAC under Wine but it doesn't seem to have worked. I don't see it listed on the plugins page in the EAC settings and it doesn't come up as one of the metadata options. I'm not a big fan of freedb's metadata but I can make do. Thanks!

---

### Post by shantiq on 2014-11-22
hmmmmm never used it or even heard of it   maybe this [here]("http://www.cuetools.net/wiki/CUETools_Download") also [there]("http://www.cuetools.net/wiki/CTDB_EAC_Plugin") might give you a reason why it does not start you may need to add some of the the prerequisites to your Wine [guessing here]

**Prerequisites**

[COLOR=#000000][FONT=sans-serif]This program requires **Microsoft .NET Framework 2.0 (SP2)** and **Visual C++ 2008 runtime** to run. If you are running Windows Vista or 7, and using Windows Update, these prerequisites are probably already installed. Windows 8 and 8.1 do not have Microsoft .NET Framework 2.0 enabled by default and no download available. You must enable Microsoft .NET Framework 3.5 (which includes 2.0) using the Windows Control Panel (instructions [here]("http://msdn.microsoft.com/en-us/library/hh506443%28v=vs.110%29.aspx")).


if you do find out please add info here for other guys too maybe[/FONT][/COLOR]

---

### Post by feelfreetoblameme on 2014-11-22
> **shantiq said:**
> hmmmmm never used it or even heard of it   maybe this [here]("http://www.cuetools.net/wiki/CUETools_Download") also [there]("http://www.cuetools.net/wiki/CTDB_EAC_Plugin") might give you a reason why it does not start you may need to add some of the the prerequisites to your Wine [guessing here]

**Prerequisites**

[COLOR=#000000][FONT=sans-serif]This program requires **Microsoft .NET Framework 2.0 (SP2)** and **Visual C++ 2008 runtime** to run. If you are running Windows Vista or 7, and using Windows Update, these prerequisites are probably already installed. Windows 8 and 8.1 do not have Microsoft .NET Framework 2.0 enabled by default and no download available. You must enable Microsoft .NET Framework 3.5 (which includes 2.0) using the Windows Control Panel (instructions [here]("http://msdn.microsoft.com/en-us/library/hh506443%28v=vs.110%29.aspx")).


if you do find out please add info here for other guys too maybe[/FONT][/COLOR]

Ah, okay, thanks for those links. I think I'm going to do without, it really isn't that big of a deal. On my Windows PC (my main usual ripping machine) the plugin gives more results for metadata (usually better quality than freedb) and also does a rip-check of some sort in addition to the Accurate Rip. Definitely not necessary and I don't want to add any unnecessary Microsoft bloat to my server. I'm only going to use EAC on it if I have a big ripping project and need to run several machines at the same time. Thanks again for all your help!

---

### Post by shantiq on 2015-02-24
All [instructions]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") for install valid for [EAC 1.0 beta4]("http://www.exactaudiocopy.de/en/index.php/resources/download/") also

May I also add that there is a really good little player which works a dream under wine if you like to play really out of the way codecs [just check the list] it is called [xmplay]("http://support.xmplay.com/")


[ATTACH=CONFIG]260207[/ATTACH]

---

### Post by andrew.46 on 2015-02-26
Shan I see your wavpack option is '-hmx3', I am a little puzzled with '-m' in there:

```

-m                      compute & store MD5 signature of raw audio data

```

I am looking at this mostly because the latest git abcde uses wavpack now...

---

### Post by shantiq on 2015-02-26
Hi Andrew   the option seems to be a combination of three options here    see below in bold


i cannot remember where i first encountered it   but works well so never queried it    ::]]




```
wavpack --help Usage:
    WAVPACK [-options] infile[.wav]|infile.wv|- [...] [-o outfile[.wv]|outpath|-]


    The default operation is lossless. Multiple input files may be specified,
    and they may be either WAV or WAVPACK (.wv) files (or raw PCM if --raw-pcm
    is included). When transcoding, all tags are copied.


 Options:
    -a                      Adobe Audition (CoolEdit) mode for 32-bit floats
    --allow-huge-tags       allow tag data up to 16 MB (embedding > 1 MB is not
                             recommended for portable devices and may not work
                             with some programs including WavPack pre-4.70)
    -bn                     enable hybrid compression
                              n = 2.0 to 23.9 bits/sample, or
                              n = 24-9600 kbits/second (kbps)
                              add -c to create correction file (.wvc)
    --blocksize=n           specify block size in samples (max = 131072 and
                               min = 16 with --merge-blocks, otherwise 128)
    -c                      hybrid lossless mode (use with -b to create
                             correction file (.wvc) in hybrid mode)
    -cc                     maximum hybrid lossless compression (but degrades
                             decode speed and may result in lower quality)
    --channel-order=<list>  specify (comma separated) channel order if not
                             Microsoft standard (which is FL,FR,FC,LFE,BL,BR,
                             LC,FRC,BC,SL,SR,TC,TFL,TFC,TFR,TBL,TBC,TBR);
                             specify '...' to indicate that channels are not
                             assigned to specific speakers, or terminate list
                             with '...' to indicate that any channels beyond
                             those specified are unassigned
    -d                      delete source file if successful (use with caution!)
    -f                      fast mode (faster encode and decode, but some
                             compromise in compression ratio)
**    -h                      high quality (better compression ratio, but slower**
                             encode and decode than default mode)
    -hh                     very high quality (best compression, but slowest
                             and NOT recommended for portable hardware use)
    --help                  this extended help display
    -i                      ignore length in wav header (no pipe output allowed)
    -jn                     joint-stereo override (0 = left/right, 1 = mid/side)
**    -m                      compute & store MD5 signature of raw audio data**
    --merge-blocks          merge consecutive blocks with equal redundancy
                             (used with --blocksize option and is useful for
                             files generated by the lossyWAV program or
                             decoded HDCD files)
    -n                      calculate average and peak quantization noise
                             (for hybrid mode only, reference fullscale sine)
    --no-utf8-convert       don't recode passed tags from local encoding to
                             UTF-8, assume they are in UTF-8 already.
    -o FILENAME | PATH      specify output filename or path
    --optimize-mono         optimization for stereo files that are really mono
                             (result may be incompatible with older decoders)
    -p                      practical float storage (also affects 32-bit
                             integers, no longer technically lossless)
    --pair-unassigned-chans encode unassigned channels into stereo pairs
    -q                      quiet (keep console output to a minimum)
    -r                      generate a new RIFF wav header (removes any
                             extra chunk info from existing header)
    --raw-pcm               input data is raw pcm (44100 Hz, 16-bit, 2-ch)
    --raw-pcm=sr,bps,ch     input data is raw pcm with specified sample rate,
                             sample bit depth, and number of channels
                             (specify 32f for 32-bit floating point data)
    -sn                     override default noise shaping where n is a float
                             value between -1.0 and 1.0; negative values move noise
                             lower in freq, positive values move noise higher
                             in freq, use '0' for no shaping (white noise)
    -t                      copy input file's time stamp to output file(s)
    --use-dns               force use of dynamic noise shaping (hybrid mode only)
    -v                      verify output file integrity after write (no pipes)
    --version               write the version to stdout
    -w "Field=Value"        write specified text metadata to APEv2 tag
    -w "Field=@file.ext"    write specified text metadata from file to APEv2
                             tag, normally used for embedded cuesheets and logs
                             (field names "Cuesheet" and "Log")
    --write-binary-tag "Field=@file.ext"
                            write the specified binary metadata file to APEv2
                             tag, normally used for cover art with the specified
                             field name "Cover Art (Front)"
**    -x[n]                   extra encode processing (optional n = 1 to 6, 1=default)**
**                             -x1 to -x3 to choose best of predefined filters**
**                             -x4 to -x6 to generate custom filters (very slow!)**
    -y                      yes to all warnings (use with caution!)
    -z                      don't set console title to indicate progress



```


as you can see works well   very slow with 6    ::]]


```
 wavpack -hmx3  *01*.wav    -o 01.wv

 WAVPACK  Hybrid Lossless Audio Compressor  Linux Version 4.70.0
 Copyright (c) 1998 - 2013 Conifer Software.  All Rights Reserved.


original md5 signature: 5837454861ba5dd0af44ab9e0acdef24        
created 01**.wv in 14.63 secs** (lossless, 36.54%)        
shantiq@shantiq-00000000000000000000000:~/Music/Mia Dyson/(2014) Idyllwild$ wavpack -hmx6  *01*.wav    -o 01.wv


 WAVPACK  Hybrid Lossless Audio Compressor  Linux Version 4.70.0
 Copyright (c) 1998 - 2013 Conifer Software.  All Rights Reserved.


overwrite 01.wv (yes/no/all)? y


original md5 signature: 5837454861ba5dd0af44ab9e0acdef24        
created 01.wv** in 118.94 secs **(lossless, 36.65%) 
```

---

### Post by Fifoxtasy on 2015-10-06
Hi, thanks for the guide.
Did you get the newest version 1.1 of eac to work? i keep getting error messages when starting eac

---

### Post by shantiq on 2015-10-06
Hi filoxtasy

it is fine it seems [and thanx for saying >>[1.1]("http://download.cnet.com/Exact-Audio-Copy/3001-2140_4-10125142.html?hlndr=1") is out i did not know]

may i suggest you go through **all the steps** from [here]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") carefully  and maybe you have already done so

what are the messages you get? at which point is it not going right?

---

### Post by Fifoxtasy on 2015-10-08
> **shantiq said:**
> Hi filoxtasy

it is fine it seems [and thanx for saying >>[1.1]("http://download.cnet.com/Exact-Audio-Copy/3001-2140_4-10125142.html?hlndr=1") is out i did not know]

may i suggest you go through **all the steps** from [here]("http://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") carefully  and maybe you have already done so

what are the messages you get? at which point is it not going right?

EAC 1.1 doesn't start up and gives this error message ```
unhandled exception at 0308AE90 -> ACCESS_VIOLATION
```

but after running the command ```
cd ~/.wine/dosdevices/c\:/Program\ Files\ \(x86\)/Exact\ Audio\ Copy/regsvr32 sql*
``` it works!!!
thanks very much

---

### Post by Fifoxtasy on 2015-10-08
by the way the command```
-8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T "COMMENT=%comment%" %source% -o %dest% 
```
didn't work for me, maybe because of using the new version 1.1. deleting the last part ```
-o %dest%
``` solved the problem.

thanks a lot for the guide!!!

---

### Post by eric110 on 2016-01-20
here I first installed the latest and greatest wine through ppa in terminal then ran the latest EAC exe from their site download.
Configured EAC exactly as I normally would in a windows environment and even used the settings described here [http://wiki.hydrogenaud.io/index.php?title=EAC_and_FLAC](http://wiki.hydrogenaud.io/index.php?title=EAC_and_FLAC)
Slight glitch out when under drive options I elected to detect read features and while that went fine it attempted to submit the info and got stuck in a loop causing EAC to self destruct haha. this option can be disabled under the tools tab though!

Had to manually force all the flac info which wasn't too bad just time consuming since it has been some years since I've configured these compression settings!
Everyone make sure you do user defined under external, then enter the .flac extension, then select the flac exe which will most likely be here - C:\Program Files (x86)\Exact Audio Copy\Flac\flac.exe
then your command line options - -T "artist=%artist%" -T "title=%title%" -T "album=%albumtitle%" -T "date=%year%" -T "tracknumber=%tracknr%" -T "genre=%genre%" -5 %source% 
or any other options if you're curious how they work
[https://xiph.org/flac/documentation_tools_flac.html](https://xiph.org/flac/documentation_tools_flac.html)

---

### Post by Np4cn3X on 2016-05-20
> **shantiq said:**
> 
  [IMG]http://ubuntuforums.org/attachment.php?attachmentid=212116&d=1328473805[/IMG]

On my Computer running Ubunut 16.04, wine looked similar to Your screenshot, but it was enough to set the type of drive Z: under "Advanced" to "CD-ROM". No fstab etc...

---

### Post by shantiq on 2016-05-21
> **Np4cn3X said:**
> On my Computer running Ubunut 16.04, wine looked similar to Your screenshot, but it was enough to set the type of drive Z: under "Advanced" to "CD-ROM". No fstab etc...



&#10122; Serious answer Np4cn3X:  probably newer versions of Wine "know more"  ?  and that is good news if same for all using 16.04 [myself on LTS so not tested yet]
&#10123; Comedic answer: must be because you run *Ubu_nut_* 16.04 :]

---

### Post by nelson9 on 2016-06-19
Thanks for your help & effort. 

Did anyone figure out how to get cue tools working? I have installed .NET & visual C++ & Mono through wine, but can't get it to do anything. All I can see is the basic built in free-db engine - not even any artwork...!!!  :icon_frown:

Any help much appreciated!!!

---

### Post by shantiq on 2016-06-22
Nelson this is very probably doable

[from]("http://www.cuetools.net/wiki/CTDB_EAC_Plugin")> **Installation**

 EAC V1.1 includes the CTDB plugin version 2.1.6; just leave it enabled when you install EAC. 
Otherwise, to install or update it, just unpack all files from [the archive]("http://www.cuetools.net/wiki/CTDB_EAC_Plugin#Links") (or copy from \CUETools_2.1.x\interop\EAC\) into the folder where you have EAC.exe (overwriting any existing files). 






Personally do not know a thing about CueTools and had a try but could not get it going; I probably have not got the right Prerequisites in my Windows in Wine
You need someone who knows about Windows requirements ; maybe one will see this post

---

### Post by nelson9 on 2016-06-26
Had Cue tools installed with EAC, also had net framework & visual c++, but no luck. Flattened the wine folder & started again, but that didn't help either! Would be good to get it going, save me having to do it all manually!

---

### Post by shantiq on 2016-11-12
> **Fifoxtasy said:**
> by the way the command```
-8 -V -T "ARTIST=%artist%" -T "TITLE=%title%" -T "ALBUM=%albumtitle%" -T "DATE=%year%" -T "TRACKNUMBER=%tracknr%" -T "GENRE=%genre%" -T "PERFORMER=%albuminterpret%" -T "COMPOSER=%composer%" %haslyrics%--tag-from-file=LYRICS="%lyricsfile%"%haslyrics% -T "ALBUMARTIST=%albumartist%" -T "DISCNUMBER=%cdnumber%" -T "TOTALDISCS=%totalcds%" -T "TOTALTRACKS=%numtracks%" -T "COMMENT=%comment%" %source% -o %dest% 
```
didn't work for me, maybe because of using the new version 1.1. deleting the last part ```
-o %dest%
``` solved the problem.

thanks a lot for the guide!!!


Thank you for that.  updated on first post.
Why do they have to move the goal posts all the time :]

---

