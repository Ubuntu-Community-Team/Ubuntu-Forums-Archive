---
title: "Mass mp3 tag conversion?"
date: 2007-08-16
forum: Multimedia &amp; Video
---

### Post by bayonetblaha on 2007-08-16
After months of off-and-on work on the mystery, I have found that the way to make mp3 tags work on my Sansa E240 player is to have all my tags in ID3V2.3 (mine are in 2.4). I have installed easytag, tagtool, k3b, kid3, and amaroK, but none seem to have a function to convert tags in mass.  How can I do this, with these or any other program?

---

### Post by tgalati4 on 2007-08-17
Have you looked for a firmware upgrade to the Sansa player?

If not, then perhaps suggest an upgrade in the firmware to Sandisk? 
 
How were the tags created originally?

---

### Post by jollemeyer on 2007-08-19
I have no problems with ID3 tags on my Sansa e280 anymore.

I figured out, that the player only considers ID3v2.3 tags.

All other kinds of tag formats are not used or ignored. (In my mp3 files I use both, id3v1 and id3v2.3 tags at the same time, although id3v1 is not used by the player).

To convert id3v2.4 to id3v2.3, I had to copy my original ID3v2.4 tags to ID3v1 using Kid3 (a KDE tool) and than re-format the ID3v1 tags to ID3v2.3 using a tool called "eyed3".
The eyed3 tool allows mass conversion. You may find it in the repos.

My command line for the second conversion step is as follows:

```

cd /your/players/mp3/music/folder/
find . -name '*.mp3' -cmin -60 -exec /usr/bin/eyeD3 --v1 --to-v2.3 {} \;
```

This basically finds all mp3 files in the current folder that were modified less than 60min ago (to skip older files with the correct format) and re-formats the id3v1 tag to id3v2.3.

I noticed that I had to delete the old files (with the wrong tag format, i.e. id3v2.4 or id3v1 only) from my Sansa e280 beforehand.
Than I had to disconnect the player to force the player to update its database.

Once this has been done, I reconnected the player, copied the files over again and executed the above mentioned command.

After disconnecting the player, it updated the database again, but this time the correct id3v2.3 tags were used.

Everything works fine afterwards. :guitar:

PS: This also demonstrates that using the command line can be a lot more efficient than doing everything using a GUI.

---

### Post by bayonetblaha on 2007-08-19
jollemeyer, thanks a lot! I tried a half-dozen other tagging programs, some of which appeared to write ID3V2.3 tags, but none of which fixed it. Eyed3 fixed it for real, no more Unknown Artist at all. Anybody reading this who has this problem, this is the fix.

---

### Post by Smith oo4 on 2007-12-22
I too have spent a couple of months off and on trying to figure out how to get tags working with my Sansa MP3 player and I think this is the solution I'm looking for.  The only thing is that I am relatively new to Linux (especially the command line) and I think I am too dumb to implement it.
First I want make sure that this is the right solution.  Over the years I've ripped numerous CDs in my collection, first using Windows with real media player or Windows media player and then using Linux with either sound juicer or banshee.  From what I can tell most if not all of these MP3’s are tagged in id3v1 and is my understanding they need to be converted to id3v2.3.
I would like to get all of these MP3s standardized to one tag format (id3V2.3 for my MP3 player) without having to go through them file by file.  If indeed your solution is the correct one for my needs could you please explain how to implement it in simple it terms.  Also if possible could you explain what each step does I would appreciate, I am trying to learn as much about Linux and the command line is possible.
Thank you

---

### Post by ianhogben on 2008-01-05
I had a slightly different command-line entry because I wanted to modify all of the files on my sansa, not just the ones that were modified recently. So I did all the the following:

```
sudo apt-get install eyeD3
ls /media
```
... now pick the directory that your sansa player is. Mine was Sansa_E280_ or something.
```
cd /media/SansaDirectoryName/MUSIC
find . -type f -print0 |xargs -0 eyeD3 --to-v2.3

```
What the last command is doing (step by step) is this:
[LIST]
[*]finding all files in the current directory and all subdirectories, and making sure that the spaces and special characters in the filenames are being read correctly,
[*]passing each filename to a program called xargs that lets you run a command on each individual file,
[*]and running the eyeD3 program that is reading whatever format tags are already on each file and converting to version 2.3
[/LIST]

Hope this helps!

Ian.

---

### Post by Smith oo4 on 2008-01-05
Thank you for your help, it worked well.
Morgan Smith

---

### Post by chochem on 2008-05-19
eyeD3 is by far the best and most actively developed id3 tagging tool, there is. However, I got frustrated having to piece a long string of commands together for each directory, so i wrote a [little bash script]("http://bash.viharpander.dk/#sego3") on top of it. It's intended for using on lots of newly acquired files to get them to adhere to the user's standards (amongst other things one of the - configurable - defaults is using 2.3 and UTF-16 since I've also got a Sansa E280), anything from using the genre 'hip-hop' rather than 'hip hop' to using all lowercase fields or a specific naming structure, like genre/year/album.

---

