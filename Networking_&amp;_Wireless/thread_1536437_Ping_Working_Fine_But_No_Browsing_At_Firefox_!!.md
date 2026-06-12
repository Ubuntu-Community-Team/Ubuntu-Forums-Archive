---
title: "Ping Working Fine But No Browsing At Firefox !!"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by mohamedyousri on 2010-07-22
Hi all , 

I am all new to Ubuntu and after installing it i can't browse any internet through firefox although ping is working good and downloading plugins to system to run MP3 or videos is also working fine but can't open any website through firefox and i tried the live cd of Ubuntu 10.4 at other PC and internet was working fine and firefox was working fine !!!! where is the problem ??!! 

can any one help

---

### Post by varunendra on 2010-07-23
Open terminal (System>Accessories>Terminal), enter and post outputs of the following commands:
```
ifconfig -a
```
```
route
```
```
sudo dhclient
```
```
cat /etc/resolv.conf
```

Also, log into the live session where you were able to browse internet, right-click on the NetworkManager applet (on the right corner of the upper panel)>click "Connection Information" and post the screenshot here (press 'Print Screen' button on keyboard to take the screenshot).
[In case of difficulties, simply run and post outputs of the commands as told above]

---

### Post by Iowan on 2010-07-23
[Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that discusses MTU and how to check/change. Sometimes it works better at 1492 - or even lower.

---

### Post by varunendra on 2010-07-25
> **Iowan said:**
> [Here]("http://ubuntuforums.org/showthread.php?t=1376506") is a thread that discusses MTU and how to check/change. Sometimes it works better at 1492 - or even lower.

Hmm.. No reply from mohamedyousri yet....
But reading the thread you provided link of was no less interesting than watching a one-day cricket match!! ;)

---

