---
title: "internet issues with Ubuntu 10.04 LTS"
date: 2010-06-29
forum: Networking &amp; Wireless
---

### Post by no1colonel on 2010-06-29
I am a newbie (only had ubuntu for about 3 days now) and everything on it seems to work except for the internet. It is a wired connection through Time Warner and worked flawless with XP. It will not load any page except for google.com homepage and I cannot access any of the links in the search results of google. I know the internet works since google will load and I have done all that I can think of (ping and manually enter my connection) and nothing works. I am running the OS on a Acer Aspire M1610 desktop. Please help!

---

### Post by dineshs on 2010-06-29
pl post the output of
```
ifconfig -a
```
```
cat /etc/resolv.conf
```
and
```
ping -c3 4.2.2.1
```

---

### Post by no1colonel on 2010-06-29
I will give it a shot when I get home. If anyone else has any solutions or tips that I can try, please leave them also. Thanks.

---

### Post by no1colonel on 2010-06-29
Just tried the above solution and it did not work. Any other ideas/fixes would be much appreciated.

---

### Post by gareththered on 2010-06-29
Hi,

The idea is that you post the reply of those commands.  Remember that the more information you can give, the easier it will be for somebody to help.

Regards,

Gareth

---

### Post by macdo on 2010-06-29
What browser are you using?
If you type a web address (such as [http://ubuntuforums.org](http://ubuntuforums.org))into the address bar, does the page come up? If not, what error message appears?

---

### Post by no1colonel on 2010-06-30
results from terminal:
ifconfig -a  ===   HWaddr 00:1c:25:3e:88:6e
                          inet addr: 192.168.2.2   Bcast: 192.168.2.255   Mask: 255.255.255.0
                          inet6 addr:  fe80: :21c:25ff:fe3e:886e/64
 
cat /etc/reslov.conf ===   domain Belkin
                                      search Belkin
                                      nameserver 192.168.2.1
 
ping sent 3 packets and recieved 3 packets
 
 
i was using firefox web browser that came with the OS

---

### Post by gareththered on 2010-06-30
Try> ping [www.ubuntu.com]("http://www.ubuntu.com")and post the result.

If that works, then try browsing [www.ubuntu.com]("http://www.ubuntu.com") and post your results.

If the ping didn't work and complained of 'unknown host' then you have a DNS issue.

If it didn't work but showed an IP address then hung (stop it with Ctl-C) then you may have a routing issue.  Try > tracepath [www.ubuntu.com]("http://www.ubuntu.com")and post your results here.

Gareth

---

