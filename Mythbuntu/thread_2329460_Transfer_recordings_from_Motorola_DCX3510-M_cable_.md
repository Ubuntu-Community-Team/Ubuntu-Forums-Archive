---
title: "Transfer recordings from Motorola DCX3510-M cable box via firewire"
date: 2016-07-02
forum: Mythbuntu
---

### Post by danno32 on 2016-07-02
My goal here is simple, but I'm not sure if possible - to transfer recordings from this DVR to a computer.  I checked diagnostics on the cable box/DVR and it shows the firewire port as available and active when physically connected to the mythbuntu computer.  I know there are possible issues with 5C encryption and/or broadcast flag issues with capturing channels from most cable channels, but I'm not sure if that applies to stored recordings on the DVR.

I had initially tried to use Win XP, CapDVHS, but was never able to find drivers for AV/C Panel (drivers for 1394 Net Adapter were found) and most links for finding drivers were dead.  I later read a thread (it's now dead and only shown as 'archive') [http://www.gossamer-threads.com/lists/mythtv/users/548664](http://www.gossamer-threads.com/lists/mythtv/users/548664) where someone claimed to have gotten this cable box working with MythTV, but no usable info was provided.

I've attempted Mythbuntu install with this cable box connected via firewire.  I'm unable to determine if any of the needed drivers for the cable box were installed or if the internal firewire PCI card is even recognized.  If I try to start the front end, it shows 'cannot connect to database', even though front and back end are both the same computer (I tried with the default of 127.0.0.1 and my actual local IP address and using a PIN of 0000 with no success).  I also checked and the mysqld process is running.

---

