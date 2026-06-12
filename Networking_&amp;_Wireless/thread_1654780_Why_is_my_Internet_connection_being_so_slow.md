---
title: "Why is my Internet connection being so slow?"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by Jammanuser on 2010-12-28
I just recently (a few months ago) purchased a Qwest modem and High-Speed Internet service. They told me I would be getting an approximately 7MBs per second fast download. When I first got it, it seemed pretty fast (at least compared to what I was used to), but now it seems to be extra slow and I don't know why. I'm using a wired ethernet connection, and I just ran a test at Speedtest.net to see how fast my current connection was, and learned its only 2.08 MBs/s fast on download and 0.02 MBs/s fast on upload.

Why the sudden and severe drop in speed? I hope someone here knows how to resolve this issue ASAP.

Thanks in advance.

-Jam Man

:guitar:

EDIT: And oh, I'm running Ubuntu 8.10 on a Dell Studio 1535 laptop, just in case anyone needs this information.

---

### Post by wilee-nilee on 2010-12-28
I have a Qwurst set up have you tried just rebooting the router, mine slows down on occasion and this seems to get it back up.

---

### Post by Jammanuser on 2010-12-31
> **wilee-nilee said:**
> I have a Qwurst set up have you tried just rebooting the router, mine slows down on occasion and this seems to get it back up.
Thanks for the suggestion. Resetting it resulted in a considerable speed boost. :popcorn:

Download speed now (according to Speedtest.net): 5.52 MBs/s
Upload speed now (according to Speedtest.net): 0.72 MBs/s

However, this is still way less than what its supposed to be. Any other suggestions?

---

### Post by elbanaan on 2011-02-17
A reason might be that the rate is not set properly (which was the case with my install OOTB):

try:

sudo iwconfig eth1 rate 54M
(or eth0 or whatever your connection is called - do iwconfig to see)

---

### Post by trooperchix on 2011-02-20
This helps, but it is still slow..

---

