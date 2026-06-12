---
title: "wlan not working on a Asus F5R"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by knbo on 2009-07-27
:(                                  Trying to install Ubuntu 9.04 on an Asus F5R. Everything  function fine, except the wlan. Lspci provide the card to be: Broadcom Corporation BCM4311, but Asus provide: AzureWave GE-780. Adding the Broadcom STA driver, the computer find thenetwork, but can not log on. I do try to set up the original driver from Asus with ndiswrapper, but that does not function at all. Is there any solution to this problem.:confused:

---

### Post by Sandhje on 2009-08-13
Same problem here! Would really like to hear if anybody finds a solution. As soon as I do I'll post it!

---

### Post by superprash2003 on 2009-08-13
post output of
1)sudo iwlist scanning
2)iwconfig

---

### Post by Sandhje on 2009-08-14
Hi,

With the help of a post on Launchpad forum I could solve my problem. If you have an ASUS F5R with BCM4311 rev01 wireless chipset, just type the following command in your terminal and you will be able to connect to the internet! :KS:KS:KS

[INDENT]sudo echo 1 | sudo tee /sys/devices/platform/asus-laptop/wlan
[/INDENT]
To make sure you don't have to do this every time you boot, just open the terminal and do the following:

[INDENT]gksudo gedit /etc/rc.local

[/INDENT]then before the line "exit 0" paste:

[INDENT]echo 1 | tee /sys/devices/platform/asus-laptop/wlan

[/INDENT]With thanks to stenlikobra1 at launchpad :)
[http://answers.launchpad.net/ubuntu/+question/71530](http://answers.launchpad.net/ubuntu/+question/71530)

Hope this helps anyone :cool:

---

