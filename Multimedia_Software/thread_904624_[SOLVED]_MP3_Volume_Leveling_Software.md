---
title: "[SOLVED] MP3 Volume Leveling Software?"
date: 2008-08-29
forum: Multimedia Software
---

### Post by iheartubuntu on 2008-08-29
Im trying to dump about 100 mp3 songs onto a disc, but Ive collected them over the past several years and they all have different volume levels. Is there any software out there for quick volume leveling? OK, any volume leveling? Many thanks!

---

### Post by djRobbieF on 2008-08-29
Are you burning this as CDA?  Or putting the MP3s directly on the disc as MP3s?

If you are indeed wanting to do an audio CD (playable in a standard CD player), I recommend using K3B.

Install K3B from the repositories, but don't open it when it's done.

When done, install libk3b-extracodecs

If you like, you can do this by typing:  sudo apt-get install libk3b-extracodecs

That gives you MP3 ability in K3B.

Now, create your CD track list as an Audio CD.

When you push BURN, choose the "Advanced" tab and check off "Normalize Volume Levels".

That's probably the quickest and easiest way, IMO.

If, on the other hand, you want to actually normalize the FILES, install the program "mp3gain" in the repositories.

---

### Post by iheartubuntu on 2008-08-30
Thanks for the info on MP3gain... it led me to this..

[http://sourceforge.net/projects/easymp3gain/](http://sourceforge.net/projects/easymp3gain/)

which someone created a deb package for easy install and GUI!

---

### Post by djRobbieF on 2008-09-04
Beautiful.  Glad I could help  :)

---

