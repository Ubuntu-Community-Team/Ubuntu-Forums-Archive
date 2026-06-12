---
title: "GoGear doesn't recognize ID3 Tags"
date: 2008-10-23
forum: Multimedia Software
---

### Post by GabrielWolff on 2008-10-23
I just bought a PHILIPS GoGear 4GB.
I edited a few ID3 Tags with EasyTag.
But the device will disply only "Unknown Artist", "Unknown Album" etc

Does anyone have a clue what I might have done wrong?

G

---

### Post by benste on 2008-12-26
My sister got a 8GB GoGear - I've got the same problem.
There is a german wiki thread:
[http://wiki.ubuntuusers.de/GoGear]("http://wiki.ubuntuusers.de/GoGear")

I said that you'll need to install [http://golb.sourceforge.net/]("http://golb.sourceforge.net/") because the phillips player uses a sql database to see all these id3tags ...

But I didn't manage it yet to see id3 tags on the player.

---

### Post by benste on 2008-12-26
Wrote a mail to the developer named on SF project page because I still don't get the right ID3 Tag on the player:

> Dear developer,
I managed to install your tool into Ubuntu - it works fine after some time of work.
For Ubuntu there was a missing required package which is called
'libqt4-sql-sqlite2' It is: Qt 4 SQLite 2 database driver.

After the isntallation still nothing happened, because you wrote to execute the command:
golb -f _system/media/audio/MyDb

I changed it to ./MyDb
or
golb -f /media/PHILLIPS/MyDb
or
golb -f ./MUSIC/MyDb

because i wasn't sure how to use it.

The player recognized now like before the installation to that it has more than 60 mp3 files loaded,
But it shows Unknown Artist - ...

Would you please so kind to send me an email with the exact position of the normal database?
Or even better answer to the Ubuntuforums Thread, in which you'll see another user having problems with the Go Gear

---

### Post by neXyon on 2008-12-26
Would have been nice of you to include the link to this thread, so I wouldn't have had to ask my friend google ;)

About that missing required package: I'm sorry, but I cannot include all distributions' package dependancies and as the sqlite 2 qt driver is part of qt, I didn't mention it seperately.

The file _system/media/audio/MyDb is right on my device, so if you have it mounted under /media/PHILLIPS, then the file path would be /media/PHILLIPS/_system/media/audio/MyDb and you have to let it run in the /media/PHILLIPS directory or append this path via the -d command line parameter, otherwise the database entries will be wrong. I'm not sure though if your player has the same structure like mine.

For the reading of the id3 tags in the mp3 files golb uses taglib, an open source library for that, so if you get Unknown Artist by golb either taglib cannot read the tags or the file doesn't have tags.

Regards

---

### Post by benste on 2008-12-26
Seems that the player structure has been changed
there is nothing like _system anymore :-(
but these stdbstr files look interesting.

If I run the command
```
benste@VAIO-fe31m:/media/PHILIPS$ golb -f /media/PHILIPS/_system/media/audio/MyDb

```
I get probted back to the normal command line withouht any action.


> benste@VAIO-fe31m:/media/PHILIPS$ ls
FMRecord   MUSIC  Photos         RAMLIST.DAT  STDBDATA.DAT  STDBSTR.DAT  VIDEO
MicRecord  PHOTO  playqueue.dat  SETSTOR.DAT  STDBDATA.IDX  STDBSTR.IDX


I'm sorry for forgetting to attach the link - I wanted to but missed it before sending :-)

---

### Post by psycho0222 on 2009-08-09
This MP3 player only supports ID3v1 tags.You need to delete all the ID3v2 tags and reset it to make it work.
You can use a freeware called MP3 tag to do this:[http://www.mp3tag.de/en/](http://www.mp3tag.de/en/)

---

### Post by jjlee on 2010-05-14
> **GabrielWolff said:**
> I just bought a PHILIPS GoGear 4GB.
I edited a few ID3 Tags with EasyTag.
But the device will disply only "Unknown Artist", "Unknown Album" etc

Does anyone have a clue what I might have done wrong?

G
As Psycho0222 points out the GoGear appears to only recognises ID3v1 tags. You can use EasyTAG To remove the remove the ID3v2 tags and leave just the ID3v1 tags.
	Go to **Settings** &#8211; **Preferences** and sellect **ID3 Tag Settings**. 
	Under **Character Set for writing ID3 tags** de-select **Write ID3v2 tag** and make sure **ID3v1 tag is selected**. Set **Additional settings for iconv():** to &#8220;no&#8221;. 
	Now when you select the folder with your music in the MP3s that need converting will be red. Highlight these and select the Save File(s)  icon. 
	This will remove the ID3v2 tags so if you want to keep cover art then you will need to copy the files to a separate folder before making the change.

---

### Post by cascade9 on 2010-05-14
> **psycho0222 said:**
> This MP3 player only supports ID3v1 tags.You need to delete all the ID3v2 tags and reset it to make it work.
You can use a freeware called MP3 tag to do this:[http://www.mp3tag.de/en/](http://www.mp3tag.de/en/)

MP3Tag is a great program for windows....for linux, your better off with EasyTAG. jjlee has given the instructions for how to change to ID3v1 tags above (thanks!) ;)

---

### Post by p221072 on 2010-08-14
Thank you guys!
I changed the Tags to ID3V1 with EasyTAG and now my player recognize the Artist and Album names.
Though the order of the songs in the albums is never correct. It seems like the Track# tag is not correctly decoded.
Any ideas? :confused:

---

### Post by Mashepherd on 2010-12-05
The Easy tag solution kinda worked for my but as 'p221072' said above the track numbers were not tagged.

My solution was to use 'Kid3-gt' which is in the repositories; install then, 

~Write appropriate tags
~Select Tools
~select 'Convert ID3v2.4 to ID3v2.3"

All the files that you want tagging need to be selected.

As I said this worked fine for my

---

### Post by jack griffin on 2011-03-14
Hello , same problem here .
Tried both EasyTag and Kid3 , followed the instructions you gave
but still no good luck !

This worked , though : I renamed STDBDATA.DAT to STDBDATA.DAT.REM
and STDBDATA.IDX to STDBDATA.IDX.REM and then unplugged the player :
it took ages to update, but after it displayed the actual tags .
Looks like the player saves the tags of an mp3 file _only_ the first time it founds it  (when the mp3 has just been added).
After updating, it created two new files (STDBDATA.DAT and STDBDATA.IDX) :
the first is of the same size of the old file, while the latter file size is zero.

My player is a Philips GoGear SA3285/02 .
Any help or info about a linux application that can handle this device is welcome .
Cheers

---

### Post by MattressVon on 2011-03-16
Hey everyone. If you install Clementine (the multi desktop port of Amoarok 1.4) and set your Phillips Go Gear player to MTP mode, it will load all your tracks on our player with the correct tags. You need to have the latest firmware upgrade, but Clementine works well with Phillips GoGear players. It uses the sqylite database so it plays well with GoGear players.

1.) Upgrade firmware (I did this via windows 7 on my netbook dual boot, but there are instructions around for linux)

2.) Install Clementine:
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine

3.) Install Easytag

sudo apt-get install easytag

4.) Back up your tracks to your computer and reformat your player via the reformat venue option on the player.

5.) Point Clementine at your library:

Tools>preferences>music library

6.) Open your music in easytag and remove all comments, composer, Orig artist, copyright, url, and encoded by tags (sqylite and the gogaer firmware do not like these tag options. I'm not sure why, but this is what I had to do.)

7.) Using the Scanner in Easytag rename all tracks to this format %n - %a - %t or %n - %t. (you can do others but the dash is the important part. No dots or parenthesis. 

8.) Now go into Clemementine and update your library.

9.) Set your GoGear player to MTP mode and plug it into your computer using the USB cable. 

10.) Go to Clmentine and click on devices. You should see your player. Double click on it to load it.

11.) Let your computer scan it.

12.) Go to your library and right click on an artist or album you want to add to your player. In the pop up menu select copy to device. 

13.) Under naming options make sure the tag format matches what you set in Easytag. For example, if you did %n - %t make sure it does {%track - }%title.%extension so if you have 01 - The Grape in your folder, you get 01- The Grape in the same folder on your player.

Also at the beginning of the string you need to add the destination folder. Your string by default looks like:

%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

You want it to look like:

/music/%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

Otherwise it will just load the music onto your players root directory and not put it in the music folder.

14.) Click ok and it will load the track. Notice it only does 10 tracks at a time. I still haven't figured out how to fix this. When I do I'll post it here.

Your music should now be on your player and in the right place. Unmount your player using clementine and unplug it from the USB cable. Let it update the database and go in and check out the working tags!

---

### Post by jack griffin on 2011-03-17
Hey , many thanks [MattressVon]("http://ubuntuforums.org/member.php?u=527988") !
That worked for me !
It's a bit of a work, but worth it !
Now I gotta find the way to do the same thing on W**dows , and I am done .

---

### Post by thekix on 2011-04-07
Hi,

I wrote some hooks for gpodder. If someone wants to try it are here:

[http://kix.es/src/gpodder/](http://kix.es/src/gpodder/)

some info about it in the blog (kix.es/blog). Bugs/comments are welcome.

Regards.

---

### Post by dlcuber on 2011-05-08
> **jack griffin said:**
> 

This worked , though : I renamed STDBDATA.DAT to STDBDATA.DAT.REM
and STDBDATA.IDX to STDBDATA.IDX.REM and then unplugged the player :
it took ages to update, but after it displayed the actual tags .
Looks like the player saves the tags of an mp3 file _only_ the first time it founds it  (when the mp3 has just been added).
After updating, it created two new files (STDBDATA.DAT and STDBDATA.IDX) :
the first is of the same size of the old file, while the latter file size is zero.


thanks that worked for me too

---

### Post by shugoshin on 2011-05-15
I have Philips GoGear Aria 8GB. Here is what worked for me, and in my opinion the easiest way to transfer my music:

Change the PC connectivity preference(within settings) from MTP to MSC in the GoGear.

Create a file in the root folder of GoGear named: ```
.is_audio_player
```
and include in the file the following lines:
```
audio_folders=Music/
folder_depth=2
name="GoGear Aria"
```

Change the ID3 tags from ID3V2.4 to ID3V2.3 using EasyTag. You can easily embed the album covers here too. 

Now you can drag and drop "/artist/album/*.mp3" folders into the Music folder in GoGear. 

That's it.

This also works within Banshee (2.0.1), if you disable MTP extension (may not be necessary) and make sure that in the General preferences of Banshee "Write metadata to files" is unchecked. I think Banshee generates ID3V2.4, which then GoGear lists as Unknown Artist, Unknown Album.

---

### Post by kforum on 2012-09-11
> **MattressVon said:**
> Hey everyone. If you install Clementine (the multi desktop port of Amoarok 1.4) and set your Phillips Go Gear player to MTP mode, it will load all your tracks on our player with the correct tags. You need to have the latest firmware upgrade, but Clementine works well with Phillips GoGear players. It uses the sqylite database so it plays well with GoGear players.

1.) Upgrade firmware (I did this via windows 7 on my netbook dual boot, but there are instructions around for linux)

2.) Install Clementine:
sudo add-apt-repository ppa:me-davidsansome/clementine
sudo apt-get update
sudo apt-get install clementine

3.) Install Easytag

sudo apt-get install easytag

4.) Back up your tracks to your computer and reformat your player via the reformat venue option on the player.

5.) Point Clementine at your library:

Tools>preferences>music library

6.) Open your music in easytag and remove all comments, composer, Orig artist, copyright, url, and encoded by tags (sqylite and the gogaer firmware do not like these tag options. I'm not sure why, but this is what I had to do.)

7.) Using the Scanner in Easytag rename all tracks to this format %n - %a - %t or %n - %t. (you can do others but the dash is the important part. No dots or parenthesis. 

8.) Now go into Clemementine and update your library.

9.) Set your GoGear player to MTP mode and plug it into your computer using the USB cable. 

10.) Go to Clmentine and click on devices. You should see your player. Double click on it to load it.

11.) Let your computer scan it.

12.) Go to your library and right click on an artist or album you want to add to your player. In the pop up menu select copy to device. 

13.) Under naming options make sure the tag format matches what you set in Easytag. For example, if you did %n - %t make sure it does {%track - }%title.%extension so if you have 01 - The Grape in your folder, you get 01- The Grape in the same folder on your player.

Also at the beginning of the string you need to add the destination folder. Your string by default looks like:

%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

You want it to look like:

/music/%artist/%album{ (Disc %disc)}/{%track - }%title.%extension

Otherwise it will just load the music onto your players root directory and not put it in the music folder.

14.) Click ok and it will load the track. Notice it only does 10 tracks at a time. I still haven't figured out how to fix this. When I do I'll post it here.

Your music should now be on your player and in the right place. Unmount your player using clementine and unplug it from the USB cable. Let it update the database and go in and check out the working tags!

THANKS MAN! Clementine did the trick, i love it!

---

