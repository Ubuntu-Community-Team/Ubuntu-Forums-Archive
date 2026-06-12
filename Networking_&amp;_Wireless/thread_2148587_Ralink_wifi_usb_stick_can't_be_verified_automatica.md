---
title: "Ralink wifi usb stick can't be verified automatically when Ubuntu start."
date: 2013-05-25
forum: Networking &amp; Wireless
---

### Post by zhengtao on 2013-05-25
Now i can use the ralink wifi usb stick(i got help at [http://ubuntuforums.org/showthread.php?t=2147236](http://ubuntuforums.org/showthread.php?t=2147236), thanks **Chilly** and **Bucky Ball**), but every time i start ubuntu,  it can not identify the usb stick automatically. the "Enable wireless"  option in the internet icon is shut down automatically. I have to plug  the usb stick out and plug it in, then it will work. How can i solve it? Thanks.

---

### Post by chili555 on 2013-05-25
Please open a terminal and do:```
sudo su
echo rt2800usb >> /etc/modules
exit
```Now does it work as expected?

---

### Post by zhengtao on 2013-05-25
No, it did not work. When the ubuntu starts, the "enable wireless" option in the Internet panel is not choosed. I still have to select the option and plug the wifi usb stick out and in.

---

### Post by chili555 on 2013-05-26
Please restart your computer. Before you do anything else, please run:```
dmesg > zhengtao.txt
lsmod >> zhengtao.txt
iwconfig >> zhengtao.txt

```Start your wireless. Find the text file zhengtao.txt in your user directory and paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

Thanks.

---

### Post by zhengtao on 2013-05-26
I have done what you said and here the link is:[http://paste.ubuntu.com/5703627/](http://paste.ubuntu.com/5703627/).

Thanks.

---

### Post by praseodym on 2013-05-26
The driver is loaded but the card is "off". Check
```

rfkill list
```
Please also check in your BIOS if the network starts before the OS

---

### Post by zhengtao on 2013-05-26
The wireless is enabled in the BIOS.
When Ubuntu starts, before I do something-
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

After I choose the "enable wireless" in the Network panel-
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no


And after I plug the wifi usb stick in and out-
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by praseodym on 2013-05-27
Strange, its renaming phy0 to phy 1. Try "sudo rfkill unblock all" directly after booting with stick plugged.

---

### Post by zhengtao on 2013-05-28
zhengtao@android-AAA:~$ sudo rfkill unblock all
sudo: unable to resolve host android-AAA

---

