---
title: "Central stroage advice when using multiple backends"
date: 2008-11-16
forum: Mythbuntu
---

### Post by rsmithgs on 2008-11-16
Hi everyone :-)

I have recently started looking at having a MythTV system at my house. After a bit of looking I thought using Mythbuntu would be the way forward.

I'm planning on using a Master Backend purely for database, storage and the booting of Diskless frontends. Basically everything apart from doing the actual recording. (I won't have TV cards in this unit). This will be a server with a RAID 10 array.

I'm also planning on having 1 or maybe more secondary backends which will have multiple TV cards.

What I would like is for the secondary backend(s) to record tv programs when scheduled and to allow the frontends to watch livetv using the tv cards in the secondary backend(s). I would like any shows that are recorded to be stored on the Primary Backend.

I guess there are 2 ways of achieving this but any advice on any other ways or how to achieve either of the below would be helpful :-)

1. Record directly to network storage like NFS, not sure if NFS would cope with 4-6 TV feeds recording though

2. Once a particular show has been recorded or once every few hours, the contents of the secondary backend(s) move there files to the primary backend. The frontends can then view these recordings from the primary backend.

Many thanks in advance for any help :-)

Cheers :-)

---

### Post by ian dobson on 2008-11-16
Hi,

How many tuners do you plan to have in total? 
Is there any reason you don't want tuners in your master backend?

I would recommend recording to a local harddisk, then copying them over to the backend and fixing up the database. You'll need to fixup the database as mythtv records information about all recordings in a MySQL database, which include the host name/storage group where the file is stored.


I currently have 2 DVB-C and a PVR-500 in my backend and no free PCI slots. I plan to add another backend for encoded channels only which would be as a slave backend with minimal hardware/diskspace. But after running afew tests I started having problems with the network connection (slow/dropouts) when using a 100MBs network connection samba/CIFS.

Maybe one day I'll have another try but at the moment I don't have the time.

Regards
Ian Dobson

---

### Post by rsmithgs on 2008-11-16
Thanks for your reply :)

The reason for not putting the tv cards in the master backend is due to the server only having PCI-X slots and not been anywhere near an antenna feed.

Do you know which entries I would need to change on the database? Suppose I could script something to run out of hours where the files would be copied and database entries modified. (Hopefully lol)

---

### Post by ian dobson on 2008-11-16
Hi,

Yep, you'll need to change the recorded table, hostname and storage group fields.

A one off script shouldn't be too hard to write, maybe I'll have a go at banging something together next week. I've wanted to write a MythMove script for sometime. Up until now I've always manually moved recordings about.

Regards
Ian Dobson

---

