---
title: "Wired ethernet [BSNL Broadband] not connected in Ubuntu 11.04"
date: 2011-08-27
forum: Networking &amp; Wireless
---

### Post by LavenderBlack on 2011-08-27
Hi. Im using Toshiba Satellite L640 installed with Ubuntu 11.04. My Internet connection is BSNL Broadband. Previously I was using Ubuntu 10.10 and my net connection was working fine but when i upgraded to 11.04, i couldn't connect at all. Also after upgrading, i installed Wireless driver, would that have created any problem?? 
I tried the following commands to connect.
```

lavender@lavender-Satellite-L640:~$ sudo pppoeconf
Plugin rp-pppoe.so loaded.
lavender@lavender-Satellite-L640:~$ pon dsl-provider
Error: only members of the 'dip' group can use this command.

```

Can anyone please help me???

---

### Post by wildmanne39 on 2011-08-27
Hi, run these commands and I will see if I can help you.
```
lspci -nn | grep -e 0280 -e 0200
```
```
sudo lshw -C network
```
```
rfkill list all
```
```
nm-tool
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by LavenderBlack on 2011-08-27
Hi
   Thanks for ur help.. I got the prob solved. :) I downloaded and installed the kernel packages from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/) and then run "sudo pppoeconf" and "pon dsl-provider", then ran update manager and restarted, prob got fixed.. :P


> **wildmanne39 said:**
> Hi, run these commands and I will see if I can help you.
```
lspci -nn | grep -e 0280 -e 0200
``````
sudo lshw -C network
``````
rfkill list all
``````
nm-tool
```and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by wildmanne39 on 2011-08-27
Hi, your welcome! I am glad it is working.

---

