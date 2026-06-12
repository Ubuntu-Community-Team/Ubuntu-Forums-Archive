---
title: "[SOLVED] Not picking up connection to iPod"
date: 2008-12-28
forum: Multimedia Software
---

### Post by GNUway Tech on 2008-12-28
I bought a new iPod Classic on Friday, and thought I would give it a try. I plugged it in for the 1st time and my computer picked it up as a connected device.

I tried dragging and dropping files onto it to see if they would play the tracks. After finding out it wouldn't I deleted all the tracks off of it. After doing that, I plugged it in to the computer again and, for some reason now, my computer will not even pick it up as being connected.:confused:

I tried plugging it into my brother's Windows computer and it picked it up fine so I thought something was corrupted on my Operating System. I spent 3 hours reformatting my computer and setting it back up only to find out that nothing was different. It still won't pick it up.:confused:

I know that the files have to be synced, it's not that. I have a couple of programs now that I would like to try with it. The issue is that the iPod says it is connected, but my computer does not, so I can't even use the programs to sync it. I'm about to give up and take the iPod back to the store. Is there anything I can do other than that??? What could have caused the computer to pick it up the 1st couple of times it was plugged in, but never again???????

---

### Post by GNUway Tech on 2008-12-28
New developments:

The computer still is not picking it up after I plug it in. It still is not showing up in Dolphin, or in /Media.

It is, however, showing up in the side of the file manager of gtkpod. That is, if I'm looking adding files to the playlist in gtkpod, it'll show up in the side of the file select screen as a USB Drive.

I still can't use that as a mount point, and it still won't sync the tracks to it. But, at least I can see it. So the question would be, how do I mount it?????? Can I get to mount if it won't show up in Dolphin?????

---

### Post by GNUway Tech on 2008-12-28
Has anybody had this happen to them before???? Does anybody have any advice to offer me?????

---

### Post by Mason Whitaker on 2008-12-28
Try to look at it in a program called Songbird, it has a Linux verison, but it isn't on the Add/Remove Applications List. 

So far, its managed to work fine with my iTouch, and I can even sync songs with it.

Just a suggestion...

---

### Post by GNUway Tech on 2008-12-28
Songbird didn't help. It's still showing up in the side of the file select menu as USB Drive, but it's still not showing under /media. I can't get any program to use it unless I can mount it.

This is frustrating me too much. I've already tried formatting my hard drive and reinstalling Kubuntu twice now. I'm seriously thinking of just taking this thing back to the store tomorrow and finding one that will work for me. I would rather have the iPod but it just doesn't look like it's going to work. I realize a lot of other people are doing just fine with theirs, but Kubuntu doesn't want to do the job for me.

---

### Post by SuperSonic4 on 2008-12-28
Do you have any luck in amarok?

Also, have you tried mounting it manually? ```
sudo mkdir /media/iPod
sudo mount /dev/[COLOR="Red"]sdd[/COLOR] /media/iPod
```

where sdd is where your iPod is

---

### Post by GNUway Tech on 2008-12-28
Trying to mount it manually that way, I get a message that says: "mount: you must specify the filesystem type"


No, I haven't had any luck in Amarok.

---

### Post by GNUway Tech on 2008-12-29
How do I specify the filesystem type to mount it manually?????

---

### Post by GNUway Tech on 2008-12-29
I was able to solve the problem myself. The iPod was corrupted.

---

