---
title: "HOWTO: Install latest MPlayer and all Codecs (Compile from source)"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by Hub-1 on 2007-01-12
outdated: removed

---

### Post by snoochems on 2007-01-12
Thanks.... it was all working well up until the last line *sudo dpkg -i mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb*.  

I got an error:
[I]
dpkg: error processing mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb[/I]


Being a total noob to linux, i wiggled my way to the folder containing the compiled program, found the file: *mplayer_1.0rc1-1_i386.deb*

This seemed to install the program.  I don't know if this is different to doing it via the terminal... 

Anyways, having assumed it's installed... where do I find the program to launch it???

---

### Post by shrimphead on 2007-01-12
should be in the sound + video menu if you compiled it with the --enable-gui switch otherwise try running 

```
mplayer
```

or

```
gmplayer
```(for a gui) 

from a terminal

---

### Post by Hub-1 on 2007-01-12
> **snoochems said:**
> Thanks.... it was all working well up until the last line *sudo dpkg -i mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb*.  

I got an error:
[I]
dpkg: error processing mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb[/I]


Being a total noob to linux, i wiggled my way to the folder containing the compiled program, found the file: *mplayer_1.0rc1-1_i386.deb*

This seemed to install the program.  I don't know if this is different to doing it via the terminal... 

Anyways, having assumed it's installed... where do I find the program to launch it???


Yes, looks like you did everything right, except point 3j. I mentioned there to set the version number to prevent ubuntu from replacing it with the official ubuntu mplayer.

If you let it stay this way, as soon as you upgrade (i.e. sudo apt-get upgrade), mplayer will be replaced by the slightly older version ubuntu distributes.

---

### Post by BigBadVoodoo on 2007-01-14
it seems that the installation was ok (without --enable-gui part, i got an error telling me to install libpng and libpng -*something i forgot* ,but i couldn't)
but how do i start it now :mrgreen:  the icon for mplayer don't work

---

### Post by Hub-1 on 2007-01-15
> **BigBadVoodoo said:**
> it seems that the installation was ok (without --enable-gui part, i got an error telling me to install libpng and libpng -*something i forgot* ,but i couldn't)
but how do i start it now :mrgreen:  the icon for mplayer don't work
Hmm, I added instructions how to enable additional repositories. The "sudo apt-get build-dep mplayer" command should take care of all dependencies. Without the --enable-gui part, mplayer will compile without a GUI *(Graphical User Interface)*, thus the icon wont work.

---

### Post by healthpellets on 2007-01-16
everything was fine and great until i reached this point:  3j.  checkinstall

it told me that the debian package failed to install, then asked if i wanted to see an error log and i can't move on from there....

thoughts?

edit:  hopefully this isn't a horrible thing to do, but i did just move on and finished with the install.  however, i don't have an MPlayer Icon anywhere...

Additional thoughts?

---

### Post by harrisony on 2007-01-18
> **healthpellets said:**
> everything was fine and great until i reached this point:  3j.  checkinstall

it told me that the debian package failed to install, then asked if i wanted to see an error log and i can't move on from there....

thoughts?

edit:  hopefully this isn't a horrible thing to do, but i did just move on and finished with the install.  however, i don't have an MPlayer Icon anywhere...

Additional thoughts?
Try $ sudo dpkg -i <what you named package here> i did the same thing and then the error log said needs superuser privalges to install it or you could do $sudo checkinstall and then that would generate and then install it
EG:Without sudo checkinstall
```
Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package

Do you want to see the log file?  [y]: y


*** SIGINT received ***

Cleaning up...OK

Bye.

```

**with sudo checkinstall**
```
======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./ChangeLog
./LICENSE
./README

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package...OK

Erasing temporary files...OK

Deleting temp dir...OK


**********************************************************************

 Done. The new package has been installed and saved to

 /home/harrisony/programs-scripts-packages/mplayer/MPlayer-1.0rc1/mplayer_1.0rc1-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r mplayer

****************************************************************
```

TO The Author considering replacing checkinstall & dkpg with sudo checkinstall :)

---

### Post by Natume on 2007-01-18
Well, I followed the how-to, perhaps too well {shrugs}, and got up to trying to run the player with gmplayer.  The error code it gives me is this :

```

MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

```

I should mention that I used sudo checkinstall.  Plain checkinstall gives me the same error that many people have been getting.  As for the skins, I placed them in /usr/lib/mplayer/skin/default, and the codecs in /usr/lib/win32.  Because of all of the output during the make session, I can't really say if that went well, except that there were a number of warnings that I saw early on, usually dealing with a deprecated something-or-other.

---

### Post by harrisony on 2007-01-19
> **Natume said:**
> Well, I followed the how-to, perhaps too well {shrugs}, and got up to trying to run the player with gmplayer.  The error code it gives me is this :

```

MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/local/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

```

I should mention that I used sudo checkinstall.  Plain checkinstall gives me the same error that many people have been getting.  As for the skins, I placed them in /usr/lib/mplayer/skin/default, and the codecs in /usr/lib/win32.  Because of all of the output during the make session, I can't really say if that went well, except that there were a number of warnings that I saw early on, usually dealing with a deprecated something-or-other.
hey Natune can you go ```
$ cd /usr/local/share/mplayer/skins/default && ls && cd ./skin && ls
``` and post the output and the make errors and normal :)
also mplayer should be looking in ```
/usr/local/share/mplayer/Skin/default
```
anyway if you run the command and then just post the output we will see

---

### Post by Natume on 2007-01-19
Ran as such, it tells me :

```
bash: cd: /usr/local/share/mplayer/skins/default: No such file or directory
```

But I have a feeling that I should be moving my skins to that directory first.  I'll get back after doing that and running gmplayer / that command again.

Edit : Well, after moving the skins to the directory above, I could open mplayer using gmplayer from the terminal.  Likewise, I'm now listening to an mp3, in what seems to be good quality.  However, there's still two issues.  One, it gives me the following code in error, which doesn't seem to have a huge effect, but is annoying :

```
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
```

Likewise, it gives me (this is number two) a popup window called 'Error!' (which is what it is), telling me that the 'requested audio codec family [mp3] (afm=mp3lib) not available'.  Now, I realize that this was disabled at compilation, as per the instructions in the tutorial, but how would I get rid of this message?

Also, might as well ask here : is there a way to loop a song in mplayer?  Just out of convenience, I ask that ; not that it's really all that important.

Ah, and the following might also be useful :

```
Playing /media/EZ BUS DT/Backup/Otome wa Boku ni Koishiteru/Otome wa Boku ni Koishiteru - 03.avi.
AVI file format detected.
VIDEO:  [XVID]  704x396  24bpp  23.976 fps  870.0 kbps (106.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
Error opening/initializing the selected video_out (-vo) device.
```

This was when I was trying to play an avi file.  I was assuming that the codecs for video files were installed with the codec pack as well, but since it's having issues with this, I'm not entirely sure what to do.  And I apologize for being a noob.  Some of this is probably pretty obvious, I know, but thanks for the help anyway.

Oh, and the new output of the command with the ampersands and all that jazz is as follows.

```
barfwd.png       equalizer.png   next.png      previous.png  stop.png
barnext.png      font.fnt        playbar.png   quit.png      subtitles.png
barplay.png      font.png        playlist.png  README        symbols.fnt
barprevious.png  fullscreen.png  play.png      rev.png       symbols.png
barrev.png       fwd.png         pospb.png     settings.png  VERSION
barstop.png      load.png        pos.png       skin
disc.png         main.png        posvol.png    skins.png
bash: cd: ./skin: Not a directory
```

---

### Post by harrisony on 2007-01-21
> **Natume said:**
> Ran as such, it tells me :

```
bash: cd: /usr/local/share/mplayer/skins/default: No such file or directory
```

But I have a feeling that I should be moving my skins to that directory first.  I'll get back after doing that and running gmplayer / that command again.

Edit : Well, after moving the skins to the directory above, I could open mplayer using gmplayer from the terminal.  Likewise, I'm now listening to an mp3, in what seems to be good quality.  However, there's still two issues.  One, it gives me the following code in error, which doesn't seem to have a huge effect, but is annoying :

```
MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
```

Likewise, it gives me (this is number two) a popup window called 'Error!' (which is what it is), telling me that the 'requested audio codec family [mp3] (afm=mp3lib) not available'.  Now, I realize that this was disabled at compilation, as per the instructions in the tutorial, but how would I get rid of this message?

Also, might as well ask here : is there a way to loop a song in mplayer?  Just out of convenience, I ask that ; not that it's really all that important.

Ah, and the following might also be useful :

```
Playing /media/EZ BUS DT/Backup/Otome wa Boku ni Koishiteru/Otome wa Boku ni Koishiteru - 03.avi.
AVI file format detected.
VIDEO:  [XVID]  704x396  24bpp  23.976 fps  870.0 kbps (106.2 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.10.1 (build 2366/release)
Error opening/initializing the selected video_out (-vo) device.
```

This was when I was trying to play an avi file.  I was assuming that the codecs for video files were installed with the codec pack as well, but since it's having issues with this, I'm not entirely sure what to do.  And I apologize for being a noob.  Some of this is probably pretty obvious, I know, but thanks for the help anyway.

Oh, and the new output of the command with the ampersands and all that jazz is as follows.

```
barfwd.png       equalizer.png   next.png      previous.png  stop.png
barnext.png      font.fnt        playbar.png   quit.png      subtitles.png
barplay.png      font.png        playlist.png  README        symbols.fnt
barprevious.png  fullscreen.png  play.png      rev.png       symbols.png
barrev.png       fwd.png         pospb.png     settings.png  VERSION
barstop.png      load.png        pos.png       skin
disc.png         main.png        posvol.png    skins.png
bash: cd: ./skin: Not a directory
```
errr i think the howto had something about getting a font but i would say grab subfont.ttf (google i gueess) and shove it there and then try again and you would have to recompile mplayer with mp3lib support 
Also what skin are you using

---

### Post by Poka64 on 2007-01-21
how do I remove the codecs from this install?

There is something seriously wrong here, the only files that I can watch in mplayer is .wmv and .mov. If I try to watch anything else the sounds gets all screwed up.

---

### Post by harrisony on 2007-01-21
> **Poka64 said:**
> how do I remove the codecs from this install?

There is something seriously wrong here, the only files that I can watch in mplayer is .wmv and .mov. If I try to watch anything else the sounds gets all screwed up.
try ```
$mplayer <file>
``` and post the output
if you give me a day or to ill try make an unofficial package with it

---

### Post by Natume on 2007-01-21
> **harrisony said:**
> errr i think the howto had something about getting a font but i would say grab subfont.ttf (google i gueess) and shove it there and then try again and you would have to recompile mplayer with mp3lib support 
Also what skin are you using
I'm using the 'productive' skin.  The only one that I really liked and thought fit with my desktop (everything loads fine there, except for the font, of course).

As for the mp3 stuff, the HowTo explicitly said to disable the mp3lib option, so I'm curious about that.  Also, mplayer won't play avis and other files of the sort, can't really create playlists (without just locking up / crashing)... so yeah... it's sorta non-functional, except for a single mp3 played without looping.

Maybe I'll just try to reinstall it with a couple different options, next time.

---

### Post by harrisony on 2007-01-21
> **Natume said:**
> I'm using the 'productive' skin.  The only one that I really liked and thought fit with my desktop (everything loads fine there, except for the font, of course).

As for the mp3 stuff, the HowTo explicitly said to disable the mp3lib option, so I'm curious about that.  Also, mplayer won't play avis and other files of the sort, can't really create playlists (without just locking up / crashing)... so yeah... it's sorta non-functional, except for a single mp3 played without looping.

Maybe I'll just try to reinstall it with a couple different options, next time.
try uninstall it and use a different skin (i use osx-brushed and it worked) i dont know why the author of the how to disabled mp3lib but [https://blueprints.launchpad.net/mplayer/+spec/mplayer-include-mp3lib](https://blueprints.launchpad.net/mplayer/+spec/mplayer-include-mp3lib) has it should be in there
if not ill continue learning how to make a basic deb package :)

---

### Post by mastif on 2007-01-21
When I start a musicvideo in mplayer I get this error after your guide.

Requesting audio codec family
[mp3] (afm=mp3lib) not available.
Enable it at compliaton

but the sound is perfect
and every .mpg video gets fu**** up, video and sound in the .mpg :/

---

### Post by harrisony on 2007-01-21
> **mastif said:**
> When I start a musicvideo in mplayer I get this error after your guide.

Requesting audio codec family
[mp3] (afm=mp3lib) not available.
Enable it at compliaton

but the sound is perfect
and every .mpg video gets fu**** up, video and sound in the .mpg :/
if you were to read the above post which quotes someone having a simillar problem you would be right :) and i dont know if it will work on dapper
(I AM NOT THE AUTHOR OF THIS GUIDE SO DONT BLAME ME!)

---

### Post by mastif on 2007-01-22
yes! now it works, i re-installed it and used a different configuration at step '3h.'

thanks for the howto :)

---

### Post by keith11 on 2007-01-23
This was an excellent guide for installing Mplayer. I was successfully able to install Mplayer, but when I tried to open a movie with it, it gave the following error:

"Error opening/initializing the selected video_out(-vo) device."

This was the exact same error I got in the Mplayer which is offered by default in Ubuntu 6.10 because of which I considered installing this newer version of Mplayer, but I am running into the same error again. What is going wrong here? Thanks.

I have been trying to get Mplayer to play streaming movies for a couple of weeks now, first in Mandriva and now in Ubuntu, but with no success. Is there another player, for example VLC which can play streaming video and audio? How to install it and configure it?

---

### Post by harrisony on 2007-01-23
> **keith11 said:**
> This was an excellent guide for installing Mplayer. I was successfully able to install Mplayer, but when I tried to open a movie with it, it gave the following error:

"Error opening/initializing the selected video_out(-vo) device."

This was the exact same error I got in the Mplayer which is offered by default in Ubuntu 6.10 because of which I considered installing this newer version of Mplayer, but I am running into the same error again. What is going wrong here? Thanks.

I have been trying to get Mplayer to play streaming movies for a couple of weeks now, first in Mandriva and now in Ubuntu, but with no success. Is there another player, for example VLC which can play streaming video and audio? How to install it and configure it?
VLC may work (install from synaptic) and google may be your friend
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-June/034113.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-June/034113.html)
[http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-June/034116.html](http://lists.mplayerhq.hu/pipermail/mplayer-users/2003-June/034116.html)

---

### Post by Natume on 2007-01-24
For those still having difficulty with MPlayer (as I was, earlier), I've actually gotten it to work for me.  Granted, I sorta ad-hoc'ed it, using the HowTo as a basic guideline.  As such, it's currently extracted and 'installed', but hasn't been installed by the dpkg method (used 'sudo make install' instead).

A few things to say on getting it to work :

First of all, for those of you with the -vo problem (or whatever the full thing is ; I had the problem as well), go into preferences, then select the codecs tab, and there should be two pull-down menus of different video and audio decoders respectively.  Mine was set to none / default on installation ; after selecting appropriate codecs, things worked much, much better.  Currently I'm using ffshow for video and MPEG for audio.  That seems to work fine, but I'm sure other codecs will work just as well.

Another issue that I had was with default directories.  Unlike what the how-to said, the default directory for codecs was certainly not /usr/lib/win32.  For me, it was (by default ; it can be changed in part 3h) /usr/local/share/codecs.  I found that out by going into the readme located in the source files, just by luck.  Make sure you know where everything is going to ; at 3h in the HowTo, you can change your default preferences to whatever you'd like.

And for any of us having the font issue, also in the preferences, somewhere, is the option to load a font.  I just selected one from the fonts folder I carried over from Windows (on my FAT32 partition), and it's been working fine.

That may not solve all of the issues, but then again, it might help out without needing to do numerous reinstallations.

(Oh, and for anybody used to using other programs [say, you've come directly from Windows, like I did], my suggestion is to make heavy use of the right click menu, depending on which skin you use.  As I mentioned before, I use productive, because I think it looks simplistic, yet nice, but a lot of the options you'll find in the right click menus alone, like changing the subtitle track on mkvs and whatnot.)

---

### Post by keith11 on 2007-01-25
I tried changing the video codecs to a number of available options, but to no avail. I still get an error, the same error. At this point in time, I seek some specific suggestions as I have tried almost everything that is out there (I hope I am wrong). Thanks.

---

### Post by tetralis on 2007-01-25
I am using the mplayer package through synaptic and had the same error message: "Requested audio codec family [mp3] (afm=mp3lib) not available."

Just make sure that you have ffmpeg installed. Then go the mplayer preferences menu and select the “Codecs & demuxer” tab. Now for "audio codec family" select "FFmpeg/libavcodec audio decoders"

Restart.

---

### Post by Hub-1 on 2007-01-26
Thanks to everyone for commenting on this thread, I will update it as soon as I have more time for those who need additional info on how to configure mplayer properly.

---

### Post by Arasfang on 2007-01-26
To be able to 

```
sudo apt-get build-dep mplayer
```

I had to add these 2 repositories

```
deb http://archive.ubuntu.com/ubuntu edgy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy universe multiverse
```

Otherwise it could not find source package for mplayer.

Good guide here also if you dont want to install from source

[http://www.debianadmin.com/install-mplayer-ubuntu.html](http://www.debianadmin.com/install-mplayer-ubuntu.html)

/Mattias

---

### Post by keith11 on 2007-01-26
Thanks Hub. Although I haven't found the solution to my problem yet, I will keep looking at this thread. I was able to play video a couple of days back with totem on cbsnews.com, but not on any other website which required windows media player. Unfortunately, I am not able to play even the cbsnews videos now. I keep on getting the -vo error for mplayer and on cbsnews.com, when I try to play a video, it just ends up bringing up a gray screen and at the bottom of it, it says "Done". That's the update from me. If someone has some suggestions, I would be thankful for the help. Thanks.

---

### Post by mervg on 2007-01-27
> **Hub-1 said:**
> Thanks to everyone for commenting on this thread, I will update it as soon as I have more time for those who need additional info on how to configure mplayer properly.

I followed your post, and all is working - except -- every song played (mp3) suffers from random hiccups. When replayed, these flaws are in different areas of the song. Any thoughts on this item? Haven't tried a DVD, yet (None handy). Good guide you posted!

---

### Post by lexarrow on 2007-01-28
I am receiving an error message: "seek failed!" from the mplayer gui when I try to play an  mp3 file

---

### Post by hodad on 2007-01-30
I installed Mplayer, and got it working, When I go to  open some videos on a "humor" site, I get an empty screen with "download plugin" with a puzzle piece, but, of course, when I go to download it, ubuntu comes up with "can't find plugin".

Any ideas on what I can do?

Thanks

---

### Post by kanna1620 on 2007-01-30
> **snoochems said:**
> Thanks.... it was all working well up until the last line *sudo dpkg -i mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb*.  

I got an error:
[I]
dpkg: error processing mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb[/I]


Being a total noob to linux, i wiggled my way to the folder containing the compiled program, found the file: *mplayer_1.0rc1-1_i386.deb*

This seemed to install the program.  I don't know if this is different to doing it via the terminal... 

Anyways, having assumed it's installed... where do I find the program to launch it???

Ya I got the same error after following the above procedure. Plz some one help me .

---

### Post by kanna1620 on 2007-01-30
> **snoochems said:**
> Thanks.... it was all working well up until the last line *sudo dpkg -i mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb*.  

I got an error:
[I]
dpkg: error processing mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mplayer_2:0.99+1.0pre8-0ubuntu8-1_i386.deb[/I]


Being a total noob to linux, i wiggled my way to the folder containing the compiled program, found the file: *mplayer_1.0rc1-1_i386.deb*

This seemed to install the program.  I don't know if this is different to doing it via the terminal... 

Anyways, having assumed it's installed... where do I find the program to launch it???

Ya I got the same error after following the above procedure. Plz some one help me .And when i play a movie file using the command mplayer <filename> then I got the error message that  Fatal Error:Could not initialize video filters.
What to do next>?

---

### Post by radiobuzzer on 2007-02-04
Hello, I have already spent two hours on this howto, and I haven't done what I wanted to. I consider myself quite experienced in such issues and this is what makes me angry at the moment. Let's take it from start:

My main reason for following this howto was to make this stream play: mms://sfera.live24.gr/sfera4132 . It is one of the most popular streams. In my old version of mplayer, what I got was an error of 

```
 Requested audio codec family [acelp] (afm=dshow) not available.
Enable it at compilation.
Cannot find codec for audio format 0x130.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Video: no video

```

Unfortunately, after downloading the essential codecs for AMD64 (that's my architecture) and running ./configure with only --enable-gui option, which according to the manual should autodetect the SUPPORTED ( [http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html) ) codec 0x130, and following thr HOWTO it doesn't work either.

Other things to point out
[LIST]
[*]checkinstall must be run with sudo. 
[*]I didn't disable mp3lib but is still missing. Then a [mp3 @ 0xd2f190]Header missing skipping one byte. is displayed in the Shell windows and the movies play slowly
[*]I get an annoying popup error "too many video codecs in the buffer" when playing mpeg videos
[*]Aspect ratio is always wrong
[*]Although I gave the same as a package name, aptget tries to upgrade it with a package of the same name with an -1 at the end.
[/LIST]

Can you play the stream I gave? Is there a way to do so?

thanks

---

### Post by aditya.sharma on 2007-02-14
> **kanna1620 said:**
> Ya I got the same error after following the above procedure. Plz some one help me .
Perhaps You people did not carry out step 3j (Checkinstall, select option 3, change version), thats why name of .deb file remained the default.

anyway, if it installed correctly from Nautilus, or using "dpkg -i mplayer_1.0rc1-1_i386.deb" , you can launch mplayer by typing command: 

gmplayer

or adding a launcher to your gnome panel with the same command.

> **keith11 said:**
> I tried changing the video codecs to a number of available options, but to no avail. I still get an error, the same error. At this point in time, I seek some specific suggestions as I have tried almost everything that is out there (I hope I am wrong). Thanks.

the problem is not with video codec here, but with output device. IT is configured via the second tab in Gmplayer preferences. Setting to first option (**xv**) works best in my case. try setting it to x11 , gl or gl2 if that doesn't work. If it doesn't, may be you need to configure your video card drivers correctly

---

### Post by aditya.sharma on 2007-02-14
I resolved a few problems in my installation,  putting it down here for reference

Followed the HOWTO but some music-videos were not having audio played correctly. Using** VLC** player and doing  Ctrl-I in it,  i pinned down the problem to those videos having "mpga" audio encoding (think this stands for Mpeg Layer 2 and 3, ie mp3 etc). In these videos, the audio simply played at the speed of light.

So i tried compiling and installing without **"--desable-mp3lib"** in step 3h. but it didn't work.

Next i downloaded  latest Subversion snapshot from MPlayer website  [http://www3.mplayerhq.hu/MPlayer/releases/mplayer-checkout-snapshot.tar.bz2]("http://www3.mplayerhq.hu/MPlayer/releases/mplayer-checkout-snapshot.tar.bz2"))
(this is updated everyday, in contrast to the release that original HOWTO refers to, which is of October 2006, but that is of course supposedly more stable)
decompressed it and followed step 3h onwards without **"--disable-mp3lib"**. I also changed the name of package as in step 3j (**checkinstall**) selecting option 2, setting it to "mplayer" and changed version to latest Ubuntu package as told in original HOWTO.

The resulting package is working correctly on all sort of videos. Just remember to set audio codec to **MPEG layer-2, layer-3 **in Gmplayer prefernces (it is the second option)

So what was the big issue with mp3lib anyway. The original Mplayer for Ubuntu and this HOWTO both spurn it ?

---

### Post by keith11 on 2007-02-14
> **aditya.sharma said:**
> 
the problem is not with video codec here, but with output device. IT is configured via the second tab in Gmplayer preferences. Setting to first option (**xv**) works best in my case. try setting it to x11 , gl or gl2 if that doesn't work. If it doesn't, may be you need to configure your video card drivers correctly

Thanks for that suggestion. It works now. This might seem strange but the way the GUI of mplayer preferences is built is very confusing. For example, I didn't know that just clicking on one of the video/audio outputs was actually selecting it because when you click on it, it doesn't push down as a button or something, it just gets highlighted. Anyways, I can play video files now in Mplayer. The problem that remains is the basic one, which is to play online media. I have Totem, VLC and Mplayer, all three installed with all the codecs but (and probably that's why) I am not able to play any media on the internet. Any suggestions?

---

### Post by 13east on 2007-02-14
I tried to install this, but keep getting stuck at "checkinstall".  i've posted the error; I really don't know what else to do.  any sort of help would be much appreciated. 

> 
checkinstall 1.6.0, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.


The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: 

Preparing package documentation...OK

Please write a description for the package.
End your description with an empty line or EOF.
>> MPlayer
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "MPlayer" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ panther@the-den ]
1 -  Summary: [ MPlayer ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 1.0rc1 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ MPlayer-1.0rc1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 3
Enter new version: 
>> 2:0.99+1.0pre8-0ubuntu8

This package will be built according to these values: 

0 -  Maintainer: [ panther@the-den ]
1 -  Summary: [ MPlayer ]
2 -  Name:    [ mplayer ]
3 -  Version: [ 2:0.99+1.0pre8-0ubuntu8 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ MPlayer-1.0rc1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 1
Enter new summary: 
>> Source-Build                                    

This package will be built according to these values: 

0 -  Maintainer: [ panther@the-den ]
1 -  Summary: [ Source-Build ]
2 -  Name:    [ mplayer ]

3 -  Version: [ 2:0.99+1.0pre8-0ubuntu8 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ MPlayer-1.0rc1 ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 
Installing with make install...

========================= Installation results ===========================
make -C loader
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/loader'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/loader'
make -C loader/dshow
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/loader/dshow'
make[1]: `libDS_Filter.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/loader/dshow'
make -C loader/dmo
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/loader/dmo'
make[1]: `libDMO_Filter.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/loader/dmo'
make -C libavformat LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libavformat'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libavformat'
make -C libavcodec LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libavcodec'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libavcodec'
make -C libavutil LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libavutil'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libavutil'
make -C libmpdemux
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libmpdemux'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libmpdemux'
make -C stream
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/stream'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/stream'
make -C libmpcodecs
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libmpcodecs'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libmpcodecs'
make -C libao2
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libao2'
make[1]: `libao2.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libao2'
make -C osdep
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/osdep'
make[1]: `libosdep.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/osdep'
make -C libswscale LIBPREF=lib LIBSUF=.a
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libswscale'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libswscale'
make -C input
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/input'
make[1]: `libinput.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/input'
make -C libvo
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libvo'
make[1]: `libvo.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libvo'
make -C libaf
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libaf'
make[1]: `libaf.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libaf'
make -C liba52
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/liba52'
make[1]: `liba52.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/liba52'
make -C libmpeg2
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libmpeg2'
make[1]: `libmpeg2.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libmpeg2'
make -C libfaad2
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libfaad2'
make[1]: `libfaad2.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libfaad2'
make -C libdha
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libdha'
make[1]: `libdha.so.1.0' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libdha'
make -C vidix
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/vidix'
make -C drivers
make[2]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/vidix/drivers'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/vidix/drivers'
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/vidix'
make -C libmpdvdkit2
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libmpdvdkit2'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libmpdvdkit2'
make -C libass
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libass'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libass'
make -C Gui
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/Gui'
make[1]: `libgui.a' is up to date.
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/Gui'
make -C libdha install
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/libdha'
mkdir -p /usr/local/lib
install -m 755  -p libdha.so.1.0  /usr/local/lib/libdha.so.1.0 
install: setting permissions for `/usr/local/lib/libdha.so.1.0': No such file or directory
rm -f /usr/local/lib/libdha.so
ln -sf libdha.so.1.0  /usr/local/lib/libdha.so.1
ldconfig
ldconfig: Can't link /usr/lib/libncurses.so.5 to libtermcap.so
ldconfig: Can't create temporary cache file /etc/ld.so.cache~: Permission denied
make[1]: [install] Error 1 (ignored)
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/libdha'
make -C vidix install
make[1]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/vidix'
make -C drivers install
make[2]: Entering directory `/home/panther/.src/MPlayer-1.0rc1/vidix/drivers'
mkdir -p /usr/local/lib/mplayer/vidix
install -m 755  -p *.so /usr/local/lib/mplayer/vidix
install: setting permissions for `/usr/local/lib/mplayer/vidix/cyberblade_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/mach64_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/mga_crtc2_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/mga_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/nvidia_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/pm3_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/radeon_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/rage128_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/savage_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/sis_vid.so': No such file or directory
install: setting permissions for `/usr/local/lib/mplayer/vidix/unichrome_vid.so': No such file or directory
make[2]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/vidix/drivers'
make[1]: Leaving directory `/home/panther/.src/MPlayer-1.0rc1/vidix'
install -d /usr/local/bin
install -m 755 -s mplayer /usr/local/bin/mplayer
install: setting permissions for `/usr/local/bin/mplayer': No such file or directory
ln -sf mplayer /usr/local/bin/gmplayer
install -d /usr/local/man/man1
for i in en; do \
                if test "$i" = en ; then \
                        install -c -m 644 DOCS/man/en/mplayer.1 /usr/local/man/man1/mplayer.1 ; \
                else \
                        install -d /usr/local/man/$i/man1 ; \
                        install -c -m 644 DOCS/man/$i/mplayer.1 /usr/local/man/$i/man1/mplayer.1 ; \
                fi ; \
        done
install: setting permissions for `/usr/local/man/man1/mplayer.1': No such file or directory
install -m 755 -s mencoder /usr/local/bin/mencoder
install: setting permissions for `/usr/local/bin/mencoder': No such file or directory
for i in en; do \
                if test "$i" = en ; then \
                        cd /usr/local/man/man1 && ln -sf mplayer.1 mencoder.1 ; \
                else \
                        cd /usr/local/man/$i/man1 && ln -sf mplayer.1 mencoder.1 ; \
                fi ; \
        done
*** Download skin(s) at [http://www.mplayerhq.hu/dload.html](http://www.mplayerhq.hu/dload.html)
*** for GUI, and extract to /usr/local/share/mplayer/skins/
install -m 644 etc/mplayer.xpm /usr/local/share/pixmaps/mplayer.xpm
install: setting permissions for `/usr/local/share/pixmaps/mplayer.xpm': No such file or directory
install -m 644 etc/mplayer.desktop /usr/local/share/applications/mplayer.desktop
install: setting permissions for `/usr/local/share/applications/mplayer.desktop': No such file or directory

======================== Installation successful ==========================

Copying documentation directory...
./
./AUTHORS
./ChangeLog
./LICENSE
./README
chown: changing ownership of `/var/tmp/AjCiYAUfIDKKjhajYhYKK/package//usr/share/doc/mplayer/AUTHORS': Operation not permitted
chown: changing ownership of `/var/tmp/AjCiYAUfIDKKjhajYhYKK/package//usr/share/doc/mplayer/ChangeLog': Operation not permitted
chown: changing ownership of `/var/tmp/AjCiYAUfIDKKjhajYhYKK/package//usr/share/doc/mplayer/LICENSE': Operation not permitted
chown: changing ownership of `/var/tmp/AjCiYAUfIDKKjhajYhYKK/package//usr/share/doc/mplayer/README': Operation not permitted
chown: changing ownership of `/var/tmp/AjCiYAUfIDKKjhajYhYKK/package//usr/share/doc/mplayer': Operation not permitted

Copying files to the temporary directory...OK

Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package...OK

Installing Debian package... FAILED!

*** Failed to install the package


---

### Post by aditya.sharma on 2007-02-16
> **13east said:**
> I tried to install this, but keep getting stuck at "checkinstall".  i've posted the error; I really don't know what else to do.  any sort of help would be much appreciated.

I hope u did
```

sudo checkinstall

```

note the **sudo**.

---

### Post by aditya.sharma on 2007-02-16
> **keith11 said:**
>  The problem that remains is the basic one, which is to play online media. I have Totem, VLC and Mplayer, all three installed with all the codecs but (and probably that's why) I am not able to play any media on the internet. Any suggestions?

You do have **mozilla-mplayer** installed, don't you ? Also try **mozplugger** package.

---

### Post by keith11 on 2007-02-16
Aditya: I have both mozilla-mplayer as well as mozplugger installed and they are the latest versions. The problem still persists. Thanks.

---

### Post by slamduncan on 2007-03-13
Had some problems compiling mplayer on Edgy with the XVMC-VLD patch for an EPIA mobo to use with Freevo, IVTV and a Hauppauge PVR 150. The mplayer 1.0rc1 compiled fine but with default settings and using -nosound option I diagnosed that audio decoding was causing playback to fail for the MPEG2 streams coming from the 150. Using the latest Ubuntu package the audio playback was fine but then it was using mp3lib which is disabled by default when compiling from source. Compiling 1.0rc1 with mp3lib enabled and using that gave better video playback without -nosound but the audio was broken-up, distorted, scratchy and slow.

Finally after three days of trying I found a combination that works. 

1.0rc1 source code, delete the mp3lib directory and replace with the mp3lib directory from the subversion check-out of the latest version and the files mpbswap.h and mpcommon.mak in the main source folder also from the latest subversion check-out. With this combination the normal ./configure, make, sudo make install produced an mplayer that could play the output from my Hauppauge card.

I'm sure there are other ways of skinning this cat but here's one that worked for me... 

For information, I'm running edgy 2.6.17-11-386 with gcc 4.1.2, Freevo 1.6.3 and IVTV 0.7.3. It seems I can't use the latest subversion check-out of mplayer because it needs IVTV 0.10 and that won't work on 2.6.17. Could be wrong on that so if anyone has a different experiences then please share them.

Duncan.

---

### Post by ivesjl on 2007-03-15
I was following the source code you posted and ran into an unexpected problem, I'm positive I missed a very simple fix to this.

At step 3h I type:

 ./configure --enable-gui --disable-mp3lib

and receive the following error:

Error: X11 support required for GUI compilation.

Check "configure.log" if you do not understand why it failed.

Thanks for any help.

---

### Post by IndyBob on 2007-03-16
Okay, I was having problems with Mplayer and tried the uninstall and your method of installing and left off the --disable-mp3lib as I had read earlier and did sudo checkinstall and I then did sudo dpkg - mplayer_1.0rcl-1_i386.deb and got the following error message:

Selecting previously deselected package mplayer.
dpkg: regarding .../mplayer_1.0rc1-1_i386.deb containing mplayer:
 mplayer-nogui conflicts with mplayer
  mplayer (version 1.0rc1-1) is to be installed.
dpkg: error processing /home/bob/src/MPlayer-1.0rc1/mplayer_1.0rc1-1_i386.deb (-
-install):
 conflicting packages - not installing mplayer
Errors were encountered while processing:
 /home/bob/src/MPlayer-1.0rc1/mplayer_1.0rc1-1_i386.deb

---

### Post by lp_jerk on 2007-03-16
They don't get any nuber than me.  When I get to the build-essential cmd I'm asked to insert my install disc.  I used the alternate install for AMD.  I insert and then freeze @ about 20%.  Hmmmmm.  Any ideas?

I though there my be a different source I could use besides the disc.  I'm pretty lost most of the time.

---

### Post by Tangerined on 2007-03-20
Hi, I'm having this problem where if I try to play certain files that I would get gargled audio, and in terminal it would show "[mp3 @ 0x887f9d8]Header missing skipping one byte." I have the audio codec set to FFmpeg. If I try to play the same file with totem it would play properly.

---

### Post by slamduncan on 2007-03-21
Tangerined,
Sounds like you're describing the same problem that I had. Please read my post above.
I can see that it contains an MP3 but out of interest what type of file are you trying to play?
Which versions of mplayer, kernel and gcc are you using?
Rgrds,
Duncan

---

### Post by pt123 on 2007-03-23
> **keith11 said:**
> I tried changing the video codecs to a number of available options, but to no avail. I still get an error, the same error. At this point in time, I seek some specific suggestions as I have tried almost everything that is out there (I hope I am wrong). Thanks.

try this 
gmplayer -vo x11


I had the same problem but this let me solve it.

---

### Post by stefangr1 on 2007-04-13
I have had two of the problems that some people seem to have here, on both (K)ubuntu Edgy and the Feisty Beta. First I only had the -vo Error problem (after installing with sudo apt-get install mplayer). When I compiled from source that was solved, but then I got the sound problems related to mp3lib in stead (after having some dependancy problems solved and installing the appropriate development packages off course). What worked for me at the end was this:

- Install mplayer from source with ./configure --disable-mp3lib

if i install without the disable mp3lib option almost all sound is scratchy, if I install like this only the mp3 can't be played, and surprisingly enough not all the keyboard controls work. I solved that in the following manner:

- Just ignore that it is already installed and install it a second time with sudo apt-get install mplayer

Strange solution if you ask me, but it at least works.

---

### Post by stefangr1 on 2007-04-13
Btw: I now have two options to play a file if I right click on it, one called "MPlayer Movie Player" which the one installed with sudo apt-get and still produces errors only, and one called mplayer (I added mplayer in the konqueror file associations menu), which plays everything perfectly.

I'm wondering if this solution is only ad-hoc very good (at least it is for me) or also technical a good solution.

---

