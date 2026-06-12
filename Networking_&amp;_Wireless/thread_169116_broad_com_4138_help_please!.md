---
title: "broad com 4138 help please!"
date: 2006-05-01
forum: Networking &amp; Wireless
---

### Post by xknight on 2006-05-01
please help ive tryed i can not seem to get my wireless network up for the life of me ive tryed reading the wiki and other forums some one please help
running ubuntu drapper  32 bit latest version on a HP dv5000 braodcom 4138 wireless amd turtion 64

> xknight@ubuntu:~/Desktop$ ndiswrapper -l
Installed ndis drivers:
netopoem                driver present, hardware present
xknight@ubuntu:~/Desktop$ sudo modprobe ndiswrapper
xknight@ubuntu:~/Desktop$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

eth0      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
xknight@ubuntu:~/Desktop$ iwlist  scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

sit0      Interface doesn't support scanning.

eth0      No scan results
xkxknight@ubuntu:~/Desktop$ iwlist eth0 scanning
eth0      No scan results
xknight@ubuntu:~/Desktop$
xknight@ubuntu:~/Desktop$ iwlist eth0 txpower
eth0      unknown transmit-power information.

xknight@ubuntu:~/Desktop$ iwlist eth0 accesspoint
eth0      Interface doesn't have a list of Peers/Access-Points

xknight@ubuntu:~/Desktop$
xknight@ubuntu:~/Desktop$ sudo ndiswrapper -m
modprobe config already contains alias directive

xknight@ubuntu:~/Desktop$



---

### Post by philipt on 2006-05-03
Check this tut out: [http://ubuntuforums.org/showthread.php?t=169542&highlight=4318](http://ubuntuforums.org/showthread.php?t=169542&highlight=4318)

---

