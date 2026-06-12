---
title: "strange headphones / movie problem"
date: 2013-03-17
forum: Multimedia Software
---

### Post by sasasasasasa on 2013-03-17
On kubuntu 12.04 I have developed a strange problem that I have no real idea how to debug.  

This first point is that everything <used> to work properly but at some point (and I'm not sure when) the headphones stopped working properly but only for VLC (and Dragon video player).

On loudspeakers the sound is fine, as soon as I plug my headphones in the sounds becomes garbled - it sounds like some of it is playing backwards in short segments while some of it is playing
fowards (another way to put it is speech sounds like the people are trying to speak underwater).  If I remove the headphones the sound is fine.

Digital audio (say amarok) is unaffected.

The only things I can think that have happened since I knew it previously worked are updates and the installation and deinstallation of the enlightenment drum machine and jack (I removed these and reinstalled vlc in a hope that might fix things).

I've no idea how pulse audio works and no idea if this is the problem - does anyone have any hints as to where I start?

[BTW on all my machines which have different sound systems pulse kmix only gives me volume control and nothing like balance etc where would I find a more complete mixer?]

Thanks!

---

### Post by sasasasasasa on 2013-03-19
Tried cross posting at VLC but the only suggestion there was this was a pulseaudio problem.

Having mucked around with paman and pavucontrol etc I can find no clue as to what is going on.

However I have found out that:

* my headphones are playing in MONO under amarok and there appears to be nothing I can do about this.  pavucontrol seems to think it is stereo and gives me separate left and right volumes (but they can't be set to different levels??) but the sound is clearly mono.

* I checked the mm settings in KDE and tried the VLC backend (instead of gstreamer) and it gave the same borked result - movie players produce highly distored sound on headphones.

This is driving my mad - anyone got any suggestions as to where to go with this problem?

---

