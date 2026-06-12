---
title: "Can't connect to an open network"
date: 2009-02-21
forum: Networking &amp; Wireless
---

### Post by skoalman88 on 2009-02-21
I have an open network at my apartment complex (provided by the landlord and we can use it), but I can't connect to it through NM or WICD. Any idea how I go about diagnosing and correcting this? I'm using 8.04 BTW

Edit: I believe obtaining the IP addy is the prob

Thanks

---

### Post by x1101 on 2009-02-22
To trouble shoot if the issue is with the wireless card or with the wireless application, try opening a terminal (Apps->Accessories->Terminal)
and using the following:

*ifconfig* - this will list your network connections and information about them

*iwconfig* - this will list your **wireless** information

This way you can see if you have a wireless card showing up. From there we can assist you in connecting.

---

### Post by skoalman88 on 2009-02-22
I am able to connect to my personal network. I thought there may be an issue with the router since I can't connect to it in XP, OpenSuse, or Ubuntu, but I can connect to it on a vista machine. I should note that the vista machine is using a different wireless than the Ubuntu/OS/XP.

---

### Post by superprash2003 on 2009-02-22
go to the terminal and post output of the following
1)sudo iwlist scanning
2)iwconfig
3)ifconfig

---

### Post by skoalman88 on 2009-03-04
Uploaded. Thanks! BTW I have updated to 8.10 and still have the problem.

---

### Post by x1101 on 2009-03-05
If your (working) vista is using a different wireless than the three (non-working) others, it might be safe to assume that the issue is not with the OS (since you have 2 diff versions on Linux + Win XP). I would try to use the same hardware that you have working in vista with a version of linux to see if it works correctly. If it does then the issue is with the hardware (obviously) and if not then the answer is less clear. This all Assumes that I understand your setup (that being Vista on 1 box, using 1 wireless card and the other OS's on the other using the same non-working wireless)

---

### Post by skoalman88 on 2009-03-05
I can now connect to the wireless in question with 8.10. Please mark as solved. Thanks to those above for their input

---

### Post by xpod on 2009-03-05
> I can now connect to the wireless in question with 8.10. Please mark as solved. Thanks to those above for their input

So what was wrong then?....it might help others with a similar issue;)

---

### Post by skoalman88 on 2009-03-05
I have no idea what was wrong. I switched to 8.10 based on the sticky list of cards and had no problem.

---

### Post by superprash2003 on 2009-03-26
just saw your outputs.. you seem to be connected to linksys. please post your ifconfig output.. you posted iwconfig output 2 times..

---

