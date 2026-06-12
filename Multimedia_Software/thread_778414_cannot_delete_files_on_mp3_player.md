---
title: "cannot delete files on mp3 player"
date: 2008-05-02
forum: Multimedia Software
---

### Post by pympnplaya on 2008-05-02
i have an archos gmini xs200 mp3 player. the screen recently went out so i am now using it as an external hardrive for my mp3s. i also used it to transfer some torrents from my laptop to my computer. i deleted the files but now they are stuck in a folder named ".Trash-1000" on my mp3 player. i want to get rid of the file because it is taking up 9.2 gigs of the 20 gig mp3 player. but when i try and delete them on xubuntu either through terminal or thunar, i get a read-only access error and cannot delete it. in terminal i get this output:

pympnplaya@pympnplaya-desktop:/media/JUKEBOX$ rm -r .Trash-1000
rm: cannot remove `.Trash-1000/files/Heroes.S02E09.HDTV.XviD-LOL.avi': Read-only file system
rm: cannot remove `.Trash-1000/files/heros': Read-only file system
rm: cannot remove `.Trash-1000/files/saigon': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg497': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg498': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg499': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg500': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg501': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg503': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg504': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg505': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg506': Read-only file system
rm: cannot remove `.Trash-1000/files/NPROTECT': Read-only file system
rm: cannot remove `.Trash-1000/files/desktop.ini': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg507.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg508.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg509.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg510.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg511.m3u': Read-only file system
rm: cannot remove `.Trash-1000/files/INFO2': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg502': Read-only file system
rm: cannot remove `.Trash-1000/files/Dg502$1': Read-only file system

i also tried sudo rm but that didnt work either. any suggestions? thanx

---

### Post by pympnplaya on 2008-05-02
nevermind i got it to delete

---

### Post by mpstump on 2009-02-21
How?????

---

### Post by Thrasherrich on 2009-11-05
This happened to me, I deleted mine on a Windows System but when I delete files from my MP3 or Memory stick I have to empty my recycle bin before disconnecting them as it stays on as  Trash file... Odd I know.

---

### Post by Crimson_Tider on 2009-11-27
I'm having the same problem with my Zen Stone on Karmic. I'm going to report this as bug. The trash bin on the player should empty itself when you unmount or eject or "safely remove" the player, right?

---

### Post by Iraqiman on 2010-03-23
I've been having the same problem with my RCA Lyra. When I choose to unmount or eject the mp3 player, I am prompted with the screen giving me the option to delete all items in the trash, which I click. However, when I plug my mp3 back into the computer, the trashcan automatically fills back up with my music files even though no music is shown when I run my Lyra through Rhythmbox. Going into the Trash and attempting to manually delete the items will give me: "Failed to delete the item from the Trash." If I try to delete mp3 files when my player isn't plugged in, I'll end up with a read-only file system error. I've tried the sudo command > rm -rf ~/.Trash/* to no avail, and manually clicking the "Empty Trash" button does not work either. I'm a little trepidacious to place "sudo" in front of the command, as I have no idea what files will end up being deleted. 

None of the previous forum topics or Google searches have helped (which help me a great deal in Ubuntu-related problems most of the time), and I'm at my wits end. I finally cracked and signed up to these forums solely to have this problem fixed. I appreciate any help offered, though keep in mind I'm an *absolute* newbie with Linux. Wording any answers into terms easily understandable would be a huge help to me. Thanks!

---

### Post by Iraqiman on 2010-03-23
Bump.

I also forgot to mention that I'm running 32-bit Ubuntu (9.10), *not* xubuntu as the title indicates.

---

### Post by Chronon on 2010-03-23
> **Iraqiman said:**
> I've been having the same problem with my RCA Lyra. When I choose to unmount or eject the mp3 player, I am prompted with the screen giving me the option to delete all items in the trash, which I click. However, when I plug my mp3 back into the computer, the trashcan automatically fills back up with my music files even though no music is shown when I run my Lyra through Rhythmbox. Going into the Trash and attempting to manually delete the items will give me: "Failed to delete the item from the Trash." If I try to delete mp3 files when my player isn't plugged in, I'll end up with a read-only file system error. I've tried the sudo command  to no avail, and manually clicking the "Empty Trash" button does not work either. I'm a little trepidacious to place "sudo" in front of the command, as I have no idea what files will end up being deleted. 
Which trash are you talking about?  Is your system merging a trash folder from your player with the one in your home folder? Try viewing hidden folders and deleting any trash folder that exists on your mp3 player.  

Using "sudo" will only run the same command as root.  Since you're trying to delete all files in that folder anyway it shouldn't cause any harm.  Make sure you are running it on the correct location, though, since you can cause a lot of damage running that command in the wrong place.

> 
None of the previous forum topics or Google searches have helped (which help me a great deal in Ubuntu-related problems most of the time), and I'm at my wits end. I finally cracked and signed up to these forums solely to have this problem fixed. I appreciate any help offered, though keep in mind I'm an *absolute* newbie with Linux. Wording any answers into terms easily understandable would be a huge help to me. Thanks!

I'm not sure why you're having trouble clearing the trash in the GUI, but hopefully some other people will have some ideas about that.

---

### Post by Iraqiman on 2010-03-24
I completely forgot about checking for hidden files in the folder that pops up when I insert my mp3, I just assumed all trash would automatically transfer to the recycle bin. The folder it made was called ".Trash-1000" or something along those lines, but at first I couldn't move it to the recycle bin or delete it due to a "Read-only filesystem error". I ran the > sudo rm -rf ~/.Trash/* command, and then kind of made up my own by replacing ".Trash" with ".Trash-1000". However, I unplugged it and replugged it in, and the trash was still there. Out of frustration I clicked on the trash folder and hit the "delete" key on my keyboard, and it disappeared! I'm not sure which method worked, but locating that hidden file was key to solving this problem. Many thanks, Chronon!

---

### Post by Chronon on 2010-03-24
You're welcome.  I'm glad to help.  

At least you know where the deleted files are on your player now, so you can manually remove them when you need to.  Maybe someone else will have some deeper insight about making everything behave as you want through the GUI (i.e. make "empty trash" work as desired).

---

### Post by PcMojo on 2012-03-01
[SIZE=2]I just had the same problem and nothing seemed to work. Found a simple solution after reading this [article]("https://help.ubuntu.com/community/RecoverLostDiskSpace"). Just like Windoze, if you delete something it automatically goes to RecyclingBin/Trash. Unfortunately it still sends a copy to the trash bin even if you are in the TrashBin at the time (obviously defeating the whole purpose). Similar to Windoze, if you hold down a key and then hit the delete key, it bypasses the RecyclingBin/Trash.

From the article, "In a file browser, use SHIFT-DELETE to bypass the Trash bin." This is similar to the rm command in terminal and "empty trash bin" icon in the file browser. They are all doing basically the same thing, deleting the file without sending a copy back to the trash bin. I was able to permanently delete the trash bin files from my mp3 player from Nautilus without using gksudo - just by going into the trash1000 folder (then into the two subfolders "files & info") and selecting all the files (ctrl_A) then using Shift-Delete. Poof! Gone! 

Others that are getting read only or file ownership errors (could be how the mp3 player formats it's file system) might have to use "sudo" in terminal or "gksudo" to launch their file browsers to take care of the permissions issues. If you've tried everything in this thread and are still having problems, your mp3 player may have formatted its "file system" in some sort of proprietary way. I suggest searching under the name of your specific player to see if others have fixed it. Also, There are some open source firmwares for certain mp3 players that are real popular, like RockBox. Check to see if RockBox is compatible with your player, back up your mp3's, install RockBox and reformat your player, re-sync your mp3's. Hope this helps![/SIZE]

---

### Post by Chronon on 2012-03-02
Usually a player getting mounted as read-only is an indication of a damaged file system.  

The behavior described in this topic depends on how the operating system handles UMS devices (including mp3 players running Rockbox).  Incidentally, those who do use Rockbox can use the Disk Tidy plugin to remove useless files and folders left over after a USB session.

---

