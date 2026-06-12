---
title: "Cannot connect wifi netgear router to ubuntu 11.04 !"
date: 2011-11-09
forum: Networking &amp; Wireless
---

### Post by srj555 on 2011-11-09
I have netgear wireless router WGR614v7 . Have connected it successfully in windows vista ,
Tried setting up new wireless connection by giving correct specifications , but not working !

Have checked rfkill command and wifi is turned on !

---

### Post by wildmanne39 on 2011-11-09
Hi, welcome to the forum! it is most likely you need a driver for your wireless card.
Please post the results of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by srj555 on 2011-11-09
[SIZE=4][B]INSTALLING b43 driver help me solve the problem . 

sudo apt-get install firmware-b43-installer

[/B][/SIZE]

---

### Post by deltacomp on 2011-11-09
Hello, I found this script to work when I had wifi problems. Open the [link]("http://pastebin.com/raw.php?i=RHSv9w8y"), then copy and paste the script into to a new text document, save it as wifix in your home folder. Then open a terminal and type sudo bash wifix (hit enter). This will attempt to install a lot of different drivers. Good luck.
[URL="http://pastebin.com/raw.php?i=RHSv9w8y"]
[/URL]

---

### Post by wildmanne39 on 2011-11-10
Hi, I am glad you have it working.
Enjoy

---

