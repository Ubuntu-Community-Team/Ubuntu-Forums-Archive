---
title: "Ubuntu slows down too much when i get an internet connection"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by Tyke112233 on 2009-05-13
I am building my computer and am currently using Ubuntu 8.0.4 and when i connect to the internet everything slows down so much that it takes usually about 5 minutes to load apps, pages, and even has a delay of about 5-7 minutes between when i type and when the letters appear on the screen. if you know what is wrong then i will be greatly appreciative. Thank you.

---

### Post by Chudilo on 2009-05-13
How are you connecting to the internet?
How slow is your internet connection?
What sort of CPU are you running on ?

---

### Post by Tyke112233 on 2009-05-13
i connect wirelessly, my internet is pretty fast, the motherboard is a few years old but runs well, but the only problem is that i dont have a ton of ram, only 1 gig in there

---

### Post by kerry_s on 2009-05-13
swap network-manager for wicd, network manager is really screwed up right now with the changes to policykit.

sudo apt-get install wicd
or
use synaptic to install the gui way.

it will automatically remove network-manager and take it's place.

---

