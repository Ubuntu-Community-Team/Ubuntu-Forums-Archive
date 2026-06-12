---
title: "How do I rip a DVD?"
date: 2008-11-08
forum: Multimedia Software
---

### Post by Maheriano on 2008-11-08
What's the best way to rip a DVD to my computer so I can watch it without the DVD? I tried ripping an ISO with K3B but obviously can't play the ISO file. I want to preserve the AC3/DTS encoding.

Also, is there any software to upconvert the DVD file to 1080i?

---

### Post by stinger30au on 2008-11-08
there is a few programs in the repos

click applications-> add remove and search on dvd and you will find a few


otherwise install wine and then dvdfab free

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

---

### Post by SuperSonic4 on 2008-11-08
dvdrip is the best I've come across. You're meant to be able to use vlc but I've never been successful after version 0.9.x

```
sudo apt-get install dvdrip
```

on my machine vlc is playing an ISO file with video but no audio

/me goes to check out k9copy

---

### Post by alwayshere on 2008-11-08
k9copy rocks 
put below command interminal to install or use add/remove and search k9copy

 sudo apt-get install k9copy

---

### Post by mich4l83 on 2008-11-08
I can play iso files with smplayer.
for rip - look for dvdrip or similar apps in repositories.

---

### Post by Steve1961 on 2008-11-08
If you just want a backup then use k9copy to create an iso.  You can then play the iso with vlc or smplayer.  If you want to compress the DVD into an avi file then use dvdrip (takes quite a long time though)

---

### Post by VeeDubb on 2008-11-08
For ripping to an .avi, I prefer to use dvdrip.  I've tried acidrip, but it's too dumbed down for my tastes.

If you want to take a commercial DVD, rip it, and make a new DVD out of it on a regular recordable DVD, I highly recommend dvd95. (DVD 9 to DVD 5 converter, which is a reference to the fact that commercial DVD's are 9GB, rounded up to the next full gig, and DVDR disks are 5GB if you round up)  It's pretty basic, but if that's what you want to do, it does it well for 90% of DVD's.

---

### Post by Maheriano on 2008-11-09
What? No. I don't want to make backups, I don't want to make copies. I want to take a DVD and put it on my hard drive so I can play it from there and keep the AC3/DTS encoding. Basically I want all my movies on my computer so I don't haver to put the disc in to play them.

---

### Post by hansdown on 2008-11-09
Dvdrip will do it.

[http://thedailyubuntu.blogspot.com/2008/02/dvdrip-copy-dvd-to-hard-drive-in-snap.html](http://thedailyubuntu.blogspot.com/2008/02/dvdrip-copy-dvd-to-hard-drive-in-snap.html)

---

### Post by mc4man on 2008-11-09
For all titles with no 'structure protection' you could use vobcopy. It will rip to file (a video_ts in a movie name or volume name folder)
The repo ver. is fine for these titles, you'll get an exact copy of the title sans css encryption.
Basic command (assumes mount at /media/cdrom0, copies to home dir.
```
vobcopy -v -m -F 16
```

Vobcopy can also be set up to autorip from dvd insertion from one or multiple drives at once, destination other than home can be added to command with -o /<destination> 

For 'structure protected titles' if you rip to file in most cases they'll need to be repaired  for proper playback. Some options are 

k9copy - setting target size above title size will prevent processing of the title (shrinking) - updated occasionally

As mentioned in several threads using DVDFab HD Decrypter in wine - will again give you complete repaired title, updated often for new protections.
Not that hard to set up

[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

Editing the source of vobcopy can make it suitable for many protected disks (enabling fast skip of unreadable sectors) but you'll need to manually repair.


If you rip to an iso then there is no need to decrypt (remove css) or fix structure protection as long as your just intending to playback on pc with open source players. (totem-xine and vlc can easily play unmounted .iso's

In this case a dd command can work though physical damage and or structure protection can cause it to fail or take a long time to rip.

An interesting way to copy to iso that is unaffected by structure protection (other than ripping time) is to use dvdisaster. It will make an exact copy in iso format. (is very fast on non s.p. titles
It also leaves css and s.p. in place which isn't an issue as far as playback. (and also means no circumvention  dmca wise

There are a few things about setting up and getting it to work on encrypted disks which it wasn't intended for, - no big deal to do,  let me know.
see screen for example of disk with minor s.p.

---

