---
title: "Broadcom BCM4311 wireless not working"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by hooookup on 2009-01-04
I have just installed ubuntu on my parents laptop after having nothing but problems with Vista.
I did a clean install and was able to get my wireless broadband usb card(sprint) to work automatically but I can't get the wireless controller to work. The wireless button doesn't work and the light wont come on. 
I am very new to Linux... Please help!
Thanks in advance!!

Jerod

---

### Post by melojo on 2009-01-04
[http://ubuntuforums.org/showpost.php?p=6077792&postcount=72](http://ubuntuforums.org/showpost.php?p=6077792&postcount=72)

---

### Post by hooookup on 2009-01-04
Got to the last line
sudo ifconfig wlan0 up

and got this

bill@bill-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

What am I missing?
I followed the guide posted step by step

---

### Post by melojo on 2009-01-04
sorry it took so long to get back to you.

goto applications>accessories>terminal and post the ouput of 

```

lspci
sudo lshw -C network
ifconfig


```

---

### Post by hooookup on 2009-01-04
> **melojo said:**
> sorry it took so long to get back to you.

goto applications>accessories>terminal and post the ouput of 

```

lspci
sudo lshw -C network
ifconfig


```

No worries brother. I was able to get the sucker working. Thanks for your help and pointing me to that thread. 
J

---

### Post by superprash2003 on 2009-01-05
please mark this thread as SOLVED under Thread Tools

---

