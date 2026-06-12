---
title: "realtime updating of music file locations"
date: 2008-05-28
forum: Multimedia Software
---

### Post by bodaciousllama on 2008-05-28
Hi, I'm a new Ubuntu user and loving it except for one small thing regarding how Banshee organizes my music.

In iTunes, when I edited the album or artist of a song, it would move the mp3 into a folder based on the new name. Banshee (or Amarok or Rhythmbox) doesn't make this update.

For example, say I download a song by the Arctic Monkeys which has an album name of [www.********.com](www.********.com). When imported into Banshee, it copies the file to Music/Arctic Monkeys/www.********.com/<track name>

I edit the metadata in Banshee to change the album title to the correct title, but it doesn't update the location to Music/Arctic Monkeys/<newly changed album title>/<track title>

Are there any music players that do this automatically, or do I just have to live with manually changing folder/file names?

---

### Post by balaknair on 2008-05-29
In Amarok(not too sure about Banshee and Rhythmbox), you can get this done by right clicking on the album or individual track and selecting "manage files--> organize file", and the files are copied or moved to the proper destination folder. The only proviso to move the file is that the the source and destination should be in a drive/folder where you have Read/Write permissions. If your music is in a shared folder or a network drive make sure you(the user name you run amarok under) have read/write permission for the drive or partition.

---

