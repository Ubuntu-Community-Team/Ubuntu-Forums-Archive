---
title: "Networking problem in ubuntu 10.04"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by zghaf on 2012-05-12
Hi,

I am using Ubuntu 10.04 and it was working fine until recently that I had problems with my graphic card which I fixed it and now I have problems with internet connection. I have no internet connection, no wireless no LAN. It is interesting for me since it was working two weeks ago and it suddenly stopped working. Also I don't have any problems in my windows. Can you please help me to find the problem? I can send you screen shots if you need me to run any commands... 

Thanks,

---

### Post by wildmanne39 on 2012-05-27
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

