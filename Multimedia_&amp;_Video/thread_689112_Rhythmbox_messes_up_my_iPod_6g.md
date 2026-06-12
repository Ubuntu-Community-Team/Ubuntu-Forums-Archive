---
title: "Rhythmbox messes up my iPod 6g"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by SandmanXC on 2008-02-06
I have plugged in my iPod Classic (6g) and played music from it with Rhythmbox. All nice and smooth, till I unplug the iPod and see that it has no songs, seen by it's (crappy) OS. Of course, the files are there, but I can't play them from the iPod. 

I found sort of a sollution, to boot windows and add a new file with Winamp (i don't use iTunes), which reverts the whole database, but that's a long and boring process for every time I leave the house. Please advise.

---

### Post by bskerr on 2008-04-07
bump
I have this exact problem. The files are still there, but only rhythmbox can access them. Itunes in Windows says my ipod is unreadable. Annoying!

---

### Post by soga_genzo on 2008-04-07
Rhythmbox relies on a library called libgpod. Gutsy has only version 0.5.2 of said library, while 6th generation iPods are only supported from version 0.6.0 onwards. The upcoming Hardy has 0.6.0 in its repositories.

---

### Post by bskerr on 2008-04-07
Thanks for the reply! Is there anything stopping me from upgrading to libgpod 0.6.0 now (I'm running Gutsy)? In the meantime, is there any way to make my ipod function normally again without restoring factory defaults and re-copying all my files?

---

### Post by SandmanXC on 2008-04-07
I managed to get my music back in the following way (but on Windows  i used Winamp 5.5, not iTunes):

1. I plugged my ipod on Windows; 
2. I opened it with winamp;
3. I selected a random track and copyied it to the media library;
4. I deleted the file from the ipod using winamp;
5. I re-added it.

Worked every time. 

Another thing that helps is to go to **System->Preferences->Removable Drives and Media->Multimedia** and uncheck *"Play music when connected"* under **Portable music players**. This allowed me to use the ipod as a storage unit, and didn't mess up the database unless I added, or copied, music to, or from,  the ipod. If you really have to add while on Ubuntu, then follow the steps above.

---

### Post by djdjules on 2008-05-09
Thanks, all my music is back. 
The remaining problem is that some of the album art is not showed by the ipod OS.

I can see the album art for every track with Itunes but when I unplug the ipod and launch coverflow the covers are gone...

any magic solution for this?

---

### Post by djdjules on 2008-05-11
ok so I got the album art for the music back.
I just selected all the audio files on the ipod and added "more" artwork. I just added a random image, the same for all the files.
With this I got Itunes to update the artwork database and the covers are back.
Now the remaining problem is with my movies.
I have tried the step that fixed the music artwork with the movies but it didn't have the same results. All I get is black boxes...

Any ideas?

---

### Post by bskerr on 2008-05-19
the new version of libgpod fixed the problem temporarily...I was able to copy music with rhythmbox without any hassles (only album art didn't work, but i wasn't going to be picky). for some reason the other day, copying mp3s from rhythmbox began having the same old problems again. i tried installing amarok and it's doing the same thing...is it possible that i didn't manage to uninstall the old libgpod completely, or that i inadvertently reverted to the old version? please help -- i don't actually have a windows computer available for me to constantly revert my ipod...it involves bugging a friend each time

---

### Post by SandmanXC on 2008-05-19
I have no idea. I only used windows to transfer music since I noticed the problem. But what you could do is stack some music, and when you have a couple of gigs to go, transfer them to the ipod as files, and go to your friends house and transfer them using itunes/winamp. I don't know what else to suggest.

---

