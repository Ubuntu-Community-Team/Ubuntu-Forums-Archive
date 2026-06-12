---
title: "wi fi speed hopeless on acer aspire"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by Jacko57 on 2013-04-01
All good in connection to router,with wi fi ,but can not achive a speed over 1mps  hard wired great
acer aspire intel 1000 bgn card

---

### Post by startas on 2013-04-01
Yeah, linux kernel is a big pains in the ass :) Just try another version of kernel - older/newer, because some kernel versions just breaks wifi, speed is jumping like crazy, and after a little bit wifi is gone... common problem on all my laptops, you just have to find a working kernel version.

---

### Post by wildmanne39 on 2013-04-01
Please try to fix the driver you have before trying a new kernel. 
Copy and paste this command in the terminal (ctrl+alt+t) please:
```
wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a text file in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the netinfo.txt file.

I am ging to be off most of the day due to my daughters surgery out of town so hopefully someone will stop by and read the results and be abe to fix your issue.
Thanks

---

### Post by Jacko57 on 2013-04-01
[ATTACH]240817[/ATTACH]

---

### Post by wildmanne39 on 2013-04-01
Please do what is in the folowing link in post 13.
[http://ubuntuforums.org/showthread.php?t=2079078&page=2](http://ubuntuforums.org/showthread.php?t=2079078&page=2)
Also set your wireless settings in network manger to match the screenshots.
Thanks

---

### Post by Jacko57 on 2013-04-01
You are the Daddy!
Cheers
Goodbye Windows 8

---

### Post by wildmanne39 on 2013-04-01
Glad to help, thanks to chili555 I manage to get one right now and again.:)
Enjoy

---

