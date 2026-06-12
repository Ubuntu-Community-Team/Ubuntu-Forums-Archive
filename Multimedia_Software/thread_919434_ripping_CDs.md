---
title: "ripping CDs"
date: 2008-09-14
forum: Multimedia Software
---

### Post by cpatton90 on 2008-09-14
I'm not sure whether this topic has been discussed or not; to be honest, I have no idea what to search for. In any case, here is my question: 
I have a CD of a symphony by Gustav Mahler that is written in 4 movements. However, the CD is split into I think something like 19 tracks. I was wondering if there was something in the ubuntu repository (or anywhere else) that would combine selected tracks into a single mp3. So instead of having 5 mp3s for the first movement, I have 1 mp3 for the first movement. The reason I care is that the splits between the tracks are pretty noticeable when listening. 

Does anyone know of a piece of software that will allow me to combine tracks? I apologize if this topic was previously discussed. 

Thanks for any help!
Chris

---

### Post by wowbuts5 on 2008-09-14
[world of warcraft gold](http://veryge.com/) Don't miss those.Here are some tips that we hope will give you a better experience in Alterac Valley. Buy world of warcraft gold, This is a very involved Battleground and it can take time to learn how everything worksDon't miss those.Here are some tips that we hope will give you a better experience in Alterac Valley. Buy [world of warcraft gold](http://veryge.com/), This is a very involved Battleground and it can take time to learn how everything works [ffxi gil](http://veryge.com/)

---

### Post by mc4man on 2008-09-14
This may not be what you want but does work well and very fast.
At first I thought it was going to be a pita but it's actually is very easy. The app is called mp3wrap.

Requires the tracks to already be ripped and encoded as .mp3's in a folder

Grip, xripper, rubyripper all work fine for that. (ripping and encoding to a single folder.

Ex.
I have a folder - Derek And The Dominos (1970) Layla And Other Assorted Love Songs

Simply cd to that folder and run command (red is a variable (name of new mp3

```
 mp3wrap [COLOR="Red"]derek[/COLOR].mp3 *.mp3
```

> doug@doug-desktop:~/mp3/Derek And The Dominos (1970) Layla And Other Assorted Love Songs$  mp3wrap derek.mp3 *.mp3
Mp3Wrap Version 0.5 (2003/Jan/16). See README and COPYING for more!
Written and copyrights by Matteo Trotta - <matteo.trotta@lib.unimib.it>
THIS SOFTWARE COMES WITH ABSOLUTELY NO WARRANTY! USE AT YOUR OWN RISK!

  7 %	--> Wrapping 01 - I Looked Away.mp3 ... OK
  14 %	--> Wrapping 02 - Bell Bottom Blues.mp3 ... OK
  21 %	--> Wrapping 03 - Keep On Growing.mp3 ... OK
  28 %	--> Wrapping 04 - Nobody Knows You When You're Down And Out.mp3 ... OK
  35 %	--> Wrapping 05 - I Am Yours.mp3 ... OK
  42 %	--> Wrapping 06 - Anyday.mp3 ... OK
  50 %	--> Wrapping 07 - Key To The Highway.mp3 ... OK
  57 %	--> Wrapping 08 - Tell The Truth.mp3 ... OK
  64 %	--> Wrapping 09 - Why Does Love Got To Be So Sad.mp3 ... OK
  71 %	--> Wrapping 10 - Have You Ever Loved A Woman.mp3 ... OK
  78 %	--> Wrapping 11 - Little Wing.mp3 ... OK
  85 %	--> Wrapping 12 - It's Too Late.mp3 ... OK
  92 %	--> Wrapping 13 - Layla.mp3 ... OK
  100 %	--> Wrapping 14 - Thorn Tree In The Garden.mp3 ... OK

  Calculating CRC, please wait... OK

derek_MP3WRAP.mp3 has been created successfully!


Takes just a few seconds (*the only thing you need to type in the whole process is the name of the new mp3* (what's in red

To install run this, I'm suggesting you also install nautilus-open-terminal. It makes cd'ing to a directory very easy, just right click on it and choose 'open in terminal'  (eliminates path issues with oddly named folders.

To split an album into a couple of mp3's make temp folders, copy the tracks wanted into each, cd, ect. and then you can delete the temps after removing new mp3. Ordering of tracks appears to be on how listed, not sure though most rippers will number them.

```
sudo apt-get install mp3wrap nautilus-open-terminal
```

---

### Post by mc4man on 2008-09-14
duplicated?

---

### Post by FrankVdb on 2008-09-14
Rename the mp3 file names to e.g. file1.mp3 file2.mp3 file3.mp3 etc.

Assuming you want to combine these files into one movement, you could run the following command from a terminal:

cat file* > movement.mp3

---

### Post by FrankVdb on 2008-09-14
Rename the mp3 file names to e.g. file1.mp3 file2.mp3 file3.mp3 etc.

Assuming you want to combine these files into one movement, you could run the following command from a terminal:

cat file* > movement.mp3

---

### Post by petronell on 2008-09-14
From memory I think Audacity will allow you to load up all five source mp3s and then cut and paste them into a new long mp3.

It is in the repos goto terminal and type:-

sudo apt-get install audacity

It was quite simple when I used is some time ago to cut up one big mp3 into three shorter mp3s.

Good luck,

daveR

---

### Post by cpatton90 on 2008-09-14
Thanks all, both are very simple situations that worked great. I don't know why I didn't think of the 'cat' command- thanks a lot!

---

