---
title: "Can't Play music files copied from external hard drive"
date: 2008-11-16
forum: Multimedia Software
---

### Post by Capt Mark on 2008-11-16
Hello everyone,

A couple of weeks ago, I formatted my hard drive and installed Ubuntu Hardy Heron as my operating system. Before I did this, I copied all of my personal documents to a Western Digital External Hard drive. Once I installed Ubuntu, I copied all of my documents and music back onto my hard drive.

Unfortunately, now when I want to play any of my music that was from my external hard drive, Amarok freezes up and can't play the file. The file formats are all .mp3 and I know my sound card works because I can play songs I downloaded post-external drive document copy.

I have all of my music still on the external hard drive so I am not worried about having to delete the ones on my computer. But is this because I am switching operating systems and file systems? And what would people recommend I do to get my music playing again?

Thanks in advance.

---

### Post by cariboo on 2008-11-16
Do you have permission to play the mp3 files? Make sure you are the owner and have at least read permissions. In at terminal cd in to the directory where your mp3s are stored and in the same terminal type:

```
sudo chown -R <user> *
```

and 

```
sudo chmod -R 755 *
```

In the above command <user> is your user name.

Jim

---

### Post by Capt Mark on 2008-11-16
What am I expecting to see if I have permission to play the songs? Right now, this is what the terminal is spitting out when I plug in those commands:

```
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/Anberlin/cities$ ls
01 Debut.mp3
02 Godspeed.mp3
03 Adelaide.mp3
04 A Whisper & A Clamour.mp3
05 The Unwinding Cable Car.mp3
06 There Is No Mathematics To Love A.mp3
07 Hello Alone.mp3
08 Alexithymia.mp3
09 Reclusion.mp3
10 Inevitable.mp3
11 Dismantle. Repair.mp3
12 _fin.mp3
13 Uncanny.mp3
14 There Is A Light That Never Goes.mp3
15 The Promise.mp3
albumart_{17ed4ec3-6e3f-483d-b3a8-673c03ddd5f0}_large.jpg
albumart_{17ed4ec3-6e3f-483d-b3a8-673c03ddd5f0}_small.jpg
albumartsmall.jpg
desktop.ini
folder.jpg
thumbs.db
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/Anberlin/cities$ sudo chown -R mark *
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/Anberlin/cities$ sudo chmod -R 755 *
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/Anberlin/cities$ 


```

---

### Post by Keyper7 on 2008-11-16
Use ls -l instead of just ls. You'll see a list with the following format:

<permissions> <directories> <group> <user> <size> <date> <time> <name>

See is the <user> field corresponds to your current username.

PS: It might take an entire day for me to check your reply to this, but I will.

---

### Post by Capt Mark on 2008-11-16
Alright, I have two examples of the kinds of permission I have. The John Legend album I can play on Amarok and the "The Format" album I cannot play.

Here is the playable album
```
mark@capt-mark:~/Desktop/John Legend - Evolver 2008$ ls -l
total 228540
-rwxr-xr-x 1 mark mark  1883994 2008-11-08 00:25 01  John Legend - Good Morning Intro.mp3
-rwxr-xr-x 1 mark mark 11374802 2008-11-08 00:08 02  John Legend - Green Light [Feat. Andre 3000].mp3
-rwxr-xr-x 1 mark mark 10715472 2008-11-08 00:28 03  John Legend - It's Over [Feat. Kanye West].mp3
-rwxr-xr-x 1 mark mark 11012223 2008-11-08 00:28 04  John Legend - Everybody Knows.mp3
-rwxr-xr-x 1 mark mark  8914068 2008-11-08 00:28 05  John Legend - Quickly [Feat. Brandy].mp3
-rwxr-xr-x 1 mark mark  8124125 2008-11-08 00:27 06  John Legend - Cross The Line.mp3
-rwxr-xr-x 1 mark mark  9570264 2008-11-08 00:28 07  John Legend - No Other Love [Feat. Estelle].mp3
-rwxr-xr-x 1 mark mark 10555602 2008-11-08 00:28 08  John Legend - This Time.mp3
-rwxr-xr-x 1 mark mark 11426002 2008-11-08 00:28 09  John Legend - Satisfaction.mp3
-rwxr-xr-x 1 mark mark  7334182 2008-11-08 00:28 10  John Legend - Take Me Away.mp3
-rwxr-xr-x 1 mark mark  9665349 2008-11-08 00:28 11  John Legend - Good Morning.mp3
-rwxr-xr-x 1 mark mark 11038345 2008-11-08 00:27 12  John Legend - I Love, You Love.mp3
-rwxr-xr-x 1 mark mark 10536399 2008-11-08 00:28 13  John Legend - If You're Out There.mp3
-rwxr-xr-x 1 mark mark 10949571 2008-11-08 00:28 14  John Legend - Can't Be My Lover [Bonus Track].mp3
-rwxr-xr-x 1 mark mark 10397864 2008-11-08 00:28 15  John Legend - It's Over [Teddy Riley Remix] [Bonus Track].mp3
-rwxr-xr-x 1 mark mark   154252 2008-11-08 00:00 John Legend-Evolver [Back].jpg
-rwxr-xr-x 1 mark mark    97529 2008-11-08 00:00 John Legend-Evolver [CD].jpg
-rwxr-xr-x 1 mark mark    79400 2008-11-07 23:59 John Legend-Evolver [Front].jpg
-rwxr-xr-x 1 mark mark 89824840 2008-11-08 00:28 John Legend Ft. Andre 3000 - Greenlight_XviD.avi

```

And here is the nonplayable album:

```
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/The Format/Dog Problems$ ls
01 Matches.mp3     04 She Doesn't Get It.mp3  07 Oceans.mp3    10 The Compromise.mp3
02 I'm Actual.mp3  05 Pick Me Up.mp3          08 Dead End.mp3  11 Inches And Falling.mp3
03 Time Bomb.mp3   06 Dog Problems.mp3        09 Snails.mp3    12 If Work Permits.mp3
mark@capt-mark:~/Documents/My Documents/My Music/iTunes/iTunes Music/The Format/Dog Problems$ ls -l
total 44864
-rwxr-xr-x 1 mark mark 2119908 2007-01-28 22:32 01 Matches.mp3
-rwxr-xr-x 1 mark mark 3669288 2007-01-28 21:20 02 I'm Actual.mp3
-rwxr-xr-x 1 mark mark 3902926 2007-01-28 21:27 03 Time Bomb.mp3
-rwxr-xr-x 1 mark mark 3739522 2007-01-28 21:52 04 She Doesn't Get It.mp3
-rwxr-xr-x 1 mark mark 3664273 2007-01-28 21:34 05 Pick Me Up.mp3
-rwxr-xr-x 1 mark mark 4055069 2007-01-28 21:40 06 Dog Problems.mp3
-rwxr-xr-x 1 mark mark 4646051 2007-01-28 21:47 07 Oceans.mp3
-rwxr-xr-x 1 mark mark 4014101 2007-01-28 21:58 08 Dead End.mp3
-rwxr-xr-x 1 mark mark 4022456 2007-01-28 22:04 09 Snails.mp3
-rwxr-xr-x 1 mark mark 3358335 2007-01-28 22:36 10 The Compromise.mp3
-rwxr-xr-x 1 mark mark 3396377 2007-01-28 22:21 11 Inches And Falling.mp3
-rwxr-xr-x 1 mark mark 5260051 2007-01-28 22:29 12 If Work Permits.mp3

```

unfortunately, I cannot find any difference between the two levels of permission.

---

### Post by mc4man on 2008-11-16
The 'My Documents' in windows will copy to removable media as 'read only' but that would be irrelevant to playback. 
 
How are you trying to load for instance 'Dog Problems' in amarok?

What happens if you r.click on an individual mp3 inside of the folder -> 'open with amarok'

---

### Post by Capt Mark on 2008-11-16
I right clicked the song and it played in Amarok! Brilliant!

Although, now I am not sure why it now plays while before it didn't. Was it the chmod command I typed in before?

Thank you to everyone who helped.

---

### Post by mc4man on 2008-11-17
> Although, now I am not sure why it now plays while before it didn't
Maybe it was a path issue...?

In any event you might wish to set up some r.click options on files and folders for amarok. The default Amarok r. click when amarok isn't open is to open, load and start playback. If amarok is already open then what you r. click on is appended to the playlist.

You can add some variations using 'load', 'queue',and 'append' commands alone or in combo with 'play'.

A very useful one for r. click is amarok --load --play (removes current playlist if any, loads what you r. click on, starts playback.

The r. click menu can be used either from the 'open with', nautilus-actions and or nautilus scripts.
some examples in screen, nautilus actions are in the bottom left panel.

Nautilus scripts based on 'load and play' in screen 2  (clicking on an 'album' (script) loads and plays it

---

### Post by Keyper7 on 2008-11-17
> **Capt Mark said:**
> I right clicked the song and it played in Amarok! Brilliant!

Although, now I am not sure why it now plays while before it didn't. Was it the chmod command I typed in before?

Thank you to everyone who helped.

Did you execute the chmod on all your songs? If not, check the permissions on the ones you didn't to confirm if the chmod was what helped.

---

### Post by Capt Mark on 2008-11-17
Actually, when I first loaded all of my songs onto Amarok, I loaded the songs from the "Load media" command under "Playlist" on the top menu. After taking the advice from this thread, I right-clicked and opened my music through the drop-down menu. Once I loaded my music through the right-click method, I could load an entire library through it's root folder and be able to play it. 

So, I must have mis-understood the capabilities of "Load Media" in Amarok. But opening files through right-clicking and "Open with Amarok" worked perfectly.

---

### Post by Keyper7 on 2008-11-18
So, is everything working as it should now?

---

