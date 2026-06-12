---
title: "Gapless playback in Ubuntu?"
date: 2009-03-20
forum: Multimedia Software
---

### Post by The Bright Side on 2009-03-20
Hey guys, simple and direct question: does anyone know of a program that does gapless playback? I just recently migrated to Intrepid from Windows, and I LOVE Ubuntu, it's frickin awesome, but that's one of the issues I haven't been able to resolve.

---

### Post by mastermindg on 2009-03-20
XMMS with the XMMS Crossfade Plugin

---

### Post by issih on 2009-03-20
If you are using rhythmbox you can just enable the crossfading backend in it's preferences.

Hope that helps.

---

### Post by vanadium on 2009-03-20
I had the same question dwelling over here.

In the mean time, there are several option for file formats that support gapless (flac, ogg), including Rythmbox although curiously enough still not by default (few people seem to care about gapless playback).

Options are still very limited for gapless playback of mp3 (properly ripped and lame encoded). mp3 might still constitute the majority of your collection because it is the only format supported by any digital audio player.

The only true gapless playback option for lame that I know is music player daemon (mpd). It is what I use. mpd is a "server" and you control it with a client of choice, command line (mpc), norton commander like (ncmpc), full fledged graphical (sonata, gmpc, ...), or through a web interface in your browser. Only drawback: somewhat more difficult to set up.

XMMS with crossfade plugin also mostly works well. XMMS is not anymore developped, but there is also Audacious, which in some way is a fork of XMMS (I am sure it is in reality more complex than this).

These two options are about it for lame mp3s. The first option allows you to set up a library based playback system. Use one of the second group if you are more in for a Winamp style of media players.

---

### Post by joris1977 on 2009-03-20
aqualung is the player you are looking for. -> [http://aqualung.factorial.hu/](http://aqualung.factorial.hu/)  The only true gapless player i know for linux. Sadly the aqualung version that is in the repositaries is broken for me. Hopefully jaunty will fix this.

(Mpd is not really a player, but a music server and a really good one, if you take the time to figure out how it works)

---

### Post by logos34 on 2009-03-20
> **vanadium said:**
> In the mean time, there are several option for file formats that support gapless (flac, ogg), including Rythmbox although curiously enough still not by default (few people seem to care about gapless playback).

+1.  Although your question concerned playback, I agree with vanadium--if you need to rip gapless consider using flac or ogg. 


> but there is also Audacious, which in some way is a fork of XMMS (I am sure it is in reality more complex than this).

+ for Audacious and crossfade plugin (with gapless/nogap option enabled). Audacious is an awesome little player.

Now, if only I could figure out a way in Linux to burn live albums (mp3) and party mixes to Audio CDs with crossfading between tracks! (so easy in iTunes).

---

### Post by The Bright Side on 2009-03-21
Hi guys!

Thanks for those tips! I am using Audacious (it really is cool) and have heard about the crossfading plugin, but when I install it Audacious won't run anymore. Any ideas? I'm using the latest versions of both (1.5.1 Audacious, and 0.13.14 Crossfade) on Ubuntu Intrepid 64 bit. After I install the plugin, Audacious simply won't start. Here's the error message I get in the Terminal:

/home/thebrightside/.gtkrc-2.0:2: error: scanner: unterminated string constant - e.g. `style'
Segmentation fault


Rhythmbox, on the other hand, just won't play any of my files. OGG, FLAC, MP3, doesn't matter. I always get a that red icon with the white dash (like the street sign). I would assume it's missing plugins, which would make sense with MP3, but is kind of strange with OGG etc.

I tried Aqualung when I first installed Ubuntu (I had to reinstall it in the meantime because I screwed it up the first time around - I'm  a beginner :-)) and it was very unstable.

But screw it, I'm gonna give it another try! Any ideas about Audacious? Did anybody have the same problem? Perhaps it's because I'm using 64 bit. But then, I specifically downloaded a 64 bit deb for the Crossfade plugin: audacious-crossfade_0.3.14-1_amd64 from here: [http://ftp.linux.org.tr/ubuntu/pool/universe/x/xmms-crossfade/](http://ftp.linux.org.tr/ubuntu/pool/universe/x/xmms-crossfade/)

Thanks!

---

### Post by vanadium on 2009-03-21
I knew about Aqualung, but I never have been able to achieve lame gapless playback with it. It is a while since I tested it, though.

> Mpd is not really a player, but a music server and a really good one, if you take the time to figure out how it works
Not really, in that it will not serve music to a remote player. Rather, it is a music player that can be controlled from over the network. It is very light in resources, and in addition to gapless playback, supports replay gain all the way (except for mp3 replaygain tags should be in ID3 format). It scales perfectly with large music collections.

Only drawback indeed: you have to figure out how to install it. Not that difficult, but neither very easy.

---

### Post by logos34 on 2009-03-21
> **The Bright Side said:**
> Any ideas about Audacious? Did anybody have the same problem? Perhaps it's because I'm using 64 bit. But then, I specifically downloaded a 64 bit deb for the Crossfade plugin: 

I'm using 64-bit and haven't encountered that particular error message before

---

### Post by hugmenot on 2009-03-21
A real gapless solution is being worked out for Quod Libet at the moment. It is based on playbin2 in Gstreamer, which allows this type of sample exact gapless mode. It&#8217;s not a cross-fader.

It already works, but it requires [patching]("http://code.google.com/p/quodlibet/issues/detail?id=49") QL at this stage.

---

### Post by joris1977 on 2009-03-22
> **vanadium said:**
> Not really, in that it will not serve music to a remote player.

True, but if you let mpd stream to an icecast2 server, you can listen to your music with any remote player that can handle shoutcast To control your music you can easily use mpd over ssh...

---

### Post by vanadium on 2009-03-23
Yes, if you let ... I just wanted to clarify that in its own, mpd is not a music server.

You can control mpd with an ssh prompt, but you can also control it with any mpd client over the network, for which it is designed.

---

### Post by amano on 2009-11-07
What is the current state here? 

Quod Libet has gapless playback for flac and ogg now (the version in Karmic?) but is still missing support for lame info tag MP3s?


And Audacious has support for gapless lame files?

---

### Post by cascade9 on 2009-11-07
Amarok 1.4.0+ and Exaile 0.3.0+, XMMS2 and Jajuk are meant to support gapless playback as well. But I'm not sure if thats ogg/flac only, or mp3 as well. 

> **vanadium said:**
> Options are still very limited for gapless playback of mp3 (properly ripped and lame encoded). mp3 might still constitute the majority of your collection because it is the only format supported by any digital audio player.

The only true gapless playback option for lame that I know is music player daemon (mpd). It is what I use. mpd is a "server" and you control it with a client of choice, command line (mpc), norton commander like (ncmpc), full fledged graphical (sonata, gmpc, ...), or through a web interface in your browser. Only drawback: somewhat more difficult to set up.

True. Pity that there is less ogg and flac support for protable devices, or the other OSes stupid media players (iTunes, WMP). While I dont like the lack of support from Apple and Microsoft, its understandable, they are pushing thier own 'audio solutions'- WMA and M4A/AAC vs Ogg Vorbis, and WMA-'lossless' and ALAC vs Flac.

---

### Post by hugmenot on 2009-11-07
> **amano said:**
> What is the current state here? 

Quod Libet has gapless playback for flac and ogg now (the version in Karmic?) but is still missing support for lame info tag MP3s?

Actually not yet. Quod Libet devs [merged the gapless patches into the main branch recently]("http://code.google.com/p/quodlibet/issues/detail?id=49#c66"), but no release including gapless has been made yet. On the upside you can look forward to perfect gapless for all formats, including LAME header based, once this release is made. I can offer to upload a package to a PPA once it is out. It already works well here, but I run from a development snapshot.

---

### Post by amano on 2009-11-07
thanks hugmenot ):P

From what my testing today showed:

NOT:
- Exaile 0.3 from the Karmic repos is NOT gapless for my flac files. Is it for anyone? I switched to the unified plugin, turned on the crossfader and set the crossfading time to zero.
-Banshee will be gapless, once this branch is merged: [http://gitorious.com/~raof/banshee/gapless-work](http://gitorious.com/~raof/banshee/gapless-work) There doesn't seem to be too much activity in there though...
- Audacious wasn't gapless for me by default. I wanted to turn the crossfader plugin on, but that isn't shipped by default? It is even not in the Karmic repos?


WORKING: Rhythmbox is gapless, though not for MP3. I hope that will be tackled soon.

FUTURE: While the current Quod Libet doesn't offer any gapless currently, it seems to be our best bet to do so soon (if hugmenot is hopefully right).

NOT tested: Aqualung is probably gapless but overall it is a PITA usability wise.

Any comments?

---

### Post by cascade9 on 2009-11-07
> Experimental support for gapless (must be enabled in prefs)

[http://www.exaile.org/](http://www.exaile.org/)

I'm not sure where you turn on gapless, and being experimental it might not work. I thought I had seen a post on hydrogen audio saying that someone had got gapless going fine with exaile 0.3.0, but I could be wrong. 

I really hope that the exaile devs dont think that crossfading = gapless..... 

I would test it myself, but I'm using foobar2000 as my main audio player, and besides that...I only have exaile 0.2.11 (guess what distro that is LMAO)

---

### Post by lazka on 2009-11-09
> **amano said:**
> 

FUTURE: While the current Quod Libet doesn't offer any gapless currently, it seems to be our best bet to do so soon (if hugmenot is hopefully right).



You can use my PPA: [https://launchpad.net/~lazka/+archive/dumpingplace/](https://launchpad.net/~lazka/+archive/dumpingplace/)

---

### Post by reacocard on 2009-11-16
On Exaile, Unified with crossfade _disabled_ is gapless, with crossfade enabled is NOT. There's just no toggle explicitly saying its gapless because it's inherent in the Unified engine.

---

### Post by amano on 2010-07-29
From what I can tell the latest Audacious 2.3 should support gapless MP3 support (even with the default input and output plugins).

At least my own test files seem to work. I am hunting down a few of really demanding samples to test it out, but the files from the hydrogenaudio wiki seem to have vanished.

EDIT: I traced down the files in the wayback machine: [http://web.archive.org/web/*/http://guruboolez.free.fr/samples/gapless/gapless_WAVPACK_free_of_right.zip](http://web.archive.org/web/*/http://guruboolez.free.fr/samples/gapless/gapless_WAVPACK_free_of_right.zip) Those are wavepack files and are completely gapless with rhytmbox and audacious. I have to transcode them to mp3 files to check if the decoder can handle the lame information in the lame info tag.

---

### Post by amano on 2010-07-29
Bad news:

First observation: Don't transcode those files with the "Sound Converter" tool of Ubuntu to MP3. That will produce files that even Winamp (on Windows) cannot play gaplessly. I had to transcode to flac first and then use LAMEDROP (a frontend for the command line LAME binary) on windows to get MP3 files with correct LAME info tags. Winamp could play those files gaplessly, Audacious couldn't. It was just a small glitch (not even a gap), but nonetheless not perfect.

:(

The Audacious MPEG plugin seems to be compiled against libmad. Compiling against mpg123 would be a much wiser choice because that features gapless playback and is still maintained (it is LGPL'ed): [http://www.mpg123.de/features.shtml](http://www.mpg123.de/features.shtml)

---

### Post by amano on 2010-07-29
I just gave the command line mpg123 from the universe repo a try. And that ultimately gave me 100% perfect gapless playing for MP3s. Thus it is definitely possible to do this on Linux. All graphical frontends should switch to use just the decoder part of mpg123 instead of their crappy homegrown decoders for MP3. If Gstreamer cannot offer it, just don't use it.

---

### Post by hugmenot on 2010-07-29
> **amano said:**
> I just gave the command line mpg123 from the universe repo a try. And that ultimately gave me 100% perfect gapless playing for MP3s. Thus it is definitely possible to do this on Linux. All graphical frontends should switch to use just the decoder part of mpg123 instead of their crappy homegrown decoders for MP3. If Gstreamer cannot offer it, just don't use it.

You don’t know what you’re talking about. GStreamer uses MAD a fine mp3 decoder. The decoder has nothing to do with the tags.

---

### Post by amano on 2010-07-30
I am not too sure that the 2004 libmad version could handle the LAME info tag. Which was necessary to handle gapless MP3 playback...

The LAME info tag has nothing to do with normal tagging. The MP3 isn't gapless by design. And the LAME info tag is written by most modern encoders to mark all padding chunks that have to be skipped. mpg123 can handle that but probably NOT the normal libmad version from 2004. A libmad Winamp plugin (by shibatch) could handle that, but that was heavily patched.

see [http://wiki.hydrogenaudio.org/index.php?title=Gapless](http://wiki.hydrogenaudio.org/index.php?title=Gapless)

>   **Format support**

Since lossless data compression excludes the possibility of the introduction of padding, all lossless audio file formats are inherently gapless. The following lossy audio file formats have provisions for gapless encoding.

    * (Ogg) Vorbis
    * Speex 

Some other formats do not officially support gapless encoding, but some implementations of encoders or decoders may handle gapless metadata.

    * LAME-encoded MP3 can be gapless with players that support the LAME Mp3 info tag.
    * AAC in MP4 encoded with Nero Digital from Nero AG can be gapless with foobar2000.
    * AAC in MP4 encoded with iTunes 7.0 can be gapless with iTunes 7.0 and latest foobar2000

---

### Post by hugmenot on 2010-07-30
I know what a LAME header is, my error was assuming that Gstreamer supports it. Sorry. They support Xing VBR header but not LAME.

Here’s the bug. Go and help them fix it.

[https://bugzilla.gnome.org/show_bug.cgi?id=620322](https://bugzilla.gnome.org/show_bug.cgi?id=620322)


Still, there’s no necessary relation to the Mp3 decoder. The Lame tag can just as well be read by the demuxer and used for gap removal outside of the mp3 decoder.

---

### Post by amano on 2010-07-31
The upcoming Audacious 2.4 switched to the mpg123 decoder from libmad as well and is now playing my MP3s gaplessly, too!!!

There is a backports PPA from Benjamin Drung with this version: [http://www.liveoxy.com/index.php?q=aHR0cHM6Ly9lZGdlLmxhdW5jaHBhZC5uZXQvfmJkcnVuZy8rYXJjaGl2ZS9iYWNrcG9ydHM%3D](http://www.liveoxy.com/index.php?q=aHR0cHM6Ly9lZGdlLmxhdW5jaHBhZC5uZXQvfmJkcnVuZy8rYXJjaGl2ZS9iYWNrcG9ydHM%3D)

For 2.4 they even switched to pure GTK+ by default, the Winamp skins are optional now.

You can test the gapless MP3 feature by using the test samples that I attached on the launchpad bug 52741434: [http://launchpadlibrarian.net/52741434/Gapless%20MP3.zip](http://launchpadlibrarian.net/52741434/Gapless%20MP3.zip)

---

### Post by hhh on 2010-08-05
> **amano said:**
> The upcoming Audacious 2.4 switched to the mpg123 decoder from libmad as well and is now playing my MP3s gaplessly, too!!!

There is a backports PPA from Benjamin Drung with this version: [http://www.liveoxy.com/index.php?q=aHR0cHM6Ly9lZGdlLmxhdW5jaHBhZC5uZXQvfmJkcnVuZy8rYXJjaGl2ZS9iYWNrcG9ydHM%3D](http://www.liveoxy.com/index.php?q=aHR0cHM6Ly9lZGdlLmxhdW5jaHBhZC5uZXQvfmJkcnVuZy8rYXJjaGl2ZS9iYWNrcG9ydHM%3D)

For 2.4 they even switched to pure GTK+ by default, the Winamp skins are optional now.
It needs to be noted that this is one of the greatest posts on the boards right now. Gapless playback right out of the box and solid as a rock with whatever you throw at it. Add this PPA and
```
sudo apt-get update && apt-get install audacious
```
!!!!!

Thanks for posting, amano.

---

### Post by Hans Upp on 2010-10-08
I'm new to Ubuntu/Linux and I just **wish** I knew what all that meant.
You guys always seem to post assuming everyone here is a computer geek.

But in the short time I have been using it this is one problem I have tried to resolve.
I really want to make Audicious work, but Ver 2.3 is the latest from Ubuntu software centre and doesn't output sound when using the crossfader (I want crossfading more than gapless if poss).

Before reading this I had downloaded Aud ver:2.4 independently but can't find a way to install it.
It would seem that, with linux, gone are the days of simply double clicking a file to install.

Please don't suggest I type a page of hieroglyphics, as seems to be the norm, but is there any other way?

---

### Post by amano on 2010-10-09
I think that you will have to upgrade your Ubuntu to version 10.10 (out today!) to get Audacious 2.4 without a lot of fiddling.

You can install it from the Software Center then...

---

