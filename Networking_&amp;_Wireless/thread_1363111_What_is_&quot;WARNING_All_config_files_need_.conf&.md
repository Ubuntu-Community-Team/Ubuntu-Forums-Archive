---
title: "What is &quot;WARNING: All config files need .conf&quot;?"
date: 2009-12-24
forum: Networking &amp; Wireless
---

### Post by MelRia on 2009-12-24
Hello all;
I have been trying to fire up my internal WLAN card on my Dell laptor . 
Recently installed Ubuntu, along with MS vista.
*** you see below I have installed the Wireless card but cant  pull it up. could you help please?
[B]

mel@Mel-laptop:~$ sudo ndiswrapper -l
[sudo] password for mel: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
bcmwl5 : driver installed
    device (14E4:4315) present (alternate driver: ssb)
mel@Mel-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
mel@Mel-laptop:~$ ^C
mel@Mel-laptop:~$ [/B]

---

### Post by KeLa on 2009-12-24
That error message means that you have file named blacklist when it needs to be named blacklist.conf

---

### Post by MelRia on 2009-12-24
Thanks for the reply, 
That I installed from a 3rd part, now how can I change it plz? do you think that's why my WLAN doesn't come up?
Thanks again.

---

### Post by KeLa on 2009-12-24
on terminal run

```
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf

```or 
```
sudo rename /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf

```it will ask your password and then rename the file.

---

### Post by MelRia on 2009-12-24
buddy; 
changing the tag name, the folder got lost and lost conection. What i'm gonna do is, I will start over ha? what do you think? all I wanna do is to get the WLAN running.

---

