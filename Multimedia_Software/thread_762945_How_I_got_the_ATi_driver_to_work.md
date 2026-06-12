---
title: "How I got the ATi driver to work"
date: 2008-04-22
forum: Multimedia Software
---

### Post by white_eagle-mk on 2008-04-22
Simply I used [this]("http://ubuntuforums.org/showthread.php?t=589637") guide, but with the latest drivers from ati.amd.com and I got 3D acceleration to work with my ATi Xpress 200m Series integrated graphics card to work (64 MB) ... Simple enough...

---

### Post by morrie on 2009-10-13
I tired that with my Radeon X1650 and got an unviewable screen at startup; had to start over.

---

### Post by doas777 on 2009-10-13
I just download teh driver from ati.com. and then run it from a terminal. usually works fine for me. just gotta make sure you have the build-essentials and kernel headers installed first.

---

### Post by morrie on 2009-10-13
The Open source driver seems to work fine,  was just troubleshoooting why it fades in games or some movies (without screensaver or power saving on)?  So I found all this stuff abot the ATi driver (which makes sense- I thnk it was the same way wiht Windows).

That's what I did.  I even searched through my synaptic for each item in the article's list, even though it appears that Ubuntu 9.04 Jaunty has them all.  I don't know if there is anything else to try.  I have read that others with the Radeon1600 had this problem.  I was wondering if anyone else with this card (Radeon x1650) got it working?  (Mine is a Sapphire AGP 512 MB model).  

Open Source Driver Symptom: fades (like sleeping) dutring movies - doesn't come back.  Also, breaks into static color pattern during games (like Urban Teror) (after about 10-20 minutes for both) unrecoverable graphic crash. (i will post this problem in the appropriate forum).

---

### Post by fox.esq on 2009-10-30
> **morrie said:**
> I tired that with my Radeon X1650 and got an unviewable screen at startup; had to start over.

How do you get a viewable screen to return? I have the same problem after installing the ATI driver.  I also have a Radeon X1650.  I have a bunch of data on that disk and don't want to have to delete it, and I have no other way to access it except by Ubuntu.  I'm running 9.04 btw.

---

### Post by claymater on 2009-10-30
In synaptic if you search ATI you will find some xserver drivers... I have 3D with thos! works great! ;)

---

