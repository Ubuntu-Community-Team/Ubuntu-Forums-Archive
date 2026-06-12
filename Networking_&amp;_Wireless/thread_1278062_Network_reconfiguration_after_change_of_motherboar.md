---
title: "Network reconfiguration after change of motherboard"
date: 2009-09-29
forum: Networking &amp; Wireless
---

### Post by jthuemmler on 2009-09-29
Hi,

I used a via CIII board with xubuntu with network onboard (eth0) and usb nw-adapter (eth1). Now I changed to intels atom board, of course with another onboard nw. Ifconfig calls it eth3 (or pan0, but it seems to me, pan0 is something else, only don't know what). 
Network manager doesn't find any sufficent way to work with the card, not as fixed-ip nw and also not as (a)dsl. pppoe-config doesn't see the adsl nac, testing eth3 and pan0 too.

As I'm mostly on Suse, I don't know clearly how to configure network on xubuntu, first i would like to delete the somewhere hidden old entries which seem to disturb the thing...

thx for any idea

cu jth

---

### Post by kerry_s on 2009-09-29
you need to go into /etc/udev/rules.d/70-persistent-net.rules

delete the devices & reboot so it can be detected a new.

---

### Post by jthuemmler on 2009-09-29
Hi & Thx,

I did this (I first only deleted the entry of the old card, so I found eth0 but doesn't work).
Now I get an "auto eth0" - configured this, doesn't work either. Checked with sysrescueCD - nw adapter works properly.
So I deleted the auto eth0 entry fully and added manual a new "wired connection", and - now it works. Strange all this...

By the way - what meaning has the "System setting" checkbox on first tab (just under "connect automatically" - sorry, I have a german system, so don't know  how are the real english names of the 2 checkboxes on the "edit" window). I couldn't discover it's use.

thx & cu jth

---

