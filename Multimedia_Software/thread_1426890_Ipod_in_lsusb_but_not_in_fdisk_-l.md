---
title: "Ipod in lsusb but not in fdisk -l"
date: 2010-03-10
forum: Multimedia Software
---

### Post by CryptSphinx on 2010-03-10
Hi - Ipod Classic (6th gen , 120gb)
was working fine up to a week ago on my desktop
running Karmic (kept up to date).


Sudden problem , have been looking online for solution.No joy so far.

=>
Basically : I connect Ipod , it doesn't auto mount any more
The device shows up in lsusb as 

Bus 001 Device 007: ID 05ac:1261 Apple, Inc. iPod Classic

but its not being listed in "sudo fdisk -l"
this only shows my HD's 3 partitions.

Installed no new hardware / software (apart from updates) since problem started.

[[Btw , tried Ipod on other PC in house , also Kubuntu-Karmic , works fine,  tried with diff cable on my pc on diff usb port. same prob]]


SOLVED - I not sure WHAT it was that did it , 

I had this sudden thought to try connect a usb stick
(my logic being that if IT wasn't recognised then it was a usb issue, not an ipod issue)
 , just after inserting it the usb stick ipod was recognised - the Ipod is now syncing  via amarok  - Weird issue?!

---

