---
title: "Integrated Web Cam problem"
date: 2009-09-04
forum: Multimedia Software
---

### Post by LinScape on 2009-09-04
Hi, i need help on getting my webcam work on ubuntu. The problem is that when i want to record a video with a program called cheese the webcam gets crazy and lags. Plus I tried to configure g-streamer but nothing fixed the problem. please some one help.

---

### Post by LinScape on 2009-09-15
Problem is that when i try recording a video Cheese starts to lag and can't record properly. I Read the FAQ here [http://live.gnome.org/Cheese/FAQ#head-6abe11f90b76e30835cd8dc8b40c7e35777ace4a](http://live.gnome.org/Cheese/FAQ#head-6abe11f90b76e30835cd8dc8b40c7e35777ace4a)  and it says that "You may have set "ximagesink" (X Window System (No Xv)) as video-output. This means, that your cpu is doing all the work. Change it to "xvimagesink" (X Window System (X11/XShm/Xv)) in order to let your graphics card do the work."  but i already configured g-streamer properly but the problem is still there and i need help, can someone help me?

---

### Post by no2498 on 2009-09-20
find and install wxcam

---

### Post by LinScape on 2009-09-29
I fixed the problem but now i need cheese to record the sounb but i don't now how to do that. Can someone help me?

---

### Post by LinScape on 2010-05-05
thanks but i fixed the problem now.

---

### Post by stevepaul on 2010-05-10
@Linscape

It would be helpful to others if you were to post your solution ...

---

### Post by LinScape on 2010-06-15
It seems that i had to change the sound configuration in System -> preferences -> sound in my case all i had to do was to change the profile to: Analog Surround 4.0 Output and any application that record sounds would record the output of the sound card.

---

### Post by LinScape on 2010-06-17
oops... wrong solution (sorry i was thinking of another problem i had.)
all i had to was go to preferences -> sound
and unmute the input and change it to (line-in)
and it would record the outside sound.

---

