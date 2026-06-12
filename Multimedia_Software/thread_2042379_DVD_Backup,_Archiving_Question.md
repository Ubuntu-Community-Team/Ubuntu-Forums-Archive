---
title: "DVD Backup, Archiving Question"
date: 2012-08-14
forum: Multimedia Software
---

### Post by cave_man() on 2012-08-14
Hello,
   
  I need some guidance on the best method to make “exact copy” backups of my DVD collection. I am using Ubuntu 12.04. 
   
  I have seen many posts on how to “backup” a DVD but, invariably, some manner of compression is being used.
   
  What I want is an archival quality copy of the DVD with no loss of information so that I don’t need to keep the physical DVD. Hard drive space is not much of a concern.
   
  What I have done in the past is use dd:
   
  Code:
  dd if=/dev/dvd of=/path/to/dvdcopy.iso
   
  I wait for a bit and dd provides me with a lovely iso file that I can watch with VLC or Movie Player.
   
  My understanding is that the above command gives me an exact (bit-for-bit) copy of the DVD. This is basically what I am after but dd isn’t removing the copy protection or region code.
   
  My questions are:
   
  1. Is the fact that I have not stripped the region code and copy protection going to cause me grief down the road?
   
  2. Is there a better method for backing up a DVD that removes copy protection and region codes but leaves me with a lossless copy of my movie including the menus and extras?
   
  3. Am I correct in believing that the dd command is giving me an exact copy of the movie? The reason that I ask is that the iso file is often much smaller than I would have expected. For example when backing up one commercial DVD the iso file was around 4.7 GB. I would have expected it to be closer to 9 GB for a commercial DVD.
   
  Thank you

---

### Post by The Cog on 2012-08-14
Oops, posted a reply to the wrong window - sorry.

---

### Post by ads52 on 2012-08-15
Have a look at vobcopy with the *-m* option.

---

### Post by mc4man on 2012-08-15
> 1. Is the fact that I have not stripped the region code and copy protection going to cause me grief down the road?
region coding is only on the physical media

As far as an encrypted iso - 
No real issue as long as you don't need to burn back to media 
Because encrypted iso's are brute force decrypted there could, (rarely),  be an occasional failure to decrypt on short samples like some extras

There is code available to do an 'in place' decryption on iso files, though it must be compiled & also is subject to brute force limitations

* I'd go with vobcopy which will work good with all disks that don't contain structure protection *

If you insist on direct ripping to .iso ala dd, then dvdisaster is superior - 
It is a gui
Allows for repeated passes after initial if there were some unreadable sectors due to physical defects, only the previous unreadable are re-read
If re-reading the read tries can be raised from the default of 1 which increases likelihood of success

It can handle also some disks with structure protection, I'd say 5000 or so unreadable sectors is about the cut off point time wise
The only 'trick' to dvdisaster is you must authenticate the drive 1st. - insert disk, start a player like vlc, stop player, start dvdisaster

I believe you could also use brasero to decrypt & make an iso though it will likely not deal with structure protection

 > For example when backing up one commercial DVD the iso file was around 4.7 GB. I would have expected it to be closer to 9 GB for a commercial DVD.

The size is solely determined by length of video/extras/menus @ the bitrate used for the mpeg2 encoding which can vary quite a bit

---

### Post by cave_man() on 2012-08-19
Hello all,

Thank you all for the responses.

I've used vobcopy -m to rip the DVD to the HDD. I can then play the DVD from the HDD using VLC. Using VLC -> open folder the DVD menues work. 

I can then use mkisofs to make an iso image:

mkisofs -dvd-video -o MOVIE_NAME.iso /PATH/TO/MOVIE/FOLDER/

I'm not sure if there is any value in creating the .iso image though because it doesn't save any space. They only thing I need to confirm is whether XBMC can play the VIDEO_TS folder with DVD menue support. I know XBMC can play .iso files.

---

### Post by ads52 on 2012-08-20
I usually convert to iso as well, it is a little tidier and an easy matter later to burn to dvd. Plus most better quality media player will play from iso...

---

