---
title: "forked-daapd showing music as movies"
date: 2014-04-27
forum: Multimedia Software
---

### Post by jochen2 on 2014-04-27
I got Ubuntu Server 14.04 LTS for my homeserver.
To make music accessible to our Apple Devices I tried using forked-daapd to publish a shared iTunes library.
After installing it I modified the configuration-file to point to the directory where the music is located, that's the only modification on the stock config-file.
The library appears in all our iTunes installations but it only shows the Movies-Icon and all music is displayed as if it was movies.
Funny enough, if I delete the forked-daapd-database and restart the server it will display correctly in iTunes and I can select everything to play.
The moment the scan is done the music-entry is gone and replaced with the movies-entry.

Any idea what might cause this behavior?

Thanks, Jochen

---

### Post by bogdan5 on 2014-05-10
I have the same issue :(

---

### Post by PC-Ente on 2014-06-12
Just wanted to confirm that this still happens...

Lubuntu 14.04 

forked-daapd from repos...

---

### Post by imilnes on 2014-06-19
Same here.

Ubuntu 14.04 LTS

Standard repositories
apt-get update
apt-get upgrade
apt-get mythbuntu-desktop
apt-get minidlna
apt-get forked-daapd

Standard config file - only thing changed is the file location

forked-daapd took over 2 hours to scan and gave a few out of memory errors.

I have something like 9500 tracks in the media folder, over 100 movies. No photo's.



forked-daapd is showing 179 movies, no music. Of that 179, there are some of my movies, maybe 50, the rest are music files

---

### Post by ejurgensen on 2014-06-20
This is a bug in forked-daapd 0.19. If you are able to upgrade to v21 it is fixed:
[https://launchpad.net/ubuntu/+source/forked-daapd](https://launchpad.net/ubuntu/+source/forked-daapd)

Otherwise, you may be able to get around it by removing all video from your library.

---

