---
title: "No internet after reboot (PPPoE)"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by hamunator on 2010-07-19
Yesterday I installed Ubuntu 9.10 (first time in my life) and conigured internet with pppoeconf. I entered username, password and pressed "yes" and "ok" in the other windows. Anything was ok, internet worked good. I rebooted couple of times, internet was ok.

Today I turned on the computer and there was no internet. plog outputted something like "CHAP authentication failed, unit [number]". I ran pppoeconf again, nothing changed, only the number became different. I thought I could be a provider's problem, but when I booted form LiveUSB and ran pppoeconf, internet was ok.

I changed nothing in the system, just installed a couple of packages, updates and the Russian language.

What can I do to solve the problem?

---

### Post by dineshs on 2010-07-20
Please try this
[COLOR="Blue"]_STEP-I_[/COLOR]
First backup  /etc/network/interfaces using
```
sudo cp /etc/network/interfaces /etc/network/interfaces.bak
```
Now run
```
 gksudo gedit /etc/network/interfaces
```
Let the file contain only these lines ```
auto lo
iface lo inet loopback
```
[COLOR="Blue"]_STEP-II_[/COLOR]
Run ```
sudo service network-manager restart
```or restart PC
[COLOR="Blue"]_STEP-III_[/COLOR]
Cnfigure your connection as in this link
[http://ubuntuforums.org/showpost.php?p=9611335&postcount=9](http://ubuntuforums.org/showpost.php?p=9611335&postcount=9)

---

