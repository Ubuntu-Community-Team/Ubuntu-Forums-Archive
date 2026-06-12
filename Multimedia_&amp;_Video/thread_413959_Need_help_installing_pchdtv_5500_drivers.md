---
title: "Need help installing pchdtv 5500 drivers"
date: 2007-04-19
forum: Multimedia &amp; Video
---

### Post by GREG1292 on 2007-04-19
I have been playing with 6.10 for a while now and know just enough to be considered semi-dangerous!!

I want to install drivers from a tar.gz and need help or a point to a thread on how to do this. I have read and googled and searched to no avail.:confused:  I just want to watch qam tv with mythtv but can't get past of installing the drivers.

Thanks Greg

---

### Post by superm1 on 2007-04-19
I believe that is one of the cards using the cx88_dvb driver.  Quoting the MythTV guide (From Feisty)
[LIST]
[*] **HD5500** - *supported but with module issues* 
[LIST]
[*]  The cx88_dvb module is not loaded on boot.  modprobe and add cx88_dvb to /etc/modules to fix this:  
 $ sudo sh -c "echo "cx88_dvb" >> /etc/modules"[/LIST] [/LIST]

---

### Post by GREG1292 on 2007-04-26
I have been enjoying a MYTHTV box for about 4 days now my first one and it is :guitar: . I have the dvd,dvb off air hd,web browser and everything runs smooth.

 I want to install a second tuner for qam tuning for Comcast cable and am stuck on this driver download for a Tar.gz and install.:confused:  Do I need to create a directory to extract it in? I will be using a second PCHDTV  5500. Better yet is there a complete how to link for newbies.


Thanks Greg

---

### Post by superm1 on 2007-04-26
> **GREG1292 said:**
> I have been enjoying a MYTHTV box for about 4 days now my first one and it is :guitar: . I have the dvd,dvb off air hd,web browser and everything runs smooth.

 I want to install a second tuner for qam tuning for Comcast cable and am stuck on this driver download for a Tar.gz and install.:confused:  Do I need to create a directory to extract it in? I will be using a second PCHDTV  5500. Better yet is there a complete how to link for newbies.


Thanks Greg
No needs to change anything if your just adding a second tuner.

---

