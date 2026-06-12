---
title: "MP3 &quot;Same Name&quot; Problem."
date: 2010-04-01
forum: Multimedia Software
---

### Post by Jotaro on 2010-04-01
Normally in my music collection, I have some songs that are the same song, just in a different album. When transferring files onto my MP3 player, if it detects the same name for the song, even though they are on different albums, it says that I have to either replace the file, retry, or cancel. Can someone help me please?

---

### Post by Grenage on 2010-04-01
Don't most MP3 players use folders to manage albums, et cetera?  If not, I don't see that you have a choice but to rename.

---

### Post by Jotaro on 2010-04-01
I was able to place them both on my MP3 Player before separately, and it didn't ask me this and just did it. They are two differently named albums, so if they are added by album names only they would have worked but they didn't.

---

### Post by Jotaro on 2010-04-01
Bump.

---

### Post by Jotaro on 2010-04-01
Bump. I took a screenshot of the problem:
[IMG]http://i680.photobucket.com/albums/vv163/DarkSpiritBakura/Screenshot-7.png[/IMG]
Does anybody know how to fix this without having to rename the song? I was able to upload it before without having to renaming the song...

---

### Post by Grenage on 2010-04-01
How were you transferring them before?  Application, or direct mass storage?

Was _before_ a different OS?

---

### Post by Jotaro on 2010-04-01
I would drag and drop the file into the music folder in the MP3 player.
Umm, I would drop the file into the music file in the MP3 player, but sometimes it wouldn't work. Then, I changed all the folders permissions to where access was on none. It transfer worked then. But now when I try that, it wouldn't work, so I changed to placing the files on Rhythmbox, and drag and drop the files into the player icon on my desktop and it would work, except for the "same name" error. No, it was in the same Ubuntu system I have now.

---

### Post by Grenage on 2010-04-02
A have nothing to suggest, but posting the model of your MP3 player might enable others to offer advice.

---

### Post by Chronon on 2010-04-02
> **Jotaro said:**
> Bump. I took a screenshot of the problem:
[IMG]http://i680.photobucket.com/albums/vv163/DarkSpiritBakura/Screenshot-7.png[/IMG]
Does anybody know how to fix this without having to rename the song? I was able to upload it before without having to renaming the song...

You seem to be using MTP to transfer files to this device.  Try changing the player's USB mode to MSC.  You should be able to drag and drop as usual.  Your player should permit read and write access.

It might be worth checking the file system if you were getting unreliable writes to the disk before.

---

