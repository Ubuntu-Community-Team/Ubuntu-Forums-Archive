---
title: "Network Setup Help Needed"
date: 2012-12-16
forum: Networking &amp; Wireless
---

### Post by kneadmore on 2012-12-16
Trying Ubuntu 12.10 installed via wubi installer.
Installed alongside my Windows 7 on a laptop.
My laptop on Windows 7 has been wirelessly connected for over a year with no problems. I had no problem setting up my home network (desktop, 2 laptops, printer).
I cannot figure out how to get wirelessly connected with my ubuntu install.
Have tried wire connection to router also with no results.
This post is being written on my XP desktop since obviously I cannot use the ubuntu laptop.
 
I have tried many suggestions but they don't seem to be for an absolute beginner.
I'm sorry, but they refer to command-line functions and terminology that I don't understand.
I need a step-by-step solution.
How would I post any results from Terminal?
 
Thanks for any help to this Ubuntu/Linux newbie.

---

### Post by 81duz1d0 on 2012-12-16
Both wired AND wireless connections aren't working?

---

### Post by kneadmore on 2012-12-16
That is correct. No wireless and no wired. I tried the laptop connected directly to router and still no connection.
 
I really don't know how to proceed.
Never had trouble in Windows.
 
Would love to try Ubuntu on laptop. 
I run it OK on Desktop using bottable CD and "Try".

---

### Post by Bucky Ball on 2012-12-16
[I]Thread moved to [B]Networking & Wireless

[/B][/I]Welcome to the forums.Open a terminal (Applications>Accessories>Terminal) and copy/paste this in:

```
sudo lshw -C network
```Copy and paste the results back here. You might need to save them to a document, get back to Windows, open the doc and copy/paste from there ...

Take note that Wubi is to try out Ubuntu before a full install. You might not have this problem when Ubuntu is properly installed. As it is a 'try before you buy' option and not a permanent solution there are not really too many Wubi gurus around ...

Just out of curiousity, have you tried Ubuntu from the install CD (LiveCD), not the Wubi install or install CD? Does wireless/wired work there? Anyhow, post that output and that will tell us more ... ;)

---

### Post by kneadmore on 2012-12-17
Hi, After a lot of manipulation between Ubuntu's Terminal and Windows I have attached (I hope) the screen-shot you requested.
The first section is my wireless adapter and the second is the ethernet adapter.
 
By the way, I downloaded the 64 bit version of 12.10 and burned the iso to a DVD.
Booting with that DVD I can access my network. I had to go to System Settings>Software Sources>Additional Drivers and select to use the Broadcom driver listed there. "Broadcom 802.......driver source from bcmwl-kernal-source (proprietary)." 
 
This did not work in the dual-boot version I tried before. It just always came back with "device not working".
 
However using the bootable disk method, nothing is saved when you exit. Therefore I have to set up the net work every time.
 
How can I get the file from that bcmwl-kernal-source?

---

### Post by kneadmore on 2012-12-18
OK I now have everything running.
The installation of 12.10 using the wubi installer, does not allow the setup for my Broadcom BCM 4312 network adapter.
I used the downloaded version directly to install and found I could setup the network just fine. The system recognized my wireless printer and I'm good to go.

The installation allows one to install ubuntu side-by-side with existing OS or use the entire HDD. I opt for side-by-side. Still getting my feet wet.

Thanks to all.

---

### Post by Bucky Ball on 2012-12-18
Glad that worked out. Yes, the wubi install is a bit of a mystery for many of us as not used. 

Please mark thread as Solved from Thread Tools to help others. ;)

Enjoy the OS and the learning curve ... and, of course, the forums!

---

