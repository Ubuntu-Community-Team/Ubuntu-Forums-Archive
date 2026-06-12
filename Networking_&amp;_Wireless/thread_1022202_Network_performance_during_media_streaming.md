---
title: "Network performance during media streaming"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by soeren72 on 2008-12-26
Hi

I have setup Ubuntu as my nas for my media files.

After solving allot of problems with dropped packets on the Realtek 8111 gigabit card .

It's now up and running, but theres a problem.

Every few minuts the streaming stops
I can still ping the server, and with good repl.

I have tryed to optimise SAMBA but its the same, and the problem is seen on two Vista clients 

If i check dstat,  i can see that disk reads goes to zero 
and net goes to a minimum (1980B)

Could it still be the Realtek ?

Br Soeren

---

### Post by Blibit42 on 2009-05-12
I too am having similar issues only not streaming video or audio. I am copying millions of image files from one server to another, and I have dual 8111 NICs on the motherboard, and after 500 to 1000 files it seems to begin to drop packets :confused: like mad then usually disconnects or just goes DOG slow until I CTRL C the cp command. I am using SAMBA and I was also going to set up NFS on the other channel (different network) but I am now using the second channel with the 1st one disabled and it seems to work (I am at 40,000 files and all seems well).  I did not try it with the #2 channel disabled, but I will try that next to see if there is soem type of interference between the channel hardware.

I did not check driver versions, but that is next on my list (I guess)... I am using Jaunty (9.04) right now so I don't think the drivers on the MOBO disk will be any newer than what is in the system right now, but I guess I will check (But I wanted to keep this system "virgin" as far as drivers go for ease of support). 

Thanks
Blibit42

---

