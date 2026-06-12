---
title: "mp3HD in ubuntu"
date: 2010-07-15
forum: Multimedia Software
---

### Post by shantiq on 2010-07-15
thought i would have a look at this mp3HD to see what it sounds like

but so far no joy 


**NB:  Please i am asking for advice to get it going so do not post remarks of the type it is rubbish and so on there are already many on the net I simply want to:KS hear it myself**


downloaded the linux toolkit from [here]("http://www.all4mp3.com/SoftwareHD.aspx")

then followed the instructions using** [grip]("http://ubuntuforums.org/showthread.php?t=1310375&highlight=grip&page=3")**
cleverly packaged by rapido

```
sudo add-apt-repository ppa:rapido/grip
sudo apt-get update
sudo apt-get install grip
``````
** Can I use the mp3HD Codec to rip my audio CDs? 
 
   To rip mp3HD files from your audio CDs you need an audio CD  
   grabber tool with external Encoder support. For example you can use 
   Grip (gnome tool). 
    
   You can include the mp3HD encoder into Grip by performing the  
   following steps: 
          
         - Open the "Config" tab  
         - Go to the "Encode -> Encoder" tab 
         - Set "Encoder" to "Other" 
         - Type the link to your mp3hdEncoder.exe file into the  
           field "Encoder Executable" 
         - Insert the following text into the Additional command-line  
           option field: 
               -if %w -of %m -br %b000 -Title %n -Artist %a -Album %d  
               -Track %t -Year %y -Genre %G  
         - Write "mp3" into the "Encoder file extension" field 
         - Go to the "Encode -> Options" tab 
         - Set the desired bit rate in the "Encoding bitrate" field.
```





then i get a message          [CENTER][IMG]http://img21.imageshack.us/img21/804/warninggrip006.png[/IMG][/CENTER]



which leaves me puzzled      any ideas?


also tried to rip with EAC through wine which works a treat which other formats (flac/wv/shn/tak/ape/tta) and no joy there either

```
http://www.exactaudiocopy.de/en/index.php/resources/download/ 
  
    
   You can include the mp3HD encoder into the Exact Audio Copy grabber  
   by performing the following steps: 
          
         - Open the "Compression options" from the "EAC" menu  
         - Go to the "External Compression" tab 
         - Enable the "Use external program for compression" option 
         - Set "Parameter passing scheme" to "User Defined Encoder" 
         - Write ".mp3" into the "Use file extension" field 
         - Type the link to your mp3hdEncoder.exe file into the 
           "Program, including Path, used for compression" field  
         - Insert the following text into the Additional command-line option field: 
            -if %s -of %d -br %r000 -Artist "%a" -Album "%g" -Title "%t" -Year "%y"  
            -Track "%n" -Genre "%m"  
         - Select the desired bit rate in the "Bit rate" field. 
         - Uncheck the "Add ID3 tag" option 
   
```
at the encoding stage I am left with the temporary file and it goes nowhere




all useful suggestions welcome:KS

---

### Post by aeiah on 2010-07-15
have you tried launching it with sudo (not a solution, but may clear up where the problem lies)?

---

### Post by shantiq on 2010-07-15
only positive result so far is using  winamp5581_lite under Wine with the mp3HD plugin (attached below) and the sound is nice but it is hardly a linux triumph on my part no ripping as yet

---

### Post by shantiq on 2010-07-15
> **aeiah said:**
> have you tried launching it with sudo (not a solution, but may clear up where the problem lies)?


well thank you for suggestion

And YES it works!:KS

---

### Post by shantiq on 2010-07-16
ok at last a breakthrough

ripping with EAC works perfect only they did not write in their info was that you do not enter a high kbps like 512 or anything over 320 since it is a backward compatible mp3 after all a hybrid lossy/lossless format

so slightly modified instructions 


> ** Can I use the mp3HD Codec to rip my audio CDs?

   To rip mp3HD files from your audio CDs you need an audio CD 
   grabber tool with external Encoder support. For example you can use
   the Exact Audio Copy CD grabber. The current version of Exact Audio 
   Copy can be downloaded at 
   [http://www.exactaudiocopy.de/en/index.php/resources/download/](http://www.exactaudiocopy.de/en/index.php/resources/download/). 
   
   You can include the mp3HD encoder into the Exact Audio Copy grabber 
   by performing the following steps:
         
         - Open the "Compression options" from the "EAC" menu 
         - Go to the "External Compression" tab
         - Enable the "Use external program for compression" option
         - Set "Parameter passing scheme" to "User Defined Encoder"
         - Write ".mp3" into the "Use file extension" field
         - Type the link to your mp3hdEncoder.exe file into the
           "Program, including Path, used for compression" field 
         - Insert the following text into the Additional command-line option field:
            -if %s -of %d -br %r000 -Artist "%a" -Album "%g" -Title "%t" -Year "%y" 
            -Track "%n" -Genre "%m" 
         - Select the desired bit rate in the "Bit rate" field  **no higher than 320**.
         - Uncheck the "Add ID3 tag" option
   


and play in winamp with the mp3HD plugin you will see you kbps fluctuate up to 980 thereabouts sounds like good lossless quality


still not a linux solution but at least it works and if anyone knows anymore on the linux side please tell

i still do not see how to use the linux encoder decoder it gives me command not found

```
shantiq@shantiq-desktop:~$ cd ./mp3HDDONOTDELETE
shantiq@shantiq-desktop:~/mp3HDDONOTDELETE$ mp3hdEncoder
mp3hdEncoder: command not found
 

```

---

### Post by cascade9 on 2010-07-16
Gah, MP3HD. 
You might find a way to rip HD-AAC files (HD-AAC = MP3HD = MPEG-4 SLS)

BTW, you might not know this- 

> Useless format:

[LIST]
[*]The lossless part is stored in ID3v2 tags.
[*]Size of ID3v2 tags is limited to 256MB by specifications; as a result, lossless part of an mp3hd file can't be larger than 256MB.
[/LIST]
I wonder what those people will think of next. Maybe resurrect VQF or something.

Addendum:

Current tagging software isn't prepared to deal with this kind of situation, so you're going to see various disturbing behaviors such as: 
[LIST]
[*]Very slow tag updates (near-full-file-rewrite with each edit).
[*]Heavy memory usage of tag editors.
[*]Retagging stripping correction data.
[*]Tag editing or even reading failures when approaching the 256MB limit because software will try to put each ID3v2 frame in a single memory block and allocating a single block of such size is likely to fail in 32-bit address space because of fragmentation issues.
[/LIST]
[http://www.hydrogenaudio.org/forums/index.php?showtopic=70548](http://www.hydrogenaudio.org/forums/index.php?showtopic=70548)

---

### Post by shantiq on 2010-07-16
:KScascade aware of all this:KS just really wanted to hear it for myself

i see you on all the format thread you seem to like exploring too
had a good look at mp3HD i fund the way it is rigged up interesting the whole lossy/lossless hybrid thing

it is fairly useless as it is since it does not work on mp3 players i do not think any of them can decode HD

and worse yet it does not even play the lossy version my samsung player has NO use whatsoever for it 


but played through winamp with the plugin it is fine oscillates between 320 and 980 kbps thereabouts

anyway can you say a bit more about HD-AAC = MP3HD = MPEG-4 SLS if you have more info

is HD-ACC anythiing to do with ALAC?


[COLOR=#000000][FONT=Times New Roman]**Fraunhofer says HD-ACC will make CDs "obsolete"**

[COLOR=#666666][FONT=georgia]*By [Donald Melanson]("http://ubuntuforums.org/editor/donald-melanson") [[IMG]http://www.blogsmithmedia.com/www.engadget.com/media/writer_rss.gif[/IMG]]("http://ubuntuforums.org/editor/donald-melanson/rss.xml") posted Jan 8th 2008 12:57PM*[/FONT][/COLOR]





[COLOR=#444444][FONT=georgia][[IMG]http://www.blogcdn.com/www.engadget.com/media/2008/01/hd-aac-4c_tcm278-92726.gif[/IMG]]("http://www.macworld.com/article/131447/2008/01/hdaac.html")Those[ Fraunhofer]("http://www.engadget.com/tag/fraunhofer") folks are nothing if not prolific, and it now looks like they're getting a little boastful as well, as evidenced by some comments reps from the group made at CES this week. As MacWorld reports, Fraunhofer IIS is not only saying that its new HD-ACC codec is "better than CD," but that it "makes CDs obsolete." That is apparently due to the codec's lossless compression of 24-bit music content, as opposed to the 16-bit, 44.1 kHz quality now found on CDs. What's more, the HD-AAC encoding process embeds a so-called "core layer" on any device that supports plain old AACs, although you'll obviously need a player with an HD-AAC decoder in order to take advantage of the fully lossless signal. Of course, some formats have a tendency to take off more quickly than others, so we'll just have to wait and see how HD-ACC plays out in the grander scheme of things.



ok so no

but 24-bit is really good in my experience


anyway the search for the next format carries on :KS:KS:KS:KS
[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by mc4man on 2010-07-16
Just for curiosity set up rubyripper to rip and encode a cd with mp3hdEncoder, took a little to get it not to crash.

Does the job but would need some fine tuning to get tags correct (got album and year right, track name got truncated (spaces?), genre wrong.
(the track names of the mp3's were correct

But as you say nothing here can play the hd mp3 except Winamp, which it does fine, so more just to try.

Edit:
this worked well in rubyripper for comm. for 'other', noting rr can be a bit finicky
(using rr 0.6 set to use libruby-1.9.1, ruby-gtk2 (0.19.4) in lucid to work around broken gui with libruby-1.8 -  though from cli libruby-1.8 is fine, gui works to set parameters

```
mp3hdEncoder -if "%i" -of "%o".mp3 -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```

---

### Post by shantiq on 2010-07-17
thanks for that mc4man will give that a whirl one of my mottos is if you don't try you don't find out:KS:KS

[good place]("http://linuxappfinder.com/package/rubyripper") for the rubyripper

---

### Post by mc4man on 2010-07-17
It appears with that setting (-mode 1), that the 'regular' mp3 is a vbr probably at -V 1 or -V 2 ( shows up as around 220 in vlc, ect.

Edit: 
I build (really just an install), my own, if picking between the 2 I'd probably go with the 'sid' one, getdeb has had issues previously for some.

(though the 'sid' one only suggests cd-discid, without it installed rr is worthless, so make sure it's installed.

---

### Post by shantiq on 2010-07-17
ok did not manage just 2 wavs in my other folder

it but hey not the first time it happens to me

first observation with rubyripper and i remember i had heard it before why does it always sound like a jumbo jet is taxi-ing inside my pc tower?

anyway no bother

now all i did was enter your line of code into the other box

[CENTER][IMG]http://img713.imageshack.us/img713/9716/rubyripper007.png[/IMG][/CENTER]

so obviously it takes a lot more than that

can you please elaborate for the thick amongst us (ie me in this case)

how does rubyripper know where to find the encoder? where do you place it  i did a search and find nowhere obvious

what else did you do if you do not mind explaining blow by blow


cheers    shan:KS

---

### Post by mc4man on 2010-07-17
While I usually place outside encoders/scripts ect. in ~/bin rr likes for them to be in either /usr/bin or /usr/local/bin

So place mp3hdEncoder in either (make sure it's executable for all (owner, group, other

here's my rr log from test
> This log is created by Rubyripper, version 0.6.0rc1
Website: [http://code.google.com/p/rubyripper](http://code.google.com/p/rubyripper)

Cdrom player used to rip:
MATSHITA DVD+-RW UJ-867S 1.00
Cdrom offset used: 120

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> mp3hdEncoder -if "%i" -of "%o"[COLOR="Red"].mp3[/COLOR] -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"

CDDB INFO

Artist	= Quicksilver Messenger Service
Album	= Best of
Year	= 1971
Genre	= Pop
Tracks	= 11 (1 selected)
blah, blah
RIPPING SUMMARY

All chunks were tried to match at least 2 times.
None of the tracks gave any problems


---

### Post by shantiq on 2010-07-17
Quicksilver Messenger Service   RSPKT !   :KS


where i got to

ok so first i went into the folder where mp3hdEncoder is kept


   ```
sudo cp mp3hdEncoder /usr/local/bin
```


and            ```
sudo cp mp3hdEncoder /usr/bin
```



then I did     ```
sudo chown shantiq mp3hdEncoder
```

so it reads

[CENTER][IMG]http://img686.imageshack.us/img686/5333/mp3hdencoderproperties0.png[/IMG][/CENTER]


but i get to this and it stops no encoding

[CENTER][IMG]http://img193.imageshack.us/img193/174/rubyripper012.png[/IMG][/CENTER]

i think maybe i have not given the right permissions

you said make sure it's executable for all (owner, group, other

maybe i have not i only gave myself full permission

how do I give permission/ownership to all? I am confused

---

### Post by mc4man on 2010-07-17
ignore

---

### Post by shantiq on 2010-07-17
getdeb

---

### Post by mc4man on 2010-07-17
sorry - I just realized that the exec bit is not set on mp3hdEncoder when unpacked

So maybe just delete the copy in /usr/bin, then from the unzipped toolkit copy it to /usr/bin and go 
```
sudo chmod +x /usr/bin/mp3hdEncoder
```


To ck open a terminal and go 
mp3hdEncoder
It should open to a info, usage dialog

Which package of rr are you using, debian-multimedia or getdebs?


Edit:
getdebs build have had issues with 'other'

Try dm or I have a package here - is the 0.6b, but I know it works properly - post 86
[http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper+mc4man&page=9](http://ubuntuforums.org/showthread.php?t=799621&highlight=rubyripper+mc4man&page=9)

---

### Post by shantiq on 2010-07-17
thanx man will try all of this and report

i think the getdeb might be the problem


this is cool here

```
shantiq@shantiq-desktop:~/mp3HDDONOTDELETE$ mp3hdEncoder -br 320000 -if 1.wav -of 1.mp3

******************************************************************************
*                                                                            *
*                      mp3HD Commandline Encoder v1.5.0                      *
*                         using mp3HD library v1.1.7                         *
*                            (Evaluation Version)                            *
*                                                                            *
*                                Revision 487                                *
*                              Build Feb  2 2010                             *
*                                                                            *
*                        (c) 2007 - 2010 Technicolor S.A.                    *
*                       (c) 1996 - 2010 Fraunhofer IIS                       *
*                            All rights reserved.                            *
*                                                                            *
*       This software and/or program is protected by copyright law and       *
*         international treaties. Any reproduction or distribution of        *
*        this software and/or program, or any portion of it, may result      *
*       in severe civil and criminal penalties, and will be prosecuted       *
*                 to the maximum extent possible under law.                  *
*                                                                            *
******************************************************************************

Encoding file: 1.wav 

Duration:  3:48:500
mp3 Bit Rate: 320 kbit/s
mp3 VBR mode: 0 
Channels: 2
Sample Rate: 44.1 kHz
Stereo Mode: 1
Fat entries: 100 (mp3 100)

Coded Frame:  8750 Time:  3:48:500
shantiq@shantiq-desktop:~/mp3HDDONOTDELETE$
```

---

### Post by mc4man on 2010-07-17
What version of ubuntu are you using?
(for future info any current package of rr will not work on Maverick - I'm going to make a maverick package later today

---

### Post by shantiq on 2010-07-17
using Lucid at the moment

Thanx for all your help


are you on maverick already?


good luck with ppa

=============================================

OK finally got there but God does that gui program crash or what?   but very stable from the command-line
maybe not quite EAC yet but hey Rome was not built in a day

again many thnx for all pointers

I have finally got an mp3HD file _ALL LINUX _  it came out called file.mode  but can be renamed file.mp3HD and played in winamp


ps and the cheeky question is what would one write in the other box if one wanted to rip to shorten

any offers anyone?


ps2    the code to bring the program on the command line is


```
rrip_cli
```   not something one might guess


what it looks like from the command line


```
shantiq@shantiq-desktop:~$ rrip_cli 
Audio-disc found, number of tracks : 9, total playlength : 33:54
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: The Doors
Album: The Soft Parade
Genre: Rock
Year: 1969

TRACK INFO
1) Tell All The People
2) Touch Me
3) Shaman's Blues
4) Do It
5) Easy Ride
6) Wild Child
7) Runnin' Blues
8) Wishful Sinful
9) The Soft Parade

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 1

Should all tracks be ripped ? (y/n)  [y] n
Current selection of tracks : 1 2 3 4 5 6 7 8 9
Enter 1 for entering the tracknumbers you want to remove.
Enter 2 for entering the tracks you want to keep.
Your choice:  [1] 2
Type the numbers of the tracks you want to keep and separate them with a space: 1
Current selection of tracks : 1
Do you want to make any changes? (y/n) :  [n] n
mp3hdEncoder -if "%i" -of "%o" -mode 1 -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
/home/shantiq/other/The Doors (1969) The Soft Parade
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 2
/home/shantiq/other/The Doors (1969) The Soft Parade
01 - Tell All The People -mode
02 - Touch Me -mode
03 - Shaman's Blues -mode
04 - Do It -mode
05 - Easy Ride -mode
06 - Wild Child -mode
07 - Runnin' Blues -mode
08 - Wishful Sinful -mode
09 - The Soft Parade -mode
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> mp3hdEncoder -if "%i" -of "%o" 1 -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"

CDDB INFO

Artist	= The Doors
Album	= The Soft Parade
Year	= 1969
Genre	= Rock
Tracks	= 9 (1 selected)

01 - Tell All The People

STATUS

Ripping progress (0 %)
Ripping track 1
Expected filesize for track 1		is 35562284 bytes.
Free disk space is 399963740 MB
Minutes ripping is 0.0004931.
Starting to rip track 1, trial #1cdparanoia [.0]-[.15119] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track1_1.wav" 2>&1
 (32 seconds)
Minutes ripping is 0.548198316666667.
Starting to rip track 1, trial #2cdparanoia [.0]-[.15119] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track1_2.wav" 2>&1
 (28 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: a30d8a8bc48ca4f6507af2493630a002

Ripping progress (100 %)
Encoding progress (0 %)
Adding track 1 (other) to the queue..
command = mp3hdEncoder -if "/home/shantiq/other/temp_sr0/track1_1.wav" -of "/home/shantiq/other/The Doors (1969) The Soft Parade/01 - Tell All The People -mode" 1 -Title "Tell All The People" -Artist "The Doors" -Album "The Soft Parade" -Track "01" -Year "1969" -Genre "Rock"
Wrong argument "1" found

Encoding file: /home/shantiq/other/temp_sr0/track1_1.wav 

Duration:  3:21:600
mp3 Bit Rate: 128 kbit/s
mp3 VBR mode: 0 
Channels: 2
Sample Rate: 44.1 kHz
Stereo Mode: 1
Fat entries: 100 (mp3 100)

Coded Frame:  7720 Time:  3:21:600
Encoding progress (100 %)
Removing track 1 (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ rrip_cli 

Audio-disc found, number of tracks : 9, total playlength : 33:54
Fetching freedb info...

FREEDB INFO

DISC INFO
Artist: The Doors
Album: The Soft Parade
Genre: Rock
Year: 1969

TRACK INFO
1) Tell All The People
2) Touch Me
3) Shaman's Blues
4) Do It
5) Easy Ride
6) Wild Child
7) Runnin' Blues
8) Wishful Sinful
9) The Soft Parade

What would you like to do?

1) Select the tracks to rip
2) Edit the disc info
3) Edit the track info
4) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 
Should all tracks be ripped ? (y/n)  [y] 1
Please answer yes or no

Should all tracks be ripped ? (y/n)  [y] n
Current selection of tracks : 1 2 3 4 5 6 7 8 9
Enter 1 for entering the tracknumbers you want to remove.
Enter 2 for entering the tracks you want to keep.
Your choice:  [1] 2
Type the numbers of the tracks you want to keep and separate them with a space: 5
Current selection of tracks : 5
Do you want to make any changes? (y/n) :  [n] y
Current selection of tracks : 5
Enter 1 for entering the tracknumbers you want to remove.
Enter 2 for entering the tracks you want to keep.
Your choice:  [1] 2
Type the numbers of the tracks you want to keep and separate them with a space: 5
Current selection of tracks : 5
Do you want to make any changes? (y/n) :  [n] n
mp3hdEncoder -if "%i" -of "%o" -mode 1 -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
/home/shantiq/other/The Doors (1969) The Soft Parade
The output directory already exists. What would you like to do?

1) Auto rename the output directory
2) Overwrite the existing directory
3) Cancel the rip and eject the disc

Please enter the number of your choice:  [1] 2
/home/shantiq/other/The Doors (1969) The Soft Parade
01 - Tell All The People -mode
02 - Touch Me -mode
03 - Shaman's Blues -mode
04 - Do It -mode
05 - Easy Ride -mode
06 - Wild Child -mode
07 - Runnin' Blues -mode
08 - Wishful Sinful -mode
09 - The Soft Parade -mode
Cdrom player used to rip:
_NEC DVD_RW ND-3550A 1.52
Cdrom offset used: 48

Ripper used: cdparanoia 
Matches required for all chunks: 2
Matches required for erroneous chunks: 2

Codec(s) used:
-other	-> mp3hdEncoder -if "%i" -of "%o" 1 -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"

CDDB INFO

Artist	= The Doors
Album	= The Soft Parade
Year	= 1969
Genre	= Rock
Tracks	= 9 (1 selected)

05 - Easy Ride

STATUS

Ripping progress (0 %)
Ripping track 5
Expected filesize for track 5		is 28788524 bytes.
Free disk space is 399918640 MB
Minutes ripping is 0.0003263.
Starting to rip track 5, trial #1cdparanoia [.65375]-[.12239] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track5_1.wav" 2>&1
 (22 seconds)
Minutes ripping is 0.3803766.
Starting to rip track 5, trial #2cdparanoia [.65375]-[.12239] -d /dev/cdrom -O 48 "/home/shantiq/other/temp_sr0/track5_2.wav" 2>&1
 (18 seconds)
Analyzing files for mismatching chunks
Every chunk matched 2 times :)
MD5 sum: 41e016320a1d498776180f344f7ac385

Ripping progress (100 %)
Encoding progress (0 %)
Adding track 5 (other) to the queue..
command = mp3hdEncoder -if "/home/shantiq/other/temp_sr0/track5_1.wav" -of "/home/shantiq/other/The Doors (1969) The Soft Parade/05 - Easy Ride -mode" 1 -Title "Easy Ride" -Artist "The Doors" -Album "The Soft Parade" -Track "05" -Year "1969" -Genre "Rock"
Wrong argument "1" found

Encoding file: /home/shantiq/other/temp_sr0/track5_1.wav 

Duration:  2:43:200
mp3 Bit Rate: 128 kbit/s
mp3 VBR mode: 0 
Channels: 2
Sample Rate: 44.1 kHz
Stereo Mode: 1
Fat entries: 100 (mp3 100)

Coded Frame:  6250 Time:  2:43:200
Encoding progress (100 %)
Removing track 5 (other) from the queue..
Inside the finished function
Encoding progress (100 %)
shantiq@shantiq-desktop:~$ 

```

---

### Post by shantiq on 2010-07-18
for wavpack i entered this in the "other" box on rubyripper

```
wavpack-w Artist="%a" -w Title="%t" -w Album="%g" -w Year="%y" -w Track="%n" -w Genre="%m" -h "%s" "%d" -Track "%n" -Year "%y" -Genre "%g"
```


and no dice    any ideas?

also would like to know the line for tta and shorten if anyone knows

---

### Post by mc4man on 2010-07-18
Too late here to look at anything but 
> it came out called file.mode 

The command in rr should be this - I may have posted a  log from a test in one of my quote boxes that was slightly off - blue is what you're missing for proper extension

```
mp3hdEncoder -if "%i" -of "%o"[COLOR="Blue"].mp3[/COLOR] -mode 1  -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```

Edit 
plus that will allow -mode 1 to be properly passed to encoder

> but God does that gui program crash or what?
It doesn't crash - just gets hung up and takes 1-2 min between tracks

This is a known problem with the version of ruby being used in lucid and also now in maverick

Have fixed here in lucid and today in maverick - but it is a bit of work, involves building some ruby packages and in maverick I had to edit rr's configure script to allow the install to succeed. 

What may prove easier for most is to set up rr in the gui and then rip from the cli which is unaffected by the ruby version

---

### Post by shantiq on 2010-07-18
> What may prove easier for most is to set up rr in the gui and then rip from the cli which is unaffected by the ruby version


i had come to the exact same conclusion and it really works very smoothly from cli but have to set up in gui which is fine


also started a new post [here]("http://ubuntuforums.org/showthread.php?p=9604207#post9604207")

and found that wavpack is

```
wavpack -w "Artist=%a" -w "Title=%t" -w "Album=%b" -w "Year=%y" -w "Track=%n" -w "Genre=%g" -hhm %i -o "%o.wv"
```


any idea what to use for shorten?

---

### Post by shantiq on 2010-07-25
> **shantiq said:**
>          [CENTER][IMG]http://img21.imageshack.us/img21/804/warninggrip006.png[/IMG][/CENTER]






well i wanted to be able to use grip to rip to mp3HD and always got this message so to cure that open with terminal

and   ```
 sudo grip
```  it cures all the permission restrictions

and finally as regards mp3HD worked it out so here goes



[CENTER][IMG]http://img684.imageshack.us/img684/7421/grip1.png[/IMG]


[IMG]http://img413.imageshack.us/img413/7113/grip2.png[/IMG][/CENTER]


and collect it in mp3HD folder in home folder

---

### Post by shantiq on 2010-08-16
slighly fine-tuned  so the lossy version plays at 320kbps  (the lossless is in the 800s)

mp3HD is hybrid it plays lossless in winamp and the mp3hd player on the site and lossy elsewhere
to my mind the only audio format which does that   neat trick



```
mp3hdEncoder  -br 320000 -if "%i" -of "%o".mp3 - -Title "%t" -Artist "%a" -Album "%b" -Track "%n" -Year "%y" -Genre "%g"
```


_ALSO IMPORTANT_


[COLOR="DarkRed"]MAke sure you have Lame installed on your synaptic the encoding relies on it for the lossy part and make it executable

ALSO make sure you go into the terminal
enter mp3hdEncoder  and ACCEPT  the agreement

When using mp3hdEncoder or mp3hdEncoder.exe under wine make sure you have accepted the terms and conditions first IT WILL SIMPLY not work otherwiseFor mp3hdEncoder enter mp3hdEncoder in the command line and follow instructions for .exe right click and do same[/COLOR]

---

### Post by shantiq on 2010-12-06
> **shantiq said:**
> :KScascade aware of all this:KS just really wanted to hear it for myself

i see you on all the format thread you seem to like exploring too
had a good look at mp3HD i fund the way it is rigged up interesting the whole lossy/lossless hybrid thing

it is fairly useless as it is since it does not work on mp3 players i do not think any of them can decode HD

and worse yet it does not even play the lossy version my samsung player has NO use whatsoever for it 


but played through winamp with the plugin it is fine oscillates between 320 and 980 kbps thereabouts

anyway can you say a bit more about HD-AAC = MP3HD = MPEG-4 SLS if you have more info

is HD-ACC anythiing to do with ALAC?


[COLOR=#000000][FONT=Times New Roman]**Fraunhofer says HD-ACC will make CDs "obsolete"**

[COLOR=#666666][FONT=georgia]*By [Donald Melanson]("http://ubuntuforums.org/editor/donald-melanson") [[IMG]http://www.blogsmithmedia.com/www.engadget.com/media/writer_rss.gif[/IMG]]("http://ubuntuforums.org/editor/donald-melanson/rss.xml") posted Jan 8th 2008 12:57PM*[/FONT][/COLOR]





[COLOR=#444444][FONT=georgia][[IMG]http://www.blogcdn.com/www.engadget.com/media/2008/01/hd-aac-4c_tcm278-92726.gif[/IMG]]("http://www.macworld.com/article/131447/2008/01/hdaac.html")Those[ Fraunhofer]("http://www.engadget.com/tag/fraunhofer") folks are nothing if not prolific, and it now looks like they're getting a little boastful as well, as evidenced by some comments reps from the group made at CES this week. As MacWorld reports, Fraunhofer IIS is not only saying that its new HD-ACC codec is "better than CD," but that it "makes CDs obsolete." That is apparently due to the codec's lossless compression of 24-bit music content, as opposed to the 16-bit, 44.1 kHz quality now found on CDs. What's more, the HD-AAC encoding process embeds a so-called "core layer" on any device that supports plain old AACs, although you'll obviously need a player with an HD-AAC decoder in order to take advantage of the fully lossless signal. Of course, some formats have a tendency to take off more quickly than others, so we'll just have to wait and see how HD-ACC plays out in the grander scheme of things.



ok so no

but 24-bit is really good in my experience


anyway the search for the next format carries on :KS:KS:KS:KS
[/FONT][/COLOR]
[/FONT][/COLOR]




whatever happened to Hd aac   been looking for it on the net and i cannot see it


would love to try it out



anyone knows where it is?


ok some info



[http://www.youtube.com/watch?v=JESMLDu_AyM]("http://www.youtube.com/watch?v=JESMLDu_AyM")

---

### Post by shantiq on 2010-12-13
made a vid to show how to use mp3hd on Linux



[URL="http://www.youtube.com/watch?v=Mn6P7339hvc"]**[COLOR="DarkRed"]To use mp3hd on Linux[/COLOR]**
[/URL]

---

