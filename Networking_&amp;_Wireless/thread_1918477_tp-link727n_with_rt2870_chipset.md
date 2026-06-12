---
title: "tp-link727n with rt2870 chipset"
date: 2012-02-01
forum: Networking &amp; Wireless
---

### Post by ringo28 on 2012-02-01
Hi,

i have a tp-link WN727N usb adapter.
it has a rt2870 ralink chipset...

i did do from this link to activate:
[https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M#rt2800usb_driver](https://help.ubuntu.com/community/WifiDocs/Device/Tenda_W311M#rt2800usb_driver)

it works, but i must put every time manual.... how can i do to be automatical??

i did try download from ralink the driver but i cant compile.
i tryin so hard and my xubuntu crashes because of this.., 

i tryin on the chat but no solution i searching on the forum i dont know what too try... who got something???
gr ringo
(it works but i put it manualy as the site here above)

---

### Post by ringo28 on 2012-02-01
spam??? whats this ?

---

### Post by ringo28 on 2012-02-01
it solved :) pffff trying too search now find te good link , damnn link lost ....,

---

### Post by anymoose on 2012-03-20
HI! This is the definitive fix for Ubuntu 11.10 and TL-WN727N(V3)

Use this link (only) if kernel version is shown below; Ubuntu 11.10

ls /lib/modules

3.0.0-12-generic

Web Link;
[http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370](http://ubuntuforums.org/showthread.php?t=1903935&highlight=5370)

Use user Chili555 post #2. Everything is done in post #2 ie no files to download
no compilation, no other changes. This fix must be entered carefully; all spelling,
spaces and capital/lc letters *must* be correct. Worked for me after reboot. Test
your adapter with MS-Win XP with Included utility on CD ahead of time, if possible.

Not sure if this will work in Ubuntu live filesystem on CD for obvious reasons. Works
when filesystem is on HD disk and USB stick.

Signed; Anymoose

---

