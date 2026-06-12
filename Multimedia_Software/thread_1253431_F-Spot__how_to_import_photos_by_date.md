---
title: "F-Spot : how to import photos by date"
date: 2009-08-30
forum: Multimedia Software
---

### Post by bd@cb8be8510 on 2009-08-30
I just upgraded from 8.10 to 9.04. I'm using F-Spot to import my photo's from my camera. In Ubunti 8.10, F-Spot was storing my photos nicely in directories on a daily basis, eg. Photos/2009/08/01, Photos/2009/08/02,
Photos/2009/08/03, ... In this way when I was importing photos at the end of the week they were automatically classified. Now F-Spot is saving all the images into the directory Photos.:(:( I have to classify them myself

How I can specify that F-Spot must save them into directories per day? Has F-Spot been changed or do I something wrong? :confused:

---

### Post by jmail524 on 2009-08-31
Hi bd@cb8be8510,s the same problem after upgrading to 9.04.

I had noticed the same problem after upgrading to 9.04.  I don't know whether Ubuntu or F-Spot is to blame because this problem didn't exist in Ubuntu 8.04. There seemed to be an easy fix, it just required me to change how I imported my photos from my camera.

If I try to import photos by plugging in my camera and using to import function that automatically pops-up, all of the photos just go into one directory.  What I do now is close the automatic pop-up import dialogue window and manually start-up F-Spot.  Then I select the import function from the toolbar or Photo menu.  Next I select my camera's memory card from the import source selector.  (In my case it is listed as 1GB Removable Volume.)  F-Spot then scans the card for pictures. (This took forever for about 100 pictures.) The pictures then showed up in the preview(?) section of the import window.  I then pressed the Import button to copy the pictures to my computer.  This put the pictures in the appropriate folders separated by date (ie, Pictures/2009/08/31/*.jpg).

I hope this helps.  (This works for me, but your results may vary.) There may be an easier way, but this isn't that much more involved, so I'm happy with this procedure for now.

Good luck.
Brian

---

### Post by bd@cb8be8510 on 2009-09-01
Dear Brian,

I tried your work-around, but it didn't help right out of the box. But your advice triggered me to try some other things. I observed that F-Spot was not storing the photos in other directories (eg. the desktop or my home-folder). Then I noticed that F-spot was automatically creating a directory nemed "foto's". In my native language "foto's" means "photos". When I now import my pictures into the destination-folder "foto's", all
pictures are saved into automatically generated folders (timestamped with the proper day). Anyhow, your solution has triggered me to find a work-around. Thank's a lot. Have a nice day!:D):P

---

### Post by Brian96 on 2009-11-22
Is there any way to get F-Spot to automatically import photos into a single folder named for the date range? Or any other customization for that matter?

I find the default format of creating a folder per day quite cumbersome, and it the tons of levels makes CoolIris not so much fun.

---

### Post by Brian96 on 2009-11-22
> **Brian96 said:**
> Is there any way to get F-Spot to automatically import photos into a single folder named for the date range? Or any other customization for that matter?

I find the default format of creating a folder per day quite cumbersome, and it the tons of levels makes CoolIris not so much fun.

Similarly, I'd like it to name the photos with the date in the title.

---

### Post by musarraf172 on 2009-11-25
Whenever I connect my canon camear and try to mount it  the " Disk Mounter utility " crashes .

Anybody know how to fix it ??
Help will be greatly appreciated::(

---

### Post by Nick Brohman on 2009-12-05
> **musarraf172 said:**
> Whenever I connect my canon camear and try to mount it  the " Disk Mounter utility " crashes .

Anybody know how to fix it ??
Help will be greatly appreciated::(

G'day, 

I've found that by just connecting my Canon without F-Spot running, I can import the photos....if I have F-Spot running, I have to use the import button.

Hope this helps

Cheers...Nicko

---

### Post by FirstByté on 2009-12-26
Thanks for this post.

Well, I ran into same problem with Ubuntu 9.04 earlier too; which made me hate uploading pix into my system. It was just too hard to lump all images in same folder.

I loved the "Folder Importing" feature so much that I sort of this thread. I just tried the F-Spot's importing again now and seems to work.

**With Ubuntu 9.10, things seems to have been fixed.**

*I launch the F-Spot from the Nautilus explorer ["Open F-Spot"],
*Edit/Perference [User Guide/Organize-F-Spot]("http://f-spot.org/User_Guide/Organize")
*Import to desired folder.

I checked... and happily all the pix seems to appear there in matter of seconds.:guitar:

---

