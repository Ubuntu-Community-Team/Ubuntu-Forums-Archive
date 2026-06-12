---
title: "DVD playback woes in 12.04"
date: 2012-05-18
forum: Multimedia Software
---

### Post by MST3Kakalina on 2012-05-18
This is always the biggest and most annoying problem I have with Ubuntu: f*cking DVD playback.

Medibuntu is in my repos and I've installed libdvdcss, libdvdnav, and so forth. I've followed all of the suggestions here:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

as well, including the install-css bash command.

The best I can get is that DVD will mount as an audio CD, but be entirely useless and unreadable in any media player  (VLC,MoviePlayer, or xine).

What the hell is going on?

---

### Post by BicyclerBoy on 2012-05-18
Some optical drives don't work..
Matushita are problematic..
Laptop slim optical drives seem to be worse..
I believe the firmware prevents the brute force CSS attack.

Some region 1 discs require regionset..
 
Try HandBrake (from nighty builds not std distro). This package has best chance of working.

Because of playback problems, you have to rip..

You might be able to find a firmware patching tool for your drive.

I find that some DVDs need to be ejected & then try again..
Some DVD intro/menus cause trouble. Navigate immediately to title menu & then play works.

---

### Post by MST3Kakalina on 2012-05-18
It has worked before though. This is my machine: [http://forum.notebookreview.com/notebook-news-reviews/41148-hp-dv5000z-review-pics-specs.html](http://forum.notebookreview.com/notebook-news-reviews/41148-hp-dv5000z-review-pics-specs.html)

It has a Toshiba-Samsung optical drive.

Unfortunately, the Handbrake hack doesn't work either. The disc can't be mounted, according to the error message that comes up.

I also seem unable to set the region on my drive. I am hesitant to do that as I'm not sure it will help (I didn't have to in older releases when it worked just fine) and I'm not sure what the repercussions might be. I'm am American living in South Korea, moving to Sweden, so I have media from more than one region.

Trying to skip DVD menus doesn't work either, unfortunately.

Output from VLC:

```
VLC media player 2.0.1 Twoflower (revision 2.0.1-0-gf432547)
libdvdread: Using libdvdcss version 1.2.12 for DVD access
libdvdread: Could not open /dev/cdrom with libdvdcss.
libdvdread: Can't open /dev/cdrom for reading
[0xb5621e60] dvdread demux error: DVDRead cannot open source: /dev/cdrom
[0xb7400618] main input error: open of `dvdsimple:///dev/cdrom' failed
```

---

### Post by BicyclerBoy on 2012-05-19
Could there be something wrong with the udev rules for/or auto-mounting..

That error sounds like the DVD device /dev/cdrom is incorrect..
Check your /dev/cdrom0 cdrom1 sr0 sr1 etc..

---

### Post by MST3Kakalina on 2012-05-19
In /dev/ both cdrom and dvd link to sr0.

I haven't even looked at udev before so I'm going to need some guidance about how check the rules for that.

---

### Post by mc4man on 2012-05-19
If you want to ck. your device symlinks just run this, with or without a disk in the drive (might as well insert a dvd, let the drive activity settle, then run command
```
sudo lshw -C disk
```
look under the *-cdrom (you may show status=ready with a dvd in which means a disk was detected but no filesystem found

The vlc error is more likely that when trying to access the UDF filesystem none was found

---

### Post by MST3Kakalina on 2012-05-19
```
  *-cdrom                 
       description: DVD-RAM writer
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       capabilities: audio dvd-r dvd-ram
       configuration: status=open

```

this regardless of whether or not there's a disc in the drive.

---

