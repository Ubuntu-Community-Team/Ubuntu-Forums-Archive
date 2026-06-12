---
title: "can't access to Windows 7 anymore"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by taekr on 2010-05-29
Hi

I have been using Ubuntu 10.04 for few days... 

Out of the box, amazingly I was able to access to Windows 7.

in Nautilus, I could see windows 7 and could access to folders shared by Windows 7. 

Oh... I tested... copied 10GB file (Windows 7 machine is connected to the router wireless...  and Ubuntu machine is wired.. ) 

It was successful.. and very impressed 

Then, now...  I can't connect windows 7 anymore.. 

I wonder why.. 


I have never hanged any networking setting.

Any thought on why this is happening?

---

### Post by quixote on 2010-05-30
Maybe the system is just no longer mounting the Windows partition.  (Sort of the same idea as putting a USB drive in the USB slot.  The computer can't read it until it's put in.  With fixed drives, or logical parts of drives -- all called partitions in linux -- it's the same.  "Mounting" is telling the computer to read the drive.)

Is Windows on the same physical drive as your ubuntu install?  (It'll be in a different partition, of course.)  Or is Windows on a separate hard drive that you attach as needed?  Or even on another computer maybe?

Once we know the situation, we can go through the steps to identify the drive and try mounting it.

---

