---
title: "disabled ipv6, firefox STILL really slow."
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by Bit_Creepy on 2011-02-01
hi guys, since upgrading my system a couple of weeks ago to  2.6.35-24-generic, my internet speeds have been painfully slow. i'm  running 10.10 64-bit, GNOME 2.32.0.  i'm using firefox and i've read a  million times about disabling the ipv6 through the about:config  menu and changing a few other settings but nothing works. i've tried  uninstalling and reinstalling firefox and the problem still persists.  i've disabled ipv6 through the terminal and still nothing works. i've  even tried google chrome and still nothing. i also use opendns if this  makes any difference?

i use a dual boot system with windows 7 and i have no problems at all  with that, its actually really fast using windows 7, so what am i doing  wrong?

is there some sort of command i can type so that you can see exactly what my internet settings are?

thank you.

---

### Post by ripat on 2011-02-01
First possible fix: add this line in /etc/resolv.conf and tell us if it works faster:
```
options single-request
```

---

### Post by drdos2006 on 2011-02-01
This is from a previous thread I saved because it helped me.
My ISP had made some changes to the network and I had constant dropouts until I disconnected IPv6.

> 
You may be having connection issues because of IPv6 even though it shows an IPv4 connection. 

 How do I prove ipv6 has been successfully disabled
There seems to be much disagreement between distros regarding how ipv6 is disabled, even between different versions of the same distro. Rather than just follow instructions for disabling ipv6 for a given distro, I would like to also test that ipv6 is not used any more. Any software or executable that relies on ipv6, that I can use to confirm that ipv6 has been successfully disabled?

cat /proc/sys/net/ipv6/conf/*/disable_ipv6
They should all be 1.

Disabling IPV6 is best done via sysctl. In ubuntu, add the following to /etc/sysctl.conf

Code:

# Disable IPV6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
ifconfig should not mention an IPV6 address on any interface after you have rebooted.

IPV6 should still be considered in your security setup on your machine, just in case it is, for example, re-enabled after an upgrade etc.

To check if IPv6 is enabled, just simply use netstat:

Code:

netstat -tlv

If you see any "tcp6" entries, then IPv6 is not disabled.

You may be also having IPv6 problems in your browser.
For Firefox, type about:config in the browser bar.
Filter with network.dns
Change IPv6disabled to true
Restart Firefox.


regards

---

### Post by ripat on 2011-02-03
I would not recommend to disable ipv6. You might need it in the very near future.
[http://tech.slashdot.org/story/11/02/01/0036227/Last-Available-IPv4-Blocks-Allocated](http://tech.slashdot.org/story/11/02/01/0036227/Last-Available-IPv4-Blocks-Allocated)

And if you do, make a note to yourself of what you have done so to be able to reverse the process.

On modern linux systems (not only Ubuntu) the latest version of the glibc resolver sends two DNS request in parallel: a ipv4 (A) request and a ipv6 (Quad-A) request. This is a correct way of doing things. But some buggy ISP DNS servers or even some router devices do not respond properly and make the requests time out.

The most simple solution is to change the default DNS server in your lan's configuration. They are plenty of free and fast DNS servers around. For example Google's 8.8.8.8 and 8.8.4.4 or OpenDNS's 208.67.222.222 and 208.67.220.220. These servers respond correctly to valid ipv4+6 requests.

Another solution is to make the glibc resolver send the two requests sequentially instead of in parallel. To do that, add ***options single-request*** or ***single-request-reopen*** in /etc/resolv.conf

As that second solution may slowdown the resolving process a bit, I would rather change the DNS server.

---

