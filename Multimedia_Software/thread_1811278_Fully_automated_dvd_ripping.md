---
title: "Fully automated dvd ripping"
date: 2011-07-24
forum: Multimedia Software
---

### Post by qwerty2k on 2011-07-24
Hi, I'm looking to somehow fully automate the dvd ripping process so i can insert a disk and have it auto rip the dvd then eject the cd so i can insert another as its something i really want for my headless ubuntu server (it is running the latest standard desktop ubuntu which i remote into via vlc).

anyone got any advice on how i can achieve this or if there are any exiting programs that can do this? either rip to iso (dvd5) or to mp4/mkv.

---

### Post by mc4man on 2011-07-24
If you weren't looking to do auto  cli rip and encode there are 2 fairly easy solutions, vobcopy(mirror disk to file) and ddresue (dump to encrypted and if present structure protected iso

The big issue is always structure protection which if present renders vobcopy generally useless. In an .iso dump SP is irrelevant other than the # of unreadable sectors - anything over 5000 or so starts to take quite some time to read thru

So you may wish look at handbrake, it does a main title re-encode and handles most Sp's well. I've never used but see if it can be run from cli

The other option would be makemkv for linux, search in google

If you decide to go to whole disk, no encoding than let me know, worked out a ddresue script to auto authenticate drive and dump to the dvd's title.iso
vobcopy is just a straight up command, both can be used to autorip

---

### Post by qwerty2k on 2011-07-25
thanks for the post, is there a cli tool for dvd5->dvd5 that will then be an iso at the end of it?

---

### Post by libbrechtemmanuel on 2011-09-20
> **mc4man said:**
> If you weren't looking to do auto  cli rip and encode there are 2 fairly easy solutions, vobcopy(mirror disk to file) and ddresue (dump to encrypted and if present structure protected iso

The big issue is always structure protection which if present renders vobcopy generally useless. In an .iso dump SP is irrelevant other than the # of unreadable sectors - anything over 5000 or so starts to take quite some time to read thru

So you may wish look at handbrake, it does a main title re-encode and handles most Sp's well. I've never used but see if it can be run from cli

The other option would be makemkv for linux, search in google

If you decide to go to whole disk, no encoding than let me know, worked out a ddresue script to auto authenticate drive and dump to the dvd's title.iso
vobcopy is just a straight up command, both can be used to autorip

Can I have some more info about the script you worked out please?

I would like to automate the process of copying a dvd to my hard drive via CLI.

---

