---
title: "Connecting to wireless modem a problem"
date: 2009-03-18
forum: Networking &amp; Wireless
---

### Post by Abhishek Sinha19850130 on 2009-03-18
Hi,

I have a TATA Indicom (India) EpiValley USB modem for internet connection. When I connect it to my computer it does not show anything that is connected. Also the instructions given in the manual does not yield me any results. What should I do? There is this command they have illustrated in the manual to type in terminal 
wvdialconf/etc/wvdial.conf   but it says bad command when I type so in the terminal. When I just type wvdialconf, after particular lines of codes I get permission denied to /etc/wvdial.conf

I am looking forward to a solution.

---

### Post by drtvasudevan on 2009-06-29
> **Abhishek Sinha19850130 said:**
> Hi,

. When I just type wvdialconf, after particular lines of codes I get permission denied to /etc/wvdial.conf

I am looking forward to a solution.

type sudo wvdialconf /etc/wvdial.conf

---

