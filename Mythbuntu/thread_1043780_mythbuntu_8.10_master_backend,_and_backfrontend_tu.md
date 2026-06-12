---
title: "mythbuntu 8.10 master backend, and back/frontend tuner problem"
date: 2009-01-18
forum: Mythbuntu
---

### Post by deltaxfx on 2009-01-18
Ok, here goes. I've been trying to figure this out for about a month now, and have gone through several different distros hoping the different install methods would alleviate the problem. But no luck yet.

I'll just describe the setup I have with mythbuntu 8.10. 
I set up a master backend, I think mythbuntu calls it a primary backend. It is a backend only, with two tuner cards. Once I set it up I was able to access it from a frontend only laptop I have (running Arch linux) and was able to watch TV on both tuner cards.

I have another box in the living room that I set up with mythbuntu 8.10 as a secondary backend/frontend. It has a single tuner card. During the setup process it connected to the master backend mysql database fine. I set up the tuner card the same way I did when I had the box running as a standalone masterbackend/frontend (everything worked fine as a standalone). 

The living room secondary backend/frontend is where I will be watching TV. And I can watch TV on it from both master backend tuner cards, but not from the card that is IN it. This is the exact problem I have been having when running both systems with Arch and doing the whole install by hand, and using knoppmyth, and now with mythbuntu. Is there a step I am missing? The mythtv documentation says that you can have multiple backends, and they can all have tuners. So why can I only access the tuners on the master backend, but not on the slave backend that the frontend is running on?

All the guides I have read in the past few weeks make it sound so simple!

Thanks in advance for any help!

---

### Post by sgtrock on 2009-05-10
I have the same symptoms you do, except I got there by adding a tuner card, 1 TB HD, and slave backend to an existing remote frontend box.  I've been doing some digging today on a couple of forums, looking for leads.  At this point, I'm about half convinced that the potential root source of the problem may be the changes in directory structure with the new HD.  If I understand the issues correctly, each slave backend should use the same directory structure the master backend does for recordings, music, etc.

I'm going to sit down and design a new directory map that should be usable by both backends, then apply it to both.  I think I'll probably leave data where it is and use symlinks as much as possible.

In addition, apparently mythtv can be pretty sensitive to SUID permissions on some subdirectories for some reason.  I need to dig into this, as it's not something that I understand.  In the past I've just forced ownership and group permissions where I need them to match applications.  That may not be appropriate for mythtv.

---

### Post by klc5555 on 2009-05-11
> **deltaxfx said:**
> Ok, here goes. I've been trying to figure this out for about a month now, and have gone through several different distros hoping the different install methods would alleviate the problem. But no luck yet.

I'll just describe the setup I have with mythbuntu 8.10. 
I set up a master backend, I think mythbuntu calls it a primary backend. It is a backend only, with two tuner cards. Once I set it up I was able to access it from a frontend only laptop I have (running Arch linux) and was able to watch TV on both tuner cards.

I have another box in the living room that I set up with mythbuntu 8.10 as a secondary backend/frontend. It has a single tuner card. During the setup process it connected to the master backend mysql database fine. I set up the tuner card the same way I did when I had the box running as a standalone masterbackend/frontend (everything worked fine as a standalone). 

The living room secondary backend/frontend is where I will be watching TV. And I can watch TV on it from both master backend tuner cards, but not from the card that is IN it. This is the exact problem I have been having when running both systems with Arch and doing the whole install by hand, and using knoppmyth, and now with mythbuntu. Is there a step I am missing? The mythtv documentation says that you can have multiple backends, and they can all have tuners. So why can I only access the tuners on the master backend, but not on the slave backend that the frontend is running on?

All the guides I have read in the past few weeks make it sound so simple!

Thanks in advance for any help!

Myth is often a bit fussy about adding a new secondary backend for the first time.

After the steps you have performed to add the slave backend, I've found it usually takes the following additional at the end: 1) Cleanly shutdown the new slave backend machine. 2) Cleanly restart the _Master Backend_ machine (or simply restart the Master Backend without restarting that machine, if you prefer). 3) When the Master Backend is on line again, now boot up that new slave backend machine. When the slave backend is back on line, its tuners should now be listed as "Not Recording" in System Status, and you should be ready to go.

It took me a quite a while the first time I added a slave backend machine to realize that the master backend also has to be restarted before the whole setup becomes aware of the new tuners. 

Cheers!

---

### Post by 4dognight on 2009-05-11
I will agree to what klc5555 said. 
In my scenario, if I ever restart the MBE, the other slaves dont reconnect, and their tuners dont become available. I usually just restart the slave BE, which then connects to the MBE. I thought about assigning a BE restart to my remote, but Im hoping this gets fixed in future releases.

Having said that, have  you tried manually changing tuners, using the onscreen menu?
In  mythweb, under backend status, does your tuner even show up?

---

### Post by deltaxfx on 2009-06-11
Well guys, I hate to say it but I took the coward's way out! I ended up with just one master/frontend for my recording/watching, only one tuner. And it connects to my fileserver for storage. When I get time I am anxious to try the restarting in order steps you have listed. Restarted the slave BE's a bunch but never though about the MBE! Thanks for the info, I'm excited to give it another shot now!

---

