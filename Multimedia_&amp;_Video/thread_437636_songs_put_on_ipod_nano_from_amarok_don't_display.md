---
title: "songs put on ipod nano from amarok don't display"
date: 2007-05-09
forum: Multimedia &amp; Video
---

### Post by rajan on 2007-05-09
hi, I'm having some difficulty with my ipod nano, specifically there are two albums that I am trying to transfer to it from amarok and they don't show up.

the strange thing is that I can actually transfer the albums to the ipod from amarok. I can then do a grep search in the actual /media/ipod/iPod_Control/Music directory and i can find the actual mp3 files (i grep the names of the albums from the text-based header in the mp3 file). It's just that the list of songs in the ipod's library doesn't include the two albums. any clues?


I have tried: 
resetting the ipod using the hold menu-center button
manually erasing the mp3 files from the ipod and then trying to reinstall them
getting really pissed


some specifics:
my ipod was formerly my wife's but i reappropriated it since she doesn't know about linux and i think every semiconducting silicon chip wants to be running linux. she uses windoz and i whenever i use amarok on that ipod, i can't use windoz based itunes afterwards because it crashes the itunes. i'm not sure what amarok does to the ipod, but i just know that twice in a row i have used amarok and the ipod stops working in windoz itunes (not a big deal usually, but now it is). 

any hints on how i can completely erase the ipod without using windoz, or ideally, help with the problem in the title? thanks to any and all posts.

---

### Post by spin2cool on 2007-05-09
If I recall correctly, iPods don't just scan their directories for new files, they also rely on a database file to access the songs.  Apps like GTKpod and amaroK rebuild this database after adding files, and it sounds like your setup with amaroK isn't doing that step properly. (It may be trying to, but corrupting the library, which is why iTunes won't recognize it later on).  

You might dig around on the amaroK forums, try newer versions, or try an alternate method of doing the transfer.

If you want to completely erase the iPod, it's simple to do - just reformat the drive (use FAT32)

---

### Post by rajan on 2007-05-09
great thanks! i came across the DB files a little while ago, but i couldn't open them from the nautilus GUI. i tried from the command line and they were binary files, so i'll have to figure out which app created them. any suggestions?

as for the reformatting, i guess i should have thought of that. good to have the forums to help out. thanks a lot spin2cool.

---

### Post by spin2cool on 2007-05-09
IIRC, GTKpod does what you're looking for - adds the songs, then rebuilds the DB.  Give it a shot.

---

