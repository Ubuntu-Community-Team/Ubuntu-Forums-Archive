---
title: "VLC will not play a large file"
date: 2008-11-14
forum: Multimedia Software
---

### Post by _Moulin_ on 2008-11-14
Currently I am running Itrepid Ibex

I decided to backup a few of my dvds, so i used dvd:rip which splits my movie into 7 vob files of approx 1gig in size each. VLC plays these vob files fine.

When i join the vobs together so the movie is all in one vob file of approx 6gig vlc will no longer play it. I know the vob file is fine as other players like mplayer play this fine.

So my question is how would i get vlc media player to play large files?

thanks

---

### Post by Robstarusa on 2008-12-04
> **_Moulin_ said:**
> Currently I am running Itrepid Ibex

I decided to backup a few of my dvds, so i used dvd:rip which splits my movie into 7 vob files of approx 1gig in size each. VLC plays these vob files fine.

When i join the vobs together so the movie is all in one vob file of approx 6gig vlc will no longer play it. I know the vob file is fine as other players like mplayer play this fine.

So my question is how would i get vlc media player to play large files?

thanks

Are you on a 32-bit distro or 64-bit?

---

### Post by rocket777 on 2009-01-26
I'm having the same problem. I have a 32 bit distro, and I find that the breaking point is just at about 4 or 4.1 gigs. All my old mpeg files that used to play (in 8.04) now won't play in 8.10. 

Files under this 4.1 gig size play ok.

I also reset all the preferences, which didn't help.

I know that 4.1 gigs is about the limit for 32 bits, but the prior version of VLC (0.8.6) worked just fine (under 8.04 ubuntu).

---

### Post by mc4man on 2009-01-26
> now won't play in 8.10.
That's because the 0.9.4 version in 8.10 is buggy. broken and a security risk.
See if someone has done a 0.9.8a rev. for Intrepid. At least some security flaws are fixed and you can play files over 4.1Gb. (other things are still broken.
Building the latest 1.0 git yesterday I noticed some things are fixed, ( the equalizer being the biggest), the upcoming 1.0 release should be pretty decent (march..?

EDit:
Here's one source for vlc 0.9.8a for intrepid (.deb's)

[http://archive.getdeb.net/dump/intrepid/vlc/](http://archive.getdeb.net/dump/intrepid/vlc/)

The reason it's not in the regular getdeb is it wasn't tested and may or may not work right.
You could wait and hope 0.9.8a was backported or just build yourself.

If you were to try you'd need to dl. at a min. the vlc, vlc-nox, libvlccore, libvlc2, and maybe vlc-plugin-pulse packages.
Put them all in a folder, cd to the folder and run
```
sudo dpkg -i *.deb
```

ReEdit:
Went ahead and installed on a tester, seems ok, tried audio files and a couple of movies. (seems a little slow to open ...?
Did the 5 mentioned above plus a couple of add. plugins.
Just make sure all the same version (0.9.8a-1) and arch (i386 or amd64

---

