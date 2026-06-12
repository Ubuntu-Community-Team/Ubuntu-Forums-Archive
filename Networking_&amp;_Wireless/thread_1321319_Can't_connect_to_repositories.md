---
title: "Can't connect to repositories"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by eyrezer on 2009-11-09
I'm new to ubuntu. Installed 9.04 about a month ago and thought it was great. I then did a clean install to 9.10. The initial problem was that it would connect to the internet but not load at all or very slowly. I disabled IPv6 and can now connect to the internet; however, I am unable to access any repositories. When I tried to add medibuntu, the only response I get is:
[INDENT]W: Failed to fetch [http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb](http://packages.medibuntu.org/pool/free/m/medibuntu-keyring/medibuntu-keyring_2008.04.20_all.deb)
[/INDENT][INDENT] Could not connect to packages.medibuntu.org:80 (1.0.0.0), connection timed out

[/INDENT]Any suggestions on how to resolve this?

~ Eyrezer

---

### Post by jerrrys on 2009-11-10
assuming that you have added medibuntu to your source list.  #1 try **sudo apt-get update **in terminal
#2 try another download source[B].

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[/B]

---

