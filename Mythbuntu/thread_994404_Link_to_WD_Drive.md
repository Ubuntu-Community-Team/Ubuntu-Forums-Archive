---
title: "Link to WD Drive"
date: 2008-11-26
forum: Mythbuntu
---

### Post by dareofficer on 2008-11-26
Hello, I got Mythbuntu going now with the help of a friend.  I love it looks and works great with my HD Homerun.  I have two questions however I can't figure out.

1. I have a Western Digital Mybook Hard Drive.  It is 750 GB.  It runs on a Gigabit connection into my Gig router.  How can I mount this so I can use it to watch videos, on my mythbuntu?  Ver 8.10

2. I'm trying to install a front end on another PC, I does not register to the back end.  I have double checked and I have the password from my frontend of my master server.  mythtv, then mythconverg, then localhost.

---

### Post by dareofficer on 2008-11-27
I was able to figure out the WD drive connection.  After finding the IP address, I smb://192.168.2.21 (My address of the network drive) and was able to access it.

Now reference the front end, I'm still working on it.  I can't connect to it at all.  I get a "Failure" everytime.  I know the Nic card is working because I can access the internet with it even in live mode.  Any assistance with this would be great.

---

### Post by ian dobson on 2008-11-27
Hi,

You need to configure the IP address of the master backend (if you want to share the backend) for the backend/sql server.

Regards
Ian Dobson

---

### Post by dareofficer on 2008-11-29
I got this working.  I had localhost, instead of the IP of the master server.

Thanks

---

