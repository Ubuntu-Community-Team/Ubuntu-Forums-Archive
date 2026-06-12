---
title: "banshee won't play songs"
date: 2007-10-20
forum: Multimedia &amp; Video
---

### Post by larsdk on 2007-10-20
Hi there,

I just upgraded from Feisty to Gutsy and everything works like a charm. However I can't get banshee to play my music. It does not crash or anything, but the meter showing the progress of the song just remains greyed out and stays on 0:00 of the-length-of-the-song.

Any suggestions appreciated :)

---

### Post by rollerdiscoman on 2007-10-20
Hello,

I too have upgraded, and installed Banshee last night. It worked fine, but when I woke up this morning and tried to play some tunes I got exactly what you got... I even rebooted my computer several times.

I'll see if I can't come up with a solution

---

### Post by rollerdiscoman on 2007-10-20
I've found an answer!

Try importing a few songs into Banshee (It doesnt matter if they're already in your library). I guess Banshee just needed some sort of kickstart.

I'm not sure if this is a permanent or temporary fix, but its worth a try.

---

### Post by larsdk on 2007-10-20
strange, but it works fine now after applying your "solution" :)

---

### Post by MrStaticVoid on 2007-10-22
I've got this or a similar problem in Gutsy Gibbon.  Banshee will play and continue to play music until Pidgin makes a sound, then Banshee will fail to play the next song until it is restarted.  The progress meter just sits at "0:00."  Both Pidgin and Gstreamer are set up to use ALSA, so that shouldn't be a problem.

The "solution" above does not seem to work for me.

Any ideas?

---

### Post by dre1187 on 2007-11-03
Hi, I just tried the "solution" that was posted and it still does not work for me, the playback meter stays at zero. Any other ideas on what it could it be?

---

### Post by jimbz on 2007-11-13
I had this problem too. Try deleting the ~/.gconf/apps/banshee folder, I think it's about audio profiles that are messed up.

Hope it can help.

---

### Post by theluddite on 2007-11-13
My update to 7.1 screwed up Banshee's playback of some radio stations and my ipod doesn't show up anymore -- what gives?  That's my  favorite music software -- I'd rather not switch... again.

---

### Post by theluddite on 2007-11-27
For different reasons, I reinstalled Ubuntu 7.04 and upgraded again to 7.10 and Banshee works fine.  I don't know what the problem was.  My system is as follows:

Dell Intel Core 2 Duo (4MB L2 Cache,2.4GHz,1066 FSB), 2GB Dual Channel DDR2 SDRAM, 300GB Serial ATA Hard Drive, 128MB ATI Radeon X1300.

I know this isn't a good solution for most people that may encounter a similar situation.  But since I don't know what was wrong, I can't offer a better solution.

---

### Post by Jake90 on 2008-01-24
Same problem. What is weird about it is if I go to my music folder and right click then select play with banshee then it goes into a que folder in banshee and plays fine
Anyone have any suggestions?

---

### Post by Mostlyharmless42 on 2008-01-24
I'm having similar problems.  It played 1 song the first time i opened it and then i exited and when i went back it was broken.  The progress bar moves, but no sound comes out.  I've tried everything on this thread, but i still can't get it to make a sound.

---

### Post by Mostlyharmless42 on 2008-01-24
I'm getting similar behavior from rythmbox

Amarok and Exaile work fine...?

---

### Post by Potatoj316 on 2008-01-29
> **Jake90 said:**
> Same problem. What is weird about it is if I go to my music folder and right click then select play with banshee then it goes into a que folder in banshee and plays fine
Anyone have any suggestions?

I have the same exact problem.  If I start banshee then tell it to play a song it doesn't work, but if I go into the Music folder and say open with banshee, it works.

---

### Post by Potatoj316 on 2008-01-29
In an attempt to fix the problem I removed all the songs from my library (but kept them in the Music folder) when it started removing them it would play like half a second or less of each song before taking it out.  (strange because they wouldn't play before) The next time I started Banshee it gave me the import music dialog, I directed it to my Music folder, it imported all the songs, I restarted Banshee and now It plays everything fine.

---

### Post by GrandMasterV on 2008-02-09
I had the same problem on Ubuntu Gutsy with latest updates at feb 8th 2008.  It was not working for one user but working for another.  I tried deleting the /home/user/.gconf/apps/banshee folder but that did not work.  I had to remove all the songs in about 300 song groups then re-add them.  Remove any more at once and it would crash out.  Hope this is fixed in the new version.  I have posted this bug to their bugzilla.

[http://bugzilla.gnome.org/show_bug.cgi?id=515351]("http://bugzilla.gnome.org/show_bug.cgi?id=515351")

---

### Post by LorisMaria on 2008-03-30
this worked for me with the "pick a song through music folder" solution. I'm using 7.10.
Not sure what the hell is happening. 
Afterwards I chose something from Banshee and it just worked. Go figure.

---

