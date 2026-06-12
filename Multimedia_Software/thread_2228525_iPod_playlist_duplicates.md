---
title: "iPod playlist duplicates"
date: 2014-06-07
forum: Multimedia Software
---

### Post by JohnDillinger43 on 2014-06-07
I'm having an issue I've seen posted in a number of places with no tangible solution.  Each time I connect my iPod to my 14.04 laptop (and this issue has persisted since 12.04, when it first appeared), each song on each playlist is duplicated.  Thus a 10 song playlist becomes 20 songs the first time I connect it, 30 songs the next time, etc. (increasing linearly, not exponentially, is what I'm saying).  The duplicates don't show up in RhythmBox or on the iPod itself, yet when the playlist actually plays, it acts as if the extra songs are there, and the total count for the number of songs on the playlist reflects this as well.  I tried Clementine as well, but there seems to be a bug with this particular version that causes it to crash every time I connect my iPod.  Interestingly, in Banshee I can see the duplicates, and I can even delete them in Banshee.  However, when I disconnect the iPod, they're still there, and when I plug it back in, Banshee shows them as if I never deleted them.  Note that these aren't duplicate files, but just duplicate entries in the playlist.

Has anyone dealt with this issue?  Has anyone heard of a way to resolve it?  Are there other iPod management programs I should be trying?

---

### Post by jonathan44 on 2014-07-15
I am experiencing the same issue.
I believe it is the same as the issue discussed in the forums:
[http://ubuntuforums.org/showthread.php?t=2004725](http://ubuntuforums.org/showthread.php?t=2004725)
[http://ubuntuforums.org/showthread.php?t=2086731](http://ubuntuforums.org/showthread.php?t=2086731)
It is listed on bugzilla as bug number 687827 and is probably related to bug number 678911
([https://bugzilla.gnome.org/show_bug.cgi?id=687827](https://bugzilla.gnome.org/show_bug.cgi?id=687827) and [https://bugzilla.gnome.org/show_bug.cgi?id=678911](https://bugzilla.gnome.org/show_bug.cgi?id=678911) respectively)

I have an iPod classic 6th generation 1st revision 120GB.  As is stated above, everytime I use Rhythmbox my iPod's playlists think there is one extra copy of every song, and similarly every podcast is duplicated. But no files are actually duplicated, the ammount of memory used/available on my iPod is the same as before.  The duplicates (of songs) do not show up anywhere but in playlists, they don't show up in the lybrary as a whole.  Since changing to Ubuntu 14.0.4 (from Windows 7) I have only made one explicit change to my iPod, and that is transfering a single file (a podcast, but not from an official podcast source, so Rhythmbox and my iPod saw it as a song).  [s]I don't see the duplicates when I am scrolling though my playlists,  only[/s] the song count in the menue changed, but I do see the duplicate  podcasts, and when I play the podcast, all four copies are listed as  currently playing if i go back to the menue while listening, and they  are all marked as played once the podcast has been played.
However, Rhythm box is not duplicating the 18 files which I had two identical copies of (do to a mess years ago when my computer crashed from trying to restore my iTunes library). It instead moved them to the top of the playlist.  The playlist I normally listen to has 6205 songs, and it now regesters as having 24766 songs ((6205-18)*4+18), since I have only plugged my ipod in 4 times.  All my playlists were created in iTunes.

EDIT: I am actually able to see the duplicate songs when schrolling through my static playlists, The duplicates are layed out differently than in the podcast menue.  The entire playlist is stacked on top of itself.  my playlist now has the order of the 18 songs mentioned above and then the main playlist repeated in original order 4 times.  Theses duplicates have the same behavior as mentioned for the podcasts.  The reason for this confusion is because my playlists are so long.  I have double checked though, this issue does not occur in iTunes' "smart" playlists (which is what I scrolled thorugh yesterday - because they are shorter).

---

