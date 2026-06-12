---
title: "Installing a second tuner card"
date: 2009-12-09
forum: Mythbuntu
---

### Post by benlyboy on 2009-12-09
I am building a system as a stand alone (front end, back end) dvr and plan is to have two tuner card. however as of now I only have the one card. What I want to know is how hard is to add a second card to a system once it is up and running?

Would I be better to to wait till I had the second tuner before installing Mythbuntu

---

### Post by matt06 on 2009-12-09
Adding an additional tuner should be as simple as plugging the card in, making sure it's detected properly, and then going into the Backend Setup to add it there.

---

### Post by azmyth on 2009-12-09
It really is simple. You just have to remember to tie the tuner with a video source which I forget. I'd probably setup udev rules so when you get your second tuner you won't have to worry about the video0 and video1 swapping on you.

---

### Post by gwagchunks on 2009-12-10
I added a second TD-500 card to my box yesterday. I just installed the card, booted, went into setup from mythbuntu control center. Selected the option for capture cards and it was detected. Like azmyth said, remember to add your video source to it. Good Luck.

---

### Post by Caps18 on 2009-12-10
It isn't that hard, but it is worth it.

---

### Post by schwinn on 2009-12-10
There's a nice script here [http://ubuntuforums.org/showthread.php?t=753434](http://ubuntuforums.org/showthread.php?t=753434) to help simplify the creation of the udev rules. Isn't working for my pcHDTV card, but works fine for the PVR150 card.

If you don't set this up, you could swap video0/video1 here and there, and cause yourself problems later on... best to just do it right the first time :)

---

### Post by benlyboy on 2009-12-11
Hy guys

Thanks for the replys, helps a lot 

sorry it took me a while to get back on here but i was away and only just got home.

---

