---
title: "MP3 player order of play"
date: 2009-10-08
forum: Multimedia Software
---

### Post by Robbyx on 2009-10-08
Is there a way of making an mp3 player play back files in alpha order?

*My mp3 player does not play the files in alpha order. I think it is playing in order of original creation, but it is not clear what is happening. For one opera the display shows the mp3 in alpha order but they are not played in the same order. It seems random.  The other opera is in reverse order with the highest number first. I tried putting the files into Rythmbox and then into a playlist and then copying the files into the mp3 player but it is making no difference.*

---

### Post by Robbyx on 2009-10-09
Anyone know the answer to getting the mp3 player to play the files in the correct sequence?

Robin

---

### Post by StuartN on 2009-10-09
> **Robbyx said:**
> Anyone know the answer to getting the mp3 player to play the files in the correct sequence?

Robin

Which MP3 player program? Rhythmbox plays in whichever order is currently selected (e.g. track number, title, duration) unless the shuffle button is toggled on.

---

### Post by Robbyx on 2009-10-09
Sorry for not making it clear that I am using an external mp3 player. I tried rhythmbox in an attempt to presort the mp3 files before copying them to the mp3 player. It did not work successfully and so the mp3 player is playing an opera or reading a book in random order.

Robin

---

### Post by StuartN on 2009-10-09
> **Robbyx said:**
>  and so the mp3 player is playing an opera or reading a book in random order.

Well perhaps your mp3 player has a shuffle setting, most do.

---

### Post by Robbyx on 2009-10-09
I have not noticed that setting. I suspect it is playing the files in dos filed order. The file managers I have automatically sort. Have you any ideas how I can see the dos order of files in a directory?

Robin

---

### Post by StuartN on 2009-10-09
> **Robbyx said:**
> I have not noticed that setting.

You can probably find the manual for your hardware, and possibly even a forum, with a quick search. It is obviously not an Ubuntu problem.

---

### Post by Robbyx on 2009-10-09
I had hoped the Ubuntu forum would help because I am copying from Ubuntu to some form of windows device, but I assume the problem is the true file order in Ubuntu.

---

### Post by StuartN on 2009-10-10
> **Robbyx said:**
> I assume the problem is the true file order in Ubuntu.

The order in Ubuntu makes no difference to an external player, although if you really want to you can see these with **ls -lt** in a terminal for modification time, **ls -lc** for creation time or **ls -li** for the inodes. The order on the (presumably FAT32) file system on your player is also unlikely to affect MP3 play order.

More helpfully, if you plug the player in and **lsusb** then it will identify the manufacturer, device and numeric id which you can report here or search with. While it is plugged in you can check what filing system your computer and the player use with **mount** and **sudo fdisk -l**.

You might be surprised how helpful people can be if you supply relevant information (like the name of the player and / or software) rather than blaming the operating system.

---

### Post by Robbyx on 2009-10-10
> **StuartN said:**
> The order in Ubuntu makes no difference to an external player, although if you really want to you can see these with **ls -lt** in a terminal for modification time, **ls -lc** for creation time or **ls -li** for the inodes. The order on the (presumably FAT32) file system on your player is also unlikely to affect MP3 play order.

More helpfully, if you plug the player in and **lsusb** then it will identify the manufacturer, device and numeric id which you can report here or search with. While it is plugged in you can check what filing system your computer and the player use with **mount** and **sudo fdisk -l**.

You might be surprised how helpful people can be if you supply relevant information (like the name of the player and / or software) rather than blaming the operating system.

My intention is not to blame Ubuntu. I actually do not understand why I am having the problem. I am trying to understand how to play the mp3's in alpha order. If I could find out why the order was wrong then I could correct it within Ubuntu. I read that one way of handling this is to put the files into a playlist but as I said earlier it is not altering the order of the play in the player. 

The device is the Navigo sat nav windows CE device. It also offers mp3 playing.  I  have posted a similar question in a site that deals with the navigo but no one is responding.

---

### Post by Robbyx on 2009-10-10
The sequence as shown and played in the MP3 player is not the same as shown by any of the LS commands you suggested. At some point in the listing in the mp3 player the alpa numbers are shown as reducing eg 40c12, 40c11 before that they were increasing.

At the moment I  can not spot what order the device is using on the screen.

On the other recording I have the numbers declining from the start. They diminish in sequence.

---

### Post by Robbyx on 2009-10-10
Here is an article that indicates the problem I am experiencing. Do you know a linux solution?

>    	

Date: December 30, 2004

Problem: Many MP3 players that are based on USB flash drives don't allow you to sort the MP3 files in the order you want to listen to them. Instead they play the MP3 files in the order they find them; usually the order you copied them to the flash drive. How do we re-order the files?

Hardware: SanDisk Cruzer Micro MP3 Companion.

Background: In the old DOS days Norton Utilities provided a tool called DS (Directory Sort) that would re-arrange the order of files in the FAT (File Allocation Table) directory structure. This was useful because many programs would only display or process files in the order they found them; they wouldn't allow you to sort the files. With the advent of Windows the need for DS was reduced as Windows usually sorts filenames before displaying them (i.e. in Explorer or the Windows file selector dialog box).

Many modern MP3 players are based on USB flash drives (i.e. Creative's MuVo range of MP3 players). These devices don't allow you to sort the MP3 files in the order you want to listen to them. Instead they play the MP3 files in the order they find them; usually the order you copied them to the flash drive. Unfortunately if you select a bunch of files in Windows' Explorer and copy them to your MP3 player, they don't always copy in alphabetical order (even if you have told Explorer to display the files alphabetically). And of course you may want to add new MP3 files at a latter date, which will result in them being added to the end of the directory.

Norton's old DS utilities was designed for FAT16 drives and so won't work with newer drives that are FAT32. The addition of long file names (VFAT) further complicates matters. Duncan Murdoch wrote a utility called LFNSORT which went some way to addressing the problems with Norton's DS not working with newer file systems, but unfortunately LFNSORT doesn't work with newer versions of Windows (i.e. Windows 2000, XP, etc).

Early versions of the Windows Defrag tool would also re-sort the directory, but this ability seems to have been removed from newer versions.

Resolution Steps: There are a few programs around that allow you to sort files by filename:

    * FAT Sorter (includes a nice write-up about how it works) (requires Windows XP and .NET Framework 3.5 (will auto-download .NET Framework if you don't already have it installed))
    * ReOrganize! (requires Windows Media Player 7 or later)
    * DriveSort (no particular requirements)

If you know of any other programs then please contact me.

Update (22 April 2008): My latest MP3 player, an iAudio U2, has the ability to specify the sort order (by file name or by file date). This is a great feature that more MP3 players should implement.

---

### Post by Robbyx on 2009-10-10
I have found a solution here:

[http://ubuntuforums.org/showthread.php?t=269101&highlight=fatsort](http://ubuntuforums.org/showthread.php?t=269101&highlight=fatsort)

As far  as I can tell I have to sort the whole drive, not just the music directory. I have just sorted the drive with fatsort and the mp3s play in the correct order.

---

