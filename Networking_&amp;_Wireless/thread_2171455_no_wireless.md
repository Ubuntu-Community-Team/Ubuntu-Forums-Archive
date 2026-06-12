---
title: "no wireless"
date: 2013-08-30
forum: Networking &amp; Wireless
---

### Post by smoothedatol412 on 2013-08-30
hi i have ubuntu 12.10 on a new dell laptop i get a few months ago.. i have been able to pick up wifi before but since a few days ago and i cant pick up any wifi signals.. i can get ethernet but no wifi, i dont know if it is a driver issue or something else
i put a live disk of mint linux since it is "similar" to ubuntu linux
any idea how i might fix this problem??
thank you

---

### Post by houstonbofh on 2013-08-30
Is the WiFi "turned off?  If you have a dual boot, boot into windows and "turn on" the card.

---

### Post by smoothedatol412 on 2013-08-31
no wireless isnt even an option
it only shows wired (on/off), network setting
i dont have a dual boot.ubuntu is my only os on my laptop

---

### Post by prodigy_ on 2013-08-31
You might want to start here: [http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

Wi-Fi issues are quite common so there's a well detailed guide on how to troubleshoot them.

[Edit]: But there's one command that may be useful regardless of what wireless card you have. Open terminal and type:
```
rfkill list all
```
If your Wi-Fi is listed as hard blocked you'll need to enable it using hardware switch (usually there's a button for that).

---

### Post by varunendra on 2013-08-31
Besides what prodigy_ asked, please also post the outputs of -
```
lspci -nnk | grep -iA2 net
lsusb
lsmod
```

While posting the outputs, please wrap them into 'CODE' tags by clicking at **#** button at the top of the edit box to auto-generate the tags, then copy-paste the outputs in-between the generated tags pair. Thanks

---

### Post by houstonbofh on 2013-08-31
I am talking about a level BEFORE the os...  If the WiFi is turned off by a switch, BIOS setting, or softswitch, (thank you Dell) turning it back on again in Linux can be a challenge.  Is there a WiFi switch somewhere on you laptop?  Is it on?

---

### Post by smoothedatol412 on 2013-09-01
no there isnt if you know have had an old dell as i have had there isnt a switch like the old laptops had


**output**
atol412@PC:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Dell Device [1028:0597]
    Kernel driver in use: r8169
atol412@PC:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 8087:07da Intel Corp. 
Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 001 Device 005: ID 064e:812e Suyin Corp.

---

### Post by smoothedatol412 on 2013-09-01
i really suck at hardware i am just a programmer in college trying to get my degree i still have wire ethernet but wireless would be very nice incase i stop by the local starbucks for a fix to keep me up on some late night porgramming project

---

### Post by varunendra on 2013-09-01
Neither lspci, nor lsusb shows any wireless device. This indicates, at best a loose connection and at worst - the possibility of wifi card failure.

A couple of things you can try are -
1) try resetting BIOS to factory defaults (or optimized defaults, whatever your BIOS calls it)
2) pull out --> re-seat the card in its slot *(if it is in a user-accessible area, else you'll need to open the case which is not recommended if you are not comfortable with it)*.

I can't think of anything else with the kind of results we have here.

---

### Post by smoothedatol412 on 2013-09-01
do you know how to Uninstall the Dell WLAN Management software in ubuntu?

---

### Post by varunendra on 2013-09-01
How did you install it?

If it came as a self contained compile-install type package, there should be an instructions file in it describing the install-uninstall procedure. If it came as a debian package, the steps would be dependent on how you installed it.

---

### Post by smoothedatol412 on 2013-09-03
sorry what?
idk if i should just send it back to dell since it still is under warranty but i would like to try to solve this issue on my own not be without a computer at home for a week or two
i may not buy another dell since this is the 2nd time this has happened (networking issues)

---

