---
title: "wifi not working"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by jwftm33 on 2013-03-10
I installed 12.04 and can not get my wifi to work. When I click on the wifi icon it says firmware missing. Can anyone help me with a solution to get wifi working.

---

### Post by Hadaka on 2013-03-10
hi please post the output of..

```
lspci -nn | egrep '0200|0280' 
```

thanks.

---

### Post by jwftm33 on 2013-03-11
Ok Here what i got 
austin@austin-Inspiron-6000:~$ lspci -nn | egrep '0200|0280'
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by jwftm33 on 2013-03-11
Here is my wireless script i believe
#!/bin/bash
#Script created by anewguy, tested by chili555 and edited by krytarik, llua and wildmanne39
exec > netinfo.txt 2> /dev/null
echo -e "\n*************** info trace ****************\n"
echo -e "\n\n**** uname -a ****\n\n"
uname -a
echo -e "\n\n**** lsb-release ****\n\n"
cat /etc/lsb-release
echo -e "\n\n**** lspci ****\n\n"
lspci -nnk | grep -iA2 net
echo -e "\n\n**** lsusb ****\n\n"
lsusb
echo -e "\n\n**** iwconfig ****\n\n"
iwconfig
echo -e "\n\n**** rfkill ****\n\n"
rfkill list all
echo -e "\n\n**** lsmod ****\n\n"
lsmod
echo -e "\n\n**** nm-tool ****\n\n"
nm-tool
echo -e "\n\n**** NetworkManager.state ****\n\n"
cat /var/lib/NetworkManager/NetworkManager.state
echo -e "\n\n**** NetworkManager.conf ****\n\n"
cat /etc/NetworkManager/NetworkManager.conf
echo -e "\n\n**** NetworkManager.conf-10.04 ****\n\n"
cat /etc/NetworkManager/nm-system-settings.conf
echo -e "\n\n**** interfaces ****\n\n"
cat /etc/network/interfaces | sed 's/wpa-psk [[:graph:]:]\+/wpa-psk <WPA key removed>/'
echo -e "\n\n**** iwlist ****\n\n"
[ -t 0 ] && sudo iwlist scan
[ ! -t 0 ] && gksudo iwlist scan
echo -e "\n\n**** resolv ****\n\n"
cat /etc/resolv.conf
echo -e "\n\n**** blacklist.conf ****\n\n"
cat /etc/modprobe.d/blacklist.conf
echo -e "\n\n**** dmesg ****\n\n"
dmesg | egrep 'air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|rt6|rt7|r818|r871|rtl8|tg3|ssb|wl|b43|bcma|brcm|b44|eth1|ndis|wmi|wlan0'
echo -e "\n\n**************** done ********************\n\n"
sed -i 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' netinfo.txt

---

### Post by jwftm33 on 2013-03-12
Can anyone help.

---

### Post by Hadaka on 2013-03-12
Hi, sorry for the late repy

please post the output of..

```
lsmod
rfkill list all
```
thanks

---

### Post by jwftm33 on 2013-03-12
Ok will do as soon as I reinstall unbuntu. Things i am trying caused my wired connection to go away.

---

### Post by Hadaka on 2013-03-12
Hi, since you are doing a re-install
please do..

```
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by jwftm33 on 2013-03-12
That did the trick wifi working but i get message additional drivers available, which is This package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4313-, BCM4321-,BCM4322-, BCM43224-, and BCM43225-, BCM43227- and BCM43228-basedhardware. should i activate it or am i good with terminal install of b43cutter I did.

---

### Post by Hadaka on 2013-03-12
Hi, thats normal.please ignore
that messege and do NOT load
any of those drivers or your wifi will
stop working.
on that note...
Glad to see you up and running.
please use thread tools and mark this SOLVED
Thanks.

---

### Post by jwftm33 on 2013-03-12
I don't see where you mark it as solved.

---

### Post by jwftm33 on 2013-03-12
Can someone tell me how to mark this as solved. I go to thread tools and does not have a solved button for me to click on.

---

### Post by Bucky Ball on 2013-03-12
The solved function in thread tools is currently broken due to upgrade. The workaround is to edit the first post in the thread, click 'Go Advanced' and then change the thread title's prefix to 'Solved' (instead of [ubuntu]). ;)

---

