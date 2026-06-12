---
title: "bad PPPoE connection with 10.04, fine with 8.04?"
date: 2010-11-05
forum: Networking &amp; Wireless
---

### Post by MattThLinuxNewb on 2010-11-05
Hi,
I connect to the internet via PPPoE due to the internet setup where I live. I had no problem setting it up in Ubuntu 10.04 but it has a strange problem where most webpages do not load properly. With most webpages I just get the the title with a blank page that is "loading" indefinitely. A few select pages load with text and no images. It is always the same pages in each case. However when I boot into Ubuntu 8.04 or WinXP, everything works fine; all web pages load normally. Which points to a problem with my Lucid configuration.
Any ideas what this might be or how to diagnose this problem?
Thanks

---

### Post by dineshs on 2010-11-05
If you are using network manager to configure DSL connection .Right click NM icon -edit connections-click DSl-select your connection and edit-set MTU to 1492 and apply.Restart PC and see if pages are loading
Note:You may try 1462,1472...(To findout MTU value try this link
[http://ubuntuforums.org/showthread.php?t=872346](http://ubuntuforums.org/showthread.php?t=872346)
You may also try disabling ipv6 
Ref :   [http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can](http://support.mozilla.com/en-US/kb/Firefox+cannot+load+websites+but+other+programs+can)

---

### Post by MattThLinuxNewb on 2010-11-05
Thanks a lot. After a lot of mucking around that fixed it. I found the mtu value on hardy by going
```
ifconfig ppp0
```
and set it to that on lucid and it worked.
Turns out ipv6 was also enabled so I disable it by following this guide
[http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html](http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html)

---

### Post by dineshs on 2010-11-05
> and set it to that on lucid and it worked.
Did you set the value in Network manager ?Can you explain?

---

### Post by MattThLinuxNewb on 2010-11-05
No, with
```
sudo ifconfig ppp0 mtu 1480
```
This will reset after rebooting however so it needs to be added to a startup config file which I am yet to do.

---

### Post by harvindercs on 2011-06-08
> **MattThLinuxNewb said:**
> No, with
```
sudo ifconfig ppp0 mtu 1480
```
This will reset after rebooting however so it needs to be added to a startup config file which I am yet to do.
can you tell me how did you set it permanently seems like i have similar problem :)

---

### Post by dineshs on 2011-06-08
If you are using network manager click on  network manager icon-edit connections-DSL tab -select the connection-edit-wired tab-set MTU to say 1492 and apply.
If you are connecting via pon command (pppoeconf) edit /etc/ppp/peers/dsl-provider

---

