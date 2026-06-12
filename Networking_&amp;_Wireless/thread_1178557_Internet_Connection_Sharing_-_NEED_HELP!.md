---
title: "Internet Connection Sharing - NEED HELP!"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by pro003 on 2009-06-04
Ok. Here's the trick. I have a wire from an ISP through which I connect to internet using PPPoE protocol and this should be adjusted on Linux (Ubuntu) box. While from this box the ethernet cable goes to switch and from switch the other machine needs to have access to internet. Also the Linux box should play a role of file server and as said an internet gateway. 

If you are not sure what I want to achieve, look at the picture:

[[IMG]http://img294.imageshack.us/img294/5134/snapshotw.th.png[/IMG]](http://img294.imageshack.us/my.php?image=snapshotw.png)

Basically, I want the first box to be under Ubuntu (Jaunty Jackalope -with Gnome), then I want to establish PPPoE connection to Internet using integrated NIC, and then I want to share (masquerade) internet from this box with other machines on network through / via PCI NIC > SWITCH.

English is not my native language, so sorry if I was maybe less clear.

Waiting for your help.

Thanks!

---

### Post by jerrrys on 2009-06-05
this may help you

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

if thats not what your looking for, i can only point you to this

[http://www.google.com/search?q=internet+connection+sharing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=internet+connection+sharing+ubuntu&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

