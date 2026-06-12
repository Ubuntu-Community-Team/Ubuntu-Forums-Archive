---
title: "Unable to connect to the master backend at 192.168.0.36:6543. Is it running?"
date: 2010-05-31
forum: Mythbuntu
---

### Post by jimp180 on 2010-05-31
I recently upgraded all my machines from 9.04 to 10.04, at first, aside from a few minor glitches, everything seemed to be working fine. After about a week I could not watch live tv, when I would try I would get the "could not connect to the master backend" message it still scheduled and recorded programs, i could watch recordings, listen to music, browse the gallery and connect to the backend with mythweb. since it was obviously able to connect to the backend to do every thing else I decided there must be something wrong with the upgrade on the master backend, so last night I decided to do a fresh install of mythbuntu 10.4.

 After getting everything setup I tried to connect from a frontend to set some schedules, and got the "Unable to connect to the master backend at 192.168.0.36:6543. Is it running?". so I thought " well I'll just go to mythweb and set my schedules then figure this out in the morning". But now even from mythweb I get the same error message "Unable to connect to the master backend at 192.168.0.36:6543.
Is it running?" Yes the thing is running I checked with "TOP" just to make sure. the IP address and the port number are correct and the frontends are connecting to the database all fine. at this point I figured maybe its a firewall problem so I loaded the frontend on the masterbackend and even with this I get the same message! 

I am at a loss as to what to do to figure this out, any help would be appreciated

---

### Post by laffinet on 2010-05-31
Have you checked the IP setting on the master backend, under backend-setup "General".
You need to enter the actual IP address for the backend here too in order for remote (and local) frontends to connect.
Also check the backend role in the mythtv control centre, make sure you have the bit enabled that allows remote frontends to connect.

One other thing: is your network connection of the backend working ? Sometimes my network connection goes down (stupid Ethernet over power) and as a result my local (!) frontend can't connect to the main backend (same machine!) anymore.

---

### Post by jimp180 on 2010-06-01
yes the IP address is correct and I think I ruled out the network since I can't even connect from the frontend on the master backend machine

---

### Post by laffinet on 2010-06-01
> **jimp180 said:**
> I ruled out the network since I can't even connect from the frontend on the master backend machine

That doesn't mean anything. If your setup includes remote frontends then even your local frontend won't be able to connect to the backend on that same machine if the network is down.

Happened to me a few times now. Tried to open the frontend on my combined front/backend. Got the messaget that I couldn't connect to the master backend. Found that I had no connection to my router. As soon as I fixed that everything was fine.

---

### Post by jimp180 on 2010-06-04
Ok after reloading again, then reloading with mythdora and I still had the same results, I switched roles on my slave backend to master and have my system useable again. Since this is obviously a hardware error, I have ordered a new mother board for the original master backend, I might have got by with putting a nic card in it but all my slots are needed for tuner cards.

---

