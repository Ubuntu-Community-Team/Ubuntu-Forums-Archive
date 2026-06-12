---
title: "Sansa Fuze (not) detected in ubuntu 10.04"
date: 2010-05-23
forum: Multimedia Software
---

### Post by aCsbD6N5xj on 2010-05-23
Hi.

I have an 8gb Sansa Fuze, filled with mp3s only. Although it appears in rhythmbox, the songs don't. Plus I can't even access it as a hard drive :confused:

I've been using it with Winamp when I was still using XP, if that matters.

Any tips?

Thx

EDIT: seems like it was in MTP mode by default when 'Auto Detect' was set. I switched to MSC and I can now access it but the music still does not appear, whether in Rhythmbox or in the folder 'MUSIC'.

---

### Post by quinnten83 on 2010-05-23
I have been having issues with Lucid not wanting to automount my NTFS files.
you can switch the Sansa over from MTP to MSC, but files added in MSC will not see files added in MTP mode and viceversa.
I think the Sansa has an option to be used as a USB device, you can try that and then go into system>admnistration>disk utility. You can  mount the disk from there.
It's not pretty, but it works for me.

---

### Post by aCsbD6N5xj on 2010-05-23
> **quinnten83 said:**
> I have been having issues with Lucid not wanting to automount my NTFS files.
you can switch the Sansa over from MTP to MSC, but files added in MSC will not see files added in MTP mode and viceversa.
I think the Sansa has an option to be used as a USB device, you can try that and then go into system>admnistration>disk utility. You can  mount the disk from there.
It's not pretty, but it works for me.

Whether it's in MSC or MTP mode, I wasn't able to mount it like you described.

But after trying 'Auto Detect' and 'MSC', I chose 'MTP' explicitly and then it was auto-mounted and my music appeared when I got into the 'Music' folder. At that point my **** PC went unbelievably slow and unusable!!! I couldn't even xkill the window!!! 

My music still does not appear in Rhythmbox :(

---

### Post by sgosnell on 2010-05-23
If you installed the music in MTP mode, it will only be seen in MTP mode.  If you want to use the Fuze on Ubuntu, the best option (maybe the only option) is to delete everything, then put it in MSC and transfer the music back to the Fuze.

---

### Post by aCsbD6N5xj on 2010-05-23
> **sgosnell said:**
> If you installed the music in MTP mode, it will only be seen in MTP mode.  If you want to use the Fuze on Ubuntu, the best option (maybe the only option) is to delete everything, then put it in MSC and transfer the music back to the Fuze.

I did just like you said and it woked thx!

Now I'd like an easier way to sync my music than just drag and drop in Ryhthmbox as it's tedious in the long run.

---

### Post by sgosnell on 2010-05-23
Both Rhythmbox and Banshee should sync to your PC music folders.  I'm not really up on that, because I prefer to just copy the music via my microSD card, or the occasional drag-and-drop, since my internal memory is mostly full, and it's much faster and easier to use a card reader.

Try [this thread ](http://ubuntuforums.org/showthread.php?t=1370738) for help in setting up your Fuze in Ubuntu.

---

### Post by aCsbD6N5xj on 2010-05-23
> **sgosnell said:**
> Both Rhythmbox and Banshee should sync to your PC music folders.  I'm not really up on that, because I prefer to just copy the music via my microSD card, or the occasional drag-and-drop, since my internal memory is mostly full, and it's much faster and easier to use a card reader.

oops i didn't phrase that well. I was looking for a better way to put music on my mp3 player through rhythmbox. 

I can't really select everything at once and just drag and drop as I may click something else by accident and restart the whole process. It happened to me a lot of time.

And selecting a few, drag and drop them, repeat is a little bit tedious. I'm having a little bit of RSI right now :S.

---

### Post by sgosnell on 2010-05-23
You can make Rhythmbox or Banshee automatically sync all your music between your mp3 player and your PC whenever you connect the mp3 player.  You don't have to drag and drop at all.  Personally, I don't want all my music on my mp3 player, so I drag and drop.  Holding down the Ctrl key when you click on a file or folder lets you select multiple non-contiguous files or folders, then you can drag all the selected files at once.  That's the way I usually do it.

---

### Post by aCsbD6N5xj on 2010-05-23
> **sgosnell said:**
> You can make Rhythmbox or Banshee automatically sync all your music between your mp3 player and your PC whenever you connect the mp3 player.  You don't have to drag and drop at all.  Personally, I don't want all my music on my mp3 player, so I drag and drop.  Holding down the Ctrl key when you click on a file or folder lets you select multiple non-contiguous files or folders, then you can drag all the selected files at once.  That's the way I usually do it.

Yeah me neither. There wouldn't be enough space on the player anyways.

I didn't see the link to the other thread at first. I'll have a look at it. Thx

---

### Post by sgosnell on 2010-05-23
I have almost enough space, and I will have if I ever decide to buy a 16GB microSD card.  The 8GB card I have is almost enough, but not quite, to load the music I really care about hearing regularly.

---

