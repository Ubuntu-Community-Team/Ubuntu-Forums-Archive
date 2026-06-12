---
title: "pvr 500 only 1 tuner working"
date: 2008-01-01
forum: Mythbuntu
---

### Post by taehC on 2008-01-01
I have the pvr 500 dual tuner card but when a show is recording mythtv won't let me watch tv even though only 1 show is recording and i can't find where the watch the currently recording show.  Can anyone help?

---

### Post by axelsvag on 2008-01-01
Can you change tuner with the "Y" keyboard command while watching tv, without recording applied?

---

### Post by taehC on 2008-01-01
no i cant

---

### Post by axelsvag on 2008-01-01
Have you configured both video0 and video1 in mythbackend?

---

### Post by taehC on 2008-01-01
No i dont.  Do i configure them under capture cards?  When i try to do it under capture cards and try to make a new capture card it doesn't let me select tuner 2 as the input

---

### Post by taehC on 2008-01-01
anyone?

---

### Post by Tteddo on 2008-01-01
> **taehC said:**
> No i dont.  Do i configure them under capture cards?  When i try to do it under capture cards and try to make a new capture card it doesn't let me select tuner 2 as the input

If I remember right when I set my 500 up you still select tuner 1 as the video source for video0 and video 1 both, the card sorts it out for you.

---

### Post by taehC on 2008-01-01
i just tried that and when i hit Y on the keyboard when i am watching tv it doesn't change to tuner 2

---

### Post by taehC on 2008-01-01
And when i try to set 1 of the video devices as video0 instead of video1 once i finish it and go back to look at it it says video1 again.  in other words it keeps changing it back to video1
do i need to add another video source or just add another capture card?

---

### Post by taehC on 2008-01-01
ok i just setup in the backend like there are 2 cards but they were both only having tuner 1 as the tuner, and when i watch tv and hit y it switches between saying 
4: Tuner 1
and
5: Tuner 1
anyone help?

---

### Post by Tteddo on 2008-01-01
Ok, I just looked and on mine I have 2 capture cards setup  /dev/video0 and /dev/video1. The first one has /dev/video0 as the Video device, and the default input is Tuner1. The second has /dev/video1 as the Video device and Tuner1 (still) as the default input.
For probed info, the first says WinTV PVR 500(unit #1) and the second has WinTV PVR 500#unit2).

---

### Post by taehC on 2008-01-01
OH!  I see what the problem was.  i have a webcam plugged it and it is taking up /dev/video0 so i needed to setup the capture cards as video1 and video_2_
thanks tteddo

---

### Post by Tteddo on 2008-01-01
You are welcome!!
Happy new Year!

---

### Post by aaltieri on 2008-01-02
if the IVTV module is loading correctly, you should see TWO seperate tuners, most likely on 

/dev/video0
/dev/video1

setup both using tuner1.  Essentially, the computer will see it as two seperate tuner cards, each having a "Tuner 1"

after that, make sure you setup the inputs for the card as well!

Edit --Sorry...didn't see the second page of posts.  Ignore me.

---

