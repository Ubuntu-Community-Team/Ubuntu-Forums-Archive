---
title: "Does Natty Narwhal have a wubi option?"
date: 2010-12-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-12-22
I have recently formated my maverick ubuntu and i want to try Natty Narwhal but 
i don't it to cause problems to my boot loader and etc so i want to try it via wubi till 
it will officialy release and then i would install it on an ext4 partition and etc. 
 
Thanks in advance.

---

### Post by nm_geo on 2010-12-22
> **aviramof said:**
> I have recently formated my maverick ubuntu and i want to try Natty Narwhal but 
i don't it to cause problems to my boot loader and etc so i want to try it via wubi till 
it will officialy release and then i would install it on an ext4 partition and etc. 
 
Thanks in advance.
Try this link

[http://ubuntu-with-wubi.blogspot.com/2010/12/natty-narwhal-1104-alpha-1-with-wubi.html](http://ubuntu-with-wubi.blogspot.com/2010/12/natty-narwhal-1104-alpha-1-with-wubi.html)

Forgot to add I would not try it!!!  Live USB would be better.

---

### Post by aviramof on 2010-12-23
Why shouldn't i try it via wubi?

---

### Post by garvinrick4 on 2010-12-23
#You are afraid of a bootloader which can be reloaded in a couple of lines of code.
#But you are not afraid of a Alpha running on new compiz-unity interface in WUBI install.
#Wow, let me know how that works out.

---

### Post by aviramof on 2010-12-23
I am not afraid of bootloader which can be reloaded in a couple of lines i just don't 
have the time to mass with burning a cd then creating a new ext4 partition then installing 
ubuntu in the hope that it would install grub 2 properly and if not boot to live
cd and install grub 2 manually but if i can run it via wubi then it's ok.
 
And by the way it didn't worked i tried to install it on my I: drive and the bootloader
didn't found it it said try (hd0,0) but didn't let me do anything so i rebooted to windows
and removed it and now i am trying creating a live usb in the hope that it would work better.

---

### Post by garvinrick4 on 2010-12-23
> **aviramof said:**
> Why shouldn't i try it via wubi?
Wubi has really got to be tested and retested for bugs before it is really safe
to use and even tougher on booting than partition install. Nothing wrong with
wubi install I still have one on a machine but make sure it is stable unless you
are wanting to test it for bugs. Do they even have a Wubi out yet in Natty?

---

### Post by garvinrick4 on 2010-12-23
> **aviramof said:**
> I am not afraid of bootloader which can be reloaded in a couple of lines i just don't 
have the time to mass with burning a cd then creating a new ext4 partition then installing 
ubuntu in the hope that it would install grub 2 properly and if not boot to live
cd and install grub 2 manually but if i can run it via wubi then it's ok.
 
And by the way it didn't worked i tried to install it on my I: drive and the bootloader
didn't found it it said try (hd0,0) but didn't let me do anything so i rebooted to windows
and removed it and now i am trying creating a live usb in the hope that it would work better. I have had trouble with making a Natty live Usb, my DVD installs work
fine. Sometimes do not install to a partition have installer problems with some dialy's for me. 
Got USB's but no persistence for some reason, have not questioned just waiting farther down the Natty road. 
A lot has been done since inception so far and Natty is going
to be real nice I believe. Good luck and happy Holidays Sir.

---

### Post by aviramof on 2010-12-23
Well so far it didn't worked with live usb all i got was grub rescue line and yes in the daily 
Natty Narwhal i downloaded there is wubi it just didn't worked for me so i guess 
i will continue to wait a bit longer before i try it again, and thank you very much 
and happy holiday to you to.:)

---

### Post by madjr on 2010-12-23
> **aviramof said:**
> I have recently formated my maverick ubuntu and i want to try Natty Narwhal but 
i don't it to cause problems to my boot loader and etc so i want to try it via wubi till 
it will officialy release and then i would install it on an ext4 partition and etc. 
 
Thanks in advance.

unless you're going to report bugs, i dont see why would you delete the stable maverik to install an alpha.

remember that is not stable enough for daily use and sometimes updates can break it.

---

### Post by nm_geo on 2010-12-24
> **madjr said:**
> unless you're going to report bugs, i dont see why would you delete the stable maverik to install an alpha.

remember that is not stable enough for daily use and sometimes updates can break it.

+1 with the break it.. LOL..
I have had at least two major breaks with the sudo mess and now the flashing login, but that is why we test to aid the developers.  I am now trying to restore my present Natty(using Harry's info), but I also have yesterdays daily build downloaded just in case.

What scares me is that I have begun to look forward to the breaks and fixes.

---

### Post by efflandt on 2010-12-24
I got persistence to work for Natty on live USB iso by first formatting part of it FAT32 and part of it ext2 (but don't give the partition any label yet).  I then used Startup Disk Creator with minimal 128 MB persistence.  Then rm casper-rw "file" from the FAT32 partition and make the ext2 "partition label" casper-rw.  Worked for me.  Also easier to look at casper-rw from another system instead of having to loop mount it.

However, from live iso on USB you cannot install video drivers, kernel updates, or other things that happen during initial boot.  Although, if persistence is working, you can install other programs that run after boot.

So if you have 8 GB or larger USB, you may want to do a regular install to it.  But make sure that you **put grub on the USB** memory or drive, **selected at bottom of manual partitioning menu** during install.

---

### Post by aviramof on 2010-12-26
Just to let you know i have decided in the end to install final version of maverick on an ext4 partition with a 2gb swap partition and i did it but amazingly i do have some problems 
that i didn't had in the past when i was testing maverick beta.

1.Favorites and my documents or what is used to be importated ware not importaed and i didn't see any option like this during the install process.

2.After installing the fglrx driver the boot screen is pink not purple(managed to fix it just now by changing from 8 bit to 24 bit resolution).

3.Grub did not installed itself on the mbr of all my driver i had to change boot sequence in the bios in order to get it working.

I do hope that in the future when i upgrade to Natty Narwhal i would no longer have this problems.

---

### Post by antileet on 2010-12-30
> **nm_geo said:**
> +1 with the break it.. LOL..
I have had at least two major breaks with the sudo mess and now the flashing login, but that is why we test to aid the developers.  I am now trying to restore my present Natty(using Harry's info), but I also have yesterdays daily build downloaded just in case.

What scares me is that I have begun to look forward to the breaks and fixes.

lol so true, been there! :lolflag:

---

### Post by navubnt on 2010-12-30
I have downloaded the ubuntu natty 11.04 using this link :[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Then I created live usb using this link : [https://wiki.ubuntu.com/Unity/InstallUSBKey](https://wiki.ubuntu.com/Unity/InstallUSBKey)


.I was able to run Ubuntu natty alpha 1 using Live USB but was facing problem installing new packages .Also facing problem installing broadcoam wireless drivers.


Live USB is the best way to test natty alpha..

---

