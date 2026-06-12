---
title: "Garbled sound after Upgrade"
date: 2012-01-27
forum: Multimedia Software
---

### Post by Geekasaurus on 2012-01-27
I have a frustrating problem after the most recent upgrade to my 10.04LTS system.  Some (and only some) of my mp3's play very quietly and garbled.  This was not a problem before the system upgraded earlier today.

I noticed the problem first when playing some Flash Video. The video was a talking-heads program intermixed with live music.  The talking heads portion exhibited this problem, but the music portion played normally.  During the talking-heads portion of the video, I had to turn the volume up TO THE MAX in order to hear it at normal level.  But when the music played, it played WAY TOO LOUD.  When the video went back to the talking heads, the problem recurred.  I use Firefox 3.6.24

I tried playing some MP3's using Rhythymbox, Movie Player, and Gnome Mplayer, and got mixed results.  Some MP3's from the same album would play garbled, the others normal (example; Chuck Mangione;_ Feels So Good _was garbled but _Hill Where the Lord Hides_ played normally). This was consistent across players.  

I don't mind rolling back the upgrades from 1/27/12, but haven't a clue which one might have munged my Pulse Audio driver.  Here's the history from Synaptics:

Commit Log for Fri Jan 27 13:57:55 2012
Upgraded the following packages:
evince (2.30.3-0ubuntu1.2) to 2.30.3-0ubuntu1.3
firefox (3.6.24+build2+nobinonly-0ubuntu0.10.04.1) to 9.0.1+build1-0ubuntu0.10.04.2
firefox-branding (3.6.24+build2+nobinonly-0ubuntu0.10.04.1) to 9.0.1+build1-0ubuntu0.10.04.2
firefox-gnome-support (3.6.24+build2+nobinonly-0ubuntu0.10.04.1) to 9.0.1+build1-0ubuntu0.10.04.2
icedtea-6-jre-cacao (6b20-1.9.10-0ubuntu1~10.04.2) to 6b20-1.9.10-0ubuntu1~10.04.3
icedtea6-plugin (6b20-1.9.10-0ubuntu1~10.04.2) to 6b20-1.9.10-0ubuntu1~10.04.3
language-pack-en (1:10.04+20110204) to 1:10.04+20110931
language-pack-en-base (1:10.04+20110204) to 1:10.04+20110931
language-pack-gnome-en (1:10.04+20110930) to 1:10.04+20110931
language-pack-gnome-en-base (1:10.04+20110204) to 1:10.04+20110931
libevdocument2 (2.30.3-0ubuntu1.2) to 2.30.3-0ubuntu1.3
libevview2 (2.30.3-0ubuntu1.2) to 2.30.3-0ubuntu1.3
libicu42 (4.2.1-3) to 4.2.1-3ubuntu0.10.04.1
openjdk-6-jre (6b20-1.9.10-0ubuntu1~10.04.2) to 6b20-1.9.10-0ubuntu1~10.04.3
openjdk-6-jre-headless (6b20-1.9.10-0ubuntu1~10.04.2) to 6b20-1.9.10-0ubuntu1~10.04.3
openjdk-6-jre-lib (6b20-1.9.10-0ubuntu1~10.04.2) to 6b20-1.9.10-0ubuntu1~10.04.3
ubufox (0.9~rc2-0ubuntu2.1) to 0.9.3-0ubuntu0.10.04.3
x11-common (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1
xbase-clients (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1
xorg (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1
xserver-xorg (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1
xserver-xorg-input-all (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1
xserver-xorg-video-all (1:7.5+5ubuntu1) to 1:7.5+5ubuntu1.1

Installed the following packages:
firefox-locale-en (9.0.1+build1-0ubuntu0.10.04.2)
xul-ext-ubufox (0.9.3-0ubuntu0.10.04.3)

The first question is; Which of these packages munged the audio drivers? I'm lazy; does someone want to give me a command line to roll it back?

I am an experienced Unix guy (command-line/shell script master).  But this the first time I've experienced a driver problem with a so-far-so-beautiful installation.  I'll report a bug if I can definitively find  out which package did the munging.

The hardware is a homebrew.  I can post the hardware specs if anyone wants them.

---

