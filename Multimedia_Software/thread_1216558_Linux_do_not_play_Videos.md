---
title: "Linux do not play Videos"
date: 2009-07-18
forum: Multimedia Software
---

### Post by rashwan on 2009-07-18
Hello ,

as title say ... am really wondering how users should make the step to an OS
do not play any Video file properly ?! i bet anyone who claims he can play 
any video format on his linux machine 
still the problems since ubuntu 4.10 till jaunty released my ubuntu cannot 
play video files properly 
now MPlayer , VLC & Movie Player plays media file too fast tried to reinstall and install new codec packs NO HOPE it seems that Linux is not designed to support multimedia uses
anyway do anyone have solution tips before leaving my beautiful eye-candy desktop and boot Win 7 up ?

---

### Post by igorzwx on 2009-07-18
It is not true.
You are misinformed.
I can play everything sinse I installed Ubuntu (2006)

---

### Post by rashwan on 2009-07-18
by default ? never , i bet

---

### Post by igorzwx on 2009-07-18
by default it can play ogg and such things

---

### Post by rashwan on 2009-07-18
LOL , well and what i suppose to do to play .avi file , note that i already downloaded codecs packs ... etc

---

### Post by ELD on 2009-07-18
If you use this: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And/Or use VLC you should be all set.

---

### Post by binbash on 2009-07-18
Dude you may have a different problem, please stop saying codec pack codec pack codec pack like a windows user.paste a terminal output or some logs.

---

### Post by rashwan on 2009-07-18
> **binbash said:**
> Dude you may have a different problem, please stop saying codec pack codec pack codec pack like a windows user.paste a terminal output or some logs.

Dont know how could this be helpful but anyway...

```
desktop:~/video$ mplayer ngsctu.avi
MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 6, Stepping: 5)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing ngsctu.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  512x288  24bpp  25.000 fps  472.5 kbps (57.7 kbyte/s)
Clip info:
 Software: MEncoder dev-CVS-051014-22:10-3.4.4
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 512 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 512x288 => 512x288 Planar YV12 
GNOME screensaver enabled.079 ct: -0.030 598/598  3%  0%  1.3% 26 0 

Exiting... (Quit)
```

Any tips , notifications or feedbacks ?

---

### Post by jerome1232 on 2009-07-18
> **rashwan said:**
> LOL , well and what i suppose to do to play .avi file , note that i already downloaded codecs packs ... etc

Huh funny, a Windows default install can't play .avi files, you have to download the xvid/divx or x264 codec they were encoded in.

Ubuntu comes with xvid by default and that's what the vast majority of avi files are encoded as. Go figure.

So what are these files your trying to play encoded as? looks like xvid video and mp3 audio, vlc can do it fine. So can Mplayer. And totem if you install the codecs for mp3.

---

### Post by SunnyRabbiera on 2009-07-18
Is using ubuntu restricted extras so bloody hard?

---

### Post by rashwan on 2009-07-18
actually as soon as i finished the Vista installation i was able to play avi , mpg & mp4 , its not our issue now to make a comparison everybody knows the fact
well am trying to just run avi and wmv mpg so on
any tips ?

---

### Post by rashwan on 2009-07-18
> **SunnyRabbiera said:**
> Is using ubuntu restricted extras so bloody hard?

ubuntu-restricted-extras is already the newest version

---

### Post by rashwan on 2009-07-18
I've noticed that the video is working well but MINIMIZED to tray !!!

that mean i have to hear the video only :p

any suggestions where the prob could be ?

---

### Post by rashwan on 2009-07-19
Any suggestions ? do i miss a package or something ? 

again the issue is when i play any video it lags and play fast unless play minimized 

any tips before closing this thread ?

---

### Post by igorzwx on 2009-07-19
Perhaps, you may try Slax and see what you like more Linux or Windows
[http://www.slax.org/build.php](http://www.slax.org/build.php)
Create your own customized Slax with all the features you    need, download your ISO or TAR directly from this site. Please note, this page is going to be redesigned, in    order to provide much easier functionality. But it works now, so you    are welcome to try it. We will see if the server gets overloaded.

---

### Post by rashwan on 2009-07-19
thanks igor, but am seeking support right now to jaunty multimedia issue

perhaps later i'll search for alternative Distro that plays Video files properly

---

### Post by igorzwx on 2009-07-19
it seems that all hackers are now busy with Slax.
it is not an alternative to Ubuntu.
it is another thing.
it works out of the box and you can learn a lot.
and you can play with it with pleasure.

---

### Post by rashwan on 2009-07-19
am shopping from slax modules too :D but how can i get the default essential modules and apps to be added ?
i mean i fear to forget adding some essential apps/modules so is there a way to have the default disto's apps and modules added ?
another thing does gnome environment included ?

---

### Post by igorzwx on 2009-07-19
default are added automatically
other you should add (+)
take only verified (in the first experiments)

It will tell the size,
and additional modules to be installed to satisfy depentences.

then click on ISO and download

very simple.

no science here

---

### Post by igorzwx on 2009-07-19
gnome can be tried later (it is not verified, can be bugs)
try the simplest first

---

### Post by igorzwx on 2009-07-19
[http://en.wikipedia.org/wiki/SLAX](http://en.wikipedia.org/wiki/SLAX)

[LIST]
[*][SLAX Homepage]("http://www.slax.org/")
[*][*SLAX* at DistroWatch]("http://distrowatch.com/table.php?distribution=slax")
[*][SLAX Guide]("http://www.geocities.com/slaxfansite/") - fan site
[*][Unofficial SLAX Wiki]("http://66.246.76.162/slax/wiki/")
[*][Unofficial SLAX 6.x.x module list]("http://66.246.76.162/slax/wiki/Module_List")
[*][Customizing SLAX Configurations]("http://www.ab9il.net/slax/slax-customization1.html")
[/LIST]

---

### Post by Arup on 2009-07-19
Mplayer plays everything you can throw at it, so does VLC. In contrast, unless codec packs like Klite and others which have their own dubious background are loaded, Windows is hapless and unable to play majority of formats out. In case you want Ubuntu with all codecs loaded, use Mint.

---

### Post by igorzwx on 2009-07-19
this seems to be something interesting too

GoblinX Micro is the smallest distribution and contains only Fluxbox
as windows manager and GTK/GTK2 based applications.
[http://www.goblinx.com.br/en/?page_id=16](http://www.goblinx.com.br/en/?page_id=16)

Try out the g:Micro, make it your small Linux LiveCD and save memory,
you can also use a minicd to burn it and some other devices.

The g:Micro contains some of the most often used and praised
applications for Linux, even though it is less than one hundred
megabytes of size. Some of these best Linux applications included are:
Firefox, Gcalctool, Totem, Gimp, Hardinfo, Audacious, Evince and more.

In comparision with g:Mini, the g:Micro does not include man pages,
extra languages, office software like Abiword and Gnumeric, 3D
libraries and applications like Compiz and Mesa, Pidgin and some other
programs. Only english support for now is available.

---

### Post by rashwan on 2009-07-19
well i repeat YES MPlayer plays everything thats not my problem now ! the issue is that the video lags and play faster than normal , ubuntu-restricted-extras is installed and nothing changed any suggests ?

---

### Post by igorzwx on 2009-07-19
[http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html](http://shibuvarkala.blogspot.com/2009/04/howto-make-ubuntu-904-jaunty-jackalope.html)

---

