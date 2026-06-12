---
title: "Symbolic Links Break"
date: 2008-03-10
forum: Multimedia &amp; Video
---

### Post by mikeserv on 2008-03-10
I have a portable hard drive with a lot of video files in a downloads folder, which is the destination for my rss fed bit torrent dls. This folder is monitored by a script which grabs metadata for each new download every thirty minutes and creates a link to each new download. The link is created like this: ```
ln -s -f /original/file/name/path /new/link/path
```

The script also inserts all of the metadata about new files it finds into the MythVideo MySQL database. It then monitors the database for items deleted from the database and then deletes the corresponding files in the Downloads folder.

The way all of this works is that all I have to do is run MythVideo > VideoManager > Scan and all of the files are managed from within the program. And, if I want to do delete a file, all I have to do is remove it from the Manager database from within the on-screen setup and all of the related data (including the original large file) is removed.

Here's my problem: For some reason, occasionally the links break. And when they do, MythVideo manager sees them as disappeared, and deletes the links. When that happens, my originals are also removed by the script.

So what's going on? Is it because the links are cross drives? Or, here's something: the portable drive is Fat32 and the links are stored in my /home directory for user /tv on an Ext3 partition. Any ideas?

-Mike

---

