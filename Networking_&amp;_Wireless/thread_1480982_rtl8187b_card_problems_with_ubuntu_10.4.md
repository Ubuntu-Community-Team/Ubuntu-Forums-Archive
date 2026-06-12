---
title: "rtl8187b card problems with ubuntu 10.4"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by patch321 on 2010-05-12
i'm honestly almost to the point of giving up. i've tried everythink i could find and think of. i'm brand new to linux and not haveing a very good experience so far. apparently ubuntu is not picking up my wireless card no matter what i do. i'm incredibly desperate for help. i think i installed the driver right but nges or something that i used to install the driver is telling me that the hardware isn't present. everything is working fine on the windows side of my laptop. please help

---

### Post by chili555 on 2010-05-12
Please tell Dr. Chili all about it. Please open a terminal and do:```
lsmod | grep -e ndis -e 818
ndiswrapper -l
```You can copy and paste the terminal output to a text editor like gedit and post the result here. We can get this sorted out.

---

### Post by Dearhell on 2010-05-12
Try "rfkill list" to see if it is hard blocked: 

[http://ubuntuforums.org/showthread.php?t=1480381](http://ubuntuforums.org/showthread.php?t=1480381)

---

### Post by Crio on 2010-05-12
Please, post results of  
lsusb 

If your card has ID 0bda:8197 and you downloaded windows driver from Realtek site (I assume we are talking about ndiswrapper), you hit a bug in the Realtek inf file, which is easily fixed. See [http://ubuntuforums.org/showthread.php?t=1478782](http://ubuntuforums.org/showthread.php?t=1478782)

---

### Post by patch321 on 2010-05-12
patrick@ubuntu:~$ lsmod | grep -e ndis -e 818
rtl8187                53204  0 
mac80211              238128  1 rtl8187
led_class               3732  1 rtl8187
cfg80211              148386  2 rtl8187,mac80211
eeprom_93cx6            1765  1 rtl8187

patrick@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

patrick@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by patch321 on 2010-05-12
thanks to Crio i was able to get the ndiswrapper menu to show that my hardware is present where it wasn't before. so hopefully i'm making some progress. anything else from anybody. network manager also says that wireless is disabled and the option to check it is greyed out.

---

### Post by patch321 on 2010-05-12
bump :(

---

### Post by chili555 on 2010-05-12
> patrick@ubuntu:~$ rfkill list
0: phy0: Wireless LAN
Soft blocked: no
[COLOR="Red"]Hard blocked: yes[/COLOR]What kind of laptop is this? Is the wireless switch on?

---

### Post by patch321 on 2010-05-12
it's a toshiba satellite l-455. i've tried turning the card on and off on and off. nothing helps

---

### Post by patch321 on 2010-05-12
thanks for ur help btw!!!!

---

### Post by chili555 on 2010-05-12
If you move the wireless switch, is there no change in:```
rfkill list
```Please do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you move the switch and see if the kernel recognizes the key press. Also, please post:```
lsmod | grep tosh
```Thanks.

---

