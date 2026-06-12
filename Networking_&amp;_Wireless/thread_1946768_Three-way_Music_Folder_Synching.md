---
title: "Three-way Music Folder Synching"
date: 2012-03-25
forum: Networking &amp; Wireless
---

### Post by UltraZone on 2012-03-25
Hi, I would like to set up a three-way synching mechanism where my laptop (Ubuntu), my Mac Mini, and my NAS server music content is triplicated.  The Mac Mini serves as my home theater server, the laptop is for general use, and the NAS is my backup.  I would like to set up a service such that once a day for example, if I download music on any of these three devices, the music gets copied over to the other two.  Anybody have any ideas how to control this?  Thanks.

---

### Post by kevdog on 2012-03-25
I probably just elect for a rsync option through a script if it were me.  It's not a perfect solution.  unison is another utility I've used before, however if you have really big data sets, it tends to choke on these.

---

### Post by papibe on 2012-03-26
> **kevdog said:**
> I probably just elect for a rsync option through a script if it were me...
+1

I have a similar situation going on in my home network. However, I use a different strategy:
[LIST]
[*]My home server (also works as a NAS) is the 'main' data repository.
[*]The clients (a desktop, and a few laptops) sync only to the server.
[*]The sync script includes (1) pushing the new files from the client to the server, and (2) pulling files from the server that are not in the client.
[/LIST]
Just sharing some thoughts. Let us know if you need more helps with that.
Regards.

---

