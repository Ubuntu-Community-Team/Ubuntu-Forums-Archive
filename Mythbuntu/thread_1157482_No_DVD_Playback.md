---
title: "No DVD Playback"
date: 2009-05-12
forum: Mythbuntu
---

### Post by yerdon on 2009-05-12
Hi, I recently built a new box and installed MythBuntu 9.04.  Everything seemed to go good, and I can browse through the menus with no problem.  However, ran into an issue:

If I go to Optical Disks -> Play DVD, it flashes and comes back to the menu.  Nothing happens.  (I have an LG Blue-Ray DVD internal drive.)  Is further setup required?

I'm obviously a newbie here - any help would be greatly appreciated!

Joseph

---

### Post by phroman on 2009-05-12
Hi, you have to go into Mythbunu Control Center, Go to > Proprietary Codecs.  Enable Medibuntu Proprietary Codec Support.  Check the Enable libdvdcss2 box, hit the Apply button, you should be good to go.

---

### Post by derrickadean on 2009-08-03
im haveing the very same probalm only ive checked the boxes and still no dvd playback

---

### Post by KillerKiwi on 2009-08-04
Every single time I have this issue its been because the drive hasn't had its region set

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#Setting%20DVD%20Region%20Codes)

```

sudo apt-get install regionset
sudo regionset

```

Make sure you select the correct region code
[http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries](http://en.wikipedia.org/wiki/DVD_region_code#Region_codes_and_countries)

---

