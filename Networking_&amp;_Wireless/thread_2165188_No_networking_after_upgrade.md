---
title: "No networking after upgrade"
date: 2013-08-03
forum: Networking &amp; Wireless
---

### Post by Last_Ship on 2013-08-03
I've just upgraded my Xubuntu to 13.04 on my Dell Latitude D610. Since the upgrade, networking seems to be completely disabled. The "enable networking" option is checked but no wifi connections appear. Ethernet is also not detected when plugged in. Since the upgrade I've also noticed a crash report notifier "The application software updater has closed unexpectedly" More specifically, "Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies". Not sure if that's related to the networking issue or not.

I apologize if this has been covered on here already, but I have been unable to find a related threat. Thanks in advance.

---

### Post by Last_Ship on 2013-08-11
Anyone have any ideas? As an added note, i dual boot this machine with Windows XP and have no trouble connecting to the internet there.

---

### Post by wildmanne39 on 2013-08-11
*Thread moved to **Networking & Wireless**.*

---

### Post by carlexpc on 2013-08-12
> **matt2422 said:**
> I've just upgraded my Xubuntu to 13.04 on my Dell Latitude D610. Since the upgrade, networking seems to be completely disabled. The "enable networking" option is checked but no wifi connections appear. Ethernet is also not detected when plugged in. Since the upgrade I've also noticed a crash report notifier "The application software updater has closed unexpectedly" More specifically, "Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies". Not sure if that's related to the networking issue or not.

I apologize if this has been covered on here already, but I have been unable to find a related threat. Thanks in advance.

The BrokenCount error is caused by an unfinished system upgrade. Try connecting to your network using a wired interface and complete the system upgrade from there.

---

### Post by Last_Ship on 2013-08-19
Well that's the problem, even when plugged into the wire interface the connection is not recognized. Any thoughts? Thanks.

---

### Post by Hadaka on 2013-08-19
Hi, please post the output of..
```
lspci -n | egrep '0200|0280'
lsmod | grep wl
```
thanks

---

### Post by Last_Ship on 2013-08-19
Here's the output of that:

mimi@mimi-Latitude-D610:~$ lspci -n | egrep '0200|0280'
02:00.0 0200: 14e4:1677 (rev 01)
03:03.0 0280: 8086:4223 (rev 05)


mimi@mimi-Latitude-D610:~$ lsmod | grep wl


mimi@mimi-Latitude-D610:~$

---

### Post by Hadaka on 2013-08-19
Hi, your wired connection uses the tg3 driver
im not sure yet what your wireless is. Let's try this..
post the output of..
```
rfkill list all
```
then do.. with wired connected.
```
rfkill unblock all
sudo modprobe tg3
```
Your wireless is an Intel card driver ipw2200
```
 sudo modprobe -r ipw2200
sudo modprobe ipw2200
```
I suspect you may have to reload 13.04 after re-reading your first post
sounds like you have some needed missing items.
any improvement?

---

### Post by Last_Ship on 2013-08-20
Here's the output of that:
mimi@mimi-Latitude-D610:~$ lspci -n | egrep '0200|0280'
02:00.0 0200: 14e4:1677 (rev 01)
03:03.0 0280: 8086:4223 (rev 05)
mimi@mimi-Latitude-D610:~$ lsmod | grep wl
mimi@mimi-Latitude-D610:~$ 

I'm guessing this is a driver issue then? You think i'm best off just reloading 13.04?

---

### Post by Last_Ship on 2013-08-20
Sorry, wrong output. Here's the most recent:
mimi@mimi-Latitude-D610:~$ rfkill list all


mimi@mimi-Latitude-D610:~$ rfkill unblock all


mimi@mimi-Latitude-D610:~$ sudo modprobe tg3


[sudo] password for mimi: 


FATAL: Module tg3 not found.


mimi@mimi-Latitude-D610:~$ sudo modprobe -r ipw2200


FATAL: Module ipw2200 not found.


mimi@mimi-Latitude-D610:~$ sudo modprobe ipw2200


FATAL: Module ipw2200 not found.

---

### Post by Hadaka on 2013-08-20
Hi, both tg3 and ipw2200 are driver modules and should
already be in the 13.04 load. since you have missing dependencies
(files that other files depend on) your current 13.04 load seems to be
corrupt. The best way to correct this is to reload 13.04. Sorry I have no
other suggestions for you.
Good luck !

---

### Post by Last_Ship on 2013-08-23
Thank you, I do appreciate the help.

---

