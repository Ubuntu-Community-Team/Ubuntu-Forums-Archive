---
title: "mkvtoolnix crashes on add file"
date: 2011-07-06
forum: Multimedia Software
---

### Post by Russell Burrows on 2011-07-06
Ubuntu 11
Mkvtoolnix plus toolnixgui version 4.5
Toshiba satellite C655  AMD 


When opening MKVtoolnix and selecting add file this makes mkvtoolnix to crash a few seconds later.

I tried reinstalling but same problem
Went to launchpad but there its listed as fixed??? not for me.,,,sigh.

Any tips to solve this??

I tried to get version 4.8 of toolnix but was unable to findit in Synaptic??

Thank you.

---

### Post by andrew.46 on 2011-07-06
> **Russell Burrows said:**
> 
I tried to get version 4.8 of toolnix but was unable to findit in Synaptic??

Mosu keeps a repository here:

[http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu](http://www.bunkus.org/videotools/mkvtoolnix/downloads.html#ubuntu)

and this should get you the latest version. Hopefully this will not crash in the same way :).

---

### Post by Russell Burrows on 2011-07-24
Thanks but toolnix version 4.9 still crashes after add file.:(

---

### Post by andrew.46 on 2011-07-24
Hmmm..... I am not sure what this means:

> 
The problem ceased to exist after applying updates to language and LSB packages released today.


Perhaps append a query to [the Launchpad bug]("ttps://bugs.launchpad.net/ubuntu/+source/mkvtoolnix/+bug/769508")?

---

### Post by stefangr1 on 2012-01-20
> **Russell Burrows said:**
> Thanks but toolnix version 4.9 still crashes after add file.:(

Just to have the solution here: this is most likely due to a bug in curl that still exists on a freshly installed ubuntu 11.10. The solution is to turn of automatic updates of mkvtoolnix *before* it crashes.

---

### Post by Russell Burrows on 2012-04-16
Problem solved! by updateing to MKVToolnix 5.5.
Mosu is great!!

---

