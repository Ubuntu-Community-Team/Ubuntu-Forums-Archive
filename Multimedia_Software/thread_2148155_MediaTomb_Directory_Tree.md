---
title: "MediaTomb Directory Tree"
date: 2013-05-24
forum: Multimedia Software
---

### Post by tvick47 on 2013-05-24
Hey all, I seem to have a problem with my MediaTomb setup on 13.04.

I am able to get it up and running, and everything is working on the media itself, but the major problem I'm having is with the listing of directories on the UPnP clients from MediaTomb.

I've tried all the config options (builtin, js, disabled), including a handful of import scripts.

The closest I can get to the root of the tree is :

-MediaTomb
--PC Directory (which I can turn off in config)
--Video
---All Video
----All Video Files are here.mp4...
---Directories
----Movies
-----All Movies Here.mp4...
----TV Shows
-----Series 1
------Episodes.mp4...
-----Series 2

And so on.

I can't seem to figure out how to make everything under "Directories" show up as the first listing under "Video".

I don't want the categories "All Videos" or "Directories" to show up, just what is inside "Directories".


I've tried adding the folders to the database recursively, manually, symlinking to the root of my drive, nearly everything I can think of!

I don't need a script to sort the files, as I organize them myself, but I really wish that I wouldn't have to navigate through so many directories as a result!

Please help!

---

### Post by keratos2 on 2014-04-24
Assuming you need a file structure that mimics your shared media file strcuture, then you need to change the config.xml to make builtin=js and change the import.js script so that it "roots" your top shared folder and then replicates the shared folder structure. there are scripts on mediatomb.cc that do this. just go there to pick your one.

You will also need to note that the client UPnP (i.e. Windows Media Player) caches folders so if they change you need to remove the UUID of the server from the windows registry - this is dangerous as if done incorrectly, will brick your windows installation.

If you do not know what I am talking about then I suggest you leave things as they are. If you understand then google is your next friend

---

