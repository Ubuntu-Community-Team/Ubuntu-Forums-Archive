---
title: "&quot;Your GStreamer installation is missing a plug-in&quot;"
date: 2011-10-18
forum: Multimedia Software
---

### Post by MelodiesonMusic on 2011-10-18
After upgrading to 11.10, whenever I try to play .m4a files in Exaile there's a "playback error" and my "gstreamer installation is missing a plug-in." When I try to play the same files in Movie Player it asks if I'd like to search for a suitable 'MPEG-4 AAC demuxer" plugin. When i click yes it says I need to refresh the repository, and when I do so, there's a message saying the internet connection has failed and that there are no suitable plugins. I can play my .ogg files just fine, and the same .m4a files worked in the previous distribution. Are there any packages i need that might have been removed when I upgraded? I have all the gstreamer plugins I can find.

---

### Post by BicyclerBoy on 2011-10-18
Do you have the gstreamer  base, good, bad & the ugly plugins ?

I have a suspicion that there are multiverse versions (extra file suffix)  with extra stuff. Can't check right now..

Can't recall if it helps but the "restricted extras" medibuntu script may expose more complete gstreamer plug-ins.

---

### Post by MelodiesonMusic on 2011-10-18
I happened to notice that last night while I was frantically downloading everything gstreamer related... :) When I search gstreamer good, for example, in Synaptic I get the following packages. I have all the packages but the ones with plus signs in front of them.

-gstreamer0.10-plugins-bad
+gstreamer0.10-plugins-bad-doc
-gstreamer0.10-plugins-bad-multiverse
-gstreamer0.10-plugins-good
-gstreamer0.10-plugins-good-dbg
+gstreamer0.10-plugins-good-doc
-gstreamer0.10-plugins-ugly
+gstreamer0.10-plugins-ugly-doc
+phonon-backend-gstreamer
-pulse audio

Gstreamer bad:
-gstreamer0.10-plugins-bad
+gstreamer0.10-plugins-bad-dbg
+gstreamer0.10-plugins-bad-doc
-gstreamer0.10-plugins-bad-multiverse
-gstreamer0.10-plugins-bad-multiverse-dbg

Gstreamer ugly:
-gstreamer0.10-plugins-ugly
+gstreamer0.10-plugins-ugly-dbg
+gstreamer0.10-plugins-ugly-doc

---

### Post by wolfen69 on 2011-10-18
I always enable the Medibuntu and Partner repos, then
```
sudo apt-get install non-free-codecs libdvdcss2
```
I'm a serious multimedia junkie, and have no problems playing *anything*. By doing that and installing vlc, you should be able to play it all.

---

### Post by MelodiesonMusic on 2011-10-18
:P My files play in VLC (I didn't even think to check that) but still no Exaile or Movie Player. 

When I type that into the terminal the output is "E: Unable to locate package non-free-codecs." When I omit the non-free-codecs part it says I already have the latest version. About those partner repos though.. after the upgrade I was notified that alot of things were being taken off my sources list, does that have anything to do with anything?

---

### Post by BicyclerBoy on 2011-10-19
Ubuntu upgrades always disables any 3rd party ppa including medibuntu..

You don't need the -dbg or the -doc

There is a gstreamer ugly multiverse
gstreamer0.10-plugins-ugly-multiverse

I have to admit that totem movie player will play from my MythTV DLNA server but there is no audio for **LATM-AAC** recordings only ones with AC3.
MythTV plays fine of course..

I managed to find a AV test track with mpeg4 AAC 5.1 audio ..plays okay (11.04).

---

### Post by MelodiesonMusic on 2011-10-19
After the upgrade I enabled everything that had been disabled. There's no ugly-multiverse in synaptic, nor can I get it through the terminal with apt-get. It's handled by gstreamer0.10-plugins-ugly according to the terminal.

---

### Post by BicyclerBoy on 2011-10-19
There is in *buntu 11.04...

but according to gstreamer website the AAC decoder is 'faad' & is part of gstreamer-bad package.

Try playing with :
gst-launch filesrc location=example.mp4 ! qtdemux ! faad ! audioconvert ! audioresample ! autoaudiosink


I don't have a 11.10 test system or bootable CD/DVD so can't really help.

The restricted extras webpage suugests re-running the medibuntu script after every upgrade.

---

### Post by no2498 on 2011-10-19
do you have winff and or ffmpeg

---

### Post by MelodiesonMusic on 2011-10-24
I re-ran the medibuntu script, I messed around with that code, and I made sure both winff and ffmpeg were installed all to no avail. I've stumbled upon a program called Insanity that says it'll test a whole bunch of GStreamer related things, but I'm not sure what to do with the sqlite db files it outputs.

---

### Post by BicyclerBoy on 2011-10-25
I wouldn't be surprised if there is some packages missing from 11.10.

11.10 seems to be missing working pulse audio for a lot of unhappy people..

Run this from terminal to check all gstreamer pulugins:
gst-inspect


There is a package needed to automagically find/install missing plugins on demand..
gnome-codec-install

This package is likely to be useful:
ubuntu-restricted-extras

---

### Post by mc4man on 2011-10-25
.m4a decoding support in gstreamer is generally supplied thru the ffmpeg plugin
```
sudo apt-get install gstreamer0.10-ffmpeg
```

(multiverse gstreamer plugins are mainly for encoding supoort

---

### Post by MelodiesonMusic on 2011-10-27
> **BicyclerBoy said:**
> 
There is a package needed to automagically find/install missing plugins on demand..
gnome-codec-install

Ha! Automagically, that made my day. :) But anywho, pulse audio, gnome-codec-install, the restricted extras and the ffmpeg plugins were all already installed.

---

### Post by BicyclerBoy on 2011-10-27
That's a highly technical computer term.

I made a 11.10 install just to see what all the forum traffic is about..
I noticed there is another package that finds missing codecs & suggests installation.
I can't recall the name right now but it came up on a gstreamer search in synaptic package manager.


There is a gstreamer package error in 11.04 with the mp3-fluedo-partner, so there could be an mistake in 11.10 packages.

---

### Post by OakRaider4Life on 2011-11-12
I'm having this problem as well! I've done all of the codec installs suggested on this thread and still can't get banshee or amarok to play my .m4a files. Anyone have ideas of what's going on here?

---

### Post by OakRaider4Life on 2011-11-12
Solved! After searching around a bit more, I found a solution on [this thread]("http://ubuntuforums.org/showthread.php?t=1859570"). The solution is:

I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

---

### Post by MelodiesonMusic on 2011-11-14
I wish I had read that sooner. I've already downgraded to 10.04 and upgraded back up to 11.10 making sure that everything worked before every upgrade. All that proved to be extremely tedious and now, unnecessary. =\

---

### Post by dudesurge on 2012-01-02
this has not worked for me with exaile

---

### Post by antiflag1980 on 2012-01-07
> **OakRaider4Life said:**
> Solved! After searching around a bit more, I found a solution on [this thread]("http://ubuntuforums.org/showthread.php?t=1859570"). The solution is:

I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

Thanks! This worked perfectly for me with exaile.

---

### Post by HappyPrime on 2013-01-29
> **OakRaider4Life said:**
> Solved! After searching around a bit more, I found a solution on [this thread]("http://ubuntuforums.org/showthread.php?t=1859570"). The solution is:

I had the same problem. Here's what I did to fix it:
open ~/.gstreamer-0.10
remove or rename the registry.x86_64.bin
Open your music player.
it'll regenerate the registry file and correctly use the aac plugin.

For me, the file was named registry.i686.bin
Meh, this still worked. Thanks.

---

### Post by breezypt on 2013-04-03
remaming  the registry.x86_64.bin to registry.x86_64.binold did the trick for me. I couldnt stream any radio stations. And as soon as I renamed this file and rebooted and reopened clementine, I was able to stream my radio stations. So Thank You for the heads up. By adding just the 3 letters old to the file, if it didn't work I could always remove the old and get back my file, no harm no foul. I always like to play it safe in Linux.

---

### Post by wildmanne39 on 2013-04-03
Thread closed. Please do not post in old threads.

---

