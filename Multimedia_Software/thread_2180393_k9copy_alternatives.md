---
title: "k9copy alternatives?"
date: 2013-10-12
forum: Multimedia Software
---

### Post by montgoss2 on 2013-10-12
I recently updated to 13.04 and was horrified to find k9copy gone.  I understand that development apparently stopped ages ago, but what is the alternative?
I have yet to find a program that can rip a dual-layer DVD to a 4.3GB iso. I can easily make an iso from the DVD (built-in to nautilus), but they're too big to fit on a regular DVD...

What is everyone else using?

I tried DVD95, which sounds like it should do what I need.  But it doesn't produce a playable/readable iso (crashes VLC every time).

---

### Post by hansdown on 2013-10-12
Welcome to the forum, montgoss2.

Haven't done any ripping lately, but

```
dvdrip and acidrip
```

are two suggestions.

Not sure if they have all the features you need.

---

### Post by montgoss2 on 2013-10-13
I've looked at Acidrip before. It seems to only convert to avi or mpg files.  I don't see a way to generate an iso.  
DVD::rip seems to be the same.  It's all about ripping a DVD to a compressed avi or mpg file.

I already use Handbrake for transcoding and it works quite well.  But that's the second step.  The first is to backup the DVD onto a blank DVD-R...  k9copy was the only program I have found that does that.

The only suggestion I've seen for creating smaller iso's is running a windows program under wine.  There's got to be a linux native app that can do what k9copy did, right??

---

### Post by hansdown on 2013-10-13
```
genisoimage
```

seems to fit the bill.

---

### Post by coldraven on 2013-10-13
Can you copy the package from another distribution? I'm not sure if this would work but I guess that it is worth a try.
Or get the source code and compile it yourself?
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by montgoss2 on 2013-10-23
> **hansdown said:**
> ```
genisoimage
```
seems to fit the bill.

Can you elaborate on that?  I don't see any way to make genisoimage do compression.  Am I just missing it?


[QUOTE=coldraven][COLOR=#000000]Can you copy the package from another distribution? I'm not sure if this would work but I guess that it is worth a try.[/COLOR]
[COLOR=#000000]Or get the source code and compile it yourself?[/COLOR][/QUOTE][COLOR=#000000]I got k9copy running, but it no longer works.  It produces unreadable/unplayable iso's.


I[SIZE=2] did some more searching.  I found several applications that claim to do what I need, but none that actually do what k9copy did...  Nor any that provide a GUI.  :-k

I did find a command-line tool called xdvdshrink that would compress the DVD folder structure (I had to mount the iso to a temp directory in order to read it). Then I was able to use genisoimage to turn that smaller DVD folder back into an iso.  It plays, but it's slightly messed up. I lost DVD navigation/menus and the timestamps are messed up: 1hr47min video shows as 1hr video in VLC...

It's also a multi-step process with at least 2 CLI tools. 
If anyone has better options, I'm all ears.[/SIZE][/COLOR]

---

### Post by stevedude on 2013-12-21
K9Copy was nice and I used it all of the time too. I wish someone would take up redeveloping that program. Anyway, since then I have used "Hand-Brake" and "DeVeDee" to fill the void left by K9Copy. Hand-Brake will rip/convert your DVD into a .MKV format (playable by VLC or Ubuntu's Video Player [Totem] ) and DeVeDee will then burn the .MKV file to a DVD for you to be playable in any DVD device. The downside is it takes about 3X the time to do this in these programs versus what K9Copy could do. The end-result though is a good quality DVD for your use.

---

### Post by 3rdalbum on 2014-04-25
Sorry for the bump, but I have just noticed this. What an enormous shame, it was the only thing that really worked!

I would like to suggest that you could probably run k9copy in an Ubuntu 12.04 VM. That's what I'll be investigating soon.

---

### Post by squakie on 2014-04-25
Hummmm......is/was k9copy open source?  Does anyone know where to get the source and any supporting non-repo's libs, etc.?

---

### Post by squakie on 2014-04-26
Okay, I downloaded the source from sourceforge and have been trying to build it.  I  get an error about an item not being defined.  I didn't copy the tons of output prior to this fatal error:```
Scanning dependencies of target k9copy
[ 63%] Building CXX object CMakeFiles/k9copy.dir/k9copy_automoc.o
In file included from /home/dave/Downloads/k9copy-2.3.8-Source/build/../src/import/k9chapteredit.h:18:0,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/moc_k9chapteredit.cpp:9,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/k9copy_automoc.cpp:15:
/home/dave/Downloads/k9copy-2.3.8-Source/build/../src/import/k9avidecode.h:32:91: error: ‘AVFormatParameters’ has not been declared
 typedef int (*av_open_input_file_t)(AVFormatContext **, const char *,AVInputFormat *,int, AVFormatParameters *);
                                                                                           ^
In file included from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/kdecmpeg2.h:24:0,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/k9decodethread.h:20,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/src/mpeg2/k9plaympeg2.h:24,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/../src/main/k9cropselect.h:33,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/moc_k9cropselect.cpp:9,
                 from /home/dave/Downloads/k9copy-2.3.8-Source/build/k9copy_automoc.cpp:41:
/home/dave/Downloads/k9copy-2.3.8-Source/src/mplayer/k9internalplayer.h:17:7: warning: ‘class k9InternalPlayer’ has virtual functions and accessible non-virtual destructor [-Wnon-virtual-dtor]
 class k9InternalPlayer {
       ^
make[2]: *** [CMakeFiles/k9copy.dir/k9copy_automoc.o] Error 1
make[1]: *** [CMakeFiles/k9copy.dir/all] Error 2
make: *** [all] Error 2
dave@davelaptop:~/Downloads/k9copy-2.3.8-Source/build$ 

``` 

Obviously "AVFormatParameters" is supposed to be from some header somewhere, but I haven't found it.  Does this look familiar to anyone?

If I can get it built against the 14.04 libs, etc., then I'll try it out to see if it works.  If so, I'll need to someone from this thread to try it with one of the dvd's they've had problems with to see if it works then.

---

### Post by squakie on 2014-04-26
Okay, it appears AVFormatParameters is supposed to be part of libavformat-dev.  So, someplace along the line it would appear the libavformat-dev, or perhaps libav itself, has changed.  Does anyone have any ideas on what name took it's place?

---

### Post by squakie on 2014-04-26
I've post for help in the programming sub forum.  When/if I can get something figured out I'll post back here again.  In the mean time, for the poster using an older version and said the results where scrambled up, do you perhaps need to have libdvdcss installed to have it decode a commercial DVD?

---

### Post by squakie on 2014-04-27
Seems the package dvd95 should be able to do all of this, but I can't get it to work correctly with my DVD's.  it's in the regular repositories for 14.04.  Still looking at k9copy, but my knowledge is minimal and k9copy is pretty complex.

---

### Post by squakie on 2014-04-27
Indeed, tried DVD95 again with a different DVD and it does create the smaller ISO (I didn't try burning it to a disk).  And as a previous poster mentioned - VLC crashes when trying to process the ISO (I mounted the ISO).

---

### Post by squakie on 2014-04-27
Ok, some potentially good news!  I found a copy of an old file that was needed in order to build k9copy in 14.04.  I modified just 2 simple things in the source, built it successfully, and currently have a test running (I've never used it before so bear with me! ;) ).  I'll post back the results of that test.

---

### Post by andrew.46 on 2014-04-27
> **squakie said:**
> So, someplace along the line it would appear the libavformat-dev, or perhaps libav itself, has changed.

Perhaps you should hunt out the release version of FFmpeg at the time of the last release of k9copy, some detective work might be in order. But this will mean that you would be working with an old version of FFmpeg which can be less than desirable...

---

### Post by squakie on 2014-04-27
That's why I just tried an old copy of the avformat.h header file and kept it local to the source, not replacing the one on the system.  The dang thing is still running - looks like it is doing what it should - but it a LOT slower than dvd95 was on this same disc.  Of course, the output ISO from dvd95 caused vlc to crash ;)

What I'm hoping:

after this finishes and I find out whether it really worked or not, then I will need to find someone who can help me through the changes from the old ffmpeg/libbav to when ever this "newer" version took effect.  I have a suspicion that's a couple of years ago, right about the time that k9copy stopped being maintained.  Don't get me wrong - I DON'T have a CLUE what the heck the code is doing or what all the functions are doing or what all the structures and their changes are.  I just know that avformat.h is different as delivered now in 14.04 - perhaps even a few releases prior to that.  I would just need someone to tell me what the heck to change the code to to make use of the "new" avformat.h.

I also have to forwarn that right now I have NO clue what dependencies, besides kde - I installed kdevelop and seem to have gotten most everything came with that except for something I found on the net and need to find again to see what it installed).

---

### Post by squakie on 2014-04-27
Jezz, let me guess:  does [this]("https://help.ubuntu.com/community/K9Copy") work?

Just tried this - doesn't work in 14.04.

Also - my system crashed (looks like something to do with my network driver - which was new last night from a 3rd party source.  So, I lost my k9copy test.  Guess I'll restart it.

---

### Post by squakie on 2014-04-27
Okay, thanks people who used to cooperate as the makers/maintainers/etc. of ffmpeg so that we've ended up with ffmpeg as one project and libav as another.  So the problem here seems to be that k9copy was coded for ffmpeg, whereas Ubuntu supported the fork to libav. So, I don't have a copy of ffmpeg's avconvert.h - I have libav's instead (at least that's what seems to be the case).  So.......can anyone tell me how to convert a program written with ffmpeg in mind to using libav instead?

---

### Post by andrew.46 on 2014-04-27
An easier method might be to see if K9copy is happy with a* local* installation of FFmpeg, I see that [Slackware uses 0.11.1]("http://slackbuilds.org/repository/14.0/multimedia/k9copy/") with a heavy warning that all options may not be available. Newer versions of this release are available: FFmpeg 0.11.5 "Happiness" is the most recent. If you can convince k9copy to use this local version (by manipulating the PKG_CONFIG_PATH variable) you might be right...

---

### Post by squakie on 2014-04-28
Part of the problem is that Ubuntu doesn't have ffmpeg anymore - it's not in the repositories.  Since the split, they have supported the libav path instead of ffmpeg.  So ffmpeg isn't really an option in Ubuntu.  Since Slackware is a completely different distribution than Ubuntu, they have apparently decided to still us ffmpeg.  Too bad Ubuntu didn't.  I really don't want to find a way to build ffmpeg in Ubuntu since that means everyone using Ubuntu who would want to try to use a (hopefully) k9copy built for Ubuntu wouldn't have a pre-requisite of trying to install ffmpeg.

---

### Post by squakie on 2014-04-28
I should add, I don't know how fast k9copy ran in the past to compress a dvd9 to dvd5 but keep everything from the source disk, but I had this running tonight for 3 1/2 hours and it was no where near completing.  For the time being, if/until someway can be found to have the source for k9copy compatible with libav, I'm not going to worry about my local build.  I'm more interested in seeing the thing ported to Ubuntu without the need for a seperate avformat.h header file.  That will require someone who is conversant in both ffmpeg (not the program, but all of the libraries that make up the package ffmpeg) and libav so they can either change things themselves or point me to what needs to change.

---

### Post by VMC on 2014-04-28
Here's a guy that has a [GitHub for K9copy]("https://github.com/blobfish/k9copy").
Here's some [comments]("https://www.kubuntuforums.net/showthread.php?64493-k9copy-fans") he made on Kubuntu.org forum.

---

### Post by squakie on 2014-04-28
I'll have to check those out - thanks! 

In the mean time, the version I built in 14.04 works perfectly.  The DVD I was testing with had 20+ titlesets that were over (edit) each pretty large - no wonder it was running for so long!  I put in another DVD with only 3 titlesets - the main one just under 4gb, the next 450mgb and the last 160mb.  Completed quite quickly and the ISO runs perfectly in VLC.

If anyone is interested, just post back and I'll see I can help you get the same thing.

---

### Post by squakie on 2014-04-29
Wow -thanks for those links!!  Someone who knew what they were doing already making everything work in Ubuntu!  Yeah!

---

### Post by George_Bush on 2014-05-25
FYI I downloaded this package [http://pkgs.org/ubuntu-12.04/ubuntu-universe-amd64/k9copy_2.3.8-1_amd64.deb.html](http://pkgs.org/ubuntu-12.04/ubuntu-universe-amd64/k9copy_2.3.8-1_amd64.deb.html) and just copied the binaries into /usr/bin. It seems to work in kubuntu 13.10. 
I have several directories with movies I had been just copying with dvdbackup i.e. no compression and no copying to dvd's. I have now successfully created 4.3G iso's from some of those directories. I havent actually copied any dvd's yet.

---

### Post by George_Bush on 2014-06-08
It turns out that k9copy will not do the whole dvd copy/shrink/burn, I still have to use dvdbackup and dvdauthor to copy the dvd. Once I have the necessary files I use k9copy to shrink the VOB files and create the iso to burn.

---

### Post by mc4man on 2014-06-09
What is the intended use (generally) of k9copy at this point (trusty
Looking at the github edit & a package in a ppa it would seem only useful to rip dvd's to file or iso (either in whole or part) & only dvds that have no or much older structure protection

 As far as using a recent ffmpeg for any encoding tasks, (assuming ffmpeg is in a bin in PATH), most would be worthless, exception seems to be to extract audio only which does work with a little help.
(k9 will not use avconv for encoding 

Using mencoder for any encoding likely works ok though I'm sure in general handbrake would be better.

---

