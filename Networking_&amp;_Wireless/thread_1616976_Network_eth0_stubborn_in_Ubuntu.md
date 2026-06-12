---
title: "Network eth0 stubborn in Ubuntu"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by egkeat on 2010-11-08
I'm kind of tired of the internet connection dropping.  I've recently upgraded to 10.10 and am having the same problems as with all the previous versions.  I have no eth0 connection at this moment, only lo. I have an Hp pavilion about three years old with a onboard ethernet, connected to router and wired broadband.  The thing is, when I am in Windows, the internet will also drop, going into "local only." I can always get that back though by running the network diagnose.

Another thing.  How to I get into the network.state file to make changes?

---

### Post by egkeat on 2010-11-08
Well, I tried ifconfig eth0 up and it came back permission denied.  I've tried restarting several times (that used to work 10.04).  Nothing. My internet connection in Ubuntu is dead. I cannot even get it back by restarting network manager or modifying network interfaces. Nothing works!

---

### Post by uncaspi on 2010-11-08
Dont give up. You must run ifconfig as root.

sudo /sbin/ifconfig eth0 up

Please post the output of sudo /sbin/ifconfig   and dmesg

---

