---
title: "How do I properly configure another station that has a PVR card?"
date: 2008-03-14
forum: Mythbuntu
---

### Post by freymann on 2008-03-14
I'm working on a configuration like this:

1 server, with frontend/backend... (the main server). This has a local TV and PVR-150-MCE tuner card.

1 client (a frontend)... simply to watch live TV or recorded shows, or access our "media" (photos/music/vidoes).

And then...

I have another station, that will have a local TV and PVR-150-MCE. This should be configured as a secondary front/end??

I want to be able, say on the "client", decide to watch LiveTV and let the system pick what tuner card is available, be that the master server or the secondary.

My question is, what are the steps to set up the secondary? I'm sure somebody has a link I can follow... 

Thanks.

---

### Post by volkswagner on 2008-03-15
If this is a new install choose advanced, install as secondary backend with frontend.  The master will need to be running during the install.  With this setup the system will choose available tuners starting with last installed local tuner.

---

### Post by freymann on 2008-03-15
> **volkswagner said:**
> If this is a new install choose advanced, install as secondary backend with frontend.  The master will need to be running during the install.  With this setup the system will choose available tuners starting with last installed local tuner.

 Yes, I did that no problem. I was just wondering about the mysql database and mediashares.

 I have the mysql stuff set up where there's a local 127.0.0.1 at the top, but the master backend is 192.168.0.2. Is this correct? does the secondary backend require it's on database and mythfilldatabase stuff?

 For the mediashares, I've mounted some NFS shares on the main server OK now. But should the recordings directory on the secondary backend remain local or mapped to the NFS on the main server? I'm thinkin I should be using the recordings directory on the master server....

---

### Post by volkswagner on 2008-03-15
> I have the mysql stuff set up where there's a local 127.0.0.1 at the top, but the master backend is 192.168.0.2. Is this correct? does the secondary backend require it's on database and mythfilldatabase stuff?

I am a little confused.

The mysql database shall reside on the master only.  The master can have 127.0...for the location of the database.  All other machines shall point to the actual ip of the master.  I notice mythtv .21 shows a little more info (local machine and master location).  

I think the recording to a local hard drive or via LAN to the master is personal preference.  You may be bandwidth limited, you may have a small HD on the slave, etc.  The recordings will be included in the database regardless of physical location.  The slave will need to be running to allow access of the recordings (located on its HD) to a remote machine.

You will need to set up shares for all media except recordings (they are automatic).

Hope this helps.

---

### Post by freymann on 2008-03-15
> **volkswagner said:**
> 
The mysql database shall reside on the master only.  The master can have 127.0...for the location of the database.  All other machines shall point to the actual ip of the master. 

When I did the install on the secondary backend/frontend, it looked like it should have a db on 127.0.0.1 and then use the master one (for me on 192.168.0.2) but I can understand what you mean. Only one "master" database makes sense. I will correct the IP on that box.

> I think the recording to a local hard drive or via LAN to the master is personal preference.

Excellent. While fiddling with my media shares I believe I discovered it is best to keep that path local.

Once again, I thank these wonderful forums in Ubuntu land and people like you, for taking the time to offer assistance. ;-)

---

