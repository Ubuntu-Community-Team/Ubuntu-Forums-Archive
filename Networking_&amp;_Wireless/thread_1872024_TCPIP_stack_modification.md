---
title: "TCP/IP stack modification"
date: 2011-10-29
forum: Networking &amp; Wireless
---

### Post by rajneesh2k10 on 2011-10-29
Hello,

I am willing to modify the source of TCP/IP stack, precisely the ARP portion of the ethernet. I don't know if there is any legal issue with that, in that case please let me know.
I am unable to find where these codes reside on the system. I hunted for the same on internet and found out a file named arp.c takes care of the ARP part of the system. But I am unable to locate it on ubuntu. I am also looking for a comprehensive text of how these Data Link Layer modules interact with each other (inter layer and intra layer), so that I can plan my way to proceed.
Any one having any resource on the same, please guide me through. If not ubuntu please let me know about other variants that you know or which variant will have the maximum freedom as well as documentation to allow me to proceed with my idea. :confused:
Sorry if I am posting it on the wrong section. I searched for kernel section but it wasn't there and I found Networking to be relevant. :(

Thank you very much!

---

### Post by Dangertux on 2011-10-30
You need to download the actual kernel source, not just use your pre-compiled kernel.  

You can get the latest kernel source from github and modify the stack until your heart's content.

the file you're looking for is under net/ipv4/arp.c

---

### Post by rajneesh2k10 on 2011-10-30
Thank you so much.:D:popcorn:
I can now locate where I have to work.
Can you suggest me any resource from where I can look up how these modules interact with each other, what are the duties of the different functions and data structures used in the code?
If not, can you suggest me where to shout for help on this topic?:confused:
It would be of great help.
Thank you.

---

