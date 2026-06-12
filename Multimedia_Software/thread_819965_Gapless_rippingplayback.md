---
title: "Gapless ripping/playback"
date: 2008-06-05
forum: Multimedia Software
---

### Post by Mako Eyes on 2008-06-05
Hello community. I'm not necessarily new to Ubuntu, but I'm new to using it as a primary operating system. The first thing I want to do is get my music library up and running again. 

What I wish to do is get perfect seamless playback between tracks. Being a Pink Floyd and Dream Theater fan, this is an absolute must. I've run into some problems, however.

What music I had backed up I tried in Amarok, but there is a very noticeable gap between tracks. I've tried Rhythmbox, Sound Juicer and Banshee to both rip and play music tracks from my CDs or library, but all of them either produce gaps when encoding or lack the ability to remove gaps between tracks natively. I can't really pinpoint which of these is the problem.

I have also tried using GRIP, but I get an error message saying "Invalid encoder executable check your encoder config" whenever I try to rip tracks. In all cases I'm trying to rip to ogg Vorbis files.

Is there something I'm missing? Is there a plugin required for these applications that allow gapless playback or ripping? What can I do to get GRIP working properly? Searching the Internet results in dead-ends.

Oh, and can any of these programs rip an entire album/CD into one track? I think GRIP can do it, as I have seen an option similar to the description but I am unable to test it out due to the reason mentioned above.

Many thanks.

---

### Post by jdneate on 2008-12-17
Hi  Have you had any success in resolving this one ? It is a definite limitation.

It is a problem with operas where the performance is continuous without gaps between arias  - when you rip the cd you end up with gaps between the arias which completely destroys the experience ! ( it would be like going to the theatre and having an interval every 3 mins) .....  Its not only Pink Floyd listeners !   John

---

### Post by vanadium on 2008-12-17
On the ripping side: most rippers should be gapless, but you should test. mp3 is gapless only when you encode with lame. ogg, mpc, flac, ... are formats that support gapless without any tricks.

grip should work fine if you use the build in cdparania. I experienced that tracks are not properly aligned when you rip using the external command line tool. rubyripper claims to be a too for secure autio ripping. I had no experience, though, where tracks were not aligned properly, resulting in a nasty click between tracks.

Rubyripper is supposed to support images, but the last time I checked, it did not work. Rubyripper is still in early developing, though.

Bottom line, though, is that I am still using EAC under Wine ...


On the playback side: increasingly, players support gapless playback for gapless audio formats. Thus, Rhythmbox should be able to playback ogg or flac gaplessly, although you first must change a setting and restart the program (strange how this essential feature for music playback is so poorly supported). However: try and test first. I am not sure if it works well and I did not test lately.

There is only one single solution I know that allows for true gapless mp3 playback. It is mpd, music player daemon. Even then, not all files that were gapless in foobar2000 are gapless in mpd. Audacity with the gapless plugin goes a long way also, but deletes the gaps by "detecting" them rather than using the lame tags for that purpose.

For the audiophile, I see mpd with one of the nice frontends (I use sonata) as the only fully satisfying option. It is gapless and fully supports replaygain (although mp3 replaygain tags must be in idv3 format, and not in ape format. Unfortunately, mp3gain only stores ape tags). It seamlessly supports large libraries. It is somewhat tricky to set up, though.

---

### Post by logos34 on 2008-12-22
> **vanadium said:**
> mp3 is gapless only when you encode with lame. ogg, mpc, flac, ... are formats that support gapless without any tricks.

+1.  ogg and flac natively support gapless w/o need for special options

The problem is that several media players that purport to support gapless playback do not work as advertised--Amarok is one (the problem appears to be with the Xine- backend/engine implementation of that feature). 

> Audacity with the gapless plugin goes a long way also, but deletes the gaps by "detecting" them rather than using the lame tags for that purpose.


The only player that I can count on for gapless playback is Audacious (or is that what you meant?) with the Cross Fade plugin (>prefs>audio>output plgin prefs>crossfader tab>crossfade/transition type: **None (gapless/off)**

---

### Post by Muttonhead on 2008-12-24
I have several audio cds that are lectures that I'd like to rip, but most of these cds are multiple tracks which span the length of one lecture.

I'm using Ubuntu 8.10 and I'd like to rip the entire audio cd as one file.  Ogg or Flac would be fine.

What is the best way to do this?  I'm not afraid of the command line.  :)

Thanks!

---

### Post by logos34 on 2008-12-24
> **Muttonhead said:**
> I have several audio cds that are lectures that I'd like to rip, but most of these cds are multiple tracks which span the length of one lecture.

I'm using Ubuntu 8.10 and I'd like to rip the entire audio cd as one file.  Ogg or Flac would be fine.

What is the best way to do this?  I'm not afraid of the command line.  :)


The best choice IMO would be either [Rubyripper]("https://help.ubuntu.com/community/CDRipping#RubyRipper") or [ABCDE]("http://www.andrews-corner.org/abcde.html") (cli).

Rubyripper>Preferences>'Rip CD to single file'

ABCDE:

abcde -1 -o ogg

or

abcde -1 -M -o flac 

([Encode the whole CD in a single file]("http://linux.die.net/man/1/abcde"). The resulting file uses the CD title for tagging. If the resulting format is a flac file with an embedded cuesheet, the file can be used as a source for creating other formats.)

good luck

---

### Post by Muttonhead on 2008-12-24
> **logos34 said:**
> The best choice IMO would be either [Rubyripper]("https://help.ubuntu.com/community/CDRipping#RubyRipper") or [ABCDE]("http://www.andrews-corner.org/abcde.html") (cli).

Rubyripper>Preferences>'Rip CD to single file'

ABCDE:

abcde -1 -o ogg

or

abcde -1 -M -o flac 

([Encode the whole CD in a single file]("http://linux.die.net/man/1/abcde"). The resulting file uses the CD title for tagging. If the resulting format is a flac file with an embedded cuesheet, the file can be used as a source for creating other formats.)

good luck

With your help, who needs luck?  :)  I tried abcde and it did ~exactly~ as I had hoped for.  These lectures have no CDDB data and abcde will even stop and allow me to select my choice of CLI text editor and write my own data.  It's the bomb. (!)

I can't possibly thank you enough for pointing me to this software.  Now I can do my lecture cds up right nice and I can also do my Pink Floyd up as well.  Thank you VERY much!

---

### Post by logos34 on 2008-12-24
> **Muttonhead said:**
> abcde will even stop and allow me to select my choice of CLI text editor and write my own data.  It's the bomb. (!)

I can't possibly thank you enough for pointing me to this software.  Now I can do my lecture cds up right nice and I can also do my Pink Floyd up as well.  Thank you VERY much!

my pleasure!  yeah, pretty neat, eh?  Although TBH I usually prefer to edit the track/album info in my music library organizer/jukebox (amarok), but it'
s nice to have the option to do so in terminal. Exact Audio Copy and ABDCE are my favs, but I hesitate to recommend the latter because so many people seem put off with the command line.  

Anyway, enjoy!

---

