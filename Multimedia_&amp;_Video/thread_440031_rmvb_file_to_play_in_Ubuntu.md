---
title: "rmvb file to play in Ubuntu"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by leefischer on 2007-05-11
I ave had Ubuntu installed for a couple of days now.  I am trying to play a rmvb file in totem.  Can i get a codec for this, or should i look for another media player?  Not sure where to continue looking.  Cheers
 Lee

---

### Post by enopepsoo on 2007-05-13
You proably need to install realplayer.  I am waiting to hear back from someone on this thread
[http://ubuntuforums.org/showthread.php?p=2644535#post2644535](http://ubuntuforums.org/showthread.php?p=2644535#post2644535)

---

### Post by zanglang on 2007-05-17
Realplayer didn't work very well for me, it seemed pretty slow and used up a fair bit of CPU. :/
You can use Totem with xine as backend to play rm and rmvb files.
> sudo aptitude install totem-xine

---

### Post by hvtuananh on 2008-01-03
> **zanglang said:**
> Realplayer didn't work very well for me, it seemed pretty slow and used up a fair bit of CPU. :/
You can use Totem with xine as backend to play rm and rmvb files.
I can't play rm file. It said problem with cook.so

---

### Post by tc10b on 2008-02-24
> **hvtuananh said:**
> I can't play rm file. It said problem with cook.so

Mine does the same, although it used to play flawlessly

---

### Post by imon9 on 2008-02-24
hi guys,

i can play rmvb just fine here... i think i installed the codec32 (or something that sound similar) from mediubuntu repos

---

### Post by felipefoz on 2008-02-24
it used to work very well with me, i think it was an update yesterday or the day before yesterday, can't find a solution yet. w32codecs installed and all other codecs too.

---

### Post by w0ng on 2008-02-25
Same problem here. totem-xine worked fine up until maybe a week ago so I'm guessing one or more updates screwed it. Now I get a cook.so (RealAudio) and drvc.so (RealVideo) "cannot be handled" error whenever I try playing rmvb files. The two codecs are located in /usr/lib/codecs/. I haven't found a fix for this problem yet.

Since xine doesn't work, here's the cliff notes to get most popular media formats (INCLUDING rmvb) running on MPlayer and Firefox for Gutsy users:

**1) Add medibuntu repository to your 3rd party software sources**
> Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).

Some of these packages include the libdvdcss package from VideoLAN and the external binary codecs package (commonly known as w32codecs) used by MPlayer and xine. 
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
``````
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
**2) Install codecs and MPlayer - a alternative media player to totem-xine**
> **ubuntu-restricted-extras:** Installing this package will pull in support for MP3 playback and decoding, support for various other audio formats (gstreamer plugins), Microsoft fonts, Java runtime environment, Flash plugin, LAME (to create compressed audio files), and DVD playback.

**w32codecs:** This package contains Win32 codec binaries, required for the decompression of video formats that have no open source alternative.

**libdvdcss2:** Library for accessing DVDs like block device usind deCSS if needed libdvdcss is a simple library designed for accessing DVDs like a block device without having to bother about the decryption.

**mpalyer-nogui:** It plays most mpeg, avi and asf files, supported by many native and win32 DLL codecs. You can watch VCD, DVD and even DivX movies too. The other big feature of mplayer is the wide range of supported output drivers. It works with X11, Xv, DGA, OpenGL, SVGAlib, fbdev, but you can use SDL (and this way all drivers of SDL) and some lowlevel card-specific drivers (for Matrox/3dfx/SiS) too! Most of them supports software or hardware scaling, so you can enjoy movies in fullscreen. 

**mozilla-mplayer:** a Mozilla browser plugin to allow playing embedded movies on web pages using mplayer.

**smplayer:** Qt Mplayer front-end, with basic features like playing videos, DVDs, and VCDs to more advanced features like support for MPlayer filters and more. One of the most interesting features of SMPlayer: it remembers the settings of all files you play. So you start to watch a movie but you have to leave... don't worry, when you open that movie again it will resume at the same point you left it, and with the same settings: audio track, subtitles, volume...
```
sudo apt-get install ubuntu-restricted-extras w32codecs libdvdcss2 mplayer-nogui mozilla-mplayer smplayer
```


Some have mentioned of download RealPlayer, so you could try that... but I don't like the idea of downloading an extra media player just for its codecs when something like mplayer can be used as an all-in-one player.

---

### Post by benjavalero on 2008-02-29
It is a bug in the backport packages of Xine. Try to downgrade the libxine package to the Gutsy repositories, it worked for me.

---

### Post by felipefoz on 2008-03-03
Problem solved here, without so many workarounds.

Doing a symlink, xine engine will find the codecs, in /usr/local
so, do this.

```
$ sudo ln -sf /usr/lib/win32 /usr/local/lib/
```

cheers...

---

### Post by The_Knight on 2008-03-03
Edit the ~/.xine/config and ~/.gnome2/Totem/xine_config, then change the following uncommented lines;

# path to RealPlayer codecs
# string, default:
decoder.external.real_codecs_path:

# path to Win32 codecs
# string, default: /usr/lib/codecs
decoder.external.win32_codecs_path:

To:

# path to RealPlayer codecs
# string, default:
decoder.external.real_codecs_path:/usr/lib/win32

# path to Win32 codecs
# string, default: /usr/lib/codecs
decoder.external.win32_codecs_path:/usr/lib/win32

Where /usr/lib/win32 is the path of the codecs.

Enjoy.

P.S. : It does work for me.

---

