---
title: "Beginner Trouble Accessing Host(XP) from Ubuntu in VirtualBox"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by BEEDO on 2011-09-30
I have Ubuntu 11.04 desktop installed in VirtualBox on XP. It has a LAMP server which seems to be working when I access http://localhost/"file" from a browser in Ubuntu. I want to get a file folder from the XP host so I can put some existing  .html and .php files in the server, for starters, but I can't figure out how to get to the file from Ubuntu. Being a pretty raw beginner, any helpful ideas will probably have to be easy to follow, since I am new to much of the terminology and protocols. Thanks!

---

### Post by An Sanct on 2011-09-30
Welcome to the forums!

Well, the quick way is to put the files on a USB stick and then enable it in the guest.


The real way to share folders is, to turn off your guest OS and open VB. 
Right click on the wished OS, select settings.
On the left, in the bottom of the list, you see "Shared folders", click on that
On the right of that, you see a folder with a "+", click there and select the folder, you wish to share between OSes. Also check "Auto Mount", to automatically mount the folder.

Now, install guest additions, on the window, in which Guest is running, select 
Devices > Install Guest Additions

Re-login or even better :) reboot Guest.

If you followed the procedure, now under /media/____ should be a mounted folder with your data.

PS.... Note, that I have to be root to access the folder ... for some  odd reason ... I never tried to fix this, as I use this maybe 2 time per  year ... chown might help :wink:

---

### Post by jumpyjester on 2011-09-30
Hi Beedo,
 
depending on whether you are running the OSE version or the Full, what you need to do is install the full version on the latesst build it is an expansion download.
 
once you have VirtualBox full, there are two ways of getting between the 2 os's. 
1. setup USB filters and use a USB key or USB HDD to transfer the files on to, note when the VB PC is running you cant access the key from the Host PC.
 
2. setup a shared folder, i havent had much experience with this one but what you do is effectivley allow VB to access a folder on your Host HDD. 
 
both of the above are found when you go in to the machine seetings.
 
please let me know how you get on.

---

