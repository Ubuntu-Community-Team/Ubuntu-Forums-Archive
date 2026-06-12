---
title: "[SOLVED] Sansa Clip not showing songs in music folder."
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by donniezazen on 2008-03-24
I have Sansa Clip M350. It works fine with vista. But when i plug it in Ubuntu, no music file is shown in Music folder. I have seen some thread related to MTP but as i am new i find them very confusing. Can any of you help me making my sansa clip work in Ubuntu and get rid of again and again going back to Vista for adding or removing my mp3 files?

Thanks
Soham.

---

### Post by spych102 on 2008-03-24
You need to create a file called .is_audio_player in the players root folder, so type in a shell (replacing the name of playername with the name that it is mounted with when you plug it in):

```
gedit /media/playername
```

when gedit opens up paste the following into the file:

```
audio_folders=MUSIC/,RECORD/
```

now click File then Save and exit gedit

Next time you use rythmbox or banshee or another HAL based music program it should be recognised. I did this with my Sony Ericsson phone and it works well.

---

### Post by heizenberg on 2008-03-25
The same solution doesn't seem to work for me. I've even played with changing the USB mode on the Sansa Clip to both MTP and MSC. Additionally, I've installed mtp-tools on my ubuntu Gutsy machine.
I just cannot see the existing files on the device... and I know they're there, since I can play them back on the device.
I can even create new folders in the device (through Nautius and a terminal), but I cannot see the existing folders. I've already set Nautilus to display hidden files without any luck.
These are the contents of my /media/SANSA CLIP/is_audio_player file

> audio_folders=MUSIC/,RECORD/
folder_depth=2
output_formats=audio/ogg,audio/x-ms-wma,audio/mpeg,audio/wav,audio/flac,audio/mp3

(I added the second and third lines later... i.e. I've tried with just the first line in the file too)

I cannot see the existing mp3 files either in Nautilus or Rhythmbox, although Rhythmbox now recognizes the Sansa Clip as a media player.

---

### Post by heizenberg on 2008-03-25
I should also mention that my gutsy machine can see files on my thumb drives when plugged into the same USB socket.

---

### Post by spych102 on 2008-03-25
One thing I did with my Sony Ericsson mp3 phone was to ignore the .trash folder. I did not realise that it was filling up more and more with music and whenever I deleted something to make more space none ever appeared! This was all because I was ignoring the folder called .trash. Perhaps the player has hidden the music somewhere non-obvious.

If you type the following command in a terminal:

```
ln -a -R /media/nameofdrive > sansafilelist.txt
```

You will be able to see every file on the entire disk that is visible to Linux and its path. (-a to see all hidden files and -R to recursively go through every folder).

---

### Post by donniezazen on 2008-03-27
> **spych102 said:**
> You need to create a file called .is_audio_player in the players root folder, so type in a shell (replacing the name of playername with the name that it is mounted with when you plug it in):

```
gedit /media/playername
```

when gedit opens up paste the following into the file:

```
audio_folders=MUSIC/,RECORD/
```

now click File then Save and exit gedit

Next time you use rythmbox or banshee or another HAL based music program it should be recognised. I did this with my Sony Ericsson phone and it works well.

Sorry for this delay.

I created the file. And my Rhythm box is able to recognize it but its giving error

file:///media/disk/MTABLE.SYS                Import Error: MIME type could not be identified
file:///media/disk/RES_INFO.SYS             Import Error: MIME type could not be identified

I installed some codecs as guided in this web page

[https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/5861]("https://answers.launchpad.net/ubuntu/+source/rhythmbox/+question/5861")

but nothing is working.

Thanks for your reply.Please Help!!!!

---

### Post by spych102 on 2008-03-27
A MIME type is just a description of the format of a file i.e. mp3 or video or some type of system file etc. As Rhythmbox is trying to import music from your player it goes through every file including MTABLE.SYS and RES_INFO.SYS. Thing is, these are not music files so it comes back with an error which should not be anything to worry about if your player and Rhythmbox are working fine otherwise.

Obviously it is not a good thing that it comes back with an error that scares the hell out of a user so it might be worth filing a bug.

---

### Post by donniezazen on 2008-03-27
> **spych102 said:**
> A MIME type is just a description of the format of a file i.e. mp3 or video or some type of system file etc. As Rhythmbox is trying to import music from your player it goes through every file including MTABLE.SYS and RES_INFO.SYS. Thing is, these are not music files so it comes back with an error which should not be anything to worry about if your player and Rhythmbox are working fine otherwise.

Obviously it is not a good thing that it comes back with an error that scares the hell out of a user so it might be worth filing a bug.

Thanks for your suggestions. I have reported the bug.  I hope i will get some help. But if Rhythm box is searching for mp3 files and my players is full of mp3 songs, why cant it find them?

Thanks.

---

### Post by spych102 on 2008-03-28
Can you post the txt file from the following command?

```
ln -a -R /media/nameofdrive > sansafilelist.txt
```

It might be quite long depending on how much music you have on the player.

---

### Post by donniezazen on 2008-03-28
> **spych102 said:**
> Can you post the txt file from the following command?

```
ln -a -R /media/nameofdrive > sansafilelist.txt
```

It might be quite long depending on how much music you have on the player.

This command is giving an error. And sansafilelist.txt is empty. I am not able to upload it right now but i will try again and upload it as soon as possible.

ln: invalid option -- a

Thanks for help.

---

### Post by donniezazen on 2008-03-28
Another information is when i changed USB mode to MTP, Ubuntu/Rhythm box stopped recognizing it.
MSC/Auto detect mode gives same previously mentioned problem.

---

### Post by spych102 on 2008-03-29
It's giving an error because I typed "ln" (link command) instead of ls (list command). Sorry soham.  Try the following:

```
ls -a -R /media/nameofdrive > sansafilelist.txt
```

---

### Post by donniezazen on 2008-03-29
> **spych102 said:**
> It's giving an error because I typed "ln" (link command) instead of ls (list command). Sorry soham.  Try the following:

```
ls -a -R /media/nameofdrive > sansafilelist.txt
```

No problem Spych102. Thank you so much for your help.

I am attaching the sansafilelist and also posting here. Thanks

/media/disk:
.
..
AUDIBLE
.is_audio_player
.is_audio_player~
.is_media_player
.is_media_player~
MTABLE.SYS
MUSIC
RECORD
RES_INFO.SYS
SYS_CONF.SYS
.Trash-sudhir
version.sdk

/media/disk/AUDIBLE:
.
..

/media/disk/MUSIC:
.
..

/media/disk/RECORD:
.
..
FM
VOICE

/media/disk/RECORD/FM:
.
..

/media/disk/RECORD/VOICE:
.
..

/media/disk/.Trash-sudhir:
.
..

---

### Post by spych102 on 2008-03-31
There's definitely no music in those files. I'm stumped.

---

### Post by donniezazen on 2008-04-01
> **spych102 said:**
> There's definitely no music in those files. I'm stumped.

How is that possible it has 1.9 GB songs and It works great with windows.

thanks

---

### Post by donniezazen on 2008-04-02
Yes !!!! Problem is solved.
I just removed the songs i added from windows machine and I copied songs from Linux machine. Everything is now working as if there was no problem.

Thanks.

---

### Post by spych102 on 2008-04-02
Yay! That was easy! You can change this thread to [Solved] from the Thread Tools menu above the posts.

---

