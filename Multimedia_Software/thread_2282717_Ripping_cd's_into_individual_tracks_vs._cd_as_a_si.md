---
title: "Ripping cd's into individual tracks vs. cd as a single file with cue sheet"
date: 2015-06-16
forum: Multimedia Software
---

### Post by riderpe on 2015-06-16
I have a dilemma. I have been ripping my collection of cd's with abcde into individual flac files and using Logitech media server (squeezebox) to stream to different devices in my home. Generally this works great. However with opera and project albums where one track players into the next without a gap, which makes for a poor listening experience. I recently read that cue sheets can control the gap space. In reading documentation on cue sheets it see that the index and track description is part of the cue sheet including any gap. 
 Does it make more sense to rip cd's as a single file and use a cue sheet or is there some way to use separate track files and eliminate the gap when necessary using a cue sheet or som other mechanism? 
 Thank you  for your time
PT

---

### Post by shantiq on 2015-06-16
1 - how about rip a cd as[ **one track**]("http://ubuntuforums.org/showthread.php?t=819965&p=6430937#post6430937")  ...    then none of that gap business   ...   better for opera surely  

```
abcde -1 -M  -o flac
```

[2 - Gapless playback - general info]("https://en.wikipedia.org/wiki/Gapless_playback#User_workarounds")

3 - or use a player which plays with no gaps as an option   Aqualung/[Deadbeef]("http://deadbeef.sourceforge.net/download.html")/

```
sudo apt-get install aqualung
```

```
sudo add-apt-repository ppa:starws-box/deadbeef-player
```
```
sudo apt-get update ; sudo apt-get install deadbeef
```




4 - Also Audacious has a **silence-removal plugin** which will cut all silent gaps and therefore move to the next track automatically;   should **sort out the opera continuity **without having to rip in any special way
[ATTACH=CONFIG]262631[/ATTACH]

---

### Post by andrew.46 on 2015-06-17
Hey Shan! At the risk of 'gilding the lily' you could add options to your flac output:

```

abcde -1  -o 'flac:-8'

```

and any other flac option as well...

---

### Post by shantiq on 2015-06-18
thanx Andrew  ...   better   :]

[ also : cuesheet info]("http://ubuntuforums.org/showthread.php?t=2282717&p=13306098#post13306098")

---

### Post by Bucky Ball on 2015-06-18
Personally, I rip them as one track then chop them up manually using Audacity. It's in the repositories.

---

### Post by andrew.46 on 2015-06-18
> **Bucky Ball said:**
> Personally, I rip them as one track then chop them up manually using Audacity. It's in the repositories. Interestingly enough in abcde you can rip and encode to a single flac file with an embedded cue sheet then subsequently use the flac file as a virtual cd and encode to whichever format you wish...

---

### Post by shantiq on 2015-06-18
install
```
 sudo apt-get install mkcue 
```

go to .abcde.conf   [situated in home folder]

and uncomment [remove # on CUEREADERSYNTAX]so you have


```
# CUE reader syntax for the CUE reader program to use.
# abcde supports 2 CUE modes: 'mkcue' and 'abcde.mkcue' so you can set the
# MKCUE variable accordingly. The 'abcde.mkcue' uses an internal
# implementation, without the need of an external program.
[COLOR=#ff0000]CUEREADERSYNTAX=mkcue[/COLOR]
```


also

```
#CDSPEED=eject
#VORBISGAIN=vorbisgain
[COLOR=#ff0000]MKCUE=mkcue[/COLOR]
#MKTOC=cdrdao
#DIFF=diff
```


**then run    >>**


```
abcde -1 -o  flac  -a  default,cue
```   

or
```
abcde -1  -M  -o  'flac:-8'  -a  default,cue
```     although I do not know what -M is for   not mentioned in manpage or --help [maybe obsolete]


example of cuesheet produced here:

```
PERFORMER "Lianne La Havas"
TITLE "Lost & Found EP"
FILE "Lost_&_Found_EP.flac" WAVE
  TRACK 01 AUDIO
    TITLE "No Room For Doubt (feat. Willy Mason)"
    INDEX 01 00:00:00
  TRACK 02 AUDIO
    TITLE "Lost & Found"
    INDEX 01 04:02:48
  TRACK 03 AUDIO
    TITLE "Age"
    INDEX 01 08:31:27
  TRACK 04 AUDIO
    TITLE "Night School"
    INDEX 01 11:14:02
  TRACK 05 AUDIO
    TITLE "Final Form"
    INDEX 01 13:54:57


```




but it **not embedded**  as advertised [cue and flac file separate in folder] ;    so how do i do that here;     any of you know or understand?

PS : also tried the 'abcde.mkcue' route but that yielded nothing :]



thanx    shan

---

### Post by andrew.46 on 2015-06-18
Hey Shan! Looks like the -M option is *partially *deprecated in abcde (left out of the abcde -h screen but still active in the usage function) but all it did was to activate the cue function so it is equivalent to:

```

-a cue

```

and thus can be left out of your commandline. Embedded cue sheet is probably there (it is hidden to mediainfo) *as well *as an external cue sheet. You can check with metaflac as follows:

```

andrew@ilium~$ [COLOR="#FF0000"]**metaflac --list --block-type=CUESHEET Atom_Heart_Mother.flac**[/COLOR] 
METADATA block #3
  type: 5 (CUESHEET)
  is last: false
  length: 672
  media catalog number: 
  lead-in: 88200
  is CD: true
  number of tracks: 6
    track[0]
      offset: 0
      number: 1
      ISRC: 
      type: AUDIO
      pre-emphasis: false
      number of index points: 1
        index[0]
          offset: 0
          number: 1
    track[1]
      offset: 62813100
      number: 2
      ISRC: 
      type: AUDIO
      pre-emphasis: false
      number of index points: 1
        index[0]
          offset: 0
          number: 1
    track[2]
      offset: 74723040
      number: 3
      ISRC: 
      type: AUDIO
      pre-emphasis: false
      number of index points: 1
        index[0]
          offset: 0
          number: 1
    track[3]
      offset: 89249580
      number: 4
      ISRC: 
      type: AUDIO
      pre-emphasis: false
      number of index points: 1
        index[0]
          offset: 0
          number: 1
    track[4]
      offset: 103455660
      number: 5
      ISRC: 
      type: AUDIO
      pre-emphasis: false
      number of index points: 1
        index[0]
          offset: 0
          number: 1
    track[5]
      offset: 137857776
      number: 170 (LEAD-OUT)
andrew@ilium~$ 

```

BTW if there are any abcde issues of this sort, or if you simply wish to chat, there is a new Freenode channel #abcde which has only been running a week or so...

---

### Post by shantiq on 2015-06-19
thanx Andrew  and metaflac shows same here;    but the cue **does not work** as an embed

flac opens in VLC and Audacious as a single track without the split cue  info    [if I load up the cue on its own all good]

No biggie but would be nice to know why it is not functioning as an embed if anyone knows


PS    thanx on -M clarification


**Edit**: but it does work in foobar under wine   although does not list the separate titles  but does split the file in tracks ;     so it is an embedded  cuesheet   but with limited use and the issue is with audacious and vlc not reading the embed


and Logos34 from 2008's command still good   so it is



```
abcde -1 -M -o flac
```       to get an embedded cue flac image

---

### Post by mc4man on 2015-06-19
deadbeef, mpv, baka-mplayer will play & list from embedded. smplayer will play as chapters (not list track names

---

### Post by andrew.46 on 2015-06-19
> **shantiq said:**
> No biggie but would be nice to know why it is not functioning as an embed if anyone knows

In abcde the single flac file with embedded cue is mostly used so the flac file functions as a virtual cd and thus you can recreated the cd in whatever format abcde can output to:

```

abcde -d Atom_Heart_Mother.flac -o mp3:-V2

```

Great for archiving :)

---

### Post by shantiq on 2015-06-20
not sure here mc   i think deadbeef "knows" the cue is in the same folder and uses that yes it does split and tag but if you remove the cue from the folder and drag **just the flac**   you are back to one track only  ...   mpv for me does no splitting   and i do not know baka  ...     but hey whichever way abcde is very handy  ...   these are minor points


PS    Andrew thanx for explaining the "split single file to other format"   trick   i could not understand when was meant on the help file ...
I almost never do.  Programmers [sorry guys] seem to find it hard to explain things to "humans" :)  to "civilians".  Manpages might as well be written in Aramaic most times.   What a "human" needs is an example that is so crystal-clear no mistakes are possible ...    I think the computing community needs those types of translators    ....     maybe it will become a job ...     a computer software-user translator  ...    the interface between the programming mind and the user.    I guess a lot of us on the forums already do this a bit...



PS2 Absolute Computing Poetry

```
shantiq@shantiq-00000000000000000000000:~/Lianne$ **abcde -d Lost_\&_Found_EP.flac -o m4a**
Grabbing entire CD - tracks: 1 2 3 4 5
Retrieving 1 CDDB match...done.
---- Lianne La Havas / Lost & Found EP ----
1: No Room For Doubt (feat. Willy Mason)
2: Lost & Found
3: Age
4: Night School
5: Final Form

Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 1: No Room For Doubt (feat. Willy Mason)...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 2: Lost & Found...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 3: Age...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 4: Night School...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 5: Final Form...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Tagging track 1 of 5: No Room For Doubt (feat. Willy Mason)...
Encoding track 2 of 5: Lost & Found...
[100%] 04:28.720/04:28.720 (24x), ETA 00:00.000   
11850552/11850552 samples processed in 00:11.100
Tagging track 2 of 5: Lost & Found...
Encoding track 3 of 5: Age...
[100%] 02:42.667/02:42.667 (23x), ETA 00:00.000   
7173600/7173600 samples processed in 00:07.125
Tagging track 3 of 5: Age...
Encoding track 4 of 5: Night School...
[100%] 02:40.733/02:40.733 (24x), ETA 00:00.000   
7088340/7088340 samples processed in 00:06.606
Tagging track 4 of 5: Night School...
Encoding track 5 of 5: Final Form...
[100%] 04:11.240/04:11.240 (25x), ETA 00:00.000   
11079684/11079684 samples processed in 00:10.214
Tagging track 5 of 5: Final Form...
Finished.
```


also tested    
```
abcde -d singlefile.flac -o "ogg:-q 10"
```
```
abcde -d singlefile.flac -o "opus:--b 256"
```

if you do not specify   but just enter

```
abcde -d singlefile.flac
``` 
  
it defaults to mp3 it seems with settings from .abcde.conf

---

### Post by andrew.46 on 2015-06-20
> **shantiq said:**
> PS    Andrew thanx for explaining the "split single file to other format"   trick   i could not understand when was meant on the help file ...

There is an example demonstrating use of the -d option with a single track file in the EXAMPLES section of the man page:

```

       abcde -d singletrack.flac
              Will  extract  the  files  contained in singletrack using the embedded
              cuesheet.

```

Would it be helpful for this to demonstrate how to extract to ogg for example?

---

### Post by shantiq on 2015-06-20
absolutely Andrew :)

most times I read a manpage i scroll to the bottom to see examples THEN i scroll back up to see if i can make head or tail of the manpage itself

Practical Examples are where it is at for the non-cognoscenti and there are many of us :]    then we might understand how it works

So yes showing how to turn a single flac into split oggs would be ace ... in this instance   ALSO    to specify that 

```
[FONT=arial]abcde -d singletrack.flac[/FONT]
```[FONT=arial]           defaults to mp3[/FONT]  ;    and then to show what to do for ogg;  then people will get it and know it is the same routine for all formats

If those manpages were always limpid people would not be daunted by command-line so much ...    AND  there would be more folks on Linux/Ubuntu I would surmise



the .abcde.conf    file too is a gem  and needs to be explained clearly   ;    the program is amazing really now;   thanx to a lot you have added of recent times no doubt

---

### Post by andrew.46 on 2015-06-20
> **shantiq said:**
> So yes showing how to turn a single flac into split oggs would be ace ... in this instance   ALSO    to specify that 

```
[FONT=arial]abcde -d singletrack.flac[/FONT]
```[FONT=arial]           defaults to mp3[/FONT]  ;    and then to show what to do for ogg;  then people will get it and know it is the same routine for all formatst

I have included the example [in the man pages]("http://git.einval.com/cgi-bin/gitweb.cgi?p=abcde.git;a=commit;h=0eec4f29ab9e6b0c1b8570d5f4c82cb2e68e6359") but bear in mind that the default is ogg, not mp3 so I am not sure what is happening there on your system...

---

### Post by shantiq on 2015-06-20
what i get :]

```
EXAMPLES
       Possible ways one can call abcde:

       abcde  Will work in most systems

       abcde -d /dev/cdrom2
              If the CDROM you are reading from is not the standard /dev/cdrom (in GNU/Linux systems)

       abcde -o vorbis,flac
              Will create both Ogg/Vorbis and Ogg/FLAC files.

       abcde -o vorbis:"-b 192"
              Will pass "-b 192" to the Ogg/Vorbis encoder, without having to modify the config file

       abcde -W 1
              For  double+  CD  settings:  will  create  the  1st CD starting with the track number 101, and will add a comment "CD 1" to the
              tracks, the second starting with 201 and so on.

       abcde -d singletrack.flac
              Will extract the files contained in singletrack using the embedded cuesheet.
```



as regards my default I think maybe tinkering with the .conf might be why but i do not see how

```
abcde -d Lost_\&_Found_EP.flac 
Grabbing entire CD - tracks: 1 2 3 4 5
Retrieving 1 CDDB match...done.
---- Lianne La Havas / Lost & Found EP ----
1: No Room For Doubt (feat. Willy Mason)
2: Lost & Found
3: Age
4: Night School
5: Final Form

Edit selected CDDB data [y/N]? n
Is the CD multi-artist [y/N]? n
Creating playlist...
Grabbing track 1: No Room For Doubt (feat. Willy Mason)...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 2: Lost & Found...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 3: Age...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 4: Night School...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Grabbing track 5: Final Form...

flac 1.3.0, Copyright (C) 2000-2009, 2011-2013  Josh Coalson & Xiph.Org Foundation
flac comes with ABSOLUTELY NO WARRANTY.  This is free software, and you are
welcome to redistribute it under certain conditions.  Type `flac' for details.

Lost_&_Found_EP.flac: done         
Tagging track 1 of 5: No Room For Doubt (feat. Willy Mason)...

track1.mp3    [ 5.56 MB ]
-------------------------------------------------------------------------------
Time: 04:03    MPEG1, Layer III    [ 192 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
No ID3 v1.x/v2.x tag found!
Setting artist: Lianne La Havas
Setting album: Lost & Found EP
Setting title: No Room For Doubt (feat. Willy Mason)
Setting track: 1
Setting track total: 5
Setting track genre: 17
Setting TDRC frame to '2011'
Writing tag...
Encoding track 2 of 5: Lost & Found...
LAME 3.99.5 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding /home/shantiq/Lianne/abcde.39043e05/track2.wav
      to /home/shantiq/Lianne/abcde.39043e05/track2.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (7.3x) 192 kbps qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
     0/10288  ( 0%)|    0:00/    0:00|    0:00/    0:00|   0.0000x|    0:00 
04:28--------------------------------------------------------------------------
   kbps      %     %
    0.0           ID3 v2.4:
 10288/10288 (100%)|    0:15/    0:15|    0:19/    0:19|   17.502x|    0:00 vas
-------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  192.0        2.7  97.3        98.5   0.9   0.6
Writing LAME Tag...done
ReplayGain: -7.8dB
Tagging track 2 of 5: Lost & Found...

track2.mp3    [ 6.15 MB ]
-------------------------------------------------------------------------------
Time: 04:29    MPEG1, Layer III    [ 192 kb/s @ 44100 Hz - Joint stereo ]
-------------------------------------------------------------------------------
No ID3 v1.x/v2.x tag found!
Setting artist: Lianne La Havas
Setting album: Lost & Found EP
Setting title: Lost & Found
Setting track: 2
Setting track total: 5
Setting track genre: 17
Setting TDRC frame to '2011'
Writing tag...
ID3 v2.4:
title: Lost & Found        artist: Lianne La Havas
album: Lost & Found EP        year: 2011
track: 2/5        genre: Rock (id 17)
Encoding track 3 of 5: Age...
LAME 3.99.5 64bits (http://lame.sf.net)
Using polyphase lowpass filter, transition band: 18671 Hz - 19205 Hz
Encoding /home/shantiq/Lianne/abcde.39043e05/track3.wav
      to /home/shantiq/Lianne/abcde.39043e05/track3.mp3
Encoding as 44.1 kHz j-stereo MPEG-1 Layer III (7.3x) 192 kbps qval=3
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  6229/6229  (100%)|    0:09/    0:09|    0:11/    0:11|   17.148x|    0:00 
-------------------------------------------------------------------------------
   kbps        LR    MS  %     long switch short %
  192.0        0.0 100.0        97.7   1.3   1.0
Writing LAME Tag...done
ReplayGain: -5.6dB
Tagging track 3 of 5: Age...


```

---

### Post by andrew.46 on 2015-06-20
Well, I only have powers over the development version so this is where the change is :). As for the mp3 I suspect that abcde is ready your default ~/.abcde.conf file which is perhaps set to mp3 output? Or indeed if you have modified your /etc/abcde.conf file...

On a bright note I now have qaac working with abcde. One major stumbling block was the space in the path for qaac in 'Program Files' which no amount of escaping would fix. So alac is possible with 'qaac -A', I have not bothered with refalac as this would just complicate matters. I will start committing this next week or so once I have tested endlessly, written in the checks, added in the docs etc etc...

---

