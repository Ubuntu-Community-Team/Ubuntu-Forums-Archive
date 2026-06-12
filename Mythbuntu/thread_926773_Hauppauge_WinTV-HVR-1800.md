---
title: "Hauppauge WinTV-HVR-1800"
date: 2008-09-22
forum: Mythbuntu
---

### Post by Shmifty on 2008-09-22
Will this tuner run well with Mythbuntu/MythTV? I'm a novice when it comes to TV tuners and I don't want to waste money on a product that won't work well (or not at all).

---

### Post by OffAxis on 2008-09-22
[http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800](http://www.mythtv.org/wiki/index.php/Hauppauge_HVR-1800)

> The HVR-1800 works with the latest v4l-dvb drivers. (Choose DVB for the card type in your capture card setup).

Only Digital (ATSC/QAM) works; NTSC does not yet work.

Choose "Windows Media Centre Remotes (new version Philips et al.)" in your lirc setup to get the bundled remote working. My remote says "RC 6" on the back. 

---

### Post by Shmifty on 2008-09-22
I'm guessing the lack of NTSC would be a problem for me since I live in the US (I currently don't have digital cable where I live).

---

### Post by OffAxis on 2008-09-23
You would still be able to receive ATSC channels that are broadcast in your area, and come February, the rest of 'em (except for low-power local ones).

---

### Post by DemonBob on 2008-09-24
The developer of the driver, has stated that when he gets a PCIx development system he will take a look at the analouge problems that people are having with this board. At the moment it's kinda hit and miss.

When i get time, probably later this week. I'm going to partition my Mythbox and install 8.10 on it with kernel 2.6.27, and try to get it working. I've already talked to the developer, and i'm willing to dive into the code to try to figure out the problem. The support is thier for NTSC, it just has issues.

---

### Post by Robstarusa on 2008-09-25
> **DemonBob said:**
> The developer of the driver, has stated that when he gets a PCIx development system he will take a look at the analouge problems that people are having with this board. At the moment it's kinda hit and miss.

When i get time, probably later this week. I'm going to partition my Mythbox and install 8.10 on it with kernel 2.6.27, and try to get it working. I've already talked to the developer, and i'm willing to dive into the code to try to figure out the problem. The support is thier for NTSC, it just has issues.

Analog is definitely broken.  I will post tonight with a screenshot of what I am seeing.

---

### Post by steve04 on 2008-10-23
Any updates to this yet?  I just bought the HVR-1800 and am currently using Windows Media Center (Vista).  I would prefer to use MythTV but I only get analog signal from my cable company.  I don't want to install Mythbunta if my card won't be able to receive signals.. :-(  Any suggestions for another good Linux based tv tuner program ?

---

