---
title: "Wireless Problem (As Always you see here, but interesting to me)"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by yaghiz on 2011-10-20
Hi guys.

I kinda have a different situation.

I'm (who has just started yesterday) using ubuntu 10.04

I'm completely new to this, i really liked it, but here is the thing.

Yesterday, i was at home and using my Wpa Encrypted wireless connection just fine.

Today i came to work, tried to connect my Wpa encrypted wireless network, but "wireless authentication required" window is looping despite i typed it correctly.

At home, everything is fine. 
But here, something's not.
(Oh yes, "working" is not fine)

As i said, i'm completely new, and it will be hard for you to help me because i know nearly nothing about ubuntu.

For example;
it took about 15 minutes to find the terminal :)
(You said something? I'm muscular babe!) :)

I know that someone is gonna come here and paste a link and say "hey check out this, this is gonna help"
And my problem will remain, because none of them is really MY problem. I've seen people that can not connect AT ALL.
I do connect at home. But whats wrong here?

---

### Post by shubham1 on 2011-10-20
this happens with me too sometimes
it can be because it cannot connect to the wifi

---

### Post by wildmanne39 on 2011-10-20
Hi, welcome to the forum! please post the results of these commands and we will see if we can figure it out, and you will need to be at your work location.
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
nm-tool
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
sudo iwlist scan
```
```
iwlist chan
```
```
dmesg | egrep 'net|eth|sky|sis|via|3c3|3c5|e100|8139|8169|acx|air|ath|atl|ar9|carl|atme|at7|herm|iwl|ipw|rtl8|r81|rt2|rt3|rt6|rt7|tg3|ssb|wl|b43|b44|ori|pri|p5|zd|ndis|wmi|ns8|wlan0'
```
post the results here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

