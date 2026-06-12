---
title: "Ogg to Sansa E280"
date: 2007-12-27
forum: Multimedia &amp; Video
---

### Post by JustinAlf on 2007-12-27
I've set up the USB options in my Sansa e280 so that Kubuntu recognizes it and syncs with it.  I can download and upload songs in MP3 form with Amorak, but cannot put OGG files onto the Sansa e280, partly because the player doesn't play OGG files.  Is there any way to hack this player to play OGG, or is there a way I can convert the OGG files to MP3 files while putting them on the E280, in other words can I convert the files in a one step process while putting the files on the E280?  Any help would be appreciated.  Thanks-

---

### Post by Keith_Beef on 2007-12-27
> **JustinAlf said:**
>  Is there any way to hack this player to play OGG, 
I very much doubt that this is possible.Googling might find something, though.

> **JustinAlf said:**
>  is there a way I can convert the OGG files to MP3 files while putting them on the E280, in other words can I convert the files in a one step process while putting the files on the E280?  Any help would be appreciated.
Not exactly a one step process, but near enough.

[LIST=1]
[*]Convert the OGG file back to WAV format (use oggdec).
[*]Convert the WAV file to MP3 format.
[*]Read the tags from the OGG file and write them to the MP3 file.
[*]Mount the Sansa player as an external disc.
[*]Copy the files to the Sansa player.
[/LIST]

Steps 1,2 and 3 can be automated as a Nautilus script quite easily, so that you can select a bunch of OGG files in a directory, run the script on them.

Step 4 should happen automagically when you connect the device to your computer.

Step 5 is drag and drop.

Read [this thread]("http://ubuntuforums.org/showthread.php?t=316919") for more information, and a Python script to do a similar job.



B.

---

### Post by benerivo on 2007-12-27
You might also try [soundconverter]("http://soundconverter.berlios.de/"), which is in the repositories.

---

### Post by nick_h on 2007-12-27
> Is there any way to hack this player to play OGG
You could try using the [Rockbox](http://www.rockbox.org/) firmware.

---

### Post by Keith_Beef on 2008-03-23
I just came back to this thread, because I dug out an old Sansa c250 that I had tucked into a bag and thrown in a corner a few months back...

I looked at Rockbox, and there is an e200 zip file that might have something of interest for your e280:
[http://build.rockbox.org/dist/build-sansae200/rockbox.zip](http://build.rockbox.org/dist/build-sansae200/rockbox.zip)

But for me, I couldn't find a 64 bit binary of sansapatcher anywhere... 404 File Not Found when I follow links from the Rockbox web site...

Sansa c250
Version 01.00.00A

Downloaded Rockbox firmware (rockbox-sansac200.zip), the font package and the x86 sansapatcher binary.

Put player in MSC mode, and connected to computer.

Extracted the Rockbox firmware and fonts directly into the player's root directory. The fonts need to go into .rockbox/fonts so need to leave options checked: Recreate folders and Overwrite existing files.

$ ls -al /media/Sansa\ c250/
total 356
drwx------  9 beef root 16384 2008-03-23 22:05 .
drwxr-xr-x  9 root     root  4096 2008-03-23 21:54 ..
drwx------ 18 beef root 32768 2007-05-16 23:19 MUSIC
drwx------  2 beef root 32768 1980-08-07 01:58 PHOTO
drwx------  2 beef root 32768 1980-08-07 01:58 PLAYLISTS
drwx------  4 beef root 32768 1980-08-07 01:58 RECORD
drwx------ 14 beef root 32768 2008-03-23 22:06 .rockbox
drwx------  5 beef root 32768 2006-10-16 04:27 SYSTEM
drwx------  2 beef root 32768 1982-01-05 04:25 tmp
-rwx------  1 beef root   512 1982-01-05 04:07 version.sdk
-rwx------  1 beef root   512 1982-01-05 04:07 VERSION.TXT
-rwx------  1 beef root   296 2007-03-12 11:44 WMPInfo.xml

Now as root, run the sansapatcher utility.

$ chmod a+x sansapatcher 
$ sudo ./sansapatcher 
[enter password]
sansapatcher v0.6 with v4.0 bootloaders - (C) Dave Chapman 2006-2007
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

[INFO] Scanning disk devices...
[INFO] c200 found - /dev/sdi
[INFO] Reading partition table from /dev/sdi
[INFO] Sector size is 512 bytes
[INFO] Part    Start Sector    End Sector   Size (MB)   Type
[INFO]    0            1017       3972095      1939.0   FAT16 (0x06)
[INFO]    1         3972096       4013055        20.0   OS/2 hidden C: drive (0x84)
Enter i to install the Rockbox bootloader, u to uninstall
 or c to cancel and do nothing (i/u/c) :i
[INFO] Bootloader installed successfully.
Press ENTER to exit sansapatcher :

Unmount device, disconnect it, see the normal "Refresh Database" message. 
Switch off then on, and see if it works...

SanDisk logo appears for a moment, then RockBox! It worked!

What's more, the display correctly shows accented letters, such as "â", that the original firmware scrambled.

When reconnected to the computer, the Rockbox firmware displays some information for a few seconds, then the original firmware is loaded.

I copied some ogg files to the player, but they didn't seem to show up after the databade refresh. I switched the device off and on again, but they still didn't show up.

K.

---

### Post by JustinAlf on 2008-03-26
I actually installed Rockbox on it, and that works wonderfully.  I'd suggest doing that for anyone with a Sansa.

---

