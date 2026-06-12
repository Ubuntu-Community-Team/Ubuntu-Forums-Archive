---
title: "Ubuntu slows down internet for the entire home network"
date: 2013-04-15
forum: Networking &amp; Wireless
---

### Post by 1gnition on 2013-04-15
When running Ubuntu on my PC, the wireless internet connection in the whole network (including in my PC) become extremely slow. It doesn't happen in Windows 7.

Please help me resolve this issue.

System specs:
- Ubuntu 12.04 LTS
Wireless adapter - DW1501 Wireless-N WLAN

What I tried:
- Disabling IPv6

---

### Post by 1gnition on 2013-04-15
Help :(

---

### Post by bigdes on 2013-04-15
What all have you been trying to run when you have been on ubuntu? I'm running a wireless printer/ tv/ dvd player/ 2 mobiles and haven't had too many issues. Have just had issues wth streaming blurays from my computer to my tv. But I don't think it wasn't an issue ubuntu just an issue with the network provider slowing the broadband down.  I take it you have carried out a speed test on ubuntu and on windows? if not here is a link to the site i use to check the broadband speed **[http://www.uswitch.com/broadband/speedtest/#speedTest](http://www.uswitch.com/broadband/speedtest/#speedTest)**. Maybe it will give you an idea if there is a problem with the internet and not ubuntu.

---

### Post by 1gnition on 2013-04-15
You got it all wrong. **The problem is with ubuntu**. There is not a single doubt about it. The moment I boot into ubuntu other users of the network start to complain. This is consistent and was checked many times. The internet slows down drastically to a point it is not usable. On my machine it almost doesn't work at all.

So please, if someone can help me I will appreciate it. I really want to work with ubuntu but this problem prevents me from doing it.

---

### Post by ahallubuntu on 2013-04-15
~

---

### Post by giliinc1 on 2013-04-15
do a speed test without ubuntu booted
then with ubuntu running
then disconnect from wifi or ethernet from ubuntu machine

---

### Post by Iowan on 2013-04-15
Unlikely cause: Verify the wireless IP address isn't a duplicate.

---

### Post by Cheesehead on 2013-04-15
1) Check the router configuration. You're really sure it not the router, I understand. Check it anyway.

2) Did you manually configure Ubuntu networking? If so, tell us what you did and be prepared to undo it.

3) Install the package 'jnettop', and run it while connected. It will tell you what application is using all your bandwidth, if indeed some application is doing that.

---

### Post by permittivity22 on 2013-04-16
I'm game with the duplicate IP but you can do some things to make sure your ubuntu truly isn't doing a huge amount of traffic.

One thing I'd do is look at where and what all traffic is going in/out of your ubuntu machine:  netstat -an  is something good to start with.
Another one is to just generally look at packet/data counts:  ifconfig -a  and look at the packet counts.  Just do some general math an see if things are really what you think they are.
Another thing, did you install some server stuff that is fighting with your router.  Maybe you have a dhcpd server running on your Ubuntu machine or something like that?

---

### Post by dodgydavec on 2013-04-21
I am having exactly the same problem. Nothing is taking up any bandwidth. No duplicate addresses. Just everytime I boot into Ubuntu the entire wireless network slows down to an absolute crawl, except for the laptop running Ubuntu.

---

### Post by dodgydavec on 2013-04-25
I have managed to fix mine. Although I don't have the same Wireless LAN controller, mine being a BCM4313, Ubuntu does offer a proprietary driver for it. When I use the proprietary driver, my whole wireless network suffers. When I don't, everything works fine. So, try deactivating the additional driver then reboot your computer.

---

### Post by EdgyPowell on 2013-08-18
I am suffering from the exact same problem, I am planning on dropping Ubuntu completely if I continue to run into anymore problems like this as I am fed up with it.

---

### Post by darinsson on 2013-09-22
I have also this problem , but only for my Lenovo e-135 all the others  does work as they should......

---

### Post by RockStone9 on 2013-09-23
I had the same problem. I fixed it by disabling STA in additional drivers and then installing WinXP drivers via ndiswrapper...

---

