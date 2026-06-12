---
title: "Issues with iwl3945 on Ubuntu 8.10"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by npace on 2009-01-05
Hello,
I'm having a very annoying issue with the iwl3945 driver in intrepid. It's pretty slow. I can't seem to be able to get more than 3-4 Mbps out of it. From what I've read - iwl3945 simply sucks.
I've tried ndiswrapper with the windows driver and it works fast but cannot connect using WPA2.
I've tried compiling the ipw3945 (deprecated driver) but gave up because I could not get it to compile.

How do you (that have intel 3945 ABG cards) deal with this issue?
Has anyone been able to use ndiswrapper with this card and have WPA2 working?

---

### Post by hamletmonkey on 2009-02-18
I agree - I have found it to be slow and often will not work after a suspend.

Would love to hear about other options.

---

### Post by okaar on 2009-03-24
the option that works is ndiswrapper
but if you are interested in the monitor mode, you cant get it with it

---

