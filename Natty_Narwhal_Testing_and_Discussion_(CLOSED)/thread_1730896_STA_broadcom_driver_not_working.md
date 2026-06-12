---
title: "STA broadcom driver not working"
date: 2011-04-16
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by landon418 on 2011-04-16
On 10.10 it worked but not anymore, I have a dell wireless 1390 minicard on my vostro 1500

---

### Post by donniezazen on 2011-04-16
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/712053)

Hop in!

---

### Post by vishalrao on 2011-04-17
I hopped in. So, as suggested by the developer, has anyone installed Natty afresh and still facing this problem? He says if you install afresh it might solve the issue or at worst be a duplicate of the other bug mentioned.

---

### Post by landon418 on 2011-04-17
They really need to get this fixed!

---

### Post by landon418 on 2011-04-17
reinstalled ubuntu 2 times, not luck. Is it becuase I changed from 32bit to 64 bit?

---

### Post by donniezazen on 2011-04-17
I have too many things installed on my system to clean install natty. I will give it a try in couple of day when i get a whole day. I have little hope of it being fixed just by clean install.

---

### Post by landon418 on 2011-04-17
Got it fixed!!!

> **drs305 said:**
> I only have wireless in a 32-bit system, so I don't know if this will work for you or not.

I got mine working via a solution posted in the following bug report (see Post 5). You uninstall the STA driver and then "sudo apt-get install firmware-b43-installer b43-fwcutter".
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/732038")
I imagine it will be fixed, as Mark Shuttleworth indicated it's affecting him as well in a duplicate bug thread.

Note install the driver in synaptic package manager!

---

