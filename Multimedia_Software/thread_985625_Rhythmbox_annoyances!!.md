---
title: "Rhythmbox annoyances!!"
date: 2008-11-17
forum: Multimedia Software
---

### Post by ratdog on 2008-11-17
Hello there!
I am using UbuntuStudio 64 Hardy Heron.
I am having some annoying problems with Rhythmbox.

Problem 1:
I have my music collection stored on a drive other than my home drive.  In order for Rhythmbox to find my music, I must first browse to that drive under 'Places'.  If I don't, Rhythmbox scans for my music and doesn't find anything and I watch the songs listed in the music collection countdown to zero as it searches for each one.  Is there a way to get Rhythmbox to know that drive exists without me accessing it first?

Problem 2:
Often times when music is playing, Rhythmbox will hang at the end of a song.  It doesn't really crash or freeze the computer, it just sits there at the point where it should go to the next song and I have to come over and hit the next button once or twice.  Really annoying when I'm trying to get some work done around the house and have to come back to the computer every song.  It seems to do it pretty randomly.  Sometimes it does it a few songs in a row on one album and then plays the rest of the album fine, but overall I'd say it does it about 1/3 of the time.

Thanks for any help!

---

### Post by Arup on 2008-11-17
I have the same situation, I have all my music on a different partition, the solution is to automount the partition at boot and then Rythmbox will see your files. As for your second issue, I face the same from time to time specially when I change radio stations etc.

---

### Post by ratdog on 2008-11-18
So I guess the next question...

How would I automount that partition?

---

### Post by ratdog on 2008-11-18
bump bump

anyone else?

---

### Post by SR_ELPIRATA on 2008-12-28
Other annoyances:

In 8.10, just last nite, I somehow double clicked on the radio list, no clue where, but all default radio stations have disappeared.

In 7.10 I had music playing and wrongly, again, hit a button and after that, no matter how many times you would open the program again... it played at slow motion, you know, the inverse of having the Beatles singing with Chipmunk voices. Since I was unable to fix it I dont think its a good idea to try and recreate the issue :)

---

### Post by ushimitsudoki on 2008-12-28
ratdog,

You'll need to edit */etc/fstab*. Check out the man pages for mount and fstab. Pay attention to the mount options there - you will want "defaults" or "auto" and additional options.("default" includes "auto" and several other common options)

Also, run "mount" while the device is mounted to see how it is mounted by the system, so you can get some of the information you will need that way, like the device and mount point and options the system chose.

---

### Post by rbringh on 2008-12-28
Auto mounting is a pain to me. If done wrong the drive just disappears. Here is what I did. Mount the drive by double clicking or right click and select "mount". Once mounted enter this in a terminal session.

sudo gedit /etc/mtab

the last line should be the last drive you manually mounted. the line will look similar to this  /dev/sda1 /media/Data/ ext3 rw,nousid,nodev,uhelper=hal 0 0

Copy the text of that line, close file then...

in the terminal session enter

sudo gedit /etc/fstab

paste the text into a new line at the end of the file.

Save file. On next reboot drive should auto mount.
No guarantees but it worked for me.

Should problems occur remove pasted line and save file.

---

### Post by jacob01 on 2008-12-28
one of my annoyances are that once in a while two songs will start to paly at the same time and i can only control one but then when i skip to the next song both stop and the new one starts to play. The second annoyance is random crashes. Besides those 2 thinks it works great for me.

---

### Post by Ketusmondai on 2010-01-15
I have the same problem as jacob01. I've only really noticed it since installing 9.10.
It is quite a frequent and annoying problem and I am considering using another program. Any suggestions?

---

