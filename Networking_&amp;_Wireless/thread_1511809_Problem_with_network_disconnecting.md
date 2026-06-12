---
title: "Problem with network disconnecting"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by s0xt3r on 2010-06-17
Hi, I am running Ubuntu 9.04 and am using a Three dongle to connect to the internet (ppp0). The problem I have is that every now and then the network disconnects and I am unable to reconnect. In order to get it to reconnect I have to logout and log back in and then it works fine. My question is is there an easier way to do this without having to logout?

I try typing "/etc/init.d/network restart" but it doesn't seem to resolve the problem. Any help would be much appreciated. Thanks.

---

### Post by mörgæs on 2010-06-17
You probably need sudo in front of the restart command.

Maybe this will help:
[https://help.ubuntu.com/9.04/internet/C/index.html](https://help.ubuntu.com/9.04/internet/C/index.html)

---

### Post by s0xt3r on 2010-06-19
Thanks for the reply. I am root, or using sudo, when I try to restart the network. I read over the link you gave but theres not any information there about troubleshooting Mobile Broadband.

The fact that the problem is resolved if I logout or restart suggests that there is some service that simply needs restarting, I just have no idea what that service would be.

---

### Post by mörgæs on 2010-06-20
I can not give an exact answer,but have you tried a live boot with 9.10 or 10.04 and checked whether the problem is solved there? The support for 9.04 is running out in a few months, so you will have to upgrade soon anyway.

---

