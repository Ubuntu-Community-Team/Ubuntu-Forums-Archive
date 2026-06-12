---
title: "Pptp vpn server issues"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by thepath on 2009-07-27
Hi all first of all!

I need some help, i have installed a PPTP VPN server in my dedicated box which runs on Ubuntu 8

using the following guide:

[http://swik.net/Ubuntu/Only+Ubuntu/Howto+setup+PPTP+server+(VPN)+on+Ubuntu+7.10/cdsjs](http://swik.net/Ubuntu/Only+Ubuntu/Howto+setup+PPTP+server+(VPN)+on+Ubuntu+7.10/cdsjs)


Now my problem is that when i connect (using windows xp sp3), i am having errors 721
I have tried 2 different configured dial connections, one for VPN with mchap security configuration and one with default protocols and with out mchap security configuration... Both same errors

also i'd like to mention that at the moment using SSH terminal and by pressing ps -aux i can see pptpd [myip:port] running which means that it thinks i am connected or something, i guess :confused:


also since i was unsure about my local ip even if i checked the ipconfig of my box i have tried with both localip/remote ip same and different, localip :127.0.0.1 and remoteip: my box's wap ip

---

### Post by ericab on 2009-07-28
ok solution is here:

[http://ubuntuforums.org/showthread.php?p=7598961#post7598961](http://ubuntuforums.org/showthread.php?p=7598961#post7598961)

look specifically at 'ufw masquerading'

---

