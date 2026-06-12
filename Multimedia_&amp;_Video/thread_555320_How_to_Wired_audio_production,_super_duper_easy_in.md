---
title: "How to: Wired audio production, super duper easy install."
date: 2007-09-20
forum: Multimedia &amp; Video
---

### Post by pixeltarian on 2007-09-20
I have loads of trouble installing wired (music production software). so here's what I did:

1. from terminal window enter these two commands (taken from ubuntu studio's website): 

> sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'

wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

2. run synaptic (from terminal: sudo synaptic)

3. search for "wired" 

4. mark for installation

5. enjoy!

---

### Post by trueclearlight on 2007-10-21
Thank you! I finally managed to get wired installed and running in a few minutes after reading your post (had previously spent the best part of half a day getting nowhere) :)

---

