---
title: "Gapless playback seems to have gone away"
date: 2011-05-03
forum: Multimedia Software
---

### Post by caulkins on 2011-05-03
I've discovered that flac files which played gaplessly in Rhythmbox on Maverick won't do so on Natty.  There is now a dropout when transitioning from one to the next.  Why might that be?

---

### Post by Claritux on 2011-05-07
I have the same problem here. Both Rhythmbox and Banshee refuses to give gapless playback even when enabling the crossfading feature in Rhythmbox. Worked fine in Maverick.

---

### Post by powerpleb on 2011-05-08
Yes, me too. This certainly blows.

EDIT: I found this but report: [https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/774417](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/774417)

---

### Post by Claritux on 2011-05-10
Is there any player for Natty where this currently works? I'd rather change media player than live without gapless playback.

---

### Post by vanadium on 2011-05-10
Somewhat tedious to install and configure, but mpd (music player daemon) combined with a frontend such as sonata was for a long time the only decent gapless playback solution in linux (so I am still using it). It is low on resources and handles large libraries extremely well.

---

### Post by Squonk07 on 2011-05-15
Unfortunately for me mpd was no dice. Same problem. In fact, I can't remember ever getting gapless to work on Ubuntu in Rhythmbox or Banshee, though until Natty the last time I spent a lot of time with an Ubuntu distro was Karmic so maybe I missed the "window of perfection." I seem to recall gapless worked in Songbird, but of course they dropped Linux support so that's no longer an option.

I'm stuck using Wine to run Foobar2000, which is neither optimal nor likely to rub committed open source users the right way. Not a single player I've tried in 11.04 (Exaile, Rhythmbox, Banshee, mpd, Amarok) has had gapless working (actually I can't say whether Exaile worked because it crashed before I could get it to play anything; Aqualung was the same).

EDIT: Exaile doesn't crash anymore (they must have fixed that), but it has the same nasty gap as all the others. Aqualung actually played something this time (last time it sat silently then hung), but the gap was there, too. I think this has to be something with audio in general rather than a player-specific issue.

---

### Post by vanadium on 2011-05-15
> **Squonk07 said:**
> Unfortunately for me mpd was no dice.
It should work out of the box for audio formats that are natively gapless such as ogg and flac. For lame-encoded mp3 files, you need to "activate" the option "gapless_mp3_playback" in the mpd config file.

You probably are aware that before mp3s can be played back without gaps, they must be properly encoded with lame, and must be played with software that understands the specific lame tags allowing this.

---

### Post by mb_3000 on 2011-05-17
native gapless playback has been something I've been looking for for years on linux and it has never worked properly. 

After trying every single music player for linux, the only way I could manage to get REAL gapless playback, not only with FLAC but also with mp3, has been using wine+foobar2000. it works flawlessly, the only thing broken is the equalizer. everything else (including a lot of 3rd party components) work perfectly.

---

### Post by Claritux on 2011-05-29
I managed to fix gapless in Rhythmbox on my system by simply increasing the network buffer slider under playback options! :D
I have no idea how to fix it in Banshee though.

---

### Post by Claritux on 2011-05-29
Also make sure the crossfade option is checked.

---

### Post by hybridxdawn on 2011-06-11
I have the same issue (with mp3s and mp4s, using banshee 2.1.0) and it's been driving me crazy. Is there a bug report about this/is there hope that this will be fixed in 11.10?

---

### Post by therieb on 2011-07-07
I have been experiencing the same issue in Natty in both Rhythmbox and Banshee.  In fact, I haven't gotten crossfading to work since Rhythmbox in Intrepid.  The only gapless playback that works consistently for me is Foobar2000 in Wine, but I can't get my Ipod to sync to it.  Has anybody been able to do this?  I'm looking for an all in one solution.

---

### Post by crazystan on 2011-09-25
Not to be tardy to the party, but after looking around for a while, I started using Listen, which has been (so far) flawless w/ gapless playback of flac files. Overall, seems to be a decent program, and for what it's worth, I prefer it to banshee in terms of looks, and functionality.

---

### Post by Claritux on 2011-09-26
Listen gives, at least on my Oneiric beta install, unfortunately no gapless what so ever. In Oneiric I can't seem to get gapless in Rhythmbox either, as the network buffer slider is gone. I really hope they will fix this before Oneiric hits stable, or at least before 12.04. A LTS release **should** have gapless playback fixed by default, considering the last one had (at least on my system).

---

### Post by Thad E Ginathom on 2011-10-01
Rant:
[I]
What is it with "gapless playback" and Ubuntu? Do all the package  developers actually like to listen to music with silences inserted in  it? Even my King of media players, VLC, cannot handle this most basic of  requirements. The forum posts go back years and years, and the  situation does not seem to improve[/I]

Rant over :)

The Good news is [**Aqualung**]("http://aqualung.factorial.hu/").

My system: Natty 11.04 with 2.6.38-8-lowlatency kernel, jackd and associated firewire components from [KXStudio]("http://kxstudio.sourceforge.net/Main_Page"), "Classic" login thus Gnome 2 desktop with compiz. Not *exactly* vanilla Ubuntu, but I doubt that anything there changes Aqualung's behaviour.

I have tested Western classical and live rock from WAV and flac, so far, as well as from CD. This is the Aqualung developer's claim:
> Pick a song that you know   really well, something that's in your bones like *Siberian   Khatru*. Grab it from CD using cdparanoia to have it as   a WAV file. Now open your favourite wave editor and slice the file   up into multiple consecutive sections. Be careful not to insert   silence, delete samples or alter any sample data. Save the slices to   separate files. Now convert the sample rate of some pieces to random   values (the example program shipped with the [libsamplerate]("http://www.mega-nerd.com/SRC/") library will   let you do this in very good quality). Pick some pieces and convert   them to [Ogg Vorbis]("http://www.xiph.org/ogg/vorbis")   format. Pick some others and encode them to [FLAC]("http://flac.sourceforge.net/"). Pick a few and convert   them to MONO. Now open up the Playlist editor of the music player in   question and add the files in order. **Push play, and   listen.**
    Aqualung is a music player designed from the ground up to   provide continuous, absolutely transparent, gap-free playback across   a variety of input formats and a wide range of sample rates thereby   allowing for enjoying quality music... 

[Link]("http://aqualung.factorial.hu/"). (Click on Read More >> at the end of the first paragraph.) It has passed my test (exception: playback from CD. The gapless-tracks thing is *fine* but there are dropouts that may or may not be removed by the configuration.).

My personal requirement is for a player with a simple interface (I'm using an audio player, not surfing the net or pretending to be using a car stereo or reading a magazine) and simple file-handling (drag and drop) capabilities (Library functions may be there but should be optional) that preferably outputs direct to jackd (for my firewire interface: KXStudio will route it from alsa or pulse, who wants to send their sound round the houses!)

There are so many players. I will check out some more and contribute the results (sometime...) but, for today's exploration, the results are:

**VLC**: *Fail*
**SMplayer**: *Fail*
**Quad Libet**: unsure. Yesterday I thought there were minute silences, today it seems to be broken. Probably not going to bother to fix it, as I now have a working player...
**Aqualung**: [I]Pass

[/I]

---

### Post by Thad E Ginathom on 2011-10-01
**audacity:** *Pass?* it was just a quick test, but it didn't seem to miss a beat in the Mahler. The position slider got very confused, though. Imperfect.

---

