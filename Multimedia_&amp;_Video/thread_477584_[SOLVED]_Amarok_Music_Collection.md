---
title: "[SOLVED] Amarok Music Collection"
date: 2007-06-18
forum: Multimedia &amp; Video
---

### Post by airbornemist6 on 2007-06-18
I have a question about Amarok, more specifically the collection. I have all my music stored on my windows partition, which, isn't showing up in Amarok. Is that normal, if it is, is there any way around it? Because I REALLY do not have enough space in my linux partition to store all my music.

---

### Post by vanadium on 2007-06-18
I am not using Amarok (have test-driven it briefly though) and my guess is that you will need to tell Amarok where your collection resides. Then it'll build the library. Indeed the file system where your music is does not matter, as long as it is mounted somewhere in your file system (and you have access permissions, of course)

---

### Post by joeally on 2007-06-18
yes on your first run of amarok you should have told it where your music collection resides.
But as you have not done that click on the hammer and screw driver icon near the 'group by menu' and select your folder.
if its on the seperate disk you need to look in /media and it will be hda1 or sda1 or similar.

---

### Post by Silent Warrior on 2007-06-18
You can always add stuff to the library, or the playlist, whatever, later. Just keep in mind you'll need to install some ntfs-tools or somesuch to get at an NTFS-partition.

---

### Post by airbornemist6 on 2007-06-19
actually, everything else will read off my nfs partition. exaile is doing it. but amarok ONLY picks up my root partition.

---

### Post by airbornemist6 on 2007-06-19
Eh sorry, but it's been 16 hours and no answer, so I'm bumping.

---

### Post by AzureIce on 2007-06-19
I had the same issue - dual boot with Windows and my music collection was on my NTFS partition.  Regardless of available space, it is impractical to copy the media library over.  But when I fired up Amarok and went to browse for my library, I found my C: drive under /media/disk/.  Try that.

---

### Post by airbornemist6 on 2007-06-20
> **AzureIce said:**
> I had the same issue - dual boot with Windows and my music collection was on my NTFS partition.  Regardless of available space, it is impractical to copy the media library over.  But when I fired up Amarok and went to browse for my library, I found my C: drive under /media/disk/.  Try that.

Ah! I found it! Thanks very much! :D Yeah, I'm still unfarmiliar with the Linux filing system. so I was seriously lost, But I'm good now.

---

### Post by Arasa on 2007-06-20
I have a similar problem, I also could not find it at first, then it turned up in the media/disk. I added the location in the options and recurring folders, but it still refused to add them to the collection. In the end I had to do a very ugly drag and drop.
Result is now I can play and view everything in my music library but it does not update the collection.. so when I add new songs, I have to manually add them to the amarok collection = lame.
All this goes back to is the lack of a linux based player that can truely compare to the awesome winamp..
Even the visualizations are rubbish compared to milkdrop for winamp - but thats for another thread..

Back on track, any tips for the collection issues out there?

---

### Post by airbornemist6 on 2007-06-20
i had a problem simliar to that, did it just say it was adding them and to check the progress bar and oyu look around and think "wtf, what progress bar?" if that's the case close amarok and restarted it and it will add the directory for your collection.

---

