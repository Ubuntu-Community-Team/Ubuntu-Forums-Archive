---
title: "To fglrx or to not fglrx"
date: 2007-12-20
forum: Multimedia &amp; Video
---

### Post by Burkey on 2007-12-20
I presently have Gutsy running on my laptop with the 7.11 fglrx driver installed manually.  I get some odd behaviour at time (World or Warcraft runs ok once, then choppy next time.. restarted X fixes it) so am considering going back to the ubuntu packaged version.

I want to reduce maintenance and perhaps normalise the install a little.  What version is the driver that comes through apt-get?  Is it current or even close to current?

Anyone else got advice on using these drivers in Ubuntu?

---

### Post by grogger13 on 2007-12-20
i switched to the 7.11 version and followed a tutorial and it screwed my whole graphics card up. still looking on how to fix it.  How would you uninstall the one driver and put the other driver in

---

### Post by acoustibop on 2007-12-20
The driver that the Restricted Driver Manager installs ATM is the 8.37.6 one, Burkey.  The Restricted Driver Manager is the best (and easiest) way of installing the repository driver.

I have two Gutsy installations on this machine; one runs the 8.37.6 driver and one runs the current 7.11 driver.  I have to say I've never had problems with either.  FWIW, for installing drivers more recent than the repository version, I've always used the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") method: recommended.

---

