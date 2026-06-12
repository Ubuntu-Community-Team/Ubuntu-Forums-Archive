---
title: "Opus players on 12.04?"
date: 2013-01-23
forum: Multimedia Software
---

### Post by shantiq on 2013-01-23
[**opus**]("http://opus-codec.org/downloads/") is a recent codec      but on 12.04 it has very limited support so far

i installed 1.0.2 and got files very quickly [crystal clear instructions]

> Usage: opusenc --bitrate 128 input_file output_file.opus   for example

and Rubyripper will rip and tag thus:

> opusenc --bitrate 128 "%i" "%o" && id3v2  %o.opus  --artist "%a" --album "%b" --song "%t" --genre "%g" --track "%n" --year "%y"

as will EAC under wine   > --bitrate 128 %source%  %dest%  and tick id3 box


**bulk **convert to opus [requires --enable-libopus when [**configuring**]("https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide") ffmpeg] [all tags maintained]

> for f in * ; do ffmpeg -i  "$f"  -c:a libopus -b:a 320k "${f%.*}.opus" ; done



there are tips to use in vlc and totem in this excellent [**thread  **]("http://ubuntuforums.org/showthread.php?t=2031309")  
but so far neither work for me on 12 .04

tried as suggested

> [noparse] cd ~/temp
wget http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.23-7_amd64.deb
wget http://ftp.us.debian.org/debian/pool/main/g/gst-plugins-bad0.10/libgstreamer-plugins-bad0.10-0_0.10.23-7_amd64.deb
 sudo dpkg -i --force-overwrite *.deb[/noparse]
 
 
 but nothing in totem as yet
 
 
 did an ffmpeg update and added    --enable-libopus

so now i have an efficient command line player for opus files   [but as i write my only opus player]


```
for f in  *opus ; do ffplay -nodisp -autoexit "$f"; done
```

which with an alias can be triggered with the word "opus"

> 1 add     ```
alias opus='for f in  *opus ; do ffplay -nodisp -autoexit "$f"; done'
```   in terminal and return
2 ```
gedit   ~/.bashrc
```
3 add    ```
alias opus='for f in  *opus ; do ffplay -nodisp -autoexit "$f"; done'
```         at bottom of page and save

4 ```
. ~/.bashrc 
```  [in terminal]
5   cd to folder with opus files then enter '```
opus
```'


ctrl +c to move to next track  



                                **=====================**


My question is does anyone know how to open more doors in 12.04  or is 12.10 the only way here ?
12.04 is so stable for me  [best ever]  that i am loath to move up...   so any tips??


PS [**asked **]("http://code.google.com/p/ddb/issues/detail?id=932&colspec=ID%20Type%20Status%20Priority%20Summary%20OpSys&start=100")for deadbeef to add funtionality to its list of codecs

---

### Post by ron999 on 2013-01-23
> **shantiq said:**
> ...  so any tips??
Hi
Ubuntu 12.04, opus files will play with VLC from this PPA ---> [https://launchpad.net/~videolan/+archive/master-daily?field.series_filter=precise]("https://launchpad.net/~videolan/+archive/master-daily?field.series_filter=precise")

---

### Post by andrew.46 on 2013-01-23
If you have opusenc you should also have *opusdec*:

```

andrew@skamandros~/media/YouTube$ **[COLOR="Red"]opusdec sample.opus [/COLOR]**
Decoding to 48000 Hz (1 channel)
Encoded with libopus 1.0.2
ENCODER=opusenc from opus-tools 0.1.5
Decoding complete. 

```

as well as opusinfo:

```

andrew@skamandros~/media/YouTube$ **[COLOR="Red"]opusinfo sample.opus [/COLOR]**
Processing file "sample.opus"...

New logical stream (#1, serial: 2a297bdd): type opus
Encoded with libopus 1.0.2
User comments section follows...
	ENCODER=opusenc from opus-tools 0.1.5
Opus stream 1:
	Pre-skip: 356
	Playback gain: 0 dB
	Channels: 1
	Original sample rate: 44100Hz
	Packet duration:   20.0ms (max),   20.0ms (avg),   20.0ms (min)
	Page duration:   1000.0ms (max),  995.8ms (avg),  100.0ms (min)
	Total data length: 1690117 bytes (overhead: 0.99%)
	Playback length: 3m:34.087s
	Average bitrate: 63.16 kb/s, w/o overhead: 62.53 kb/s
Logical stream 1 ended

```

opusdec is not exactly feature-loaded but it gets the job done :)

---

### Post by shantiq on 2013-01-23
thanx guys will check the VLC

but as regards opusdec i had tried that and got


> opusdec '12 I Love Music.opus'
Decoding to 48000 Hz (2 channels)
Cannot open /dev/dsp: No such file or directory


on any file.... not sure what it means

---

### Post by mc4man on 2013-01-23
> **shantiq said:**
> thanx guys will check the VLC

but as regards opusdec i had tried that and got





on any file.... not sure what it means
It means you didn't specify an output (file
Run just opusdec to see options

---

### Post by shantiq on 2013-01-23
not sure there mc  i just want to use it as a player not a converter


with wine it works as a player

> wine opusdec '02 You Never Love The Same Way Twice.opus'
Decoding to 48000 Hz (2 channels)
Encoded with libopus 1.0.2
ENCODER=opusenc from opus-tools 0.1.6
[\] 00:00:12



but the linux one gives me this


> opusdec '02 You Never Love The Same Way Twice.opus'
Decoding to 48000 Hz (2 channels)
Cannot open /dev/dsp: No such file or directory

---

### Post by andrew.46 on 2013-01-24
Hmmm.... did you build this yourself? Latest version is:

```

andrew@skamandros~$ **[COLOR="Red"]opusdec -V[/COLOR]**
opusdec opus-tools 0.1.6 (using libopus 1.0.2)
Copyright (C) 2008-2012 Xiph.Org Foundation

```

Might be worth building your own if you have not already done so and this would eliminate the possibility of a shoddy compile/package...

---

### Post by shantiq on 2013-01-24
yes my own build :KS

> opusdec -V
opusdec opus-tools 0.1.6 (using libopus 1.0.2)
Copyright (C) 2008-2012 Xiph.Org Foundation

---

### Post by mc4man on 2013-01-24
> **shantiq said:**
> not sure there mc  i just want to use it as a player not a converter

If you were to do a google site search on Cannot open /dev/dsp:  maybe you'll find some workaround.
(there was a change quite some time ago concerning sound/pulseaudio & or oss/oss-compat that is at the root of your issue 

At least here almost all players support opus though some need to be self built.

---

### Post by shantiq on 2013-01-24
yes cool will look again    had a look on google yesterday and as you say many articles;   it is not of the utmost importance since i have ffplay going

will wait for players to catch up!:KS   thsnx for info

[B]
=======================[/B]


ok had a look again on google and it turns out when one has the message [with any/all software]> cannot open dev/dsp  the fix is to prefix your command with > padsp


so cd to the opus folder and

enter  > for f in *.opus; do padsp opusdec  "$f" ; done   omit padsp if you do not need it


so for me commandline players 2     linux gui  0 so far   [b.drung vlc not a success on my install]   


PS        [**foobar 1.1.4**]("http://www.saunalahti.fi/~cse/Opus/") under wine is my only gui so far  plays opus OOTB

---

### Post by shantiq on 2013-04-15
opus now plays excellently in 13.04 with vanilla repo VLC and what is now termed Videos [which is still called Totem if you click on About ]

---

### Post by evilsoup on 2013-04-15
Also, firefox :V

---

### Post by andrew.46 on 2013-04-16
And of course the great commandline ripper abcde can now rip to opus, but still only in the development version:

[http://code.google.com/p/abcde/source/detail?r=374](http://code.google.com/p/abcde/source/detail?r=374)

---

### Post by evilsoup on 2013-04-16
It's probably safe to say that all the actively-developed open-source players/converters/etc will support Opus by now. IIRC Rockbox now supports it too, so if you have a rockbox-based hardware player you should be able to use it on that.

Well, except for HandBrake, which has a limited selection of codecs by choice.

Speaking of which... has anyone tested Rhythmbox on 13.04? Though I guess it uses gstreamer, so if Totem can support it then so can Rhythmbox.

---

### Post by andrew.46 on 2013-04-16
> **evilsoup said:**
> It's probably safe to say that all the actively-developed open-source players/converters/etc will support Opus by now..

Mind you now the dust has settled has Opus had such a huge impact in the world of audio?

---

### Post by evilsoup on 2013-04-16
Well, I would still distribute things online in MP4/Webm for video and MP3/*maybe* M4A for audio. Until Internet Explorer and Safari support Opus natively, I wouldn't bother using it for distribution purposes. Someone like Google could change that - youtube allows them to flex a lot of muscles - so if there's some kind of webm+ with Opus instead of Vorbis, the codec could see *some* wider adoption.

I understand that Skype uses Opus now, so I assume that other VOIP services have/will move over to it - but that won't have any effect on people using it for listening to music.

Maybe pirates will pick up on it? Audible transparency (with my ears, YMMV) at 96 kbit/s for stereo... but then, they could just use AAC...

Anyway: MP3 has survived WMA, Vorbis and AAC - it'll probably survive Opus too. MP3 offers transparency for most people on most tracks at around 128 kbit/s, and anyone who claims they can tell the difference between CD-audio and MP3 at 192 kbit/s or higher is either a lying liar or using some obsolete 1990s encoder. Sure, Opus sounds great at as low as 96 kbit/s; but I don't think that's a large enough gain for most people to care.

---

### Post by mc4man on 2013-04-16
opus is supported in gstreamer-0.10 in 12.10 &  gst1.0 in13.04 if the bad plugin is installed. What's not yet been done is to add opus to the mime so if the bad plugin isn't installed then gstreamer players can't 'find' which plugin to suggest enabling.
(bug on that filed quite some time ago.

---

### Post by shantiq on 2013-04-16
> **andrew.46 said:**
> And of course the great commandline ripper abcde can now rip to opus, but still only in the development version:

[http://code.google.com/p/abcde/source/detail?r=374](http://code.google.com/p/abcde/source/detail?r=374)



hmmmmmmm   Andrew 'aving teething problems here if you do not mind having a look at this

i wrote this one like that  [might be i made mistakes]


> # -----------------$HOME/.abcde.conf----------------- ## 
# A sample configuration file to convert music cds to 
#   opus using abcde version v2.5.5-UNRELEASED
# 
# -------------------------------------------------- #




# Specify the encoder to use for m4a/aac. In this case
# we are using the closed source neroAacEnc.
OPUSENCODERSYNTAX=opus


#[COLOR=#b22222]and here is the mistake  :  it should say opusenc not opus    thanx mc4man for spotting this[/COLOR]


# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/faac
OPUSENC=opusenc


# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
OPUSENCOPTS='--bitrate 256 --ignorelength --artist "%a" --title "%t"'


# Output type opus.
OUTPUTTYPE="opus"


# Use AtomicParsley for tagging.
ATOMICPARSLEY='AtomicParsley'


# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia            
                                     
# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia  
CDPARANOIAOPTS="--never-skip=40"


# Give the location of the CD identification program:       
CDDISCID=cd-discid            
                               
# Give the base location here for the encoded music files.
OUTPUTDIR="$HOME/Opus/"               


# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean
              
# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'


# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'


# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'


# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}


# What extra options?
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)





but sadly get this


> shan@shan:~$ cd abcde_build/abcde-read-only && ./abcdeExecuting customizable pre-read function... done.
Getting CD track info... Querying the CD for audio tracks...
Grabbing entire CD - tracks: 01 02 03 04 05
Checking CDDB server status...
Querying the CDDB server...
Obtaining CDDB results...
Retrieving 1 CDDB match...done.
---- Lianne La Havas / Lost & Found EP ----
1: No Room For Doubt (feat. Willy Mason)
2: Lost & Found
3: Age
4: Night School
5: Final Form


Edit selected CDDB data? [y/n] (n): 
Is the CD multi-artist [y/N]? 
Creating playlist...
Grabbing track 01: No Room For Doubt (feat. Willy Mason)...
cdparanoia III release 10.2 (September 11, 2008)


Ripping from sector       0 (track  1 [0:00.00])
      to sector   18197 (track  1 [4:02.47])


outputting to /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track01.wav


 (== PROGRESS == [                              | 018197 00 ] == :^D * ==)   


Done.




Grabbing track 02: Lost & Found...
cdparanoia III release 10.2 (September 11, 2008)


Encoding track 01 of 05: No Room For Doubt (feat. Willy Mason)...
Tagging track 01 of 05: No Room For Doubt (feat. Willy Mason)...
Ripping from sector   18198 (track  2 [0:00.00])
      to sector   38351 (track  2 [4:28.53])


outputting to /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track02.wav


 (== PROGRESS == [                              | 038351 00 ] == :^D * ==)   


Done.




Grabbing track 03: Age...
cdparanoia III release 10.2 (September 11, 2008)


Encoding track 02 of 05: Lost & Found...
Tagging track 02 of 05: Lost & Found...
Ripping from sector   38352 (track  3 [0:00.00])
      to sector   50551 (track  3 [2:42.49])


outputting to /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track03.wav


 (== PROGRESS == [                              | 050551 00 ] == :^D * ==)   


Done.




Grabbing track 04: Night School...
cdparanoia III release 10.2 (September 11, 2008)


Encoding track 03 of 05: Age...
Ripping from sector   50552 (track  4 [0:00.00])
      to sector   62606 (track  4 [2:40.54])


outputting to /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track04.wav


Tagging track 03 of 05: Age...
 (== PROGRESS == [                              | 062606 00 ] == :^D * ==)   


Done.




Grabbing track 05: Final Form...
cdparanoia III release 10.2 (September 11, 2008)


Encoding track 04 of 05: Night School...
Tagging track 04 of 05: Night School...
Ripping from sector   62607 (track  5 [0:00.00])
      to sector   81449 (track  5 [4:11.17])


outputting to /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track05.wav


 (== PROGRESS == [                              | 081449 00 ] == :^D * ==)   


Done.




[COLOR=#000000]Encoding track 05 of 05: Final Form...
Tagging track 05 of 05: Final Form...[/COLOR]
[COLOR=#a52a2a][ERROR] abcde: The following commands failed to run:[/COLOR]
[COLOR=#a52a2a]movetrack-01: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track01.opus /home/shan/music//opus/Lianne La Havas-Lost & Found EP/01.No Room For Doubt (feat. Willy Mason).opus[/COLOR]
[COLOR=#a52a2a]movetrack-02: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track02.opus /home/shan/music//opus/Lianne La Havas-Lost & Found EP/02.Lost & Found.opus[/COLOR]
[COLOR=#a52a2a]movetrack-03: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track03.opus /home/shan/music//opus/Lianne La Havas-Lost & Found EP/03.Age.opus[/COLOR]
[COLOR=#a52a2a]movetrack-04: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track04.opus /home/shan/music//opus/Lianne La Havas-Lost & Found EP/04.Night School.opus[/COLOR]
[COLOR=#a52a2a]movetrack-05: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track05.opus /home/shan/music//opus/Lianne La Havas-Lost & Found EP/05.Final Form.opus[/COLOR]
[COLOR=#a52a2a]Finished. Not cleaning /home/shan/abcde_build/abcde-read-only/abcde.39043e05.[/COLOR]
[COLOR=#a52a2a]shan@shan:~/abcde_build/abcde-read-only$[/COLOR]


and really not sure what the red stuff means
no opus files are produced



PS and no it has had no impact as a codec insofar as i know but just one more to play with   ::]]


[B]
Rubyripper [/B]does a great job with opus
```
opusenc --bitrate 256 --artist "%a" --title "%t"  --ignorelength "%i" "%o".opus
```

in the Other line

---

### Post by andrew.46 on 2013-04-16
There is a problem with the mv command with abcde and opus, I can duplicate your error. I shall dig a little deeper and see if I can fix it... See the extra '/':
```

 /home/shan/music**[COLOR="#FF0000"]//[/COLOR]**opus/Lianne La Havas-Lost & Found EP/01.No Room For Doubt (feat. Willy Mason).opus

```

---

### Post by mc4man on 2013-04-17
At least here the mv error is because there is nothing to mv (the extra / shouldn't matter & can be removed from .abcde.conf

A bit curious is the posted .conf -  (irrelevant to encoding/mv issue
OUTPUTDIR="$HOME/Opus/"
and the dir. that mv failed to mv to - 
/home/shan/music//opus/

(maybe you edited .abcde.conf before encoding & didn't remove working folder..

---

### Post by mc4man on 2013-04-17
I think you should use  - 
```
OPUSENCODERSYNTAX=opusenc 
```
instead of what you have - OPUSENCODERSYNTAX=opus
I use a fuller .conf & adjust as desired the OUTPUTTYPE= line

---

### Post by shantiq on 2013-04-17
hummmmmm   puzzling; thanx for replies



by changing line 39 to ```
OUTPUTDIR="/home/shan"
```  [instead of [COLOR=#000000]*OUTPUTDIR="$HOME/Opus/" *[/COLOR]
] it gets rid of the // but still not there yet


```
Encoding track 05 of 05: Final Form...Tagging track 05 of 05: Final Form...
[ERROR] abcde: The following commands failed to run:
[COLOR=#b22222]movetrack-01: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track01.opus /home/shan/opus/Lianne La Havas-Lost & Found EP/01.No Room For Doubt (feat. Willy Mason).opus[/COLOR]
[COLOR=#b22222]movetrack-02: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track02.opus /home/shan/opus/Lianne La Havas-Lost & Found EP/02.Lost & Found.opus[/COLOR]
[COLOR=#b22222]movetrack-03: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track03.opus /home/shan/opus/Lianne La Havas-Lost & Found EP/03.Age.opus[/COLOR]
[COLOR=#b22222]movetrack-04: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track04.opus /home/shan/opus/Lianne La Havas-Lost & Found EP/04.Night School.opus[/COLOR]
[COLOR=#b22222]movetrack-05: returned code 1: mv /home/shan/abcde_build/abcde-read-only/abcde.39043e05/track05.opus /home/shan/opus/Lianne La Havas-Lost & Found EP/05.Final Form.opus[/COLOR]
[COLOR=#b22222]Finished. Not cleaning /home/shan/abcde_build/abcde-read-only/abcde.39043e05.[/COLOR]
shan@shan:~/abcde_build/abcde-read-only$ 





```

i ran the neroAacEnc one again just to verify; so yes it seems a problem with opus specifically

---

### Post by mc4man on 2013-04-17
Did you try changing the OPUSENCODERSYNTAX line?
and remove the working folder before re-attempting

---

### Post by shantiq on 2013-04-17
------------see lower down

---

### Post by mc4man on 2013-04-17
Maybe repost your current .abcde.conf (in a **code** box
Works fine here with my .abcde.conf

---

### Post by shantiq on 2013-04-17
-----------------

---

### Post by mc4man on 2013-04-17
> **shantiq said:**
> 


so we are all clear this is the untouched abcde.conf page
Don't you use a local .abcde.conf ? (Home folder

---

### Post by shantiq on 2013-04-17
ok mc got there!!   [and yes use a home folder .abcde.conf]


which now looks like that

> # -----------------$HOME/.abcde.conf----------------- ## # A sample configuration file to convert music cds to 
# opus using abcde version v2.5.5-UNRELEASED
# 
# -------------------------------------------------- #








# Specify the encoder to use for opus
**OPUSENCODERSYNTAX=opusenc**




# Specify the path to the selected encoder. In most cases the encoder
# should be in your $PATH as I illustrate below, otherwise you will 
# need to specify the full path. For example: /usr/bin/faac
**OPUSENC=opusenc**




# Specify your required encoding options here. Multiple options can
# be selected as '--best --another-option' etc.
**OPUSENCOPTS='--bitrate 256 --ignorelength '**




# Output type opus.
**OUTPUTTYPE=opus**




# Use AtomicParsley for tagging.
ATOMICPARSLEY='AtomicParsley'




# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia 


# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia 
CDPARANOIAOPTS="--never-skip=40"




# Give the location of the CD identification program: 
CDDISCID=cd-discid 


# Give the base location here for the encoded music files.
**OUTPUTDIR="/home/username/Desktop" **




# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean


# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'




# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'




# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'




# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}




# What extra options?
MAXPROCS=2 # Run a few encoders simultaneously
PADTRACKS=y # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y # Useful for debugging
EJECTCD=y # Please eject cd when finished


the mistake therefore was using    **OPUSENCODERSYNTAX=opus    **as opposed to    [B]OPUSENCODERSYNTAX=opusenc    
[/B]thanx for that mc

---

### Post by mc4man on 2013-04-17
> **shantiq said:**
> hi mc    is it not simpler if you post the one that worked for you;    then i can run it here please

Ok - note this assumes oggenc,  lame,flac,opus-tools & neroAacEnc are installed, if any aren't then comment out the appropriate 'Path to' line like done for #MPPENC=mppenc & might as well the  'Options for' line like seen for #MPPENCOPTS='--extreme'

What determines the encoder(s) used is then solely the OUTPUTTYPE= line, in this case I just enabled opus (blue line
(if you have alternate method for aac tagging then comment out ATOMICPARSLEY= line, been a while here since this laptop drive is in poor shape


```
# -----------------$HOME/.abcde.conf----------------- #
# 
#   A sample configuration file to convert music cds to 
#      MP3, Ogg Vorbis, FLAC, Musepack, AAC & Opus
#          using abcde version 2.5.4
#      Modified for neroAacEnc, atomicParsley, & opus from
#       http://andrews-corner.org/abcde.html
#      Uses either cdparanoia or Jörg Schilling's cdda2wav, default is cdparanoia
# -------------------------------------------------- #
CDROM=/dev/sr0

OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLACcdparanoia
MPPENCODERSYNTAX=mppenc                # Specify encoder for Musepack
AACENCODERSYNTAX=neroAacEnc             # Specify encoder for AAC
OPUSENCODERSYNTAX=opusenc               # Specify encoder for Opus

OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
#MPPENC=mppenc                          # Path to Musepack encoder
AACENC=neroAacEnc                       # Path to AAC encoder
OPUSENC=opusenc                         # Path to Opus encoder
ATOMICPARSLEY='AtomicParsley'

OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='-V 0'                         # Options for MP3 
FLACOPTS='--verify --best'              # Options for FLAC
#MPPENCOPTS='--extreme'                 # Options for Musepack
AACENCOPTS='-q 0.65'                    # Options for AAC
OPUSENCOPTS='--bitrate 112'             # Options for Opus
 
[COLOR="#0000CD"]OUTPUTTYPE="opus" [/COLOR]     # Add desired output formats, if more that one, then comma separated

# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean

CDROMREADERSYNTAX=cdparanoia
CDPARANOIA=cdparanoia 
#CDROMREADERSYNTAX=cdda2wav 
CDDA2WAV=cdda2wav            
CDPARANOIAOPTS="--never-skip=40"
#CDDA2WAVOPTS="-paranoia -paraopts=proof"

# Give the location of the CD identification program:       
CDDISCID=cd-discid           
                               
OUTPUTDIR="$HOME/Music"               
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'

# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'


mungefilename ()
{
  echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}
MAXPROCS=2                              # Run a few encoders simultaneously
PADTRACKS=y                             # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y                          # Useful for debugging
EJECTCD=y                               # Please eject cd when finished :-)
```

Edit: just to note about the ENCODERSYNTAX line - 
You can also likely just use 'default', ex. - 

OPUSENCODERSYNTAX=default

---

### Post by shantiq on 2013-04-17
excellent idea!
 putting them all in there for future use



now it is even possible to remove


[B]OUTPUTTYPE=opus
[/B]


and then to use 

```
cd abcde_build/abcde-read-only && ./abcde **-o opus**
```

and **never **again to have to touch .abcde.conf   if all codecs installed which is way **more user-friendly**


```
cd abcde_build/abcde-read-only && ./abcde** -o m4a**
```


or even

```
cd abcde_build/abcde-read-only && ./abcde **-o opus,flac,m4a**
```




using



> # -----------------$HOME/.abcde.conf----------------- #





OGGENC=oggenc                          # Path to Ogg Vorbis encoder
LAME=lame                              # Path to MP3 encoder
FLAC=flac                              # Path to FLAC encoder
AACENC=neroAacEnc                       # Path to AAC encoder
OPUSENC=opusenc                         # Path to Opus encoder
ATOMICPARSLEY='AtomicParsley'


OGGENCOPTS='-q 6'                      # Options for Ogg Vorbis
LAMEOPTS='-V 0'                         # Options for MP3 
FLACOPTS='--verify --best'              # Options for FLAC
AACENCOPTS='-cbr 38000 -ignorelength'                    # Options for AAC

# Options for AAC  Bitrate	
#HE-AAC: 48 to 64 kbit/s Stereo, 160 kbit/s for 5.1 Surround (HE-AAC: AAC-LC + SBR)
#HE-AAC v2: 24 to 38 kbit/s Stereo (HE-AACv2: AAC-LC + SBR +PS)
#for good quality audio 

OPUSENCOPTS='--bitrate 320 --cvbr --ignorelength' # Options for Opus


OGGENCODERSYNTAX=oggenc                # Specify encoder for Ogg Vorbis
MP3ENCODERSYNTAX=lame                  # Specify encoder for MP3
FLACENCODERSYNTAX=flac                 # Specify encoder for FLACcdparanoia
AACENCODERSYNTAX=neroAacEnc             # Specify encoder for AAC
OPUSENCODERSYNTAX=opusenc               # Specify encoder for Opus




# The cd ripping program to use. There are a few choices here: cdda2wav,
# dagrab, cddafs (Mac OS X only) and flac.
CDROMREADERSYNTAX=cdparanoia 


# Give the location of the ripping program and pass any extra options:
CDPARANOIA=cdparanoia 
CDPARANOIAOPTS="--never-skip=40"




# Give the location of the CD identification program: 
CDDISCID=cd-discid 


# Give the base location here for the encoded music files.
OUTPUTDIR="/home/[COLOR=#ff0000]**username**[/COLOR]/Desktop" 




# The default actions that abcde will take.
ACTIONS=cddb,playlist,read,encode,tag,move,clean


# Decide here how you want the tracks labelled for a standard 'single-artist',
# multi-track encode and also for a multi-track, 'various-artist' encode:
OUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${TRACKNUM}.${TRACKFILE}'
VAOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${TRACKNUM}.${ARTISTFILE}-${TRACKFILE}'




# Decide here how you want the tracks labelled for a standard 'single-artist',
# single-track encode and also for a single-track 'various-artist' encode.
# (Create a single-track encode with 'abcde -1' from the commandline.)
ONETRACKOUTPUTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}'
VAONETRACKOUTPUTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}'




# Create playlists for single and various-artist encodes. I would suggest
# commenting these out for single-track encoding.
PLAYLISTFORMAT='${OUTPUT}/${ARTISTFILE}-${ALBUMFILE}/${ALBUMFILE}.m3u'
VAPLAYLISTFORMAT='${OUTPUT}/Various-${ALBUMFILE}/${ALBUMFILE}.m3u'




# Put spaces in the filenames instead of the more correct underscores:
mungefilename ()
{
echo "$@" | sed s,:,-,g | tr / _ | tr -d \'\"\?\[:cntrl:\]
}




# What extra options?
MAXPROCS=2 # Run a few encoders simultaneously
PADTRACKS=y # Makes tracks 01 02 not 1 2
EXTRAVERBOSE=y # Useful for debugging
EJECTCD=y # Please eject cd when finished


[B]
ps   [/B]to install in the first place see Andrew's info [here]("http://ubuntuforums.org/showthread.php?t=2055916&p=12397253#post12397253")  and save conf as    .abcde.conf in Home folder

---

### Post by andrew.46 on 2013-04-18
> **mc4man said:**
> 

What determines the encoder(s) used is then solely the OUTPUTTYPE= line [...]

I did not realise that ~/.abcde.conf could be set in this way, thanks mc4man :). I guess you could also specify the OUTPUTTYPE on the commandline rather than manually altering the ~/.abcde.conf file each time, although I have not tested this...

**Edit: **Ooops looks like shantiq has though :)

---

### Post by shantiq on 2013-04-19
Well Andrew credit is due it to seeing mc4man's  .abcde.conf 
it made me see it was an option that way   

am I right in thinking that the -o option is a new one on abcde


hey maybe not.  Either way ; it is so much easier now; once set up the conf can remain "invivisible"; maybe abcde to my mind much more attractive:KS

---

### Post by andrew.46 on 2013-04-19
Almost time another release, blocked by an eyed3 issue at the moment though :(

---

