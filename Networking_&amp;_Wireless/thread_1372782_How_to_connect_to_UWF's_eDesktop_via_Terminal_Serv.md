---
title: "How to connect to UWF's eDesktop via Terminal Server Client"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by aaronchall on 2010-01-04
More for my own posterity than anything else, I thought I'd document here the way to get to eDesktop through linux (debian, ubuntu) at the University of West Florida (UWF), since they appear to only support Windows through their documentation on the University web site, and the link through Argus (the secure web site) doesn't work in Linux.  This is sometimes needed to use the University resources (libraries and computer programs) from remote locations, and otherwise a google search is fruitless.  I had to have a guy in the computer science department show me how to do it.  This may apply for other Universities with similar setups.  It was impossible for me to figure it out on my own, I had to go back to my old 9.04 partition to get the info...

1) Open Terminal Server Client (Applications>Internet>...)
2) Insert as follows:```
Computer: eDesktop.uwf.edu
Protocol: RDP
User Name: YOUR USERNAME
Password: YOUR PASSWORD
Domain: argonet
```
leave the other fields blank
3) OPTIONAL BUT RECOMMENDED click Save As and save it as a quick connect so you don't have to refer to this again.
4) Flip through the other tabs and configure as desired, and click Connect!

Good luck.

---

### Post by French t0ast on 2010-04-28
Hi, im glad to see someone else here uses ubuntu :o

But i tried what you said, and i get a error, I click details and get:


Autoselected keyboard map en-us
ERROR: getaddrinfo: Name or service not known. 

Im using 10.04

---

