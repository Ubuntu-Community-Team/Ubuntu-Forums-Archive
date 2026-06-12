---
title: "House music burn help"
date: 2012-09-30
forum: Multimedia Software
---

### Post by Diametric on 2012-09-30
Hi,

I'm trying to burn a house cd and remove the track markers.  I've converted the individual .mp3 to .wav (for my old *** car).  The problem is when I burn the files to disk (using brasero) there is a "track gap"...a small second gap between tracks that I don't want there.  I've looked at the prefs in audacity and brasero to see if i can edit the files so that they are read continuously by the player but can't seem to find anything.

What I want is to be able to burn the .wav files so that they are read as the disk was intended - uninterrupted the way house music was designed.

Make sense?

Thanks!

---

### Post by shantiq on 2012-09-30
Ok Diametric   rafac24 explained [**howto**]("http://ubuntuforums.org/showpost.php?p=6846999&postcount=2") here with Brasero  [not tried it myself] but looks good


> Opening the 'New Audio Disc Project' on Brasero
 Adding all your songs you want to burn to the right-hand side column.
 Highlighting all the songs on the same column and right clicking.
 -Edit Information-
 A menu should come up, on the bottom it reads: 'Pause Length'
 You can change it to 'Remove Silences'.

[ATTACH]224882[/ATTACH]


@@@@@@@@@@@@@@@@


also [**commandline**]("https://wiki.archlinux.org/index.php/Gapless_Audio_CD_Creation_from_MP3s") with cdrdao

---

### Post by Diametric on 2012-10-03
Great!  Thanks for your help!

---

