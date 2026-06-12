---
title: "Broadcom BCM43225 not working on Acer Laptop"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by afinnarn on 2013-07-05
Hello, 

I have been poking around these forums and trying to solve my wireless card problem but to no avail. I'll list what I know so far, and hopefully one of you wizards/unicorns can help me. 

```
lspci -nn | grep 0280

02:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)

```

```
/sbin/iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.

```

Under additional drivers it says: "Using Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source (proprietary)"

I was following another thread ([http://ubuntuforums.org/showthread.php?t=2159289](http://ubuntuforums.org/showthread.php?t=2159289)) with the same 14e4:4357 ID and was hopeful until it was solved without solving my problem. I did try:

[COLOR=#000000]Hi, give this a try..[/COLOR][COLOR=#000000]

```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```[/COLOR]
[COLOR=#000000]
boot[/COLOR]
[COLOR=#000000]then do..[/COLOR][COLOR=#000000]

```
sudo modprobe -rf wlsudo modprobe wl
```[/COLOR]
[COLOR=#000000]
[/COLOR]but only got "FATAL: Module wl not found." as a response.

Any help would be appreciated as I am stumped as to what to do.

---

### Post by Hadaka on 2013-07-05
Hi, please do..
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```
*If it does not come to life, then please post..
```
rfkill list all
lsmod
```
thanks

---

### Post by Hadaka on 2013-07-05
@goatropeaz
Hi You may have an acer computer but not a braodcom card.
This thread is for a broadcom problem,
you have the ath9k card. Please start a new thead with your
issue.
thanks.

---

### Post by afinnarn on 2013-07-05
Hallelujah, it works! Thanks to @Hadaka for those commands, and hopefully this thread will help others with a similar problem.

...I don't know how to mark this thread as solved though...noob.

---

### Post by BlinkinCat on 2013-07-05
Hi,

Here is how you mark your first post as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by Hadaka on 2013-07-06
Great ! glad that worked for you.
how to mark solved -> [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
thanks.

---

