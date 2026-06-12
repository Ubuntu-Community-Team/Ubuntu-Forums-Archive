---
title: "Can't ssh or sftp --- ipv6?"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by ooboontoo86 on 2010-11-12
Hi all!

I'm (relatively) new to ubuntu.

I had version 9.10 and have just upgraded to 10.04. Originally I had some problems connecting to the internet after the upgrade (fixed by disabling ipv6 in firefox's about:config). But I can't SSH or SFTP. I get the following error message:

```
ssh: connect to host <hostname> port 22: Network is unreachable
Couldn't read packet: Connection reset by peer

```Also, my AWN weather applet has connectivity issues (I'm not sure if this is related?). Yet Skype works perfectly fine. Here's some of the things I remember trying:

I have installed openssh-server
I tried sshing after disabling the firewall
The following command returns the value 1 (i.e. ivp6 is disabled):
cat /proc/sys/net/ipv6/conf/all/disable_ipv6Could this still be an ipv6 issue?

EDIT: I can ping the address I'm trying to ssh to:
```
338 packets transmitted, 303 received, 10% packet loss, time 558077ms
rtt min/avg/max/mdev = 395.773/403.700/639.889/16.238 ms

```
If I ping myself:
```
89 packets transmitted, 89 received, 0% packet loss, time 88125ms
rtt min/avg/max/mdev = 2.632/9.459/281.480/36.266 ms

```

Thank you in advance for any help/suggestions!!!

Best, Ryan.

---

### Post by ooboontoo86 on 2010-11-12
After a full days work... I can now ssh and sftp, and my weather app is working.

It turns out the DNS server should be set as per the following guideline (it speeds your internet up):

[HTML]https://store.opendns.com/setup/device/ubuntu/[/HTML]

see also:
[HTML]http://ubuntuforums.org/showthread.php?t=1434732[/HTML]

I hope this is able to help someone else too.

Ryan.

---

