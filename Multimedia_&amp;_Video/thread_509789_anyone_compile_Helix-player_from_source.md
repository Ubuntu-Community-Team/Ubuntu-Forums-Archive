---
title: "anyone compile Helix-player from source?"
date: 2007-07-25
forum: Multimedia &amp; Video
---

### Post by logos34 on 2007-07-25
It seems like RealAudio does not like me--I have had nothing but problems getting it to playback correctly, glitch-free, in edgy and feisty.  Mplayer takes forever to launch, and after an error message or two eventually will play ram files fine (and I can record fine too).  RealPlayer starts up faster but is unresponsive once playback starts.  Video .rm files are another matter--I have yet to get it to play back with buffering problems or whatnot.

I'd like to use just one player and I hope with a little tweaking I can get RealPlayer to work.  I've tried all the different settings in prefs like transport and buffering options and nothing seems to help.  I'm not sure what the problem is.  Could it be the Helix-player mozilla plugin?  I noticed the nphelix.so plugin (from the repos) was compiled using an earlier gcc version than the firefox browser.

Here's what about:plugins shows:
> 
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.623 built with **gcc 3.2.0** on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes 


While about:config shows this:

> about:buildconfig

Build platform
target
i486-pc-linux-gnu

Build tools
Compiler 	Version 	Compiler flags
gcc 	**gcc version 4.1.2** (Ubuntu 4.1.2-0ubuntu4) 	-Wall -W -Wno-unused -Wpointer-arith -Wcast-align -Wno-long-long -pthread -pipe
c++ 	gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4) 	-fno-rtti -fno-exceptions -Wall -Wconversion -Wpointer-arith -Wcast-align -Woverloaded-virtual -Wsynth -Wno-ctor-dtor-privacy -Wno-non-virtual-dtor -Wno-long-long -fshort-wchar -pthread -pipe

Would it help to uninstall the helix-plugin and compile from this [source pkg (.bz2)]("https://player.helixcommunity.org/2005/downloads/")?  And is it just the usual ./configure, make, make install routine to install it?  I tried replacing the helix-player 1.0.6 with the rpm 1.0.8 (converted with alien), but that didn't help--the mozilla plugin is a separate package.  If I install from the source pkg will it deposit a newer mozilla plugin compiled against gcc 4.1.2 and is that the answer?  

I'm really at wits end with Real media and the various players.  I just need one dedicated player to reliably handle playback from Streamtuner and sites like BBC radio without a lot of fuss or locking up.

---

### Post by logos34 on 2007-07-27
bump

---

