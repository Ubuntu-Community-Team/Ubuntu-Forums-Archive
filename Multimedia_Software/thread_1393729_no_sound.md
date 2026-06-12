---
title: "no sound"
date: 2010-01-29
forum: Multimedia Software
---

### Post by joe10 on 2010-01-29
wondering if any one can help me. I'm brand new to this sort of thing. so far ubuntu is does everything i need it except play some files from my church. they are wma format. i can down load them and i can change the format to ogg and they still dont play. i have tried several of the players offered  and none seem to work. rhythm box , audacious 2 , movie player,m player media player,and vlc media player. the web site is [Grace Bible Church of Houston]("http://www.gracebiblehouston.com/")

---

### Post by quixote on 2010-01-31
When you say you change the format to ogg, what are you using to do that?  Maybe the conversion isn't working.  You can also play wma directly, but you need files that tell the media players how to do that.  Those things are called "codecs" and there are dozens of them.

a) Are you sure the sound is working at all?  There's (maybe too much) troubleshooting information here, [https://help.ubuntu.com/community/SoundTroubleshooting#Loading%20a%20working%20sound%20configuration](https://help.ubuntu.com/community/SoundTroubleshooting#Loading%20a%20working%20sound%20configuration). 

b) I've found these very thorough instructions useful:  [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683").  It's a lot to plow through, but maybe if you skip around and skim, there'll be some useful pointers there.  At the very least, it tells you which files and codecs to download.

---

### Post by Yellow Pasque on 2010-01-31
You need w32codecs package from Medibuntu: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
Then you can use mplayer.

---

### Post by andrew.46 on 2010-01-31
Hi Joe,

I downloaded one of these files:

```
wget http://www.gracebiblehouston.com/recordings/bible_study/2010/09-I%20John%2019.wma
```

and on closer examination it looks like it is a very Microsoft audio format:

```

andrew@skamandros~/Desktop$ mplayer '09-I John 19.wma' 
MPlayer SVN-r30473-4.3.3 (C) 2000-2010 MPlayer Team

Playing 09-I John 19.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: I John 1:9
 author: David Dunn
 copyright: Grace Bible Church - Houston, Texas
 comments: 2010-01-27
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 16000 Hz, 1 ch, s16le, 12.0 kbit/4.69% (ratio: 1500->32000)
**[COLOR="Blue"]Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)[/COLOR]**
==========================================================================
AO: [oss] 16000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:   7.8 (07.7) of 3240.7 (54:00.6)  1.6% 

```

If you are running a 32bit version of Ubuntu you should have no troubles because, as Temujin has already mentioned, the w32codecs from Medibuntu will allow MPlayer to play this file. If you have a 64bit installation you are in a bit of trouble though...

All the best,

Andrew

---

### Post by mc4man on 2010-01-31
> if you have a 64bit installation you are in a bit of trouble though...

Just set up a 64 bit install and what was really simple was to run a cli mplayer thru wine, either for playback or to extract the audio to .wav and then convert to ogg or whatever.

There were 2 ways - thru the linux terminal, though with no keyboard controls that's better for extraction.

Or thru a 'win' command prompt which allowed for controls.
(even played some video well, didn't look into directx 10 ect. Edit: -vo gl2 works quite well

> doug@doug-laptop:~$ cmd
CMD Version 1.0.1

H:\>Mplayer1\mplayer.exe John19.wma -ao pcm:fast:waveheader:file=john19.wav
fixme:msvcrt:MSVCRT__sopen : pmode 0x01b6 ignored
MPlayer Sherpya-SVN-r30369-4.2.5 (C) 2000-2009 MPlayer Team
getch2: 6 can't get number of input events  [disabling console input]

Playing John19.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 title: I John 1:9
 author: David Dunn
 copyright: Grace Bible Church - Houston, Texas
 comments: 2010-01-27
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 16000 Hz, 1 ch, s16le, 12.0 kbit/4.69% (ratio: 1500->32000)
Selected audio codec: [wma9spdmo] afm: dmo (Windows Media Audio 9 Speech DMO)
==========================================================================
[AO PCM] File: john19.wav (WAVE)
PCM: Samplerate: 16000Hz Channels: Mono Format s16le
[AO PCM] Info: Faster dumping is achieved with -vc null -vo null -ao pcm:fast
[AO PCM] Info: To write WAVE files use -ao pcm:waveheader (default).
AO: [pcm] 16000Hz 1ch s16le (2 bytes per sample)
Video: no video
Starting playback...


---

### Post by joe10 on 2010-01-31
I can play  my music cd's and watch and hear streaming vidios like youtube and hulu I haven't tried a dvd though. i used  sound converter to change the format form wma to ogg and that didnt work. I'm not very slick about this stuff I'm brand new  at tinkering with computers in general thanks for the help I'll be off line for a while as i am in the middle of move when i get a chance i'll get back with you.  Joe Yeiser

---

### Post by mc4man on 2010-01-31
> I'm not very slick about this stuff I'm brand new at tinkering with computers in general thanks for the help I'll be off line for a while as i am in the middle of move when i get a chance i'll get back with you

I'd say the odds are you have a 32 bit install, so the above instructions to add the medibuntu repo, install w32codecs and mplayer should work out for you.
You can also install a gui for mplayer like gnome-mplayer or smplayer.

I don't think soundconverter can convert wma speech in karmic, if not there are other converters that can if need be.

If you run this in a terminal *Applications > Accessories -> terminal, it will show you what your install is
```
uname -m
```

64 bit - 
> doug@doug-laptop:~$ uname -m
[COLOR="Blue"]x86_64[/COLOR]

if it returns i686 or i386 then you have a 32 bit install

---

### Post by quixote on 2010-01-31
Yup, the medibuntu repository is essential for getting all the necessary codexes.  Good point.

Adding it involves the following steps (from the [Comprehensive Multimedia Guide]("http://ubuntuforums.org/showthread.php?t=766683")): > 
Quick Method using command line: Open the terminal (Applications > Accessories > Terminal) and paste the following command into it:  *[select and copy with ctrl-c as usual, but in the terminal, paste with ctrl-**shift**-v]*

sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

> Manual Method: If the above method didn't work, and you received an error, you will have to add the repository manually, which is actually quite easy. First of all, open the sources file with your default or favourite text editor (replace "gedit" with "kwrite" in Kubuntu and "mousepad" in Xubuntu):

gksudo gedit /etc/apt/sources.list

Add the following two lines to the bottom of the list, remembering to change the Ubuntu version accordingly:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free *[eg substitute jaunty if that's what you're using]*
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

Finally, close and save the sources file and install the Medibuntu key by copying and pasting the following command into the terminal:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

> Ubuntu Users: It's also a good idea to make sure the Multiverse and Universe repositories are enabled, although they should be enabled by default in the latest versions of Ubuntu. To make sure they are, go to "System > Administration > Software Sources" and tick whichever sources you wish to use,

Hope your move is going well!

---

