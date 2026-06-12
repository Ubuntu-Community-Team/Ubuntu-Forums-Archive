---
title: "Is ndiswrapper incompatible with 2.6.24 kernel?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by shelbyvision on 2009-04-30
I recently upgraded my HP laptop P4 from gutsy to hardy, using the update manager. Now if I restart the computer, there is no internet connection after rebooting. There are two ways I can get my wifi card (a U.S.Robotics MAXg) to work: 1. pull out the card before rebooting, then put it back after the system is completely up, signed in and all. I just put it in and the lights light up and everything works normally. 2. Boot up with "Ubuntu 8.04.2, kernel 2.6.22-16-generic", and all works normally.
When I installed the wireless card, in 7.10, I had to use ndiswrapper 1.50, which was the latest version at the time. Would a newer version correct this problem, or is there something else I need to do? I really don't know much about this stuff, so I need all the help I can get.
Thanks,
Steve

---

### Post by shelbyvision on 2009-05-01
Waiting for a reply...

---

### Post by shelbyvision on 2009-05-01
I was reading through the "Comprehensive ndiswrapper troubleshooting guide" which is at the top of this forum, and found this by pytheas22 on page2:

[I]Code:

sudo gedit /etc/modprobe.d/blacklist

and add these lines to that file:
Code:

blacklist b43
blacklist ssb
blacklist b43legacy
blacklist b43 ssb

Then save the file, and reboot.

[/I]

I did this and it worked! Apparently the newer kernel was disabling ndiswrapper on bootup by supplying the wrong driver instead. Thank you, pytheas22! :P

---

