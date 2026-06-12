---
title: "Koala DSL connection problem x64"
date: 2009-11-28
forum: Networking &amp; Wireless
---

### Post by dragomir on 2009-11-28
Hi all. That's my first post here and I start with a problem - sorry for that.

I recently installed Ubuntu 9.10 Karmic Koala  and tried to establish a DSL connection through the Network Manager. I set my username and password for the new connection and saved it but it did not connect. It did not even show my connection as available through the left-click network manager menu.
I read somewhere in here that it is a common problem with Koala and some of you suggested downloading some new network-manager packages from launchpad to solve the problem but the links were for x86 and I am using the x64 version.

I am really new to Linux although I did use Ubuntu 7.10 (with no internet connection problem) 2 years ago.

Would someone suggest a solution for me, please ? If you think the problem can be solved with the above mentioned network manager packages would you give me download links to them because I really don't know what to look for.

Thank you.

edit: Changing [ifupdown] managed=false to true in  /etc/NetworkManager/nm-system-settings.conf resolved the issue. No thanks to ubuntu  community though.

---

### Post by rksingh54 on 2009-12-05
I too am using Ubuntu 9.10 and having a lot of problem connecting DSL to Karmic to reach Internet. 

It was easily connecting with 9.04 but 9.04 was flaky with HP  Broadcom Wireless. Need real help to solve this problem.

RKS

---

