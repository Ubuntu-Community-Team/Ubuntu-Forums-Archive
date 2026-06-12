---
title: "Music file player (flac)"
date: 2016-02-10
forum: Multimedia Software
---

### Post by h_piper on 2016-02-10
I am looking for a good music file player for Ubuntu Linux. It needs to support the flac file format. If it has the ability to burn as well as play cd's that would be a large plus.

---

### Post by deadflowr on 2016-02-10
Moved to Multimedia Software

---

### Post by Dennis N on 2016-02-10
> **h_piper said:**
> I am looking for a good music file player for Ubuntu Linux. It needs to support the flac file format. If it has the ability to burn as well as play cd's that would be a large plus.

Most of them will play flac provided the necessary plugin or codec is installed. If you installed "Ubuntu Restricted Extras" package, you are covered on many plugins and codecs.

If I need to burn a CD, I use Brasero which is a dedicated tool to that purpose.

---

### Post by SeijiSensei on 2016-02-10
FLAC is an open format so the restricted-extras package isn't really needed.  Pretty much any modern Linux audio player should handle FLAC.  I know Clementine and Amarok on Kubuntu do, and I suspect things like Rhythmbox do as well.

---

### Post by monkeybrain20122 on 2016-02-12
Anything on Linux will play flac. I don't think you even need restricted-extras.

---

### Post by mc4man on 2016-02-12
> **monkeybrain20122 said:**
> Anything on Linux will play flac. I don't think you even need restricted-extras.

correct, ubuntu comes with libflac8 installed by default

---

### Post by Nuno_Abreu on 2016-02-12
There's no need for **ubuntu-restricted-extras**, as some have said before.

There are some good players out there, I think all of them do play FLAC files (they're great for Surround sound!). Here is a short list:
[B]
Rhythmbox (the default player)
Clementine
Amarok
Xnoise
Banshee
Tomahawk
Lollypop
Guayadeque
Cmus (if you like simple music players in the Terminal window)[/B]

---

### Post by Rob Sayer on 2016-02-12
Yep, lots of good linux music players.  I actually found the selection better (at least as far as quality is concerned) than in windows.  You should be able to find one you like in the repos.

I actually use 2 programs to play music.  Mostly Clementine.  It's a large, heavy program for a music player but the playlist features are pretty much the best I've used.  I generally just keep a couple of tracks form a CD and categorize music by folders myself.  A flat file (if that's the expression) music playlist library like most players have doesn't cut it.

Also I use Audacious.  The playlist features aren't so great but it's light and very fast.  If I want to just play a single file or foider I'll use it for its speed.

VLC is also an excellent music player with good playlist capability.  It's my favorite in WIndows.

---

### Post by Dennis N on 2016-02-12
I can recommend Aucacious, which comes loaded with AAC decoder, MIDI play plugin, audio CD support, mp3 decorder, flac decoder, ogg decoder, ffmpg plugin, and a few more. All this without Ubuntu restricted extras.

And it does not try to make a music library for you for those who prefer their own organizing.

---

### Post by Nuno_Abreu on 2016-02-12
I think Audacious might not need Restricted Extras as a dependency, but it needs it for file playback - and it makes sense because we're talking about FOSS.
By default, Ubuntu does not install it due to infringements that can occur, as well as some incidents people can have with this kind of proprietary software (I hate the DRM!). Also, it's an incentive for people to encode and decode with better formats (mp3 files are bad compared to m4a (proprietary) and ogg standards, for example) and greater development of those.

But the MP3 seems to stay and we can't do nothing about it - not even all portable music players know how to decode an ogg file.

---

### Post by Dennis N on 2016-02-12
>  I think Audacious might not need Restricted Extras as a dependency, but it needs it for file playback
No, Audacious installs with audacious-plugins (dependency), which contains the necessary packages. Here is the default support:

> _Default codec support_

    MP3 using libmpg123
    Advanced Audio Coding (AAC and AAC+)
    Vorbis
    FLAC
    Wavpack
    Shorten (SHN)
    Musepack
    TTA (codec)
    Windows Media Audio (WMA)
    Apple Lossless (ALAC)
    150 different module formats
    Several chiptune formats: AY, GBS, GYM, HES, KSS, NSF, NSFE, SAP, SPC, VGM, VGZ, VTX
    PlayStation Audio: PSF1 and PSF2
    Nintendo DS Sound Format: 2SF
    Ad-lib chiptunes via AdPlug library
    WAV formats provided by libsndfile plugin.
    MIDI via native OS synthesizer control or TiMidity.
    CD Audio


source: Wikipedia

---

### Post by Rob Sayer on 2016-02-12
Trying to keep your system FOSS and wanting to play media is IMHO a hopeless cause.  You think Firefox (or any other browser useble by most users) contains no closed source code?

---

### Post by yoshii on 2016-02-12
Personally, I like DeaDBeeF.  It's still being developed but you have to go to the website to get it as a .DEB file.  
It's pretty much just a portable install, no fancy stuff.  Put the folder where you want it and launch it from there.  
It's easy to configure and is nice looking and simple.  

It doesn't burn discs, but K3B is nice for audio discs instead.

---

### Post by Yellow Pasque on 2016-02-12
This question comes up a lot. The bottom line is that there is no "best" player for every user and you should try different players until you find the one you like.
If you do a lot of CD burning, start with Rhythmbox.

I personally use Audacious because I like its approach to organization (playlists instead of a library).
I use Clementine to tag my library. Yes, there are tag programs, but I find Clementine sufficient for most cases, and I'll drop to command line and use 'metaflac' command if I want more direct editing of metadata on a FLAC file.

---

### Post by shantiq on 2016-02-13
Audacious to play or for me latest discovery [Cantata]("http://ubuntuforums.org/showthread.php?t=2287569&p=13324508#post13324508")   or another amazing library player [Clementine]("https://www.clementine-player.org/")  EDIT:   and yes of course Deadbeef especially very easy to install [portable]("http://sourceforge.net/projects/deadbeef/files/deadbeef-static_0.7.0-1_x86_64.tar.bz2/download")   ....    
[[img]http://s20.postimg.org/xtbdv5dw9/image.jpg[/img]](http://postimg.org/image/xtbdv5dw9/)

and for the brave who likes oldies [XMMS]("http://ubuntuforums.org/showthread.php?t=2267576")   the old Swedish beast :]

TO BURN:

[K3b]("http://www.k3b.org/")
```
sudo apt-get install k3b
```





Another useful trick/tip:

WODIM
===================

To copy an audio CD in the most accurate way, first run to rip >>

```
icedax dev=/dev/cdrom -vall cddb=0 -B -Owav
```

and then to write run:

```
wodim dev=/dev/cdrom -v speed=2 -dao -useinfo -text *.wav
```

---

### Post by Yellow Pasque on 2016-02-13
Also recommended to install libk3b6-extracodecs package for K3b if you want to burn mp3's..

---

### Post by monkeybrain20122 on 2016-02-13
I use nightingale. [https://sourceforge.net/projects/ngale/](https://sourceforge.net/projects/ngale/)

---

### Post by mc4man on 2016-02-15
> **monkeybrain20122 said:**
> I use nightingale. [https://sourceforge.net/projects/ngale/](https://sourceforge.net/projects/ngale/)
At some point Debian/Ubuntu are going to drop gst-0.10, not clear if for 16.04 or not..
[http://comments.gmane.org/gmane.linux.ubuntu.devel.desktop/4839](http://comments.gmane.org/gmane.linux.ubuntu.devel.desktop/4839)

---

