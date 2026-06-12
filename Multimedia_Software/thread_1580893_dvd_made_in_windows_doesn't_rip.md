---
title: "dvd made in windows doesn't rip"
date: 2010-09-24
forum: Multimedia Software
---

### Post by andrea000 on 2010-09-24
I have a dvd that was made on windows and acidrip rips about 75% of it then stops.All others that was made on ubuntu ripped but not the one made on the windows pc.Can someone tell me how to rip it or maybe a software better then acidrip.Thanks

---

### Post by silent_shade on 2010-09-24
I don't know if it is better, but you may give a try to dvd::rip, it appears to be pretty advanced piece of software. Now, does this dvd contain video or just the data? In first case, consider trying to rip it with MPlayer with the command
mplayer dvd://1 -v -dumpstream -dumpfile ~/Your_DVD/1.vob
and than transcode.
As far as I recall, you need following packages to any of these programs to work: 
libdvdcss2, libdvdnav4, libdvdread4,
but may be you already have them?

---

### Post by Crazedpsyc on 2010-09-24
just open the cd in nautilus and copy everything you want. Nautilus has a built in ripper that makes ripping and even burning just like copying form one folder to another

---

### Post by andrea000 on 2010-09-24
> **silent_shade said:**
> I don't know if it is better, but you may give a try to dvd::rip, it appears to be pretty advanced piece of software. Now, does this dvd contain video or just the data? In first case, consider trying to rip it with MPlayer with the command
mplayer dvd://1 -v -dumpstream -dumpfile ~/Your_DVD/1.vob
and than transcode.
As far as I recall, you need following packages to any of these programs to work: 
libdvdcss2, libdvdnav4, libdvdread4,
but may be you already have them?

The dvd contains a video.I have libdvdcss2, libdvdnav4, libdvdread4, installed i didn't think of ripping it with mplayer only acid rip and dvd rip.I'll try it with mplayer.Thanks

---

### Post by Crazedpsyc on 2010-09-25
For playing purchased dvd movies you have to install ubuntu-restricted-extras. This is because having the ability to access dvds on your computer in some countries is illegal.

---

