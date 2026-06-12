---
title: "[SOLVED] Xubuntu Studio"
date: 2008-09-04
forum: Multimedia Software
---

### Post by Xochipilli on 2008-09-04
Is it possible to install whole the Ubuntu studio package (all the programs) on Xubuntu at one time?
I want to try installing Ubuntu Studio on an old pc (intel PIII 1,3 GHz, 256 MB RAM), for my younger brother who likes to work with music. But I think it will be better to install Xubuntu than Ubuntu because of the low memory and clock-rate.

---

### Post by snowpine on 2008-09-04
Yes. Start by installing xubuntu, then you can install the rest with:

sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rt

There are also ubuntustudio-desktop, ubuntustudio-graphics, and ubuntustudio-video packages if he's interested. But the command I gave above will install all of the audio apps.

[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

---

### Post by Malcolmx86 on 2010-06-03
I am planning to do the same because it sounds good to me . I too will add studio by adding the packages after installing xubuntu 10.04 . 

I have a DELL laptop with a broken CD/DVD drive , but I can boot live xubuntu from usb (with pendrive linux [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) ) . On the desktop of this live xubuntu is a link to install xubuntu 10.04 .

I have 16gigs free on the hard drive , but the rest of it is full of a horrible corrupted Windows XP .

I figure that even though I've got 16gig free , it is probably not all in the same place , but spread out randomly all over the drive and what I have to do is push all of the information to one end of the space on the disk , so all of the free and empty space is in one contiguous chunk on the other end of the disk before repartitioning .

I don't know . How big does the partition have to be to install studio on top of xubuntu ?

 
:guitar:

---

### Post by Pangoria on 2010-06-03
@MalcomX86:  Your problem is separate from the topic of this thread, but, I just did a clean install of Ubuntu on my desktop (formatted the drive), and I ended up getting all 500gb of my hard drive back (- about 5gb for Ubuntu).

So if you install, just do a full install with formatting the drive etc, you will just wipe everything out, including the XP.

---

### Post by TBerk on 2010-06-25
> **Pangoria said:**
> @MalcomX86:  Your problem is separate from the topic of this thread, but, I just did a clean install of Ubuntu on my desktop (formatted the drive), and I ended up getting all 500gb of my hard drive back (- about 5gb for Ubuntu).

So if you install, just do a full install with formatting the drive etc, you will just wipe everything out, including the XP.

If you boot from the LiveCD (or equiv on USB) you can manually adjust the size of the partitions w/ gparted (and actually other comparable apps).
 
By doing this it will 'shrink' the existing partition (the one with the current, dreaded XP), freeing up room for other partitions to be created. 

As a general guideline I'd suggest you make more than one w/ the new OS on something like 3-6G and the rest given over to a separate /HOME partition. 

(You can google/search all about have a separate /home dir.)


TBerk
Holy Resurrected Threads Batman!

---

### Post by moosenamedmorton on 2011-12-25
will this enable realtime priority for jackd? It's been my ongoing battle to get pure-data functioning with jack but this error message follows me wherever I go.


JACKerror: Cannot use real-time scheduling (RR/5)(1: Operation not permitted)
JACKerror: JackClient::AcquireSelfRealTime error

---

### Post by overdrank on 2011-12-25
Hi and welcome, please start a new thread with your issues. Thread closed.

---

