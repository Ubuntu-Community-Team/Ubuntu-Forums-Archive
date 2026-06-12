---
title: "ethernet"
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by ololad8 on 2006-07-10
hey whats up ubuntians

i have just installed ubuntu and was really impressed but everything groud to a halt when i realized that my ethernet was recognized but not working. i know you've probably heard this a million times but i have an nforce 430 with 6100 video. i have verizon dsl with pppoe configured on a dlink router. do i have to install nvidia nforce drivers? if so how? (because i already tried)  once agian thats verizon dsl and a dlink router with pppoe configured with dhcp

---

### Post by mogelhead on 2006-07-11
Hi ololad8,

There is a thread called ["Wired Ethernet Troubleshooting Process"]("http://ubuntuforums.org/showthread.php?t=87643") on this forum, you might wanto check it out.

A while ago when I was using the kubuntu 5.10 Live CD, on some computers the network card was identified but not enabled, I had to do this:
```
 sudo ifconfig eth0 up
```
That will get the network card started, but next time you start the computer you have to do the same.

So it might be that you have to change a setting so it automatically enables every time the computer starts, try this short guide on the Ubuntu Wiki: [NetworkNotEnabled]("https://wiki.ubuntu.com/NetworkNotEnabled")

---

### Post by ololad8 on 2006-07-11
thank you

---

