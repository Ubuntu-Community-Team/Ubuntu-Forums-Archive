---
title: "error on exiting mythtv-setup"
date: 2008-10-01
forum: Mythbuntu
---

### Post by sdowney717 on 2008-10-01
Card1 (type composite1) is set to start on channel Please add, which does not exist

Card1 (type S-video1) is set to start on channel Please add, which does not exist

Do you want to fix these problems?

selecting yes does not fix the problem, select no exits and whentrying to watch TV, I get a black screen.

this is a avc-2010 capture card with svideo and composite inputs
the card is working with VLC streaming

---

### Post by stevanbt on 2008-10-01
Hi,
I assume you've scanned for channels and that setup has retrieved the channels ok.  You need to go into Input Connections (I think that's what it's called) and tell setup which channel the card should start on.

Thanks, Steve.

---

### Post by sdowney717 on 2008-10-01
well the problem is, this is not a tuner card.
But supposedly this is supported in mythtv.

It is a video capture card only.
All it does is take either svideo or composite input with left and right audio.

Anyway I can use VLC to capture the stream and even record a show from a vcr tuner.

Do you think this issue of a channel setting is stopping it from working?
Any I dont see how you would set a channel

[http://gentoo-wiki.com/HARDWARE_Setup_MythTV](http://gentoo-wiki.com/HARDWARE_Setup_MythTV)

this is my capture card

[http://linuxtv.org/v4lwiki/index.php/Ivtv_devices_(cx23415%2C_cx23416](http://linuxtv.org/v4lwiki/index.php/Ivtv_devices_(cx23415%2C_cx23416))

```

05:0a.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)



```

---

### Post by gcummins on 2009-03-13
I am experiencing the same problem with a Brooktree BT848 capture card. Did you find a workaround?

---

### Post by vancheese on 2009-12-28
Was this ever resolved?

---

### Post by sdowney717 on 2009-12-29
no, I never did figure it out.
I simply use VLC to open the card
and I can record using vlc, select advanced controls and you get a red record button

---

### Post by vancheese on 2009-12-30
I asked this question on the mythtv-users forum
Here is the response 

[http://www.gossamer-threads.com/lists/mythtv/users/414967](http://www.gossamer-threads.com/lists/mythtv/users/414967)

---

