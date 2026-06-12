---
title: "Playing a dvd from harddisk"
date: 2008-02-08
forum: Multimedia &amp; Video
---

### Post by protenniser on 2008-02-08
Hi all,

I have a dvd folder(s) in my harddisk. As you know, there is 2 folders AudioTS and VideoTS. And VideoTS has many files in it.
If I burn all these files to a dvd using k3b(let's say) than all video programs recognize this as a dvd movie and I can watch it with all extras, controls without any problem.
However I want to do the same without burning all these files to a dvd, directly from harddisk. And I am stuck. Is there a way to do it? (Preferabbly in mplayer or totem).

Thanks for all help, regards...

---

### Post by ron999 on 2008-02-08
Hi
I don't know whether mplayer or totem will do this.
But VLC media player will definitely do the job.
Use File > Open Directory...
Then load the video_ts folder.
:cool::cool:

---

### Post by protenniser on 2008-02-08
Hi, it didn't work :( VLC closes itself after I do what you said.
Here is the log I get running the same thing from terminal:
```

VLC media player 0.8.6c Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/kmuslu/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8
libdvdread: Invalid IFO for title 64 (VTS_64_0.IFO).
libdvdnav: ifoOpenVTSI failed - CRASHING!!!
vlc: vm.c:198: ifoOpenNewVTSI: Assertion `0' failed.
Aborted (core dumped)

```
Any ideas how to fix?
Thanks for help...

---

### Post by ron999 on 2008-02-08
Hi
I dunno, it works OK for me.
Maybe try copying a different DVD and test it again.

This is my output when I run from terminal.
It's similar to yours - but it doesn't crash, it runs OK.

```
ron@ron-desktop:~$ vlc /home/ron/Desktop/video_ts
VLC media player 0.8.6 Janus
libdvdnav: Using dvdnav version 0.1.10 from http://dvd.sf.net
libdvdread: Using libdvdcss version 1.2.9 for DVD access
libdvdread: Couldn't find device name.
libdvdnav: Can't read name block. Probably not a DVD-ROM device.
libdvdnav: Unable to find map file '/home/ron/.dvdnav/.map'
libdvdnav: DVD disk reports itself with Region mask 0x00000000. Regions: 1 2 3 4 5 6 7 8

```

---

### Post by weeds on 2008-02-08
Try right-clicking on the DVD desktop icon and select copy disc. This should create an ISO image. Right click on the ISO image and select open with VLC. I have had good luck so far with this process.

---

### Post by protenniser on 2008-02-08
Hi ron,

Thanks for response, after you post your output and suggested, I tried another video file and that worked. It is obvious that there is some problem with my ifo file 64. I still wonder, if there is way to repair or skip this error and force vlc to open this directory as a DVD?

Thanks for all help...

---

### Post by mc4man on 2008-02-08
You could easily fix this with a couple of win apps in wine (vobblanker, pcgedit, fixvts), but otherwise k9copy might work. In settings>dvd you'd set the size above your video_ts source so it doesn't transcode and see if it can process without error

---

### Post by protenniser on 2008-02-08
Hi, mc4man, 

Thanks for you response however all 3 of the programs failed to repair the ifo files that are corrupted. 
Vobblanker terminates in wine when it came to corrupted vob,
pcgedit couldn't load the dvd because both ifo and bup files are wrong.
fixvts opens and repairs the dvd but at the end it is broken again. (Process doesn't affect at all.)
So any other solutions, ideas? Thanks for all help...

---

### Post by mc4man on 2008-02-08
If you know your way around pcgedit and vobblanker I'd try this. Delete or ( re)move everything associated with that vts (.vob(s), .ifo, .bup). Then open in pcgedit, work your way thru any messages/ warnings (generally answer yes) and save - it should mention about # of vts's. Then open in vobblanker and do a mock strip (ck. use input folder). then test, or delete/move vobblanker backup and run thru another mock strip (should run thru relatively clean)
Can't account for what fixvts did - did/can you restore backup?
what was used for orig. rip?
Do you want to post title or pm

---

### Post by mc4man on 2008-02-08
Based previous on fact that usually these type vts are garbage - you might as well get rid of it/them. On some rare cases they contain useful content and just the .ifo is corrupted. You could compare the .ifo and .bup - if different sizes it won't hurt to copy the.bup to desktop, rename to .ifo and replace the existing .ifo, might work, might not.

---

### Post by protenniser on 2008-02-08
Hi,

Nor your suggestions on previous post worked, neither this post.
All vob and bup files are exactly the same kilobytes. I think they are both corrupted. I need 'em since dvd supports multi angle, without opening it as a dvd messes the files a lot.
Title is Grad Concert, which is a dvd of a concert that I participated in highschool. However as I say, somehow the ifo and bup files are damaged :(

Thanks for all help though.

---

### Post by mc4man on 2008-02-08
Sorry to hear, a non commercial disk like that would be problematic. If nothing else arises consider posting over at [http://forum.doom9.org/](http://forum.doom9.org/)  Alot of very talented people - takes 5 days from registering till you can post

---

### Post by protenniser on 2008-02-08
Thanks mate, you really tried everything you can do :)
It is upto me from now on ;)

Regards...

---

