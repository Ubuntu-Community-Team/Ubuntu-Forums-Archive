---
title: "Can't browse folders in gnump3d"
date: 2008-04-14
forum: Multimedia &amp; Video
---

### Post by Vcount on 2008-04-14
Hi, I wanted to start serving my media, so I installed gnump3d.  

I have it working, and I can access it both through localhost and online.  However, the only way I can play music is by browsing through tags.  I can't browse my folders and subfolders at all.  It sees the subfolders in my Music folder, but then whenever I click on, for example, my "Audiobooks" folder, I get the following error:

```
The requested file /home/username/Music/Audiobooks/ couldn't be found. Please try returning to the index
```

Also, if I search for "audiobooks" it will come up with everything in my audiobooks directory, as though I'm browsing it.  But then when I click on any of the files to play it, I get a "couldn't be found" error about the file, much like the error above.  

If I go through the tags, though, I can play my music.  

It sounds like a permissions thing, so I've done a number of permissions modifications trying to get it to work.  The latest I've done is:

```

find . -type d -exec chmod 755 {} \;
find . -type f -exec chmod 644 {} \;

```

I've done that with sudo, I've tried it with 777 permissions in both slots, I've tried og+X for the directories, I've tried -R +rw for the files...I don't know what else I could try or do to change the permissions.  

One thing to note about the way I CAN play music.  I can browse through tags, and then click on an artist.  Then it will pull up a page that is blank, with several blank lines where it looks like the names of songs should be.  I can then click on one of those blank lines, and it will start playing the song.  However, I don't know what song it will be before playing it, because the line is blank.  

So when I browse in a way when I can see the song names, it won't play them and gives me a "couldn't find" error, but if I browse through tags in a way that I can't see the song names, it plays them.  

Is there some way I can fix this so I can browse through my folders and subfolders, and see the song names of the songs before I play them?  

Any help is appreciated, thanks.

---

