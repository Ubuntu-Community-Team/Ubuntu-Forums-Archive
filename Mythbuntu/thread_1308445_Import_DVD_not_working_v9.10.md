---
title: "Import DVD not working v9.10"
date: 2009-10-31
forum: Mythbuntu
---

### Post by barts2108 on 2009-10-31
hi

out of the box installed mythbuntu 9.10 release in VMWare server. To be exact, installed the 64bit version. After install it runs without any problem. However I want to import a DVD and it says:

No Jobs. Checking and/or waiting for DVD

If I close the mythtv, I see the DVD is mounted and on my desktop, I can also browse it.

I also tried to play this DVD with mythTV... also no luck.

Why do these options not work "out of the box" ? What should I do to make it work ?

---

### Post by barts2108 on 2009-10-31
Well, got something further...

Default device is set to /dev/dvd
In my case it was /dev/scd0

Wondering in these ages... why can it not be set correctly first time ???

Well.. uhm.. at least something more happens with that /dev/scd0 setting, but playing and ripping still doesn't work...

Whate else to do ???

---

### Post by kja999 on 2009-11-01
There have been DVD related errors reported for Ubuntu 9.10, it doesn't seem to be MythBuntu specific.  VLC still works for me .. but Fluendo DVD doesn't work any more.

---

### Post by andyfrizzle on 2009-11-03
Using Mythbuntu 9.10 I have experienced similar problems.

>>Default device is set to /dev/dvd
>>In my case it was /dev/scd0

I examined the above settings and found that the default device is, as stated above, set as /dev/dvd


>>Whate else to do ??? 

Further examination revealed that when a DVD is inserted, the system mounts it as /media/cdrom0.

I have changed my default device to that location, and the ripping function now appears to be working correctly.

I hope this also works for you.

---

### Post by barts2108 on 2009-11-03
>> and the ripping function now appears to be working correctly.

Indeed... if I change to /media/cdrom0 (after mounting manually) the rip page shows me some option, but the begin ripping button does not do anything except for coloring green...

In the darkgreen box at the bottom there's some buttons or so with a checkbox inside and an empty one...  (see [IMG]http://www.bings.nl/images/myth.png[/IMG])

Somehow there is a time set... (1st chapter?) but as said... pressing the Begin Ripping does not do anything.

VLC player on the mounted disk also does not play anything... its only attempting to do something.

A pity such things...

---

### Post by barts2108 on 2009-11-07
bump: anyone know more for this ?

---

### Post by barts2108 on 2009-11-12
Found this page [https://bugs.edge.launchpad.net/mythbuntu/+bug/469583]("https://bugs.edge.launchpad.net/mythbuntu/+bug/469583")

Seems to be something worth to try

---

### Post by barts2108 on 2009-11-28
The link posted earlier seems indeed a solution to this particular problem. Default the pathname is empty, and with correct path a rip is possible.

---

