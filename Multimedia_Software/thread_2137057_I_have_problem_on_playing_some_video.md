---
title: "I have problem on playing some video"
date: 2013-04-19
forum: Multimedia Software
---

### Post by amam on 2013-04-19
i have a problem on playing some .flv files
and this message appears for me, only playing audio with out video

[IMG]http://s11.postimg.org/td5gmbbv7/ttt1.png[/IMG]

i hope a fast solution pls

---

### Post by amam on 2013-04-19
i have already installed Kubuntu-restricted-extras but i don't know what is the problem

---

### Post by sudodus on 2013-04-19
Welcome to the Ubuntu Forums :-)

In Lubuntu and Ubuntu the restricted extras will give me possibility both to play and create h264 encocded videos. I think it comes with the install iso in Lubuntu (but not Ubuntu). I don't know if and how the kubuntu restriced entras package is different. Or maybe vlc is using its own codecs. Try another video player, for example mplayer (or mplayer2).

*Edit*: By the way, I wonder if the flv container is supposed to use h264 encoding. I use that with the mp4 container. Can you play the file in another system, for example Windows or Mac (with or without VLC)?

---

### Post by amam on 2013-04-19
the problem is not only on vlc 
i have tried different players
with no benefit

---

### Post by sudodus on 2013-04-19
What about the files? Are you sure they are good; can they be played anywhere?

---

### Post by amam on 2013-04-19
they are working fine

---

### Post by sudodus on 2013-04-19
Have you got or can you make a small video clip that can be uploaded to some cloud service? I can try if it works in my Lubuntu system and what packages that would be needed.

---

### Post by amam on 2013-04-19
this is one of the videos 

```
 http://a22.tk.swteh.ru/files/Steroid_Hormone_Biosynthesis_1.flv 
```

---

### Post by matt_symes on 2013-04-19
Hi

Can we double check it's installed the restricted extras correctly. They may not have installed correctly.

Please post the output of...

```
apt-cache policy {k,}ubuntu-restricted-extras
dpkg -l {k,}ubuntu-restricted-extras
```

Kind regards.

---

### Post by sudodus on 2013-04-19
Sorry, I can't resolve that internet address, not even 

[http://www.sudamedica.com](http://www.sudamedica.com)

Is the website restricted or blocked somehow? Can you upload a file to some other service, for example Ubuntu One, Dropbox or Google Plus?

*Edit*: Now I can resolve it. It won't play video for me either, only audio (in firefox). I'll download it and try it locally ... Mplayer complains:

> [h264 @ 0xb64b79e0]Overread VUI by 8 bits
[h264 @ 0xb64b79e0]Different bit depth between chroma and luma not implemented. Update your Libav version to the newest one from Git. If the problem still occurs, it means that your file has a feature which has not been implemented.

---

### Post by amam on 2013-04-19
i am using kubuntu

ok let me upload it again

amam.

---

### Post by sudodus on 2013-04-19
I think these files contain a non-standard feature. I can't play the video (only audio) locally in a computer where I make, convert and play h264 encoded video.

---

### Post by amam on 2013-04-19
me too having same problem
playing audio without video

---

### Post by amam on 2013-04-19
i updated the link
```

http://a22.tk.swteh.ru/files/Steroid_Hormone_Biosynthesis_1.flv

```

i forget to mention that they were playing even on 12.10

but later on, they are not !?

---

### Post by sudodus on 2013-04-19
That is an important bit of information. Do you remember if you had installed some particular set of codecs?

Will they play again, if you run a live session booted from an Ubuntu 12.10 boot drive? If necessary, you can install restricted extras and restricted addons to a live session.

---

### Post by dabl on 2013-04-19
That video plays in RealPlayer (latest version) on Windows.

---

### Post by amam on 2013-04-19
> **sudodus said:**
> That is an important bit of information. Do you remember if you had installed some particular set of codecs?

Will they play again, if you run a live session booted from an Ubuntu 12.10 boot drive? If necessary, you can install restricted extras and restricted addons to a live session.

i installed kubuntu-desktop on ubuntu 
at the begining it was working fine !

---

### Post by sudodus on 2013-04-20
> **amam said:**
> i installed kubuntu-desktop on ubuntu 
at the begining it was working fine !

When I try to play the uploaded video, Mplayer complains:
>                                                          [h264 @ 0xb64b79e0]Overread VUI by 8 bits
[h264 @ 0xb64b79e0]Different bit depth between chroma and luma not  implemented. Update your Libav version to the newest one from Git. If  the problem still occurs, it means that your file has a feature which  has not been implemented.                      

     
 


I guess you have the same problem, and I think this is what happened:

At some point, maybe when you installed kubuntu-desktop or at some upgrade, a new version of the codec was installed, and it replaced the one that could decode the video clip.

Install if necessary and run ***Synaptic***, search for codecs, and try different codec packages.

Or use the method suggested by the system: 'Update your Libav version to the newest one from Git.'

---

### Post by Aide9aic on 2013-04-20
amam visited us at Kubuntu Forums, too. Eventually I found a solution. For those who are interested, please see this post.

[http://www.kubuntuforums.net/showthread.php?p=326695&viewfull=1#post326695](http://www.kubuntuforums.net/showthread.php?p=326695&viewfull=1#post326695)

---

### Post by sudodus on 2013-04-21
Thanks for sharing the solution :KS

---

### Post by andrew.46 on 2013-04-21
Mind you a recent copy of the svn MPlayer had no trouble at all in playing this file. I attach a screenshot...

---

### Post by sudodus on 2013-04-21
Hi andrew.46,

Nice :-) What version and flavour of Ubuntu are you running? And what codec package?

---

### Post by andrew.46 on 2013-04-21
I have tested this on Raring Ringtail with a self-built copy of MPlayer and no external codeca, Guide is here if you are interested:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

---

### Post by sudodus on 2013-04-22
> **andrew.46 said:**
> I have tested this on Raring Ringtail with a self-built copy of MPlayer and no external codeca, Guide is here if you are interested:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

I read the link, and will try to use it soon. You will get feed-back :-)

---

### Post by andrew.46 on 2013-04-22
> **sudodus said:**
> I read the link, and will try to use it soon. You will get feed-back :-)

Always glad for that, this guide ha been running for many years but has been a little less popular lately as Ubuntu satisfies media needs a little better...

---

### Post by sudodus on 2013-04-22
In the lubuntu raring i386 (installed from the desktop iso daily build 2013-04-21) I tried but could not find the package **[FONT=courier new]libggi-target-fbdev[/FONT]**

```
tester@kollen:~$ sudo apt-get -y install libaa1-dev libasound2-dev libcaca-dev libcdparanoia-dev libdca-dev libdirectfb-dev libggi-target-fbdev libenca-dev libesd0-dev libfontconfig1-dev libfreetype6-dev libfribidi-dev libgif-dev libgl1-mesa-dev libjack-jackd2-dev libopenal1 libpulse-dev libsdl1.2-dev libsvga1-dev libvdpau-dev libxinerama-dev libxv-dev libxvmc-dev libxxf86dga-dev libxxf86vm-dev librtmp-dev libsctp-dev libass-dev libfaac-dev libsmbclient-dev libtheora-dev libogg-dev libxvidcore-dev libspeex-dev libvpx-dev libschroedinger-dev libdirac-dev libdv4-dev libopencore-amrnb-dev libopencore-amrwb-dev libmp3lame-dev liblivemedia-dev libtwolame-dev libmad0-dev libgsm1-dev libbs2b-dev liblzo2-dev ladspa-sdk libopenjpeg-dev libfaad-dev libmpg123-dev libopus-dev libbluray-dev libaacs-dev libgtk2.0-dev
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
E: Kunde inte hitta paketet libggi-target-fbdev
tester@kollen:~$
```
I updated&upgraded, but still no go.

What do you suggest next?

Edit: I continued anyway, but got this error

```

No FFmpeg checkout, press enter to download one with git or CTRL+C to abort
...
Error: The GUI requires libavcodec with PNG support (needs zlib).

Check "config.log" if you do not understand why it failed.
tester@kollen:~/mplayer_build/mplayer$
```

Running mplayer I got the following output. Should mplayer2 be removed before I try agian?
```

tester@kollen:~/mplayer_build/mplayer$ mplayer
WARNING: gnome-keyring:: couldn't connect to: /run/user/tester/keyring-ADp4Vj/pkcs11: No such file or directory
MPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
Usage:   mplayer [options] [url|path/]filename

Basic options: (complete list in the man page)
 -vo <drv>        select video output driver ('-vo help' for a list)
 -ao <drv>        select audio output driver ('-ao help' for a list)
 vcd://<trackno>  play (S)VCD (Super Video CD) track (raw device, no mount)
 dvd://<titleno>  play DVD title from device instead of plain file
 -alang/-slang    select DVD audio/subtitle language (by 2-char country code)
 -ss <position>   seek to given (seconds or hh:mm:ss) position
 -nosound         do not play sound
 -fs              fullscreen playback (or -vm, -zoom, details in the man page)
 -x <x> -y <y>    set display resolution (for use with -vm or -zoom)
 -sub <file>      specify subtitle file to use (also see -subfps, -subdelay)
 -playlist <file> specify playlist file
 -vid x -aid y    select video (x) and audio (y) stream to play
 -fps x -srate y  change video (x fps) and audio (y Hz) rate
 -pp <quality>    enable postprocessing filter (details in the man page)
 -framedrop       enable frame dropping (for slow machines)

Basic keys: (complete list in the man page, also check input.conf)
 <-  or  ->       seek backward/forward 10 seconds
 down or up       seek backward/forward  1 minute
 pgdown or pgup   seek backward/forward 10 minutes
 < or >           step backward/forward in playlist
 p or SPACE       pause movie (press any key to continue)
 q or ESC         stop playing and quit program
 + or -           adjust audio delay by +/- 0.1 second
 o                cycle OSD mode:  none / seekbar / seekbar + timer
 * or /           increase or decrease PCM volume
 x or z           adjust subtitle delay by +/- 0.1 second
 r or t           adjust subtitle position up/down, also see -vf expand
 double click     toggle fullscreen
 right click      pause (press again to continue)

 * * * SEE THE MAN PAGE FOR DETAILS, FURTHER (ADVANCED) OPTIONS AND KEYS * * *

tester@kollen:~/mplayer_build/mplayer$ 

```

---

### Post by andrew.46 on 2013-04-22
> **sudodus said:**
> 
```
E: Kunde inte hitta paketet libggi-target-fbdev
```
I updated&upgraded, but still no go.

On my Raring build this is available. Try the following command:

```

andrew@corinth:~$**[COLOR="#FF0000"] apt-cache search libggi-target-fbdev[/COLOR]**
libggi-target-fbdev - General Graphics Interface direct access framebuffer target

```

and this might throw some light on the missing package. I suspect the following error:

> **sudodus said:**
> 
```

No FFmpeg checkout, press enter to download one with git or CTRL+C to abort
...
Error: The GUI requires libavcodec with PNG support (needs zlib).

Check "config.log" if you do not understand why it failed.
tester@kollen:~/mplayer_build/mplayer$
```


means that the listed dependencies, and *their *dependencies, have not been successfully downloaded. (Probably because of the libggi-target-fbdev error).

> **sudodus said:**
> Should mplayer2 be removed before I try agian?

It is easier to have only one copy of MPlayer installed at a time. I had not realised that the default MPlayer installation now actually installs the fork MPlayer2, seems like an odd arrangement...

---

### Post by andrew.46 on 2013-04-23
mc4man as usual has the answer, a late scratching:

[http://ubuntuforums.org/showthread.php?t=2130221&page=2&p=12615932&viewfull=1#post12615932](http://ubuntuforums.org/showthread.php?t=2130221&page=2&p=12615932&viewfull=1#post12615932)

so simply omit this dependency, I have altered the guide to suit...

---

### Post by monkeybrain2012 on 2013-04-24
Interestingly the file doesn't play in any player in Ubuntu 12.04 (vlc complains no codec for h264 even though an updated version of x264,--self compiled,-- is installed), mplayer (from MOTU ppa)  and mplayer2 (self compiled)  plays only audio and totem is completely useless), but in Debian SID both totem and mplayer2 (from the debian multimedia repo I think) work, I have a self compiled version of ffmpeg and x264 there though, don't know if it has anything to do with it. Haven't tested vlc on Debian, am planning to compile it in a few days. 


EDITED: More strange, I compiled mplayer2 from git in Debian and it doesn't open the file (only audio) just like in Ubuntu..

---

### Post by sudodus on 2013-04-24
> **andrew.46 said:**
> I have tested this on Raring Ringtail with a self-built copy of MPlayer and no external codeca, Guide is here if you are interested:

Howto: Build the svn MPlayer under the latest release version of Ubuntu
[http://www.andrews-corner.org/mplayer.html](http://www.andrews-corner.org/mplayer.html)

> **andrew.46 said:**
> mc4man as usual has the answer, a late scratching:

[http://ubuntuforums.org/showthread.php?t=2130221&page=2&p=12615932&viewfull=1#post12615932](http://ubuntuforums.org/showthread.php?t=2130221&page=2&p=12615932&viewfull=1#post12615932)

so simply omit this dependency, I have altered the guide to suit...

Now I succeeded in compiling your version of mplayer in Lubuntu Raring, and it can play *amam*'s file (the lecture about Steroid Hormone Biosynthesis).

Thank you :-)

*Edit*: I continued to test this version of mplayer, and it can play all the video files I tested. But a difficult MTS file (with a lot of motion in the picture) directly from my video camera, 1920x1080, 50 fps progressive, 28 Mb/s was too much, it lagged behind without vdpau. Mplayer2 can play that without issues, so it is faster. This mplayer can play the difficult file without issues using vdpau. It complains, but plays well[FONT=courier new] '**** Your system is too SLOW to play this!  ****[/FONT]'

This version of mplayer can also play simplified versions of the 'difficult MTS file' without issues. A file with the same frame size and frame rate (1080-50p), but reduced bitrate, 9.2 Mb/s, and encoded with x264 (made in ffmpeg) is close to the threshold. And smaller or easier video formats play well :-)

[COLOR=#696969]I tested it in an aging HP xw8400 workstation with 2x2 xeon processors with a newer nvidia geforce gt430 card.[/COLOR]

[COLOR=#696969]Maybe mplayer2 is the default player in Lubuntu because it is the fastest one, and Lubuntu is often used in old and slow computers. I don't think mplayer comes with Ubuntu, and I don't remember about the other flavours. But I usually install it because I like it, also in other flavours of Ubuntu.[/COLOR]

---

### Post by monkeybrain2012 on 2013-04-24
Hi, Andrew, 

I followed your instructions to build mplayer on Precise and it does work. I made only two changes, I added --prefix=$HOME/bin in the ./configure line so this is a local version and I didn't build a static version of x264 as I have already compiled the updated version for system use. I am wondering why it doedsnt work for mplayer2. I compiled it from git ([http://www.mplayer2.org/downloads/](http://www.mplayer2.org/downloads/) , mplayer2-build.git) It is up to date and it comes with its own libva and the codecs should be the same as mplayers? Could it be ffmpeg? I noticed that in Debian mplayer2 from system repo does work but the compiled version doesn't. I have compiled ffmpeg there as a shared library. But then even Totem works there.

---

### Post by monkeybrain2012 on 2013-04-24
Just compiled vlc in Debian and it plays the video there too.

---

### Post by sudodus on 2013-04-24
> **monkeybrain2012 said:**
> Just compiled vlc in Debian and it plays the video there too.

Your findings are interesting. So if the version of the video player is not working, it is worthwhile to compile an own version also in precise and debian.

---

### Post by andrew.46 on 2013-04-24
Good to hear you can now hear and see the original difficult file :). My apologies to the OP if we have diverted a little from his or her question...

---

### Post by andrew.46 on 2013-04-24
> **monkeybrain2012 said:**
>  I am wondering why it doedsnt work for mplayer2. I compiled it from git ([http://www.mplayer2.org/downloads/](http://www.mplayer2.org/downloads/) , mplayer2-build.git) It is up to date and it comes with its own libva and the codecs should be the same as mplayers? Could it be ffmpeg? I noticed that in Debian mplayer2 from system repo does work but the compiled version doesn't. I have compiled ffmpeg there as a shared library. But then even Totem works there.

Unfortunately I have very limited knowledge concerning MPlayer2 :(. Hopefully there are others who can comment on this...

---

### Post by monkeybrain2012 on 2013-04-24
Hi Andrew,

I think maybe it is because of ffmpeg? My  Mplayer2  build appears to use libav instead of ffmpeg so may be that is the difference. I think ffmpeg from the repo is actually libav and maybe the mediaplayers in Ubuntu's repo and ppas are compiled against it. I would want to test this by compiling a local version of vlc. I have read your guide on that, but since I have already a static build of ffmpeg for compiling mplayer last night, I don't feel like duplicating that. Is there a way to use a  ./configure option so  that vlc would build against that copy of ffmeg?  I think this is probably important if you build a whole bunch of multimedia things yourself and use the same static libraries over and over again. Thanks.

Edited: Just found out that Debian-Multimedia's version of ffmpeg is actually  ffmpeg instead of libav (the default in Debian's proper repositories),  so may be that's why the file did play in my SId installation by all  players (all installed from Debian Multimedia) but not in Ubuntu

---

### Post by andrew.46 on 2013-04-24
I try to stay away from the FFmpeg/libav debacle but I always use FFmpeg to compile against :). With vlc you can select the copy of FFmpeg used by [manipulating the PKG_CONFIG_PATH variable]("https://help.ubuntu.com/community/CompileVLC#Building_vlc-git..").

---

### Post by monkeybrain2012 on 2013-04-24
Hi, Andrew,

I  figured it has to do with changing PKG_CONFIG_PATH, but I don't know what it should be changed to, in my build of mplayer I don't have the lib and share folders since I use the system's x264 and I only need to grab the ffmpeg files, not sure which directory I should use as PKG_CONFIG_PATH (like = $HOME/mlayer-build/mplayer/ffmpeg"?) 

Thanks.

---

### Post by andrew.46 on 2013-04-25
I confess that I am a little unsure of exactly what you are trying to do here, my apologies for being a little obtuse :(. Where is the copy of FFmpeg that you wish to point the vlc ./configure process towards?

---

### Post by monkeybrain2012 on 2013-04-25
Hi, Andrew, 

I am trying to compile vlc, but instead of making a second static version of ffmpeg, I want to use the one I have already compiled by using your guide to compile mplayer. So I think I should point the PKG_CONFIG_PATH to the ffmpeg library and shared files in the ~/mplayer_build/mplayer folder  somewhere, but I am not sure which one.

---

### Post by andrew.46 on 2013-04-25
Now I see :). As far as I am aware this is not possible, although I have been wrong before. You will have to compile a fresh local copy of FFmpeg for vlc or use a system copy (preferably from git). I will have to admit that I have neglected the vlc guide which is now on the Ubuntu wiki for some time so the version of FFmpeg there could probably do with a bump.

---

### Post by monkeybrain2012 on 2013-04-25
Hi, 

I figured it may not be possible to share static ffmpeg libraries (that's why they are static I suppose) I have tried to compile a system copy of ffmpeg from git and configure it to be a shared library. But I was getting errors because of some lines in x264. x264 is up to date, I think it may be a problem in the ffmpeg nightly build (compile worked with ffmpeg 1.2 tarball) I will try again in a few days.

I have a strong hunch that OP's file doesn't play because of ffmpeg rather than the player. I will try to compile vlc using the original ffmeg (rather than libav), I expect it will work too.

Edited: While I succeeded in compiling ffmpeg1.2 tarball, typing "ffmpeg" in the terminal produced a long list of libraries and enabled modules, but also a line about "incompatible libraries", seems like it may be in conflict with some libav stuffs in the system though I don't know what harm it may do. Seems a bit tricky to use a compiled version of ffmpeg for the whole system.

---

### Post by monkeybrain2012 on 2013-04-29
So I have compiled ffmpeg 1.2 in Raring (tarball downloaded from fffmpeg) and then compiled vlc against it. vlc plays the file perfectly, so the problem does appear to be with Ubuntu's ffmpeg (libav) packages.  Now I should have compiled vlc 2.06 from tarball instead of git in order to have the same version as in Raring's repo. But  I think that is probably irrelevant (I will do another compile of 2.06 in a few days)

---

