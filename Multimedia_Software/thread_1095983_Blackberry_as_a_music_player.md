---
title: "Blackberry as a music player"
date: 2009-03-14
forum: Multimedia Software
---

### Post by slamMaster on 2009-03-14
I'm having an odd problem with my blackberry and I was wondering if anyone else had figured it out.

I'm trying to set up my blackberry to be my music player, but rhythmbox isn't recognizing it.  When I plug it in and select it as a mass storage device then ubuntu recognizes it as such, and I can load music directly into the music file, but I'd like to do it through rhythmbox.  Ubuntu even recognizes it as a portable music device, prompting me to open rhythmbox with that convenient button, but when I press it to launch rhythmbox it doesn't list the device on the left side of the rhythmbox where it's supposed to.

Does anyone have any ideas?  I feel like it's a rhythmbox problem, but I can't figure it out.  I tried messing around with Amarok but it was no use.

Thanks!!

---

### Post by pvicc on 2009-08-12
Last week i installed ubuntu 9.04. I added all the files in synaptic with a word blackberry. After i connected my BB 8900 as Mass storage device, the rhythmbox app came as default and it also listed my BB.
But I could not do barry backup (error!) can not sync my contacts calendar with evolution.

---

### Post by scottaye on 2009-11-23
have you ever figured that one out.  I'm having the same problem and went through the same thing (liked Amarok but to buggy since for KDE).  I'be gotten use to Rhythmbox, but I'm tired of copy and paste work around.

---

### Post by gfunkdave on 2009-11-27
Another request here for help getting the Blackberry to play with RhythmBox.

---

### Post by imyth on 2009-12-08
I've been having this same problem for a while now, i found a pretty simple fix, but i'd love to know if anyone found something better.

my fix:
in a terminal type:
touch /media/BLACKBERRY1/.is_audio_player
touch /media/BLACKBERRY2/.is_audio_player

this creates two empty, hidden files that tell rythembox that the blackberry is an audio player. it worked for me

---

### Post by Kangaroo_Style on 2010-04-26
Anyone else have any success? I tried to upgrade to Rhythmbox 12.8 and hasn't worked. Pretty much this is the only thing that I need to figure out until I will be perfectly happy with Ubuntu.

---

### Post by Kangaroo_Style on 2010-04-26
> **imyth said:**
> I've been having this same problem for a while now, i found a pretty simple fix, but i'd love to know if anyone found something better.

my fix:
in a terminal type:
touch /media/BLACKBERRY1/.is_audio_player
touch /media/BLACKBERRY2/.is_audio_player

this creates two empty, hidden files that tell rythembox that the blackberry is an audio player. it worked for me


This worked in getting it to display, but it's not detecting any of music files on Blackberry2?

---

