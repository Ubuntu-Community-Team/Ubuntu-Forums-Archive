---
title: "Can't print to network printer"
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2012-03-11
I have a Samsung SCX4826FN MFD to which I print from our Windows, Apple and Ubunutu 10.04 computers. I am setting up a new 10.04 computer on the network and am stumped at making this new computer print to the Samsung. Can't for the life of me remember how I got it installed on the other 10.04.

When I use System/Administration/printing, it finds the printer just fine, but cannot find the drivers.

I have downloaded the drivers from the Samsung site and unpacked them. At the top of the extracted directory " cd root " is a file (autorun) and a directory (Linux). In the Linux directory are, among others, install.sh and installer.htm.

I have tried installing using Gnome, and the Console, using everything I can think of but I am not getting anywhere. I cannot seem to find a command that executes an install process.

Can anyone step me through this process so that I can understand it please? Thanks.

---

### Post by Odyssey1942 on 2012-03-11
Finally got it. Ran:
```
sudo cdroot/autorun
``` from the directory just above cdroot which started the install program.

Working now.

---

