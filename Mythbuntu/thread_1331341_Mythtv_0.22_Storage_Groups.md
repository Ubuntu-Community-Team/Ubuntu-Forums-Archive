---
title: "Mythtv 0.22 Storage Groups"
date: 2009-11-19
forum: Mythbuntu
---

### Post by novellahub on 2009-11-19
Does anyone know if you define a storage group on a Slave Backend if it overrides the Master Backend or other Slave machines?  I have a situation on my Slave Backend last night where the drive filled up.  It did not write to any other storage groups on my Master Machine or second slave machine.

I had the impression if the local storage group on the Slave Machine fills up, it would then uttilize the storage group on a remote system.  

[http://www.mythtv.org/wiki/Storage_Groups#Storage_Groups](http://www.mythtv.org/wiki/Storage_Groups#Storage_Groups)

I am not sure if it is a situation where if you overrride a recording schedule (I wanted to record a show on a different tuner) where it threw things off.  Maybe it is just a configuration issue.

---

### Post by ian dobson on 2009-11-19
Hi,

Did you define a storage group on your slave backend that points to a directory on your main backend?

Reading the description it looks as if the backend (master or slave) will prefer a local storage directory before it'll use a networked directory. I don't think the slave uses the masters storage list to save data to the masters storage groups.

I hope this makes some sense.

[I]Maybe this would help to findout what mythtv is doing:-
If you run mythbackend with the "-v schedule,file" option, you can
see the weights as they are applied and the logs will show you why
Myth chose one directory over another when determining where to put
the next recording.[/I]

Regards
Ian Dobson

---

### Post by novellahub on 2009-11-19
The slave machine has just a local storage group assigned. It is not pointed to master machine at all.  I was hoping if the space on the Slave machine is low it would write to the master or second slave machines storage.

Perhaps I have to play with the "Extra Disc Space" option and set the value a bit higher.  I had it set to 7 GB (The default is 3 GB).  The recording the slave machine was doing is easily 20 GB when completed (3 /12 hour recording of a sports event).

---

