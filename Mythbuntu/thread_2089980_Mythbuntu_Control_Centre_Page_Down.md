---
title: "Mythbuntu Control Centre Page Down"
date: 2012-11-30
forum: Mythbuntu
---

### Post by brianafischer on 2012-11-30
I just installed a fresh copy of 12.04 on my home desktop.  Unfortunately, it looks like the MythBuntu Control Centre repo page is down (returns page not found):

[http://www.mythbuntu.org/download/getmythbuntu.php](http://www.mythbuntu.org/download/getmythbuntu.php)

Is there a way to install this?  I am guessing this just automates the install of a PPA?

---

### Post by dannyboy79 on 2012-11-30
it says to email him at [email]tgm4883 (AT) mythbuntu.org[/email] if something with the new site isn't working

---

### Post by brianafischer on 2012-11-30
So to answer my questions after some better googling:

> sudo add-apt-repository ppa:mythbuntu/0.26
sudo apt-get update
sudo apt-get install mythbuntu-control-centre

---

