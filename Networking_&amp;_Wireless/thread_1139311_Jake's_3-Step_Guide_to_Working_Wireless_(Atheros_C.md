---
title: "Jake's 3-Step Guide to Working Wireless (Atheros Cards Only)"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by asuastrophysics on 2009-04-26
ATTENTION:

if you are having problems with wireless drivers, and you have an Atheros built-in wireless card, (specifically AR5XXX card), **fear no more**

_Jake's complete guide to working wireless_

This is very simple, and I think everybody out there (to my knowledge) overlooks it. (Somebody correct me if I'm wrong here)

***the reason your wireless doesn't work is because madwifi doesnt work** 
in fact, somebody needs to just axe the madwifi project in my opinion, because *madwifi prevents the ath5/9k drivers from properly working*
and gives both new and old linux users a nightmare of trouble. I know people who have spent weeks trying to get wireless to work. You shouldn't have to. I really hope I save somebody from switching back to Windows, because I was about to, until I came up with this great idea

Step #1: Follow this Guide: 
[http://ubuntuforums.org/showpost.php?p=5545069&postcount=5](http://ubuntuforums.org/showpost.php?p=5545069&postcount=5)
(Even if you haven't already, follow it, because it eliminates any goof-ups you might have done during installation.

Step #2: Go to "Places" and select "Search for Files"
Look in Folder: File System 
"Select More Options" -> Add the "Show hidden and backup files" option from the drop-down menu.

Search for "madwifi" (without the parenthesis())

Now just delete every file that comes up. **All of them**. This unorthodox method gets rid of the stupid Madwifi drivers. 

Step #3: 
in terminal, ```
sudo nautilus
```
Navigate to /etc/modprobe.d/

Examine each file for the lines:
"blacklist ath5k"
"blacklist ath9k"
"blacklist ath_pci"
...and **delete those lines**
I know this might be a pain, but thank Madwifi for that! :lolflag:

Now in terminal:
```
sudo modprobe ath9k
```
```
sudo modprobe ath5k
```
```
sudo modprobe ath_pci
```

Shut down your computer. Turn it back on

DONE. 

Troubleshooting:
If after turning the computer back on, you still don't have wifi:
      1. Make sure the wifi switch/button is on
      2. Enter this into terminal to manually start your wireless:
```
sudo ifconfig wlan0 up
```

That's my two cents for the day. I really should've been studying for a calculus exam, but I thought saving hundreds from misery was probably more worth my time. 
:guitar:

Comments, Problems, Feedback:

---

