---
title: "sound converter not converting files"
date: 2009-03-18
forum: Multimedia Software
---

### Post by ene_dene on 2009-03-18
When I put some files in sound converter and click on convert I just get the empty directory of artist and album, but not the converted file. Conversion is immediate so it never actually took place. What could be the problem? All the formats seem available, but I can't convert anything.

---

### Post by jward3010 on 2009-07-11
Exact same problem, no matter what I convert from or to. 

- MP3 - OGG (NO)
- FLAC - OGG (NO)
- FLAC - WAV (NO)

It seems to analyse all the tracks (very quickly) but not do anything with the conversion. Might be worth running from the command line, I'll try and post back, basically what I mean is I'm hoping it will display something useful.

---

### Post by jward3010 on 2009-07-11
OK, here's the output of running it from the command line:

Some things of note: The source files (the .flac files) are on an NTFS partition, which is mounted and working correctly. Where I want the results to be is in my /home partition so should be no problems there. Both areas can be written to by a normal user without problems.
```
wards@wards-pc:~$ soundconverter 
SoundConverter 1.4.1
  using Gstreamer version: 0.10.22, Python binding version: 0.10.14
  using gio
  using 1 thread(s)
error: Could not determine type of stream. (Torrent_downloaded_from_Demonoid.com.txt)
Mime type skipped: text/plain
Mime type skipped: text/plain
Mime type skipped: text/plain
Mime type skipped: text/plain
Mime type skipped: text/x-vhdl
Mime type skipped: text/plain
Queue done in 0s
Queue done in 0s
Queue done in 2s
Creating folder: 'file:///home/wards/Muse/Origin%20of%20Symmetry'
home
wards
Muse
Origin%20of%20Symmetry
error: Could not open resource for reading. (01 - New Born.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/01 - New Born.ogg'
error: Could not open resource for reading. (02 - Bliss.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/02 - Bliss.ogg'
error: Could not open resource for reading. (03 - Space Dementia.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/03 - Space Dementia.ogg'
error: Could not open resource for reading. (04 - Hyper Music.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/04 - Hyper Music.ogg'
error: Could not open resource for reading. (05 - Plug In Baby.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/05 - Plug In Baby.ogg'
error: Could not open resource for reading. (06 - Citizen Erased.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/06 - Citizen Erased.ogg'
error: Could not open resource for reading. (07 - Micro Cuts.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/07 - Micro Cuts.ogg'
error: Could not open resource for reading. (08 - Screenager.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/08 - Screenager.ogg'
error: Could not open resource for reading. (09 - Darkshines.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/09 - Darkshines.ogg'
error: Could not open resource for reading. (10 - Feeling Good.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/10 - Feeling Good.ogg'
error: Could not open resource for reading. (11 - Megalomania.flac)
Cannot set permission on '/home/wards/Muse/Origin of Symmetry/11 - Megalomania.ogg'
Queue done in 1s
```

---

### Post by jward3010 on 2009-07-11
Last thing: Just in case it's a read / write permission's thing with NTFS (which is silly at this stage) I copied the files I wanted converted to my /home directory so here's how it is now:

Source: /home/username/Music/Muse/song1,2,3...flac
Destin: /home/username/Muse/song1,2,3...ogg

...and still no luck! 

Because I saw "Cannot set permission on /home/...." I thought I'd run it as "sudo soundconverter" - same problem!

---

### Post by kuric on 2010-12-14
This is a known bug related to destination folders.
Go to Edit > Preferences and change the output folder.
Eg. /home/%username%/music

Or else, try gksudo soundconverter.

---

