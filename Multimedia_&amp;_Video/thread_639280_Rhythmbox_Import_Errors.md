---
title: "Rhythmbox Import Errors"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by NET WT on 2007-12-13
Hi, can someone please help me again? A few hours ago I used Sound Juicer to extract some music. I then opened Rhythmbox to listen to them, but none of the songs were imported into Rhythmbox. The songs are mp3, and on the left side under Library there is an icon which says Import Errors. Rhythmbox says: Couldn't access file, File not found. I am not having this problem under my user account, but under a family member's. Rhythmbox works well on my account but not on their's. The version of Ubuntu that I am using is 7.10, Thanks for any help.

---

### Post by daengbo on 2007-12-13
Is the music yours or the family member's? I ask because that could be a permission problem. It doesn't sound like a codec error to me. You can check the permissions on the files by right-clicking on them and choosing "Properties."

Just to be safe, though, make sure that Rhythmbox is able to play MP3s by installing the[ Ubuntu Restricted Extras]("apt:ubuntu-restricted-extras") package.

---

### Post by NET WT on 2007-12-13
The music belongs to them, and is in their Music folder. Under my account I am able to listen to my music in Rhythmbox, which are all MP3. Under their account Rhythmbox doesn't import anything and I get that error. If I double click on a song though, I does play in Totem. I right clicked on their Music folder and on some of their songs. To check the permissions. It all looks fine but I am not sure.

---

### Post by NET WT on 2007-12-14
I just remember something. I entered some command into the terminal back when I setup Ubuntu on this computer. The command was:

> chmod 700 /home/<username>

Do you think that is causing this problem? Because I did that to each of our accounts.

---

### Post by NET WT on 2008-01-01
I still need help with this problem.

---

### Post by TheAxeR on 2008-01-01
I am having the same problem.  The files are in my home/music/ and I have read and write premissions for the files.  The one thing I think it could be is that there are spaces in the names of the files, there is one file i made a copy of and gave it a name without any spaces which does import.  However, this confuses me because I have another machine running ubuntu and rhythmbox does not have an issue with spaces in the name.

---

### Post by fadain on 2008-01-15
Same issue here. Though Rhythmbox works fine on my laptop but on my desktop throws all these import errors. Interesting thing is that I have the same music folder on my laptop and my desktop and even the permissions are same.

---

### Post by mandelbro on 2008-01-31
I get import problems too but the music loads and plays fine!
:guitar:

---

### Post by NET WT on 2008-02-01
I noticed something else. When I tried to backup their music to my external hard drive, I got an error message. Which said: 

> Error "Invalid Parameters" while copying, Would you like to continue?

Some songs could be copied to the disk, but not others.

---

### Post by NET WT on 2008-03-07
This is an older thread, but I am now able to import their music into Rhythmbox. Although I don't think that I actually fixed the problem. Here is what I ended up doing:

I created a new folder on the desktop. I then moved all of their music into it. Opened up Rhythmbox and went to Edit>Preferences. On the Music tab, I changed their "Library Location" to the new folder that I had made. All of their music then imported into Rhythmbox. 

That is what I ended up doing, although there is probably a better way of fixing it. 

 When I upgrade to Hardy Heron, I will not be entering

 > chmod 700 /home/<username> 

to avoid this problem. Since that may have caused it. In the future I will be more careful about what I enter into the terminal.

My problem with the external hd was also solved. There was a colon in the name of several files, so I just removed them.

---

