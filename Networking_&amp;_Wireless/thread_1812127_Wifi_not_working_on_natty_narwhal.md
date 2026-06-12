---
title: "Wifi not working on natty narwhal"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by shadowhooves on 2011-07-25
I have a Broadcom BCM4318 that isn't working with the B43 or the other (I tried installing both and while they supposedly installed successfully, neither shows up in the Additional Drivers tab for me to enable.) I tried using both sets of directions stickied up at the top of this forum. Neither seems to be working for me (no guarantees on whether I did it right) though the B43 is apparently the one I need. Help!?

Disclaimer: I'm a total newbie to using command line and a new convert from Windows so I'm rusty at navigating and making things work, though things are finally starting to make a little sense after two days of hacking at it. Any help is appreciated, using small words! Thanks.

---

### Post by wildmanne39 on 2011-07-25
Hi, let have a look at the issue, please run these commands in terminal
```
sudo lshw -C network[CODE]
[CODE]lspci -nn | grep 0280
```
```
lsmod
```
```
iwconfig
```
```
rfkill list all
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by garvinrick4 on 2011-07-25
If you want you can open Synaptics package manager and type "bcm" without qoutes
in upper right hand search window. See the 2 I have highlighted in screenshot. (click on
screenshot) Those are two needed and uninstall others. Then take wired cable out and reboot.
If still gives problems give post 2 his feedback so as to evaluate your situation with card and driver.

---

### Post by shadowhooves on 2011-07-26
IT WORKS!!! Thank you. I guess that kernel thing at the top of the list was installed and shouldn't have been? So I uninstalled it and reinstalled the other two. I've been using too many sets of directions. :D

---

### Post by wildmanne39 on 2011-07-26
Hi, I am glad you got it working,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Dustonio on 2011-07-28
Excellent solution! I had the same problem as described and the fix worked for me too. Thank you for posting this. The screen shot was very helpful by the way.

---

