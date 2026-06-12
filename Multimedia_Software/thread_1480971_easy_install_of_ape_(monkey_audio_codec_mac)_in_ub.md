---
title: "easy install of ape (monkey audio codec mac) in ubuntu"
date: 2010-05-12
forum: Multimedia Software
---

### Post by shantiq on 2010-05-12
**[==>> here]("http://ubuntuforums.org/showpost.php?p=9562445&postcount=3")   or [there]("http://ubuntuforums.org/showpost.php?p=11066731&postcount=16")**

---

### Post by shantiq on 2010-05-12
[B][COLOR="Blue"]also INFO for qmmp and xmms



Ape plays in qmmp through the ffmpeg plugin and in xmms with the [libmacinput.so]("http://www.hqshare.net/redirector.php?url=http%3A%2F%2Fmembres.lycos.fr%2Fmazzaru%2Flibmacinput.so.gz") which needs to Be in your home/.xmms/plugin folder  


-====>go into your home folder control H to find hidden .xmms folder[/COLOR][/B]

---

### Post by shantiq on 2010-07-08
one step install


the .deb you need in attachment
here below for 32-bit and 64-bit

works all the way up to Lucid

---

### Post by shantiq on 2010-08-01
might be of interest to some of you


from [ here]("http://www.legroom.net/software/apeinfo")  and  [ here]("http://www.legroom.net/mysoft") 


[COLOR=#000000][FONT=Times New Roman][COLOR=#494949][FONT=Arial]**Introduction**

apeinfo is CLI (command line interface) program designed to display tag data and audio format information for [APE (Monkey's Audio)]("http://www.monkeysaudio.com/") files.
Monkey's Audio is a lossless audio compression format, similar to [FLAC]("http://flac.sourceforge.net/").  It's become fairly popular, but suffers from two primary limitations; very limited cross-platform support (only Windows is officially supported), and a non-free license (note: this may have recently changed).  As a result, I wanted an easy way to convert APE files to the FLAC format, which is my preferred lossless compression format.  There are no available CLI APE tag readers available for Linux at the time of this writing, so I modified a sample program included in the MAC distribution to output this information.  I then use this information in my [Convert to FLAC]("http://ubuntuforums.org/software/convtoflac") script to migrate the APE tags to the new FLAC file.
apeinfo is written in C++, and utilizes the [MAC]("http://www.supermmx.org/linux/mac/") (Monkey's Audio Codec non-win32 ports) libraries written by Matthew T. Ashland.  Also, special thanks to Bill Anderson for his much appreciated assistance with developing and troubleshooting apeinfo.
[Return to top]("http://ubuntuforums.org/#introduction")
**Download  *Current Version: 1.1, Released: 05/13/2009***

[apeinfo 1.1 (64-bit) binary]("http://ubuntuforums.org/files/software/apeinfo_64") (140.3 KB) - This is a 64-bit compiled version of apeinfo.  It was compiled on a Kubuntu Linux system with GCC 4.3.3 and glibc 2.9.
[apeinfo 1.0 (32-bit) binary]("http://ubuntuforums.org/files/software/apeinfo_32") (127.54 KB) - This is a 32-bit compiled version of apeinfo.  It was compiled on a Gentoo Linux system with GCC 3.4.4 and glibc 2.3.5.
[apeinfo 1.1 source]("http://ubuntuforums.org/files/software/apeinfo11_source.tgz") (6.75 KB) - This is the apeinfo source code.  If you receive any error messages when trying to run the binary version, try using this instead.  To compile it, also download the MAC source code and follow the instructions below.
[ChangeLog]("http://ubuntuforums.org/files/software/apeinfo_changelog.txt") - apeinfo development details
[Return to top]("http://ubuntuforums.org/#introduction")
**Installation**

**Downloading apeinfo binary**

Installation of the apeinfo binary is simple:

[LIST=1]
[*]Download the binary
[*]Copy to a directory in your $PATH (eg, /usr/local/bin/)
[*]Ensure that the binary has the execute bit set (eg, chmod a+x /usr/local/bin/apeinfo)
[/LIST]
Try executing apeinfo after installation.  If it returns usage information, then you're good to go.  If you get any error messages, then you'll likely need to follow the compilation instructions below.
**Compiling apeinfo from source**

To compile apeinfo, follow these steps

[LIST=1]
[*]Download the apeinfo source tarball above
[*]Download the [MAC source tarball]("http://www.supermmx.org/resources/linux/mac/mac-3.99-u4-b5.tar.gz")
[LIST]
[*]Note: This was originally written and compiled against MAC version 3.99-u4-b5.  Other versions should work as well, but are not guaranteed.
[/LIST]
 
[*]Extract the MAC tarball
[*]Extract the apeinfo tarball to the following directory: mac-<version>/src/Examples/Analyze/Sample1/
[LIST]
[*]Note: This will overwrite the two makefiles in that directory
[/LIST]
 
[*]From the root of the MAC source code, run ./configure --disable-shared --enable-static && make
[LIST]
[*]This will configure the MAC environment and compile a static apeinfo binary
[/LIST]
 
[*]Copy mac-<version>/src/Examples/Analyze/Sample1/apeinfo to a directory in your $PATH (eg,/usr/local/bin/)
[*]*Optional:*  If you'd like to install the mac binary as well, which can be used to encode or decode APE files, repeat the above step for mac-<version>/src/Console/mac
[/LIST]
Execute apeinfo to verify that compilation and installation was successful.  Once apeinfo is installed, you can delete the MAC source code if you'd like.
[Return to top]("http://ubuntuforums.org/#introduction")
**Usage**

Execute apeinfo -h to display the apeinfo help information.  This will describe the syntax for running the program and list all available options.  Depending on which option is used, apeinfo will display detailed information about the given APE file, or will display a list of all tags in [VORBISCOMMENT format]("http://www.xiph.org/vorbis/doc/v-comment.html").  The VORBISCOMMENT tags can be be applied to another file using a separate program, such as [Convert to FLAC]("http://ubuntuforums.org/software/convtoflac").
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by l-x-l on 2010-08-12
Many thanks for this.

---

### Post by zelo78 on 2010-12-15
Thanks a lot!
It works!

---

### Post by shantiq on 2010-12-16
Once installed enter ```
mac
``` in a terminal 
and this will come up


```
--- Monkey's Audio Console Front End (v 3.99) (c) Matthew T. Ashland ---
Proper Usage: [EXE] [Input File] [Output File] [Mode]

Modes: 
    Compress (fast): '-c1000'
    Compress (normal): '-c2000'
    Compress (high): '-c3000'
    Compress (extra high): '-c4000'
    Compress (insane): '-c5000'
    Decompress: '-d'
    Verify: '-v'
    Convert: '-nXXXX'

Examples:
    Compress: mac.exe "Metallica - One.wav" "Metallica - One.ape" -c2000
    Decompress: mac.exe "Metallica - One.ape" "Metallica - One.wav" -d
    Verify: mac.exe "Metallica - One.ape" -v
    (note: int filenames must be put inside of quotations)

```

fairly straightforward

```
mac "inputfile.wav" "outputfile.ape" -c5000
```

              =======================================================
If you want to bulkconvert to and from ape change directory 

cd to your files then enter

Compress (remove red section if you want to keep the original file)

```
for f in *.wav; do mac "$f"  "${f%.wav}.ape" -c5000 [COLOR="Red"]&& rm "$f"[/COLOR];  done

```


Decompress

```
for f in *.ape; do mac "$f"  "${f%.ape}.wav" -d [COLOR="Red"]&& rm "$f"[/COLOR];  done

```

---

### Post by shantiq on 2011-03-30
and for 64-bit...

---

### Post by d-Pixie on 2011-05-13
Thank you for the 64bit deb version of mac ;o) Works like a charm on 10.10 for me ...

---

### Post by Bitter Peace on 2011-05-23
A big thank you from me for the 64-bit version, as well. 

I remember installing mac the last time was a big pain in the ***, so this is appreciated.

---

### Post by barmaley on 2011-06-06
Hi, ubuntu people
I was trying to compile mac-3.99-u4-b5 on my ubuntu 11.04 32bit version, and I got the following error:
APELink.cpp: In member function 'void CAPELink::ParseData(const char*, const str_utf16*)':
APELink.cpp:66:55: error: invalid conversion from 'const char*' to 'char*'
APELink.cpp:67:66: error: invalid conversion from 'const char*' to 'char*'
APELink.cpp:68:68: error: invalid conversion from 'const char*' to 'char*'
APELink.cpp:69:70: error: invalid conversion from 'const char*' to 'char*'
make[3]: *** [APELink.lo] Error 1
make[3]: Leaving directory `/home/dosin/soft/audacious/mac-3.99-u4-b5/src/MACLib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dosin/soft/audacious/mac-3.99-u4-b5/src/MACLib'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dosin/soft/audacious/mac-3.99-u4-b5/src'
make: *** [all-recursive] Error 1

Can someone help with the compilation, please.
Thanks.

---

### Post by shantiq on 2011-06-06
may i suggest the [deb route]("http://ubuntuforums.org/showpost.php?p=9562445&postcount=3")


i think i tried to compile once and never got there; but hey someone might come along and help you with this; personally the debs have always worked on any of the distros   your choice of course:KS

---

### Post by barmaley on 2011-06-06
Thanks for your help.
I have tried to use the deb-file, but there was a problem with that as well:

dpkg: warning: parsing file '/var/lib/dpkg/available' near line 52069 package 'mac-3.99-u4':

 error in Version string 'b3-1': version number does not start with digit

dpkg: error processing /home/dosin/soft/audacious/mac-3.99-u4_b3-1_i386.deb (--install):

 parsing file '/var/lib/dpkg/tmp.ci/control' near line 7 package 'mac-3.99-u4':

 error in Version string 'b3-1': version number does not start with digit

Errors were encountered while processing:

May be the file is obsolete or incompatible with the 11.04 ubuntu?

---

### Post by kuh3h3 on 2011-06-27
i had same error.
i add const_cast<char*> to error line.
but i don`t know this is right solution :)
anyway compile ok. 

    if (pData != NULL)
    {
        // parse out the information
        char * pHeader = const_cast<char*>(strstr(pData, APE_LINK_HEADER));
        char * pImageFile = const_cast<char*>(strstr(pData, APE_LINK_IMAGE_FILE_TAG));
        char * pStartBlock = const_cast<char*>(strstr(pData, APE_LINK_START_BLOCK_TAG));
        char * pFinishBlock = const_cast<char*>(strstr(pData, APE_LINK_FINISH_BLOCK_TAG));

and had another minor error.
copied file with same name

[mac-3.99-u4-b5/src/Examples/Analyze/Sample1]$ cp apeinfo.cpp Sample1.cpp

---

### Post by shantiq on 2011-06-27
[QUOTE=]

May be the file is obsolete or incompatible with the 11.04 ubuntu?[/QUOTE]


BARMaLEY i have installed it on my natty 64-bit and it works here; sorry i do not have the technical competence to understand the problem you have encountered    no doubt someone will.  best of luck

---

### Post by shantiq on 2011-07-20
If anyone one wants another route to installing APE   equally straightforward   (thanx to Ibidem)   here it is (32-bit or 64)


```
sudo add-apt-repository ppa:ibid-ag/oldgtk1 
```
```
sudo apt-get update
```
```
sudo apt-get install monkeys-audio
```


works very well too:KS

---

### Post by andrew.46 on 2011-07-22
Hi shantiq!!

I have just started dabbling with ape after reading a few of your comments about it. I see that it is possible to add some meta-tags to ape files and I have found that this is easy enough with EasyTag. Do you know how to do this from the commandline?

---

### Post by shantiq on 2011-07-22
wow Andrew   from the command line?   no but i have used easytag quite often with the gui

more than happy to have the info if you have it handy:KS i am sure many will welcome it

---

### Post by andrew.46 on 2011-07-22
Well, I could not find any commandline utilities that wrote authentic ape tags but it did not take long to see that ape files take id3v2 tags quite happily. Mind you vlc and xmms did not seem to like the resulting file :(. I produced it as follows, first ripping the first track from the Solaris audio cd:

```

cdda2wav -t 1 -cddb=0 -paranoia

```

Then converting to ape:

```

mac 'audio.wav' 'solaris_01.ape' '-c4000'

```

and then adding in the tags drawn from the cddb lookup:

```

id3v2 --album "Solaris" --artist "Cliff Martinez" \
      --song "Is That What Everybody Wants?" \
      --track "01/11" --year "2002" --genre "Soundtrack" \
      solaris_01.ape

```

I have placed the file here if anybody wants to try the results against other media players:

```

wget http://www.andrews-corner.org/tmp/solaris_01.ape

```

Not quite sure why only MPlayer is happy with this file, but then I am a little new to Monkey's Audio encoding :).

**Edit**: Looks like the tags are a problem with vlc, plays fine until tagged ... Mind you apeinfo shows the tags nicely:

```

andrew@skamandros~/Desktop$ **[COLOR="Red"]apeinfo_32 solaris_01.ape [/COLOR]**

File Information
     File Name: solaris_01.ape
     File Size: 11934 kb
   APE Version: 3.99
   Compression: Extra High
    Tag Format: ID3

Audio Information
   Track Length: 2:48.600 (168 s)
    Samples/sec: 44100 Hz
    Bits/sample: 16
       Channels: 2
     Peak level: -1

Tag Information
    Album: Solaris
   Artist: Cliff Martinez
    Genre: Soundtrack
    Title: Is That What Everybody Wants?
    Track: 1
     Year: 2002

```

---

### Post by shantiq on 2011-07-22
well cool stuff nice tune

xmms happy here on 64-bit natty but crashes when i want to read info
mplayer from command line no good here   does not start or atrocious white noise

```
mplayer solaris_01.ape
MPlayer 1.0rc4-4.5.2 (C) 2000-2010 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing solaris_01.ape.
libavformat file format detected.
[mp3 @ 0x17d6de0]Header missing
    Last message repeated 1041 times
[mp3 @ 0x17d5da0]Estimating duration from bitrate, this may be inaccurate
[lavf] stream 0: audio (mp3), -aid 0
Clip info:
 album: Solaris
 artist: Cliff Martinez
 title: Is That What Everybody Wants?
 track: 01/11
 TYER: 2002
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
ADecoder init failed :(
ADecoder init failed :(
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'mp3float' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Unknown/missing audio format -> no sound
ADecoder init failed :(
Requested audio codec family [mad] (afm=libmad) not available.
Enable it at compilation.
Requested audio codec family [mp3acm] (afm=acm) not available.
Enable it at compilation.
Opening audio decoder: [hwmpa] MPEG audio pass-through (fake decoder)
Cannot sync MPA frame: 0
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x55.
Audio: no sound
Video: no video


```

[B]but opens in the gui   MoviePlayer
[/B]
qmmp will not play and gives me this info  !!!!!
```

Sample rate
0 Hz
Length
-34620872:-22
Bitrate
0 kbps
Channels
0
File size
11934 KB

```

no vlc

but deadbeef does play and tags perfect     go figure   bloody machines:D:D

---

### Post by andrew.46 on 2011-07-22
Goodness me it all sounds a bit hit and miss :). The most recent MPlayer has no trouble here:

```

andrew@skamandros~/html/andrews-corner/tmp$ mplayer solaris_01.ape 
MPlayer SVN-r33883-4.5.3 (C) 2000-2011 MPlayer Team

Playing solaris_01.ape.
libavformat file format detected.
[lavf] stream 0: audio (ape), -aid 0
[B][COLOR="Red"]Clip info:
 album: Solaris
 artist: Cliff Martinez
 title: Is That What Everybody Wants?
 track: 01/11
 genre: Soundtrack
 date: 2002[/COLOR][/B]
Load subtitles in ./
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 0.0 kbit/0.00% (ratio: 0->176400)
Selected audio codec: [ffape] afm: ffmpeg (FFmpeg Monkey's Audio)
==========================================================================
AO: [oss] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A: 168.3 (02:48.2) of 168.5 (02:48.5)  4.2% 


Exiting... (End of file)

```

Perhaps you should try one of those svn MPlayer guides that seem to litter these forums! BTW have a look at the movie one day, it does have George Clooney in it but is still a great movie :). I am such a big fan that I have a copy of the original Russian version of Solaris and a well thumbed copy of the book by Stanislaw Lem.

---

### Post by shantiq on 2011-07-22
now there has to be a way to tag with rubyripper for sure using

id3v2   as Andrew suggested

```
 id3v2
Usage: id3v2 [OPTION]... [FILE]...
Adds/Modifies/Removes/Views id3v2 tags, modifies/converts/lists id3v1 tags

  -h,  --help               Display this help and exit
  -f,  --list-frames        Display all possible frames for id3v2
  -L,  --list-genres        Lists all id3v1 genres
  -v,  --version            Display version information and exit
  -l,  --list               Lists the tag(s) on the file(s)
  -R,  --list-rfc822        Lists using an rfc822-style format for output
  -d,  --delete-v2          Deletes id3v2 tags
  -s,  --delete-v1          Deletes id3v1 tags
  -D,  --delete-all         Deletes both id3v1 and id3v2 tags
  -C,  --convert            Converts id3v1 tag to id3v2
  -1,  --id3v1-only         Writes only id3v1 tag
  -2,  --id3v2-only         Writes only id3v2 tag
  -r,  --remove-frame "FRAMEID"   Removes the specified id3v2 frame
  -a,  --artist       "ARTIST"    Set the artist information
  -A,  --album        "ALBUM"     Set the album title information
  -t,  --song         "SONG"      Set the song title information
  -c,  --comment      "DESCRIPTION":"COMMENT":"LANGUAGE"  
                            Set the comment information (both
                            description and language optional)
  -g,  --genre   num        Set the genre number
  -y,  --year    num        Set the year
  -T,  --track   num/num    Set the track number/(optional) total tracks

You can set the value for any id3v2 frame by using '--' and then frame id
For example: 
        id3v2 --TIT3 "Monkey!" file.mp3
would set the "Subtitle/Description" frame to "Monkey!". 

```



the no tag rubyripper    other line code   is [thus]("http://ubuntuforums.org/showpost.php?p=9630025&postcount=24")

```
mac  "%i" "%o"  .ape -c5000  
```



so to add tags   i have tried   **do not use**

```
mac  "%i" "%o"  .ape -c5000 - id3v2 --A "%b" --a "%a" --t "%t"
```

```
mac  "%i" "%o"  .ape -c5000  id3v2 --A "%b" --a "%a" --t "%t"
```

```
mac  "%i" "%o" - id3v2 --A "%b" --a "%a" --t "%t" .ape -c5000 
```

```
mac  "%i" "%o"  id3v2 --A "%b" --a "%a" --t "%t" .ape -c5000

```



not as yet working must have the order wrong or missing something    any ideas?

---

### Post by mc4man on 2011-07-22
> **kuh3h3 said:**
> i had same error.
i add const_cast<char*> to error line.
but i don`t know this is right solution :)
anyway compile ok. 

    if (pData != NULL)
    {
        // parse out the information
        char * pHeader = const_cast<char*>(strstr(pData, APE_LINK_HEADER));
        char * pImageFile = const_cast<char*>(strstr(pData, APE_LINK_IMAGE_FILE_TAG));
        char * pStartBlock = const_cast<char*>(strstr(pData, APE_LINK_START_BLOCK_TAG));
        char * pFinishBlock = const_cast<char*>(strstr(pData, APE_LINK_FINISH_BLOCK_TAG));

and had another minor error.
copied file with same name

[mac-3.99-u4-b5/src/Examples/Analyze/Sample1]$ cp apeinfo.cpp Sample1.cpp
The ppa would be best route, if building this is patch (b5)
```

--- monkeys-audio-3.99-u4-b5.orig/src/MACLib/APELink.cpp	2006-06-01 11:00:57.000000000 +0200
+++ monkeys-audio-3.99-u4-b5/src/MACLib/APELink.cpp	2010-02-08 10:47:15.000000000 +0100
@@ -63,10 +63,10 @@
     if (pData != NULL)
     {
         // parse out the information
-        char * pHeader = strstr(pData, APE_LINK_HEADER);
-        char * pImageFile = strstr(pData, APE_LINK_IMAGE_FILE_TAG);
-        char * pStartBlock = strstr(pData, APE_LINK_START_BLOCK_TAG);
-        char * pFinishBlock = strstr(pData, APE_LINK_FINISH_BLOCK_TAG);
+        char * pHeader = (char*)strstr(pData, APE_LINK_HEADER);
+        char * pImageFile = (char*)strstr(pData, APE_LINK_IMAGE_FILE_TAG);
+        char * pStartBlock = (char*)strstr(pData, APE_LINK_START_BLOCK_TAG);
+        char * pFinishBlock = (char*)strstr(pData, APE_LINK_FINISH_BLOCK_TAG);
 
         if (pHeader && pImageFile && pStartBlock && pFinishBlock)
         {
```
The i386 package linked in this thread is mis-packaged, again use the ppa or build

---

### Post by andrew.46 on 2011-07-22
Interestingly enough EasyTag appears to be using APEv2 tagging, as I found when I added the same tags with EasyTag 2.1.6:

```

andrew@skamandros~/Desktop$ apeinfo_32 solaris_01.ape 

File Information
     File Name: solaris_01.ape
     File Size: 11932 kb
   APE Version: 3.99
   Compression: Extra High
    **[COLOR="Red"]Tag Format: APEv2[/COLOR]**

Audio Information
   Track Length: 2:48.600 (168 s)
    Samples/sec: 44100 Hz
    Bits/sample: 16
       Channels: 2
     Peak level: -1

Tag Information
    Album: Solaris
   Artist: Cliff Martinez
    Genre: Soundtrack
    Title: Is That What Everybody Wants?
    Track: 01/11
     Year: 2002

```

and this use of tags meant that the file plays fine in vlc so it is probably a better choice than using id3v2 tagging. It is a great pity that a commandline APEv2 tagger does not appear to exist :(.

**Edit:** Looks like I was missing a Monkey's Audio plugin for xmms, once I had this in place xmms played files easily with either tags. Looks like vlc has a problem though...

---

### Post by mc4man on 2011-07-22
I'd guess if you wish to rip/encode and tag thru RR then you should look at doing an && like for NeroAacEnc and NeroAacTag

So for id3v2 something like this for starters (-cxxxx whatever

```
mac  "%i" "%o".ape -c2000 && id3v2  %o.ape --artist %a --album %b --song %t --genre %g --track %n


```
Note that when using ruby-1.9.2 to fix the gui performance RR has no issue with other codecs, -  there is something up w/ .ape, so the ruby-1.8 and rrip_cli is advised

Edit: while it may work - the previous posted mac parameters has a space between "%o" and .ape, I'd not use one..
(and the same deal w/ vlc - doesn't like id3v2 in ape but is fine w/ apetags, have a prog here that runs in wine and does ape fine dBpoweramp

---

### Post by shantiq on 2011-07-22
thank you mc4   you really are a wizard on all this stuff :KS

i was missing &&    and i had put id3v2 in the wrong place


so will add it to the collection.   would there be a way to tag with the APEv2 mentioned by Andrew instead of id3v2   when ripping with RR?


wiki says


> APEv2
The Musepack format developer Frank Klemm extended the original APE tag format to add a header, allowing APE tags to be at the beginning of files, and also allowed metadata values to be Unicode rather than simply ASCII. Because of its simplicity and flexibility, the[COLOR="Red"] WavPack [/COLOR]and OptimFROG formats also adopted it as their primary tag format. Version 3.99 of Monkey's Audio also switched from using APEv1 to APEv2.
foobar2000, and Jack! The Knife software can tag MP3 files with APEv2 tags instead of ID3 tags.[citation needed] Some music library managers and mass taggers like MusicBee, Mp3tag also support this feature. The tagging string APETAGEX signals the start of a APEv2 record, and the string TAG signals the start of an ID3v1 tag. The popular media player software "Winamp" also support reading and writing of APEv2 tags in mp3 files..


---

### Post by shantiq on 2011-07-23
Having a look around found there is also a small program called [**Apetag**]("http://muth.org/Robert/Apetag/")   also zipped and attached here


Instructions


```
apetag -h
APETAG version: 146  (C) Robert Muth 2003 and onwards
Web: http://www.muth.org/Robert/Apetag

Usage: [COLOR="Red"]apetag -i input-file -m mode  {-p tag=value}*[/COLOR]

change or create APE tag for file input-file

apetag operates in one of three modes:

Mode read (default):
	read and dump APE tag if present

Mode update:
	change selected key,value pairs
	the pairs are specified with the -p options
		e.g.: -p Artist=Nosferaru -p Album=Bite 
	remove item Artist, change item Album to Cool
	tags not listed with the -p option will remain unchanged
	tags with empty vaalues are removed

Mode overwrite:
	Overwrite all the tags with items specified by the -p options
	tags not listed with the -p option will be removed
	this mode is also used to create ape tags initially

Switch summary:

debug    default ["0"]
	enable debug mode
i string   default [""]
	specify input file
m string   default ["read"]
	specify mode (read, update or overwrite)
p string   default ["$none$"]
	specify ape tag and value, arguments must have form tag=val, this option 
	can be used multiple times
```


so i tried ( after a few attempts:KS )

```
mac  "%i" "%o".ape -c5000   && apetag  -i  %o.ape  -m overwrite  -p Trackname=%t  -p Artist=%a -p Album=%b   -p Year=%y -p Track=%n  -p Codec=%f
```

and fine   see xmms info on a track ripped with Rubyripper (attached)

=============================================

**STEPS**:

1.  install [rubyripper]("http://linuxappfinder.com/package/rubyripper")
2.  install apetag (attached)   then to activate   also make mac executable

```
sudo mv apetag /usr/bin 

```
```
cd /usr/bin

```
```
 sudo chmod +x apetag  && sudo chmod +x mac

```

3.  enter this line of code in other box in Rubyripper


```
mac  "%i" "%o".ape -c5000   && apetag  -i  %o.ape  -m overwrite  -p trackname=%t  -p Artist=%a -p Album=%b   -p Year=%y -p Track=%n  -p Codec=%f
```

---

### Post by mc4man on 2011-07-23
> found there is also a small program called Apetag 
That seems to be a good find, will have to give it a try

---

### Post by andrew.46 on 2011-07-24
Brilliant shantiq :). Works very nicely on my system, I have replaced the solaris file on my website with one tagged by apetag. BTW you might be interested in making a $HOME/bin folder for yourself, add it to your $PATH and dump little applications like apetag in there. I usually place my custom scripts etc in this location....

---

### Post by shantiq on 2011-07-24
hi Andrew. Nice idea but i am under the impression that Rubyripper needs apetag to be in /usr/bin to be picked up. That is why i place it there.  I also thought that is where all applications are directed when one installs them but i might be wrong thinking that...



PS  the music piece is really nice will check the 2002 version (i actually am a fan of Clooney and Natasha Mcelhone) i always stayed away from that film as the write-ups were poor as for the 1972 version i stayed really away since it is Tarkovsky and i once "suffered" Mirrors :KS:KS  i do not know if you are aware of this but there is a 1968 tv film version too and it is **[here ]("http://torrage.com/torrent/59FE21E7CEC6ED0F3878A083CEB4B3A42A615226.torrent")**also on the ed2k network .   Full thing is here in Russian on YT [Part 1]("http://www.youtube.com/watch?v=hKPTMWwbyR8") [Part 2 ]("http://www.youtube.com/watch?v=yubdkWs_cU8") will seek out subs; there is also [a cut]("http://www.youtube.com/watch?v=_xZ0IG7K4t4") with German subs and [**one**]("http://www.youtube.com/watch?gl=GB&hl=en-GB&v=Y3vWid1xAYw") with english subs

PS2  Your new ape version of the track plays on VLC now but on nothing else !!!   Looks like these files pick up stuff that is related to the system they are on. Weird! Mine work on everything BUT VLC    Go figure....
Maybe humans and machines really cannot understand each other:KS

---

### Post by mc4man on 2011-07-24
You can place it *and anything else, in ~/bin, RR will find
There was a short period some time ago where it seemed to only want neroAacEnc in /usr but that's not the case anymore

(as far as vlc - it plays ape with ape tags if I use another encoder/tagger but not RR and apetag ones, the tags show up fine in vlc's window but no playback. Though this is on 11.10 where nothing good or bad surprises me

Edit: vls's issue's start here - 
[0x8d9a168] main input warning: clock gap, unexpected stream discontinuity
[0x8d9a168] main input warning: feeding synchro with a new reference point trying to recover from clock gap
no big loss really (vlc that is

---

### Post by shantiq on 2011-07-24
> **mc4man said:**
> You can place it *and anything else, in ~/bin, RR will find
There was a short period some time ago where it seemed to only want neroAacEnc in /usr but that's not the case anymore

(as far as vlc - it plays ape with ape tags if I use another encoder/tagger but not RR and apetag ones, the tags show up fine in vlc's window but no playback. Though this is on 11.10 where nothing good or bad surprises me


Thanx for clarifications Mc4 on that. Same in 10.04 on VLC mind!.  But for me plays everywhere else fine Deadbeef Qmmp Xmms mplayer from commandline but not movieplayer (!!) with all tags visible...


Ps has your moniker anything to do with the great MC5 ?

---

### Post by mc4man on 2011-07-24
> Ps has your moniker anything to do with the great MC5 ?
No just based on last name - 
for yr's I've used for email logins and whenever an account would  get spammed I'd dump it and move up a number like mc3man@, mc4man@ ect. ect.
(And when going back to rarely visited sites easier to figure out a forgotten login, not that many combos

---

### Post by andrew.46 on 2011-07-24
> **shantiq said:**
> hi Andrew. Nice idea but i am under the impression that Rubyripper needs apetag to be in /usr/bin to be picked up. That is why i place it there.  I also thought that is where all applications are directed when one installs them but i might be wrong thinking that...

I will admit that I don't use Rubyripper so you are probably correct :). I use $HOME/bin for a handful of applications and scripts:

```

andrew@skamandros~$ ls $HOME/bin
AtomicParsley	       jigdo-file		    rsync_dreamhost.sh
apeinfo_32	       midentify.sh		    rsync_slrn.sh
apetag		       mirror-slackware-current.sh  slackware_updates
ftgws_download.sh      neroAacDec		    sligdo
get_flash_videos-1.24  neroAacEnc		    youtube-dl
janette.sh	       neroAacTag

```

which mostly I call directly from the commandline rather than from within other applications so I guess my usage is a little different to yours.


> PS  the music piece is really nice will check the 2002 version (i actually am a fan of Clooney and Natasha Mcelhone) i always stayed away from that film as the write-ups were poor as for the 1972 version i stayed really away since it is Tarkovsky and i once "suffered" Mirrors :KS:KS  i do not know if you are aware of this but there is a 1968 tv film version too and it is **[here ]("http://torrage.com/torrent/59FE21E7CEC6ED0F3878A083CEB4B3A42A615226.torrent")**also on the ed2k network .   Full thing is here in Russian on YT [Part 1]("http://www.youtube.com/watch?v=hKPTMWwbyR8") [Part 2 ]("http://www.youtube.com/watch?v=yubdkWs_cU8") will seek out subs; there is also [a cut]("http://www.youtube.com/watch?v=_xZ0IG7K4t4") with German subs and [**one**]("http://www.youtube.com/watch?gl=GB&hl=en-GB&v=Y3vWid1xAYw") with english subs

I would recommend watch the Clooney version and make your own judgement, I have watched it many, many times and the story and soundtrack are very well done. I shall chase up the the tv version, I had not heard of it before...

---

