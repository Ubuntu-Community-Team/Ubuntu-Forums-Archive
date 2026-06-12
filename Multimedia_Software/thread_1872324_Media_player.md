---
title: "Media player"
date: 2011-10-30
forum: Multimedia Software
---

### Post by DisMember on 2011-10-30
Hi guys i am an avid Ubuntu user (been using it exclusively for about 5 yrs) but due to unity i have decided to move to Kubuntu (still getting the hang of KDE vs Gnome lol) anyways.. i want a media player with the ability to loop sections of a song for when i am learning music for my band.. any ideas??

---

### Post by inobe on 2011-10-30
audacity will loop a selected segment with ease.

a powerful audio editor, it can be found in software management.

---

### Post by SeijiSensei on 2011-10-30
[Clementine]("http://code.google.com/p/clementine-player/downloads/list") is a nice audio player based on Amarok 1.x.  I wasn't happy with the changes made when Amarok moved to version 2.x and was glad to see the earlier code forked as Clementine.  To loop a track or set of tracks, create a playlist, then tell Clementine to repeat it using the Playlist > Repeat functions.

If you're also interested in something that will play video, I recommend smplayer with mplayer2 as the backend.  You'll need to install the latter from [PPA repositories]("http://www.ubuntugeek.com/install-mplayer2-on-ubuntu-using-ppa.html").  Install smplayer first, then add the repository described in that article and run "sudo apt-get update; sudo apt-get upgrade" to replace the original version of mplayer with its mplayer2 alternate.

---

