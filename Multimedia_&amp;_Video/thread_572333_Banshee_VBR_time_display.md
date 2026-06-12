---
title: "Banshee VBR time display"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by bbchalmers on 2007-10-10
I recently re-encoded my CD collection to high quality VBR  mp3 using Grip and Lame.

Banshee however does not display the correct time on any of the new rips.  When a song is played banshee seems to struggle for the first few seconds until it eventually displays the correct time. I'm pretty sure that it;s affecting sound quality for the first 10-15 seconds of each song.

Is this a known problem with Banshee or more likely to be a problem with my lame settings?

Rhythmbox does not have this issue but I much prefer the design of Banshee and would prefer to continue with it if I could find a solution to this problem.

Many thanks in advance.

---

### Post by tgalati4 on 2007-10-10
What rate are you encoding at and what version of Banshee?

I have not experience any problems with ~192 kbps VBR and Banshee 0.13.1.

---

### Post by bbchalmers on 2007-10-10
My encoder command line looks like this:-

-V 1 --vbr-new %w %m

The files usually average around 210-220 kbp/s   My version is banshee is 0.12.1 which i installed from the repos.

Is there any way of updating this to the newer version you are using?

---

### Post by tgalati4 on 2007-10-10
I'm running Dapper.  I followed these instructions:

[http://banshee-project.org/Distributions/Ubuntu](http://banshee-project.org/Distributions/Ubuntu)

Checking some more of my mp3 files:

Some files ripped at 192 VBR show up as 128 kbps in the "Edit Song Metadata-->Details".  Plays OK, and I can tell by the size of the file 7 MB vs 4MB that it's encoded at a higher rate.

I think it has to do with a preprogrammed table of stream rates in Banshee.  If it doesn't find a standard stream rate, it defaults to 128 in the Details box regardless of what the real rate is.

Banshee doesn't have a real-time stream rate display (like XMMS does).  Perhaps there is a plug-in that will display actual stream rate.

It's a minor annoyance, but as long as it doesn't affect playback, who cares.  Audioscrobbling works.  Multimedia keys under Gnome do not work (some problem with initializing), Lyric server doesn't work.  

Banshee is a work in progress, but it works fast for my meager 3k library.

---

### Post by bbchalmers on 2007-10-10
I found instructions on the banshee site to install 0.13. First time I have compiled anything so  thats been a bit of an adventure. No change on the time issue but the search works a good bit quicker than on 0.12.1

I asked my flatmate whether he could hear anything wrong with the sound at the start of songs and he reckons I'm talking out of my **** so I think I'll stop worrying about it.

as you say Banshee is a work in progress and I'm sure the little issues will be fixed along the way.

Many thanks

---

### Post by tgalati4 on 2007-10-10
I will sometimes hear clicks and pops at the beginning of a track between song changes.  I don't know if its an encoding problem or buffer problem.  I usually listen to Banshee from another machine (through ssh) and my music library is on another machine through sshfs.  So as long as I hear music, I don't worry too much about it.

Helpful tip:

If you run banshee from a remote machine:

>dbus-launch banshee --debug

This will alow dbus messages to go to the proper host machine and the debug switch gives you a debug tab to watch for errors.

---

