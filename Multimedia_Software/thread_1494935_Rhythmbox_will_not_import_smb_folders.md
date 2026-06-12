---
title: "Rhythmbox will not import smb folders"
date: 2010-05-27
forum: Multimedia Software
---

### Post by cbope on 2010-05-27
I have Rhythmbox installed in 10.04 on a fresh install with all current updates. I have the FLAC and FAAD libs installed and gstreamer-plugins-ugly, plus the default set of plugins that come with Rhythmbox in 10.04.

All my music is stored on a self-built NAS running FreeNAS and serving files over SMB. This NAS has been in use for more than 4 years and has worked flawlessly with all my Windows machines using Winamp as a music player frontend.

I can mount the SMB chare in 10.04 and I have no trouble browsing my music files/folders on the NAS. However, if I try to import the music stored on the NAS using Music > Import Folder... nothing happens in RB. Even dragging and dropping individual music files from a nautilus browser window does not work (nothing happens). Most of the files are FLAC with some MP3's. All music is organized as \artist\album\tracks. My music collection is a bit more than 16k songs (about 95% are ripped from my own CD's). All tracks are properly tagged.

There are no error messages, just nothing happens when dragging tracks into the library or using the Import Folder menu item. What am I missing or doing wrong?

---

### Post by cbope on 2010-05-29
Bump

Seriously, am I the only one storing my media library on an SMB share? This is either seriously broken or I am just not doing something right. I have several boxen running Lucid now and all of them behave the same when trying to import a folder from the SMB share.

---

### Post by andyfied on 2010-05-30
I did try the same thing (I retired my old computer and converted it into a big network drive of sorts) but right now I'm having trouble getting rhythmbox to open external drives. I did have the SMB share working with rhythmbox, but that was a while ago and I can't remember how I did it. I certainly can't getting it working again now either.

---

### Post by SeraphicDeviltry on 2010-05-31
Same problem here. Have all my mp3 on a smb share (windows xp), drive is mounted, can see the files, can play them in VLC, can play files that I imported before the 10.4 upgrade, but I can not import new ones.

I'd appreciate any help I can get.

---

### Post by stevebeaumont on 2010-06-02
Yes, I am experiencing the same problem. Rhythmbox will not import form smb folders. I can't speak for version before 10.04. In addition when using sftp (ssh) server connection, as a substitute for smb, not all files imported. This can be fewer than 20% on occasions. It's a shame really, can this be sorted out.

Best Regards
Steve B

---

### Post by patrickvdbemt on 2010-06-04
just done the 10.04 upgrade this afternoon.
on the 9.x I was still able to add SMB shared libraries into my Rhytmbox.
since the update : NOPE !!!:mad:

---

### Post by canplaythegame on 2010-06-05
after days of crawling through forums about this issue
i had the same problem and tried so many so called fixes
but still nothing
and went to bed last night thinking i might just have to go back to windows
( this is not the only problem i have to fix)
but i woke up this morning did a little bit more searching found 
some more people with the same problem
then i noticed a red arrow for updates
a couple of the updates were for rhythmbox
and thought could it be
after the updates and a restart
i can now play files from my readynas duo
now onto the other problems
ill have to post this everywhere i looked now

lol

daniel d

---

### Post by SeraphicDeviltry on 2010-06-08
Installed the latest updates and it now works. For some reason the updates had not downloaded on their own.

---

