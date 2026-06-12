---
title: "Error &quot;Invalid Parameters&quot; while copying"
date: 2007-01-15
forum: Multimedia &amp; Video
---

### Post by rainwalker on 2007-01-15
I'm trying to transfer my music collection over to my PSP, and it's all been good except for one sone. When I try to copy the song "Is This My Fate?" He Asked Them I get an error message saying 
> Error "Invalid Parameters" while copying "/home/r... Them.mp3".
Would you like to continue?
with the option to either retry or cancel. Retrying doesn't work, and canceling means I can't put it on my PSP. Is it the quotation marks in the song title that mess it up? If so, what can I do to transfer the song without removing them?

---

### Post by rodericj on 2007-03-04
I have had the same problem. I tried to copy files from a "music" directory into a FAT32 Music directory. Most of the files copied but not all. The files that did not copy all had that obscure error message. The offending files have characters in them that are not accepted in filenames in the FAT32 file system.  (used by the iPod )These are [COLOR="Red"]* . " / \ [ ] : ; | = ,[/COLOR] If you rename the files it works ok. If you manage the files from within AMORAK it has a facility to do this automatically.

I hope this helps.

---

### Post by Unoone on 2007-03-08
I'm getting the same problem will all of my three Ubuntu installs. I name my web folders as "link_name", "home_name", etc. Nothing fancy yet later on as I want to backup directories that are full of these named folders to my fat32 drives I get "Invalid parameters" while copying.....  with random folders in a directory.

I can transfer these directories to any of the ext3 drive with no problems. To test for errors I make a new folder with a name similar to the old folder name like-  "link_name" to "linked_name". I then transfer all of the contents from the old folder "link_name" to "linked_name". Now the the folder named "linked_name" copies without error to the fat32 drive.  It's an error that effects the way data is written to ext3 drives.

I'm also getting folder permission errors on certain files that I copy from my usb drives. I have to manually give myself permissions. I never had these types of errors in Ubuntu until I installed Edgy. I hope that there will be a fix for this soon.:???: :-({|=

---

### Post by MockY on 2007-08-14
Same issue with Feisty...
Too bad FAT32 really blows. But formatting the stick in ext3 makes it impossible to use on Windows machines.

---

### Post by darkcrab on 2007-10-11
I am also getting an error for this. When I try to copy an open office file from my desktop into my fat32 usb drive in feisty, I get invalid parameters. However, if I try to copy a picture file from my desktop to the usb drive it is fine.

---

### Post by OsakaWilson on 2007-10-28
Same here. Bump.

---

### Post by papatrpt89 on 2008-01-04
This thread has essentially been solved...look at the reply from rodericj:

> 
I have had the same problem. I tried to copy files from a "music" directory into a FAT32 Music directory. Most of the files copied but not all. The files that did not copy all had that obscure error message. The offending files have characters in them that are not accepted in filenames in the FAT32 file system. (used by the iPod )These are [COLOR=Red]* . " / \ [ ] : ; | = ,[/COLOR] If you rename the files it works ok. If you manage the files from within AMORAK it has a facility to do this automatically.

I hope this helps.     


---

### Post by Plissken@plissken on 2008-01-13
All you have to do is change the name of your file to something else and the drag and drop to where your saving it to. For an example if your music folder is named KISS then change it to KISS Albums it worked for me and i hope it will work for you.

---

### Post by Plissken@plissken on 2008-01-16
> **OsakaWilson said:**
> Same here. Bump.

just change the name of your file to a different name and it should copy with no problem

---

### Post by philidox on 2008-02-25
> **MockY said:**
> Same issue with Feisty...
Too bad FAT32 really blows. But formatting the stick in ext3 makes it impossible to use on Windows machines.

Its not impossible to use ext3 hard drive/partitions with windows just install a lil program and windows will see ext3 partions just fine.  Here is the link to the downloadable program that will make windows read linux partitions [http://www.softpedia.com/get/System/OS-Enhancements/Ext2-IFS.shtml](http://www.softpedia.com/get/System/OS-Enhancements/Ext2-IFS.shtml)

---

### Post by mark1969 on 2008-04-13
find /home/mark/Music -iname "*" -exec rename -v 's/[\\:*?"<>|]//g' "{}" \;

I had the same problem and was given this by my brother, it removed all characters that caused the problems and I am now able to transfer my whole audio collection to my FAT partitioned media player.
The best thing is, it's recursive so no mater how many folders in folders you have it still works.
You're probably better off copying  the command (to save typos) and paste it into a terminal, then change the bit "/home/mark/Music" to match the path to your audio files and that should be it.

---

