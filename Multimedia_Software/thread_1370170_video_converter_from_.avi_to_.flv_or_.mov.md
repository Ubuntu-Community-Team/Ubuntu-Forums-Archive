---
title: "video converter from .avi to .flv or .mov"
date: 2010-01-01
forum: Multimedia Software
---

### Post by Lakeside5 on 2010-01-01
Hi, I have Hardy Heron on here.  I've downloaded a few suggested converters, but they don't seem t ohave the right combination..I have some .avi's (from my camera) and want to put them on my website (using Joomla  AllVideo component) so they have to be converted to .flv  or maybe .mov.  Is there a good, free one? thanks

---

### Post by andrea000 on 2010-01-02
Try pytube it converts to .avi .mpeg or .flv and a lot more
you can download it from [here]("http://old.getdeb.net/search.php?search_distro_id=9&keywords=pytube")

---

### Post by prshah on 2010-01-02
> **Lakeside5 said:**
> 
I have some .avi's (from my camera) and want to put them on my website so they have to be converted to .flv  or maybe .mov.  Is there a good, free one? 

I use ffmpeg for all my conversion needs; it is available from the repositories, though I'm not sure about the version.

In a previous OS version (Intrepid), it seemed as though flv support was not available in the repositories version of ffmpeg; I downloaded the latest version and compiled it in accordance to the instructions, and everything worked fine.

Caveat: ffmpeg is a commandline program, and I use it as such; it may have a GUI frontend somewhere, but I don't know about it.

---

### Post by Lakeside5 on 2010-01-02
Thanks andrea000, I shall try it when i need something like that ;)
@ prshah, I'll donwload the latest verseion, and if I have a question of how to use in the command line...I shall ask you ok? lol  thanks.

---

### Post by HappyFeet on 2010-01-02
If you prefer a GUI, Winff is the frontend for ffmpeg.

---

### Post by prshah on 2010-01-02
> **Lakeside5 said:**
> @ prshah, I'll donwload the latest verseion, and if I have a question of how to use in the command line...

Maybe if you are using Karmic, the latest version may already be in the repos. Please first try the repositories version, and, if it doesn't do what you want, then try the latest version.

I'm no ffmpeg expert, but I will help out to whatever level I can. Basically, it's as simple as```
ffmpeg -i somefile.avi somefile.mpg
``` which will convert the input file (-i) somefile.avi to somefile.mpg.

There are a number of other options to adjust video and audio parameters; really extremely comprehensive.

---

### Post by Lakeside5 on 2010-01-02
Thanks prshah, this is very helpful! I actually prefer the command line sometimes, although I am still learning new things about it (my join date is old, but I spend a lot of time away from 'computer stuff',  then I start to forget..the perpetual 'newbie' lol   So,  I downloaded the source code from here:[http://ffmpeg.org/download.html](http://ffmpeg.org/download.html) and now I just use sudo apt get or something to install it? I am using Hardy Heron btw, is Karmic the newest distro? thanks again :) edit*  oops, I see now Karmic is, I will try it after it has been out a while longer, I see u are testing it too (should give  MS a good fight! take that windows 7 lol)

---

### Post by mc4man on 2010-01-02
you may wish to have a read [here]("http://ubuntuforums.org/showpost.php?p=6963607&postcount=360") for building ffmpeg on hardy

Main thread is [here]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by Lakeside5 on 2010-01-02
@ PRshah..so, I have been googling, and it seems that if I am running a server (I am hosting my own website with Hardy Heron server on here) that  there is a different way of installing ffmpeg? Something about not 'compiling source code' (which   I'm not sure what that means anyway). thanks again

---

### Post by FakeOutdoorsman on 2010-01-02
> **Lakeside5 said:**
> @ PRshah..so, I have been googling, and it seems that if I am running a server (I am hosting my own website with Hardy Heron server on here) that  there is a different way of installing ffmpeg? Something about not 'compiling source code' (which   I'm not sure what that means anyway). thanks again

You have three options for installing FFmpeg in Hardy Heron.  You can either compile FFmpeg using the link mc4man gave you, you can install FFmpeg from the official Hardy Heron repository, or you can install FFmpeg from the Medibuntu repository.

Also consider using your desktop to convert your videos and then uploading the encoded video to your server.  This is the method I use.  This way you don't have to upload a potentially large input file or add more software or packages to your production server.

**Compiling FFmpeg**
Compiling FFmpeg will give you the best quality videos and is much newer than the repository or Medibuntu FFmpeg versions.  I recommend this method if you are encoding more than a few videos. After compiling you can use the libx264 encoding presets to encode to H.264 video.  The presets make the command much simpler:
```
ffmpeg -i input.avi -acodec libfaac -vcodec libx264 -vpre hq -crf 24 -threads 0 ffmpegoutput.mp4
```
Now run the output through *qt-faststart* (part of FFmpeg) to allow it to play before the file is completely downloaded:
```
qt-faststart ffmpegoutput.mp4 finaloutput.mp4
```

**FFmpeg from the Ubuntu Repository**
This is easy to install:
```
sudo apt-get install ffmpeg
```
Unfortunately, by default Ubuntu can't enable encoding to restricted formats such as mp3, aac, mpeg4, H.264, etc.  No libx264 presets either.  Old.  Not very useful unless you don't need those formats.

**FFmpeg from Medibuntu**
Also old, but includes restricted encoders.  No presets.  Installation is described under option C in this guide:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by Lakeside5 on 2010-01-02
I just gave all this great advice here a quick look, it seems that (from what I can figure, as I'm still not sure what it means to 'compile') it's saying this:  download the source code?(which I did, from here: [http://ffmpeg.org/download.html](http://ffmpeg.org/download.html) . I decided to take the advice of not installing it to the server, but use it on the desktop and upload the converted files.  So my next step is..uninstalling anything that looks like it's connected to ffmpeg (in the synaptics package manager) because it's from the old vesion of ffmpeg?  I guess compiling means to download the source code (so, newest version) rather than enable what is by default, in the package manager?  Then I must do some kind of apt get or something (but be in the directory, in the command line, of where that download is.../home/desktop

---

### Post by Lakeside5 on 2010-01-03
'You can either compile FFmpeg using the link mc4man gave you'  That's what I did but I think I messed it up ..(please bear with me..) I followed these directions from start to finish  ( [http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360) ) but got a few error messages along the way... especially with ones like this:  sudo checkinstall --pkgname=yasm --pkgversion "0.8.0" --backup=no --default ...where there were more than one, I didn't know if I should just 'cut and paste' or if the dashes meant  sudo checkinstall, THEN 'enter' and the next one, sudo pkgname=ysm  and so forth... anyway when it was all done, I was able to convert an avi, to an .mpg using the simple command  sudo -i filename.avi filename.mpg  but I couldn't do any others (*.avi *.mov,  or .flv etc.)And I really only want something to convert avi to mov or flv.  Can I find out where I went wrong or...do I have to uninstall and do it all over again *sigh*

---

### Post by mc4man on 2010-01-03
> do I have to uninstall and do it all over again *sigh* 
probably not

To clear something up - 
each code box contains a number of commands, each one is a separate command and each line is to be used as 1 complete command
You need to make sure you don't skip any and for the longer commands copy and paste carefully ( you can easily type cd, ./configure, make

Booted up a fairly vanilla 8.04 and did the complete how-to - only took about 25 min on an older p4
Got no errors, everything went smooth

As far as what needed to be removed first - really only what's in the how-to
> sudo apt-get remove ffmpeg x264 libx264-dev

**If** you were to be using the** ffmpeg package to build off of **then it's best to make sure no ffmpeg lib -dev's are installed (libavcodec1d-dev -> libswscale-dev

If you got an error message during any of the various build and couldn't resolve better to post the message in context (ie. the lines preceding

For now try a conversion that's failing and post **the complete terminal output** in a quote box

Ex ( though here I'm just opening the new ffmpeg - no comm.

> doug@doug-desktop:~$ ffmpeg
FFmpeg version SVN-r21005, Copyright (c) 2000-2010 Fabrice Bellard, et al.
  built on Jan  3 2010 15:59:57 with gcc 4.2.4 (Ubuntu 4.2.4-1ubuntu4)
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 7. 0 / 50. 7. 0
  libavcodec    52.45. 0 / 52.45. 0
  libavformat   52.46. 0 / 52.46. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 2 /  0. 7. 2
  libpostproc   51. 2. 0 / 51. 2. 0
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...

Use -h to get full help or, even better, run 'man ffmpeg'

---

### Post by Lakeside5 on 2010-01-03
Great! Thanks mc4man.  so I was supposed to do: sudo chckinstall,(enter) 
sudo pkgversion, etc.  not  sudo checkinstall --pdgversion --pkgname=version ?  Also, I see in the synaptic package installer a few ffmpeg things are installed, do I uninstall them: (libxine1-ffmpeg, gstreamer0.10-ffmpeg, and ffmpeg)  Here, I tried to convert an .mpg to a .flv.     lady@ubuntu:/var/www$ ffmpeg -i dand.mpg dand.flv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mpeg, from 'dand.mpg':
  Duration: 00:00:53.2, start: 0.110000, bitrate: 2912 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 32000 Hz, mono, 64 kb/s
    Stream #0.1[0x1e0]: Video: mpeg1video, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 104857 kb/s, 25.00 tb(r)
Output #0, flv, to 'dand.flv':
    Stream #0.0: Video: flv, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: adpcm_swf, 32000 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[adpcm_swf @ 0xb7ed12f0]Sample rate must be 11025, 22050 or 44100
[B][B][B]Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
[/B][/B][/B]  It does create a file called 'dand.flv' but it has '0' bytes, and says 'stream contains no data' when I try to play it.

---

### Post by FakeOutdoorsman on 2010-01-03
> **Lakeside5 said:**
> Great! Thanks mc4man.  so I was supposed to do: sudo chckinstall,(enter) 
sudo pkgversion, etc.  not  sudo checkinstall --pdgversion --pkgname=version ?
No.  Each line is a single, complete command.  Like this:
```
this line is the first command
this line is the second command
```
You should enter the complete line one at a time.

> **Lakeside5 said:**
> Also, I see in the synaptic package installer a few ffmpeg things are installed, do I uninstall them: (libxine1-ffmpeg, gstreamer0.10-ffmpeg, and ffmpeg)  Here, I tried to convert an .mpg to a .flv.     lady@ubuntu:/var/www$ ffmpeg -i dand.mpg dand.flv
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
Input #0, mpeg, from 'dand.mpg':
  Duration: 00:00:53.2, start: 0.110000, bitrate: 2912 kb/s
    Stream #0.0[0x1c0]: Audio: mp2, 32000 Hz, mono, 64 kb/s
    Stream #0.1[0x1e0]: Video: mpeg1video, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 104857 kb/s, 25.00 tb(r)
Output #0, flv, to 'dand.flv':
    Stream #0.0: Video: flv, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 25.00 tb(c)
    Stream #0.1: Audio: adpcm_swf, 32000 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
[adpcm_swf @ 0xb7ed12f0]Sample rate must be 11025, 22050 or 44100
[B][B][B]Error while opening codec for output stream #0.1 - maybe incorrect parameters such as bit_rate, rate, width or height
[/B][/B][/B]  It does create a file called 'dand.flv' but it has '0' bytes, and says 'stream contains no data' when I try to play it.

You're using FFmpeg from the Ubuntu Intrepid repository.  It does not have some encoders enabled by default.  Encoders are the software that actually make the video.  Some people call encoders by a different name: *codecs*.

If you want to compile FFmpeg you can remove FFmpeg.  Don't worry about the other packages that you asked about.  It would probably be easier for you in the long run if you remove your current FFmpeg before you compile.

However, if you don't want to compile, then you can easily enable the rest of the encoders and use your current FFmpeg by installing one package: **libavcodec-unstripped-51**.  I am unsure if you have this installed already or not.

FFmpeg is telling you what you need to do to remove that error: Sample rate must be 11025, 22050 or 44100.  So in your command, add *-ar 44100*.  So your final command will look like:
```
ffmpeg -i dand.mpg -ar 44100 dand.flv
```

---

### Post by mc4man on 2010-01-03
> so I was supposed to do: sudo chckinstall,(enter) 
No...

> **each code box** contains a number of commands, **each one is a separate command **and **each line is** to be used as **1 complete command**

Ex.
for yasm ( the last of 7 separate commands
```
sudo checkinstall --pkgname=yasm --pkgversion "0.8.0" --backup=no --default
```


The only way to make any clearer is this
the Install ffmpeg box is done as such

in the terminal enter this
```
cd
```
then press enter on keyboard, after which enter this

```
svn checkout svn://svn.ffmpeg.org/ffmpeg/trunk ffmpeg
```
then press enter on keyboard, after which (the source downloads) enter this

```
cd ffmpeg
```
then press enter on keyboard, after which enter this

```
./configure --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
```
then press enter on keyboard, after which (the configure finishes) enter this

```
make
```
then press enter on keyboard, after which (the make is done) enter this


```
sudo checkinstall --pkgname=ffmpeg --pkgversion "3:0.svn`date +%Y%m%d`-12ubuntu3" --backup=no --default
```
and press enter on keyboard to install

> Also, I see in the synaptic package installer a few ffmpeg things are installed, do I uninstall them: (libxine1-ffmpeg, gstreamer0.10-ffmpeg, and **ffmpeg**


IF you want to use the how-to then you need to follow it from begining to end
> Quote:
sudo apt-get remove **ffmpeg** x264 libx264-dev 


You also said you're on hardy, but you have an ffmpeg version from intrepid, what are you running

Edit I see FO has answered while I was typing but am posting this anyway

---

### Post by Lakeside5 on 2010-01-03
So (sorry to be dense lol)  It is  'sudo checkinstall --pdgversion --pkgname=version etc,  all one line?  'You're using FFmpeg from the Ubuntu Intrepid repository' -by 'repository' u mean from the source code I downloaded?  I thought that was the most up to date version and would iclude what I needed. All I know is, I downloaded a source code 'ffmpeg.0.5.tar.bz2' to my desktop, and then ran the codes from the link.  I'm confused about where things were from  installing from, if not from the new download. I think I will have to reread some stuff about what is meant by 'compiling', and repository etc. *edit* Ooops I see u just posted, thanks.  I will do the whole thing over, the way you showed.    And i am running Hardy Heron, server edition.
Also,  do I need to be in a directory called 'ffmpeg'?  I was running these commands from the root, being at the root and typing ffmpeg -i etc.

---

### Post by Lakeside5 on 2010-01-03
I hope u don't mind, I'll post each error message I get as I go thru the installation:   sudo apt-get install build-essential subversion git-core..etc.) and at the end it says this: Package liblame-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmp3lame-dev
E: Package liblame-dev has no installation candidate

and the 9th command (if I did it right) sudo checkinstall --pkgname=yasm --pkgversion "0.8.0" --backup=no --default : I get sudo: checkinstall: command not found
Not sure how to enter code here:  y@ubuntu:~/x264$ ./configure
'Found no assembler
Minimum version is yasm-0.6.2
If you really want to compile without asm, configure with --disable-asm.(so I typed: ./configure --disable-asm  hope that was right.

---

### Post by FakeOutdoorsman on 2010-01-03
> **Lakeside5 said:**
> I hope u don't mind, I'll post each error message I get as I go thru the installation:   sudo apt-get install build-essential subversion git-core..etc.) and at the end it says this: Package liblame-dev is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmp3lame-dev
E: Package liblame-dev has no installation candidate

You are following the guide for installing FFmpeg for Ubuntu Hardy Heron 8.04, but I believe you are using a computer running Ubuntu Intrepid Ibex 8.10.

I recommend that you use the Ubuntu supplied version of FFmpeg instead of trying to compile.  Go to *System -> Administration -> Synaptic Package Manager* and install *ffmpeg* and *libavcodec-unstripped-51*.

Now you will be able to run your FFmpeg command:
```
ffmpeg -i dand.mpg -ar 44100 dand.flv
```

---

### Post by Marrkk on 2010-01-03
yep, WinFF is a nice simple GUI.
if its from youtube n stuff, i suggest Firefox's plugin called
video download helper.
whic, after enabling the conversion tickbox in the options,
downloads and converts most youtube like sites videos into a mpeg or avi or whatever - without you doing anything much.
it dumps them in your home folder, in a directory called  dwhelper.
hth
Mark

---

### Post by Lakeside5 on 2010-01-03
:oops: Intrepid WAS mentioned a few times,  and it just clicked in that, yes, I switched to Intrepid at some point (long absences from 'computer stuff' and I forget everything lol) Sorry about that, ok I have just enabled the files u mentioned in the package manager, and the ffmpeg command worked!!!  I can't believe it, and I can't believe how patient ALL of you were with me :) I mainly want just .avi to .flv conersion (my camera 'movies' to play on my website) so all I need for now is that command...should I need to know more I shall definately study this site more, I just have no time right now, busy at college. thanks again, very much :)

---

### Post by Lakeside on 2010-01-06
Thanks for the great help.  I have run this command: ffmpeg -i dand.mpg -ar 44100 dand.flv and it worked well on a few .avi files to flv, but I just did another one and it looks..not so good.  choppy,  pixelated, jerky.  How can I 'fine tune' it, any suggestions, either in the terminal (or in 'Avidemux', which I can open the new .flv in) thanks

---

### Post by FakeOutdoorsman on 2010-01-07
> **Lakeside said:**
> Thanks for the great help.  I have run this command: ffmpeg -i dand.mpg -ar 44100 dand.flv and it worked well on a few .avi files to flv, but I just did another one and it looks..not so good.  choppy,  pixelated, jerky.  How can I 'fine tune' it, any suggestions, either in the terminal (or in 'Avidemux', which I can open the new .flv in) thanks

Yes, it is going to look bad because your command does not contain any quality related options, therefore FFmpeg uses the default *-b 200k* which is quite low for that encoder.  Secondly, there are better encoders than FFmpeg's *flv*, such as *libx264*.

I already gave you an example command (see [post #10](http://ubuntuforums.org/showpost.php?p=8598632&postcount=10)) that would work well for you, but unfortunately your FFmpeg version is too old to use that.  It would just take me far too long to figure out something that will work for your ancient FFmpeg.  A waste of time when instead you could compile FFmpeg and use the previously mentioned example.

So I'll recommend a quality option (*qscale*) for you.  I also added an option that will tell FFmpeg to encode to MP3 audio instead of the default *adpcm_swf*:
```
ffmpeg -i dand.mpg -ar 44100 -acodec libmp3lame -qscale 5 dand.flv
```

---

### Post by Lakeside on 2010-01-09
@ FakeOutdoorsman,  You are totally right, I'll have to 'compile',  and I really appreciate you taking the time to give me a code to work 'for now',  I just  tried it and the video does look much better than what I was getting before,  thanks again, great forum!

---

