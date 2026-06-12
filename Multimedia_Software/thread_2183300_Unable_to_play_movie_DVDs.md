---
title: "Unable to play movie DVDs"
date: 2013-10-24
forum: Multimedia Software
---

### Post by Coder88 on 2013-10-24
I have a fairly nice xbuntu 13.10 recently installed on my desktop PC (six core AMD64, 16GB RAM, xubuntu on 128GB SSD, ASUS HD 7750 1GB silent video card). Wanting to tweak my xubuntu now. Having a problem playing DVD movies on my LG blu ray burner drive. Could use any help/suggestions. I have tried to do a little homework on this, but I am still at a dead end:

ubuntu 13.10 AMD64
my video player software installed: VLC, gxine, SMplayer, Mplayer, Banshee, Parole
i have installed: xubuntu-restricted-addons  ubuntu-restricted-addons  xubuntu-restricted extras libdvdread4 libdvdnav4 libbluray1  libzine1-ffmpeg libxine2-ffmpeg  libquiktime2        mencoder  libavcodec53 libopenexr6  libfaac0 gstreamer0.10-ffmpeg

I already had created a symbolic link to /dev/dvd
   ```
sudo ln -s /dev/sr0 /dev/dvd
```

if i insert a DVD (not bluray, just a simple dvd) movie  (e.g. The Man Who Knew Too Little, or Eight Legged Freaks) the DVD icon shows on desktop with title of DVD movie

if I try to play using gxine 0.5.905
  Encrypted media stream detected
   Media stream scrambled/encrypted
   [Close]

if I try to play using SMPlayer
   Seems to accessa and read DVD movie then dvd drop stops being accessed.

if I try to play using VLC player
 Media: Open Disc
 I choose default /dev/dvd to open and click the [Play] button
 VLC Media: Open Disc
   Playback failure:  DVDRead could not read block 0.

---

### Post by oldos2er on 2013-10-24
You probably need libdvdcss2. Run ```
sudo sh /usr/share/doc/libdvdread4/install-css.sh
``` to install it.

---

### Post by Coder88 on 2013-10-24
> **oldos2er said:**
> You probably need libdvdcss2. Run ```
sudo sh /usr/share/doc/libdvdread4/install-css.sh
``` to install it.

sweeeeeeeeeeeeeeeeeeet! That worked! Thank you so much!

Always frustrating when hitting roadblocks with common app needs, when the solution is often so simple a fix when discovered or shared by someone like you. I am going to make a doc of common issues like this and the solutions for subsequent installs.

---

### Post by Coder88 on 2013-10-24
Dare I even try playing a Blu Ray disc given my drive is a blu ray reader/burner? (i should probably start another thread on this, or do some searching, just wondering)

---

### Post by Pierre16 on 2013-11-03
I have a similar problem with Lubuntu 13.10.  Gnome-mplayer cannot play videos because it looks for them in /dev/dvd instead of /dev/sr0.  If I create a link:sudo ln -s /dev/sr0 /dev/dvd  it works but the links is wipe out each time I reboot.Can anybody help?

---

### Post by Dennis N on 2013-11-03
Pierre16;

You need to start a **new thread** - this one has been marked solved, and few people will see your post.

---

### Post by Pierre16 on 2013-11-06
Thanks Dennis.I have filed a Bug Report as this is something that should work out of the box... and people should not be forced to go to forums to get their player to work:[https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/1248194That](https://bugs.launchpad.net/ubuntu/+source/gnome-mplayer/+bug/1248194That) being said, I found a temporary answer:Adding ln -s /dev/sr0 /dev/dvd to /etc/rc.local creates the link each time I reboot.  While this resolves my situation, the problem remains a bug.  Ubuntu needs to address this.If anyone has the same problem, please confirm the bug at the above site so that it is fixed.Thanks.

---

### Post by bookrt on 2014-01-14
I had this problem with VLC in LUbuntu. I had a couple of brand new DVDs with a new kind of encryption that puts 99 titles on the DVD with the chapters all scrambled, and only 1 title is the correct one. This prevented the disc from playing in VLC and also prevented Handbrake from working since there is no way in Handbrake to tell which is the correct title. Just experimenting with stuff, I installed Totem and surprisingly the DVDs played perfectly (and also enabled me to find the correct title on the disc that had the chapters in the right order, which I was then able to rip in Handbrake).

---

