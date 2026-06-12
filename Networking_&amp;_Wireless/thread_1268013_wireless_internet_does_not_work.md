---
title: "wireless internet does not work ?"
date: 2009-09-16
forum: Networking &amp; Wireless
---

### Post by Trimex on 2009-09-16
hello their ;)

a good friend of me that is of to paris for studing has a problem !

she has dualboot vista and linux.

on her vista she can recieve every wireless internet in paris
but linux ubuntu does not find any connection :s

how can she fix this ?

ty very much ;)

---

### Post by jdripper on 2009-09-16
This is one very vague post, but I'll give it a shot anyway:

Get the output of the following run in a terminal :
```

lshw -C network

ifconfig -a

iwconfig

netstat -rn

for i in  `cat /etc/resolv.conf |  grep "[0_9]\.[0-9]" | awk '{print $2}'`; do ping -c 3 $i; done
(one long line, you might want to copy and paste this one, not the easiest to type if you're not familiar with the shell, Ctrl+C and edit->paste in the terminal window)


```

---

### Post by vogia on 2009-09-16
welcom

you are using a rt2860 Ralink chipset for your connection
see in this thread:
[http://ubuntuforums.org/showthread.php?t=683085](http://ubuntuforums.org/showthread.php?t=683085)

---

### Post by Trimex on 2009-09-16
ty , i wil give it to her, and if its not working , il post some more details :D

ty alot ;)

---

