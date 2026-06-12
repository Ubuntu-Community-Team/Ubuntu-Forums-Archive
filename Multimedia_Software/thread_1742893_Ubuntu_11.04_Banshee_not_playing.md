---
title: "Ubuntu 11.04 Banshee not playing"
date: 2011-04-29
forum: Multimedia Software
---

### Post by nicki20048 on 2011-04-29
I have just installed 11.04 but Banshee will not play any songs. I have all the codecs installed but when I try to play a song nothing happens, the song doesn't even start.

Anybody else having the same problem?

---

### Post by snappy90 on 2011-04-29
I have the same problem I have found that if I open it from file manager in banshee it will work but it wont work from the banshee library.
anybody got any ideas ???

---

### Post by cpcmike on 2011-04-29
I have this problem. I upgraded to 11.04 from 10.10 with the "upgrade" button. Banshee will not import any songs, but I can open them directly via open location. I tried the Rythmbox import option.

---

### Post by nicki20048 on 2011-04-29
I will allow me to import songs but nothing will play from the library.

Like above, if I open a song from nautilus it will play but not otherwise

---

### Post by StevenSteavis on 2011-04-30
I have the same problem. Yesterday it worked.. today nothing.

I've had one problem after the other since upgrading to 11.04.. wish I stayed at 10.10.

---

### Post by nicki20048 on 2011-05-01
Anybody with any ideas?

---

### Post by dpwilson on 2011-05-02
Same problem here, can play by going through nautilus, but nothing when opening banshee and trying to play.

---

### Post by b3organ on 2011-05-03
I had Rhythmbox as a default player in previous version and everything worked. As I installed the newest version (of Ubuntu) Banshee refused to play mp3-files. I tested Rhythmbox again and it worked and when Rhythmbox was playing I opened Banshee and pressed "play" and "voila". Since then Banshee has worked as it should. No need to "wake" it with RB.

---

### Post by stuart221 on 2011-05-04
I have the same problem!

---

### Post by owennewo on 2011-05-04
I had a problem today was similar, banshee (and rhythmbox) would not play any flac, mp3 or ogg track.  I would press play and nothing happened - the track progress did not move

In my case I was also running a java application that uses javax.sound (jmf) - this must have had some lock on the sound stack - because as soon as I stopped this application, banshee started playing.

Most modern linux applications will happily play at the same time - however if I start this java application before hand it causes problems.

It would  be useful if banshee put some message in the logs the reason for why it's not playing - e.g. being blocked, missing codecs, etc as I suspect there are numerous reasons why it doesn't play.

Owen

---

### Post by lidex on 2011-05-04
Try opening with Alt+F2 run dialog. Type banshee and hit enter. If that works try changing the command line for your launcher.

---

### Post by nicki20048 on 2011-05-05
> **lidex said:**
> Try opening with Alt+F2 run dialog. Type banshee and hit enter. If that works try changing the command line for your launcher.

Doesn't work for me i'm afraid. Banshee opens up ok but won't play any songs from the library

---

### Post by Alien.col on 2011-05-06
Had a similar problem, i added a large library and banshee wouldn't play while downloading the cover art. Had to clear everything from the library (right-click) and add a dozen of songs at a time to get it to work.

---

### Post by nicki20048 on 2011-05-06
> **Alien.col said:**
> Had a similar problem, i added a large library and banshee wouldn't play while downloading the cover art. Had to clear everything from the library (right-click) and add a dozen of songs at a time to get it to work.

Spot on, worked for me

Thanks :D

---

### Post by cheesekiller on 2011-05-08
yesterday banshee played music today it plays nothing when i hit play its completely useless....  on a different computer i have it crashes when i go to import music....   why did they default a media player that has waaaaaaay to many bugs?

---

### Post by abisdad on 2011-05-18
Hi - [COLOR="Red"][SIZE="4"]SOOOOO FRUSTRATING!!!!![/SIZE][/COLOR]

Working fine last time. Open Banshee up, select a song, hit play....

](*,)     :sad:

[COLOR="Red"][SIZE="4"]AND NOTHING HAPPENS![/SIZE][/COLOR]  No error message, nothing - just sits there...

[SIZE="4"][COLOR="Blue"]Solution to my issue...[/COLOR][/SIZE]

[COLOR="Blue"]I was playing tracks that are on my Win7 partition (or volume)...  so I mounted my Win7 by clicking on the Home Folder, then clicking on my Win7 partition, which then appears on my desktop.  Click play, and SUCCESS!:guitar::-({|==D>[/COLOR]

Hope this helps some of you,

Rob.

---

### Post by Jimmybe on 2011-05-19
Hi,

I had the same problem today.

My music is located on my 2nd hard disk. I opened it with Nautilus. The disk icon appeared as mounted on my desktop. It worked fine for me afterwards. I was able to play all songs again.

Jimmy

---

### Post by lidex on 2011-05-19
Wow, I'm sorry, I assumed you would mount a disk before trying to access data from it.

---

### Post by abisdad on 2011-05-20
> **lidex said:**
> Wow, I'm sorry, I assumed you would mount a disk before trying to access data from it.
=; Hey - most people have a life... 

So most people don't even know what [COLOR="Blue"]"mounting a disk"[/COLOR] means in this context, therefore it is reasonable to expect well written software to display some kind of feedback to the user when something don't work right... #-o

:?: Can the others who posted give some constructive feedback as to whether this is the cause of their problem, and if the general consensus is that it is, then it needs to be marked as solved.

Thanks,

Rob.

---

### Post by jeisonsj on 2011-07-02
Hello everybody! It's my first post, and i hope its helpfull.
Verify if the source disk of your music library is mounted. I solved the same problem mounting my "Data:" partition, and now its playing normally. :D

---

### Post by James! on 2011-07-02
All of you installed the proper files and drivers for Banshee? Because I had the same problem, and then I installed the drivers for Banshee, for a second it didn't play, and i restarted the program and it works like a charm... I would say either restart the program, and if that doesn't work, restart your computer.

---

### Post by Luke M on 2011-07-03
This one bit me too...the music was on an NTFS volume which apparently isn't automatically mounted, and Banshee just sits there stupidly, not playing and not giving any error message.

---

### Post by DrJohn999 on 2011-07-04
I had mixed success at first on my desktop PC. My media files are located on an external nfs automount share, on a system that runs Mythbuntu. After upgrading the desktop PC in-place from 10.10 to 11.04, I ran Banshee and started to import the Music folder under the nfs share. No problem finding the files, I didn't have to go outside Banshee to trigger the automount -- it just worked. I had switched from an nfs share mounted in fstab last year: the system would hang during boot when it attempted to statically mount the nfs share whenever the nfs share server (the Mythbuntu system) wasn't up for some reason. More information on autofs is found here: [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)
 
However, Banshee became quite busy at first importing album art. Banshee played OK while this was going on, but was slow to get the the next track in shuffle mode or when directly clicking on the next track button. Also some hesitation when moving the Banshee window.

After album art import seemed to be done I found that the Banshee task was reporting 100% for its CPU. There is no 'Exit' item in the menu, just close, but Alt-F4 did cause it to quit. Restarting from the notification Speaker icon worked fine. Media keyboard play / stop / next buttons are mapped correctly by default. No problems now...

---

### Post by flipper T on 2011-07-21
this has just happened to me too. banshee working fine 1 hour ago, not playing anything now.

in my case i have found the solution:

i had vlc playing a dvd at the time. i opened banshee....no play

closed vlc, banshee working fine again


no idea why this is happening (or for that matter, why anyone would want to be playing a dvd and listening to banshee at same time)...but it did


...on second thought, if you were watching a movie and listening to a commentary from banshee, then you would.

---

### Post by Busarow on 2011-08-01
> **Luke M said:**
> This one bit me too...the music was on an NTFS volume which apparently isn't automatically mounted, and Banshee just sits there stupidly, not playing and not giving any error message.

  This worked for me. Make sure the volume that your music is located on is MOUNTED. DOH!

---

### Post by Vyodacoda on 2011-08-07
Hi All
I have a problem with Banshee where if I go into nautilus and double click the File Banshee will open up but nothing plays. This does seem similar to the earlier posts here. However I find that if I go and right click the file, select "Open With"  and then select Banshee it does seem to play o.k. Hope that helps!

---

### Post by DrGonzo94 on 2011-08-19
I experienced this issue when I manually edited fstab to automount the ntfs volume where I keep my music files. When I mount it manually, Banshee plays fine.

---

