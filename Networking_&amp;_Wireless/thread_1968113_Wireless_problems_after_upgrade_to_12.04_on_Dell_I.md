---
title: "Wireless problems after upgrade to 12.04 on Dell Inspiron 6400"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by Douginho1990 on 2012-04-28
Last night, I upgraded to 12.04 on my Dell Inspiron 6400 and since then the wireless function of the laptop hasn't been working. I've looked at other threads and tried to run the same fixes but to no avail. Any help would be appreciated.

---

### Post by Douginho1990 on 2012-04-30
Bump

---

### Post by nateisen on 2012-08-01
My Inspiron has no hard drive, so I am running Ubuntu from a USB stick.  I chose the option to allow space to save files when I made the stick.  I've tried the fix with b43 (checked my model number and all that).  I tried simply activating the driver, but it gives a jockey log with a lot of errors.  From what I can tell, the files are not where they used to be or something.  Is getting this driver, especially using a Live USB option, even a possibility?

---

### Post by wildmanne39 on 2012-08-01
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # then paste the information between the brackets.
Thank you

---

