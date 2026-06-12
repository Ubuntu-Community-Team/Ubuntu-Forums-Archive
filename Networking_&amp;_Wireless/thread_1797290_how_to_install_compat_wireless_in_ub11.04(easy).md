---
title: "how to install compat wireless in ub11.04(easy)"
date: 2011-07-04
forum: Networking &amp; Wireless
---

### Post by shaifeyna on 2011-07-04
i newbie.... plezz hlp... my wireless crd atheross not working... i try to install ath9k... but not working... pless give me right installation.. step by step... plezzzzzz :(

---

### Post by chili555 on 2011-07-05
Installing compat-wireless is not too difficult, however, it is no substitute for solving some other underlying problem. Before we install anything, let's take a few readings and see if we can figure out why ath9k won't work for you. Please open a terminal and run and post:```
rfkill list all
lsmod | grep acer
dmesg | grep ath
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by shaifeyna on 2011-07-06
thankzzz... i will try later.. now i'm running windows.. bcause i want to find how to use linux.. thankz again:)

---

### Post by shaifeyna on 2011-07-07
why my wireless is disable??? 
(wireless is disable by hardware switch)

---

### Post by chili555 on 2011-07-07
> **shaifeyna said:**
> why my wireless is disable??? 
(wireless is disable by hardware switch)It is disabled by hardware switch because either the switch is pressed to disable it or some module *thinks* it is pressed; likely acer-wmi. I have been trying to find out and it will help us both if you provide the information that I requested.

By the way, installing compat-wireless is not going to move the switch or correct acer-wmi.

---

### Post by shaifeyna on 2011-07-07
after that , what I need to do???

---

### Post by chili555 on 2011-07-07
Post it here so we can diagnose what's wrong by reading what it says. Post it!!

Once we figure out what's wrong, we'll do our best to fix it. We can do nothing until we see what's wrong.

---

### Post by shaifeyna on 2011-07-08
hehehehe!! sory.

it display this output

rfkill list all

0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: acer-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


lsmod | grep acer

acer_wmi               23123  0 
sparse_keymap          13666  1 acer_wmi


dmesg | grep ath

[    0.280283]  [<c104f912>] ? warn_slowpath_common+0x72/0xa0
[    0.280294]  [<c104f9e3>] ? warn_slowpath_fmt+0x33/0x40
[    1.291077] device-mapper: multipath: version 1.2.0 loaded
[    1.291080] device-mapper: multipath round-robin: version 1.0.0 loaded
[   14.536705] ath9k 0000:06:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   14.536713] ath9k 0000:06:00.0: setting latency timer to 64
[   14.972352] ath: EEPROM regdomain: 0x65
[   14.972356] ath: EEPROM indicates we should expect a direct regpair map
[   14.972360] ath: Country alpha2 being used: 00
[   14.972362] ath: Regpair used: 0x65
[   14.996149] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   14.997270] Registered led device: ath9k-phy0::radio
[   14.997382] Registered led device: ath9k-phy0::assoc
[   14.997457] Registered led device: ath9k-phy0::tx
[   14.997541] Registered led device: ath9k-phy0::rx

---

### Post by chili555 on 2011-07-08
Please see post #5 here: [http://ubuntuforums.org/showthread.php?t=1798972](http://ubuntuforums.org/showthread.php?t=1798972)

You have the same problem and I believe the same fix applies. Please post back if you need more help.

---

### Post by shaifeyna on 2011-07-08
thankzzzzzzzzz..... it work perfect... thankzzz u very much... hahaha... you so spectacular..  now i can learn ubuntu unhindered:popcorn:

---

### Post by chili555 on 2011-07-08
> **shaifeyna said:**
> thankzzzzzzzzz..... it work perfect... thankzzz u very much... hahaha... you so spectacular..  now i can learn ubuntu unhindered:popcorn:Glad to hear it's working. Please use thread tools at the top to Mark Solved.

---

