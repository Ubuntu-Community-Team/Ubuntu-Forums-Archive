---
title: "Wireless does not work"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by Cloud Wolf on 2010-01-26
Hey,

I have used ubuntu in the past, on my main desktop. On my new netbook (HP Compaq 311c - 1010SA Varient) I can not access wireless connections. I am guessing it is something to do with my wireless card by browsing these forums, but I am not techie enough to understand what it is :S
I think it is a Broadcom one, from following commands in other threads.
What can I do to sort this out? I am fed up of having a LAN cable trailing across the floor from my router. I need it put into fairly simple terms!

P.S.
In regards to the above broadcom thing, the command and output were:
```
$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```

and in case its any use, I found this command floating round the forums aswell:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

---

### Post by bkratz on 2010-01-26
You might want to look at this thread

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

### Post by Cloud Wolf on 2010-01-29
Sorted, Thank you! I had a play with guidance from that thread, and it solved my problem, thanks again!

---

