---
title: "Acer wireless and Broadcom - HELP!"
date: 2011-06-29
forum: Networking &amp; Wireless
---

### Post by Jh60082 on 2011-06-29
Hi all! It has been a while since I posted and sadly I am here to report an issue. I installed Ubuntu 11.04 on an Acer Travelmate 290E computer. The installation went fine and everything was up and running until I wanted to use the wireless.

1. I got the "firmware not installed message" and installed the Broadcom b43 firmware. 

2. I receive a new message: " wireless is disabled by hardware switch" (My acer does have a wireless switch that is switched to on.

3. After hours of research I tried to install Acer ACPI but my laptop model is not supported. I assume Ubuntu knows my wireless is there but thinks it is turned off, and the wireless switch can't communicate to Ubuntu properly.

This is where I am stuck.

ANY advice will help

I have already tried rfkill and all that good stuff. Doesn't work for me, Wireless is still hard blocked. Thanks in advance!

---

### Post by bkratz on 2011-06-29
> **Jh60082 said:**
> Hi all! It has been a while since I posted and sadly I am here to report an issue. I installed Ubuntu 11.04 on an Acer Travelmate 290E computer. The installation went fine and everything was up and running until I wanted to use the wireless.

1. I got the "firmware not installed message" and installed the Broadcom b43 firmware. 

2. I receive a new message: " wireless is disabled by hardware switch" (My acer does have a wireless switch that is switched to on.

3. After hours of research I tried to install Acer ACPI but my laptop model is not supported. I assume Ubuntu knows my wireless is there but thinks it is turned off, and the wireless switch can't communicate to Ubuntu properly.

This is where I am stuck.

ANY advice will help

I have already tried rfkill and all that good stuff. Doesn't work for me, Wireless is still hard blocked. Thanks in advance!

Check out this thread and especially see if acer-wmi is installed. See post 2.

[http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi](http://ubuntuforums.org/showthread.php?t=1790646&highlight=acer-wmi)

---

### Post by Jh60082 on 2011-07-01
Ok I followed the advice exact but now my wireless connection doesn't even show up.
Also acer-wmi is not installed on my computer.

---

### Post by garvinrick4 on 2011-07-01
Post the results of these so users can see what they are dealing with.
```
sudo lshw -C network
```
```
rfkill list
```

---

