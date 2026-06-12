---
title: "DVD help?"
date: 2008-03-13
forum: Multimedia &amp; Video
---

### Post by skylinedna on 2008-03-13
Im trying to play dvds (wll rip them to my laptop as well) But some play fine others play but the screen is all kind of pixilated? screenshot below. ive tried downloading the gstreamer codecs throu add remove with no results also i tried using mplayer and vlc with no result? at the moment i just wanna play them :)

---

### Post by xc3RnbFO8P on 2008-03-14
Install this:
> 
sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list
> wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
> sudo apt-get install w32codecs

> wget -c [http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb](http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb)
> sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb
> sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot
> sudo /usr/share/doc/libdvdread3/install-css.sh

Backup Dvds (in Add/Remove All Available Application)i: >  DVD::RIP and K9copy

EDIT:   I think you have problem with video driver: 

> In Mplayer Preferences> video> available drivers: x11
Restart player.
In Vlc Preferences> video> output module> x11

---

### Post by skylinedna on 2008-05-03
when i do the second quote it says non valid gpg format or something similar??

---

