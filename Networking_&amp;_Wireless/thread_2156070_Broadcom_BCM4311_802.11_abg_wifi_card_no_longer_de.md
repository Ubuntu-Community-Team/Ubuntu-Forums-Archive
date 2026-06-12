---
title: "Broadcom BCM4311 802.11 a/b/g wifi card no longer detected"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by afrocod on 2013-06-20
My first install of any linux system. The wifi was detected but had no drivers and so with a bit of trouble I found some terminal commands that would install them. I reboot and the drivers show up in synaptic but the network manager no longer detects the wifi card. I found 2 solutions 1. Turn the wifi switch on and off (didn't work no response) 2. terminal command "rfkill unblock all" to which I get "Can't open RFKILL control device: Permission denied"

I'm a complete novice so any help would be much appreciated...

Thanks in advance,

Cillian.

---

### Post by chili555 on 2013-06-20
> I found some terminal commands that would install them. Which commands? Also please post:```
lsmod | grep -e wl -e b43
```

---

### Post by afrocod on 2013-06-20
[FONT=Ubuntu Mono]sudo apt-get install b43-fwcutter firmware-b43-installer

[FONT=arial]In the process of reading another thread with a similar problem I tried some other commands (I can't find that thread anymore) and I lost my ethernet connection now every few minutes the loading wheel goes on the top right and says Wired network Disconnected you are now off line.

the commands were something to the effect of  rfkill unblock list all and ifconfig wlan0 up. I really wish I could find that thread now (It's disappeared from my history)

I reinstalled xubuntu from scratch to see if it would solve the problem but the ethernet is still not working. This hinders the length of what I can post from the output of terminal commands, I can't just copy and paste as i'm using another laptop to  write on this forum.

Anyway because I have reinstalled the drivers are gone now and the network manager is recognizing the wifi again but saying device not ready (firmware missing) which is what it said before.

lsmod | grep -e wl -e b43
b43                         342669   0
mac80211              436493   1   b43
cfg80211                178877   2   b43, mac80211
bcma                        25611   1   b43
ssb                           50691   1   b43


[/FONT][/FONT]

---

### Post by chili555 on 2013-06-20
You have two competing drivers and no firmware! Please get a temporary wired ethernet connection and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install linux-firmware-nonfree
```Reboot and tell us how it's working.

---

### Post by afrocod on 2013-06-20
That's what I was saying my ethernet was working and now it's not. I can't get it back working. I really wish I talked to you before I read those other threads. Can you troubleshoot the ethernet?

EDIT: Nevermind it's working now, thank god.... I'll try those solutions and get back to you. Thanks for all the help so far...

---

### Post by afrocod on 2013-06-20
@chili555 woooooo!!!! It's working, you're a genius. You wouldn't believe the amount of other threads there has been with the same problem and no solution. You give me a couple of lines of code and i'm away. Thank you very much for all your help....

---

### Post by chili555 on 2013-06-20
Glad it's working! Please mark the thread solved so that the searchers who follow you can find the key: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

