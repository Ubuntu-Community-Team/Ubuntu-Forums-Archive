---
title: "ipv6 module not showing up, but ipv6 enabled in ifconfig"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2012-07-20
I can't cut and paste because my network is broken. However:

lsmod | grep ipv6 shows no results, yet there is an ipv6 address when I type ifconfig. 

How is this possible? Why is ifconfig trying to use ipv6 if my kernel doesn't support it? I am fairly certain this is the cause of my current networking issue.

Thanks a ton!!

---

### Post by kerryhall on 2012-07-20
Tried deleting ipv6 address with:
[http://tldp.org/HOWTO/Linux+IPv6-HOWTO/x1050.html](http://tldp.org/HOWTO/Linux+IPv6-HOWTO/x1050.html)

But I get:
SIOCDIFADDR: Cannot assign requested address

lol I can't even delete the ipv6 address from my machine :(

---

### Post by sanderj on 2012-07-23
> **kerryhall said:**
> I can't cut and paste because my network is broken. However:

lsmod | grep ipv6 shows no results, yet there is an ipv6 address when I type ifconfig. 

How is this possible? Why is ifconfig trying to use ipv6 if my kernel doesn't support it? I am fairly certain this is the cause of my current networking issue.

Thanks a ton!!

I checked, and there is no module "ipv4" either! ;-)

Apparently IPv6 is built into the kernel just like IPv4.

---

### Post by sanderj on 2012-07-23
> **kerryhall said:**
> 
lol I can't even delete the ipv6 address from my machine :(

Yes, you can, but why?

---

### Post by kerryhall on 2012-07-23
Alright, someone told me that the way to check for ipv6 support is to do an lsmod | grep ipv6 but I guess that's wrong. 

When I use an access point that doesn't have ipv6 enabled, I can connect fine, but I have problems connecting to this ipv6 access point.  I can connect to it fine via ipv6 on a macbook, so my guess is the issue is probably ipv6 in Ubuntu.

What debugging info should I provide here?

---

### Post by sanderj on 2012-07-23
Yes, in the old days there was an ipv6 module. But apparently not anymore.

To see if the AP provides IPv6, type this:

```
ifconfig
time wget www.google.com
time wget -6 www.google.com
time wget -4 www.google.com

```
and post the output here.

---

### Post by kerryhall on 2012-07-24
The first two commands time out, the third one manages to get an IP out of google.com, I get an http 200, then things time out.


Do you have a one liner to disable ipv6 for debugging? All my google results for that have been incorrect so far.

---

### Post by kerryhall on 2012-07-24
Tried this as well to disable ipv6:

[http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html](http://www.noobslab.com/2012/05/disable-ipv6-if-your-internet-is.html)

Still apparently get an ipv6 address in ifconfig. Tried rebooting after those instructions as well.

---

### Post by kerryhall on 2012-07-24
Commented out ipv6 lines in /etc/hosts, ifconfig still reports an ipv6 address. (after rebooting)

---

### Post by kerryhall on 2012-07-24
I realized I should be looking at the network manager lol. I changed ipv6 settings there to "ignore" and ifconfig reports no ipv6 address now.

It seems at least part of the problem is ipv6. Indeed, I can now ping google and at least get at response. However, ping times are quite slow (300 ms or so) compared with 2 ms on a MacBook Pro on the same AP. Sites load, but they take a bit of time (5 seconds for google) or sometimes longer.

Any ideas? I have noticed this issue as well

service networking restart
stop: Unknown instance:
networking stop/waiting

/etc/init.d/networking restart
(message about being deprecated)
* Reconfiguring.... [ OK ]

(messages are not exact as I do not have cut and paste but you get the idea)

---

### Post by lemming465 on 2012-08-07
On the "lsmod | grep ..." front, that detects dynamically loaded kernel modules.  In general, kernel components can be not built, built as modules, or statically built into the kernel binary.  Ubuntu kernels install with /boot/config* files which tell you what the setting was for each such option (n,m,y).  If you do```
grep IPV6 /boot/config-$(uname -r)
```it will probably show you *CONFIG_IPV6=y*, meaning your IPV6 support is statically built in.  This is necessary for scenarios such as PXE boots on IPV6-only networks, and represents a change from 4-5 years ago, when the default indeed used to be CONFIG_IPV6=m.

Personally, I prefer the iproute2 "ip -6 ..." commands to the legacy ipconfig, but tastes can vary.  Useful commands include```

ip address show
ip maddr show
ip -4 route show
ip -6 route show
```A large difference in ping round-trip-times given two different WIFI devices on the same access point might be due to some kind of suboptimal 802.11 a/b/g/n technology choice.  Can any of the clients dual-boot other operating systems, e.g. windows+linux or OS-X+Linux?  Comparing different OS's on the same hardware can help tease out what's a hardware issue and what's a software issue.

---

