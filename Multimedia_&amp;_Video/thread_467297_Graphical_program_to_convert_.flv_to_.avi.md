---
title: "Graphical program to convert .flv to .avi?"
date: 2007-06-07
forum: Multimedia &amp; Video
---

### Post by Killtown on 2007-06-07
If trying to find a graphical video converter to convert .flv files to .avi or .mpg, etc.

I used to use MediaCoder in Win.

---

### Post by Gwasanaethau on 2007-06-07
I don't know about a graphical editor, but 'ffmpeg' on the command line will convert videos from one form to another. I use it frequently for the very formats you outlined in your post!

---

### Post by wolfen69 on 2007-06-07
dont trash your xp partition just yet. it's obviously next to impossible for someone to make a basic (user friendly) audio/video converter in linux. sad.

---

### Post by Killtown on 2007-06-07
> **Gwasanaethau said:**
> I don't know about a graphical editor, but 'ffmpeg' on the command line will convert videos from one form to another. I use it frequently for the very formats you outlined in your post!
I tried it: 

```
ffmpeg -i input.avi output.avi
```

but said my .flv was truncated/corrupted. 

I used the Firefox addon DownloadHelper.

Is there maybe a better video downloader than D.H.?  I didn't grab the video from youtube.  It's from LiveVideo.com.

---

### Post by revertex on 2007-06-07
> **wolfen69 said:**
> dont trash your xp partition just yet. it's obviously next to impossible for someone to make a basic (user friendly) audio/video converter in linux. sad.

Smells like FUD.

downtube has a gui version, you can grab debs here, 

[http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-2.1.deb](http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-2.1.deb)

[http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-en-1.0_i386.deb](http://dreamlinux.incubadora.fapesp.br/portal/packages/downtube-gui-en-1.0_i386.deb)

or use a linux version under wine, according to the developer, it works flawlessly.

[http://sourceforge.net/projects/downtube-gui](http://sourceforge.net/projects/downtube-gui)

also you can use one of these zillions of online converters like [http://www.youtubex.com/](http://www.youtubex.com/)

or

[http://vixy.net/](http://vixy.net/)


---

### Post by khardbored on 2007-06-07
Will ffmpeg also convert .ogg (video) to .avi? If so, what would the options be? I did ffmpeg --help and was so overwhelmed by the output I almost cried. hehe.

---

### Post by revertex on 2007-06-07
> **khardbored said:**
> Will ffmpeg also convert .ogg (video) to .avi? If so, what would the options be? I did ffmpeg --help and was so overwhelmed by the output I almost cried. hehe.

```
ffmpeg -formats | grep ogg
```

---

### Post by Gwasanaethau on 2007-06-07
> **khardbored said:**
> Will ffmpeg also convert .ogg (video) to .avi? If so, what would the options be? I did ffmpeg --help and was so overwhelmed by the output I almost cried. hehe.

It should do, but every time I tried I got mad white artefacts in the video. A similar question was asked [here]("http://ubuntuforums.org/showthread.php?t=467032") but at the time of posting I don't know whether it worked or not.

---

### Post by kostkon on 2007-06-07
A good video converter and editor is [Avidemux]("http://www.avidemux.org/") but I don't know if it can accept a FLV video file as input. Anyway, check it out, and I hope it can do everything you need.

You can easily install it from the *Add/Remove Applications* in Ubuntu.

---

### Post by revertex on 2007-06-07
> **kostkon said:**
> A good video converter and editor is [Avidemux]("http://www.avidemux.org/") but I don't know if it can accept a FLV video file as input. Anyway, check it out, and I hope it can do everything you need.

You can easily install it from the *Add/Remove Applications* in Ubuntu.

no flv nor ogm imput, but ogm output.

 there is no need to install just to check it.

[http://www.avidemux.org/admWiki/index.php?title=Input_formats](http://www.avidemux.org/admWiki/index.php?title=Input_formats)

[http://www.avidemux.org/admWiki/index.php?title=Output_formats](http://www.avidemux.org/admWiki/index.php?title=Output_formats)

---

### Post by iamandypipkin on 2007-06-10
i use a program on windows called super © to take videos off youtube and it doesnt say anywhere on the website that it is compatible with ubuntu but i was wondering if anyone had tried anything compatible?bear with me i'm a beginner lol!! :D

---

### Post by NewDisciple on 2007-06-10
I use Zamzar which is a free on line service which gives you a list of options to convert to.  It's kinda slow but it does work.

---

### Post by izizzle on 2007-06-11
I use this site: [www.vixy.net](www.vixy.net)    Its better than zamzar.

---

### Post by takuhii on 2007-06-12
> **Killtown said:**
> I tried it: 

```
ffmpeg -i input.avi output.avi
```

but said my .flv was truncated/corrupted. 

I used the Firefox addon DownloadHelper.

Is there maybe a better video downloader than D.H.?  I didn't grab the video from youtube.  It's from LiveVideo.com.

FFMpeg ususally says this when it can't find the file you are trying to convert. I re-installed FFMpeg 4 times until I realised I wasn't executing it from the directory with my FLVs in...

---

### Post by wilberfan on 2007-06-15
> **takuhii said:**
> FFMpeg ususally says this when it can't find the file you are trying to convert. I re-installed FFMpeg 4 times until I realised I wasn't executing it from the directory with my FLVs in...

That did the trick for me on my Sabayon 3.3 system!   :D  (Haven't tried it yet on my Feisty install...)

I used the Firefox plugin:  [VideoDownloader]("http://videodownloader.net/") to download it to my desktop.    the ffmpeg command worked great!

---

### Post by linuxfan3 on 2007-07-07
> **Killtown said:**
> I tried it: 

```
ffmpeg -i input.avi output.avi
```

but said my .flv was truncated/corrupted. 

I used the Firefox addon DownloadHelper.

Is there maybe a better video downloader than D.H.?  I didn't grab the video from youtube.  It's from LiveVideo.com.


if you want to re-encode the videos "on the fly" try clive:

[http://home.gna.org/clive/index.shtml](http://home.gna.org/clive/index.shtml)

---

### Post by xjgnsdof on 2007-09-22
> **Killtown said:**
> I tried it: 

```
ffmpeg -i input.avi output.avi
```

but said my .flv was truncated/corrupted. 

I used the Firefox addon DownloadHelper.

Is there maybe a better video downloader than D.H.?  I didn't grab the video from youtube.  It's from LiveVideo.com.

Navigate to the directory that contains the file(s) to be converted before entering the above command. Also, make sure that you enter a different file format for the output file; the example that you gave contains both input and output video as AVI.

---

### Post by darkazurka on 2007-10-14
I'm replying to threads related to .flv to .avi programs.
I'm using Ubuntu feisty fawn 7.04

I've tried using the package ffmpeg 3:0.cvs20060823-3.1ubuntu4 (feisty):
```
ffmpeg -i yo.flv yo.avi
```

But it gives so many errors saying: "[flv @ 0xb7f5e2d0]Unsupported video codec", so it isn't working. 
elgilicious, did it work for you?

---

### Post by CronoDekar on 2007-10-14
> **darkazurka said:**
> I'm replying to threads related to .flv to .avi programs.
I'm using Ubuntu feisty fawn 7.04

I've tried using the package ffmpeg 3:0.cvs20060823-3.1ubuntu4 (feisty):
```
ffmpeg -i yo.flv yo.avi
```

But it gives so many errors saying: "[flv @ 0xb7f5e2d0]Unsupported video codec", so it isn't working. 
elgilicious, did it work for you?

It was doing this for me on an flv, but then I tried it on another flv and it worked.  So I think it has more to do with the flv itself than ffmpeg.

---

### Post by vishzilla on 2007-10-14
> **NewDisciple said:**
> I use Zamzar which is a free on line service which gives you a list of options to convert to.  It's kinda slow but it does work.

+1

---

### Post by mocha on 2007-10-14
I do FLV to MPEG2/DVD conversions all the time on my Feisty box using an svn version.  There are a number of nice GUI frontends for it.  WinFF is one on my favorites.  You can also use programs like DeVeDe or ToVid.  Mencoder is a better encoder in my opinion, it handles WMV conversions a lot better.  There is a nice script that I found on these forums to convert videos using mencoder.  It was called "video convertor beta" or something like that.  It gives you a nice GUI checkbox to choose the options you want.

For ffmpeg I built my own with all codec support.  Sadly I don't remember the link to the instructions.  Google for something like "build ffmpeg ubuntu r8998" or something like that.  8998 was the svn version that the howto used.  The howto shows you how to compile in all the codecs for decoding and encoding.

I used to use SUPER in Winblows as well.  That was a nice program.  In general, Linux has better tools for video conversion IMHO.  Some other GUI frontends off the top of my head are:  Vive, Winki the ripper, KVideoEncoder, Gmencoder, WinFF, DeVeDe, Tovid, Avidemux.

There is another project that looks promising called, "Multimedia converter" written in Gambas2.  It's on these forums.  It's going to be a nice front end for mencoder.  It kind of reminds me of SUPER.  It looks like the developer is still working on it though.

In conclusion I would try to mencoder script first since ffmpeg is giving you problems.  Search for it on these forums.

---

### Post by troy1of2 on 2007-10-15
After much tinkering around, searching the forums, etc. I finally came up with some options that covert an FLV to an AVI that my Samsung HT-Q45 Home Theater system will play without giving me the Unsupported Codec error. The only problem is, the audio and video is way out of sync. Now I'm a newbie at this stuff so please bear with me but can anybody tell me what I might be able to do to get the audio and video better synced?

Here's what I am converting with:

mencoder -idx input.flv -ovc xvid -xvidencopts bitrate=4500 -oac mp3lame -srate 44100 -o output.avi

---

### Post by Creative2 on 2007-10-16
add -t option ( +\ - value) example

-t 00:02:37.200

i think , not sure 100% 

37 seconds
2 minutes

here there is my gui and many command line for conversion 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)

---

### Post by troy1of2 on 2007-10-16
> **Creative2 said:**
> add -t option ( +\ - value) example

-t 00:02:37.200

i think , not sure 100% 

37 seconds
2 minutes

here there is my gui and many command line for conversion 

[http://ubuntuforums.org/showthread.php?t=567016](http://ubuntuforums.org/showthread.php?t=567016)


Thank you Creative2! This looks promising. I'll give it a try.

---

### Post by tarekeldeeb on 2007-11-16
Hello ..

it seems an excellent tool ..

I have Gutsy 64-bit ..

I followed the installation steps .. then typed: convertit.gambas

i had an error:
/usr/bin/env: gbr2: No such file or directory

is this related to 64-bit .. or i missed something else ?

---

### Post by hfdragon on 2007-11-21
> **revertex said:**
> no flv nor ogm imput, but ogm output.

Avidemux now supports .flv files

You can find it here :

[http://www.getdeb.net/app.php?name=Avidemux]("http://www.getdeb.net/app.php?name=Avidemux")

It is still a preview version, but works quite fine :)

---

### Post by Creative2 on 2007-12-13
> **tarekeldeeb said:**
> Hello ..

it seems an excellent tool ..

I have Gutsy 64-bit ..

I followed the installation steps .. then typed: convertit.gambas

i had an error:
/usr/bin/env: gbr2: No such file or directory

is this related to 64-bit .. or i missed something else ?
i am sorry but gambas has still some problem with 64 bit system ...so converit cannot work in your system...

---

### Post by archosfan on 2007-12-25
I know a tool can convert .flv to .avi called nidesoft video converter ,but i dont know it is a graphical program or not, you can try!

---

### Post by eye208 on 2008-01-11
> **kekelka said:**
> hi i like to use Flash to Video Encoder PRO you too can try it or elso i worked with Flash to Video Encoder it was great too!this progs have demo versions without timelimit!
here you can find more infor and downlod it
Will those Windows fanboys ever get a clue? ](*,)

---

### Post by ubuntu-freak on 2008-01-11
Winff is the best and updated often with new presets.
 
[http://biggmatt.com/winff/](http://biggmatt.com/winff/)
 
Save to home folder then do

sudo dpkg -i filename.deb 

If you have enabled the medibuntu repo then you might want to 
 
sudo apt-get install faac
 
Just to make sure you have everything you need to convert videos. 
 
Nathan
 
Edit: See my [how-to](http://ubuntuforums.org/showthread.php?t=661833) also.

---

### Post by corstar on 2008-01-11
One stop solutions.....

PyTube. does all you want and more. OSS, linux native blah, blah ...
here's the [link]("http://www.bashterritory.com/pytube/")

---

### Post by stooshbunutu on 2008-02-04
for .flv files there is a realy easy porgram for converting most media files especiall .flv files [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") that uses the [ffmpeg]("http://packages.ubuntu.com/gutsy/graphics/ffmpeg") codec to covert the file.

hope this helps you, it works great for me.

---

### Post by $igmund on 2008-02-20
I just did this with ffmpeg. Some .flv's that I got with the firefox plugin. 

At first it told me that the .FLV was corrupt or truncated, but I had renamed the file, and left a %20 at the beginning of the file name. After I corrected that, it worked fine.

---

### Post by jack888 on 2008-03-03
> **hfdragon said:**
> Avidemux now supports .flv files

You can find it here :

[http://www.getdeb.net/app.php?name=Avidemux]("http://www.getdeb.net/app.php?name=Avidemux")

It is still a preview version, but works quite fine :)

installed 2.4.1 for gusty. 

I tried this version it works great.

I open the flv file.
I selected the first video codec mpeg-4(xvid) and audio codec of mp3(lame) then save as avi.

Conversion was fast and the audio and video turned great .

thanks

---

